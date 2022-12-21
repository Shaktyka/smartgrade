# Скрипты создания схему БД в сервисе dbdiagram

// Профессии
Table profession as PR {
  idkart int [pk, increment, not null, PK]
  dttmcr timestamptz [not null]
  dttmup timestamptz
  dttmcl timestamptz
  idispl int [ref: > U.idkart]
  name text [not null, unique]
  description text
}

// Пользователи
Table users as U {
  idkart int [pk, increment, not null, PK]
  dttmcr timestamptz [not null]
  dttmup timestamptz
  dttmcl timestamptz
  idispl int [ref: > U.idkart]
  last_name text
  first_name text [not null]
  middle_name text
  nick text 
  bdate date
  email text [not null, unique]
  password_hash text [not null]
  profession_fk int [ref: > PR.idkart]
  pdb_data jsonb
  uuid_pdb uuid
  pdb_hash text
  contract_data jsonb
}

// Города
Table city as CI {
  idkart int [pk, increment, not null, PK]
  dttmcr timestamptz [not null]
  dttmup timestamptz
  dttmcl timestamptz
  idispl int [ref: > U.idkart]
  name text [not null, unique]
  description text
}

// Подразделения
Table division as D {
  idkart int [pk, increment, not null, PK]
  dttmcr timestamptz [not null]
  dttmup timestamptz
  dttmcl timestamptz
  idispl int [ref: > U.idkart]
  code text
  city_fk int [ref: > CI.idkart]
  name text [not null, unique]
  description text
  email text
}

// Группы
Table group as G {
  idkart int [pk, increment, not null, PK]
  dttmcr timestamptz [not null]
  dttmup timestamptz
  dttmcl timestamptz
  idispl int [ref: > U.idkart]
  division_fk int [ref: > D.idkart]
  name text [not null, unique]
  description text
  user_fk int [ref: > U.idkart]
}

// Сотрудники
Table employee as E {
  idkart int [pk, increment, not null, PK]
  dttmcr timestamptz [not null]
  dttmup timestamptz
  dttmcl timestamptz
  idispl int [ref: > U.idkart]
  division_fk int [not null, ref: > D.idkart]
  group_fk int [ref: > G.idkart]
  user_fk int [not null, ref: > U.idkart]
  work_email text
  email_signature text
  work_phone text
  profession_fk int [ref: > PR.idkart]
}

// Группы статусов
Table state_group as SG {
  idkart int [pk, increment, not null, PK]
  dttmcr timestamptz [not null]
  dttmup timestamptz
  dttmcl timestamptz
  idispl int [ref: > U.idkart]
  name text [not null, unique]
  description text
}

// Статусы
Table state as S {
  idkart int [pk, increment, not null, PK]
  dttmcr timestamptz [not null]
  dttmup timestamptz
  dttmcl timestamptz
  idispl int [ref: > U.idkart]
  state_group_fk int [not null, ref: > SG.idkart]
  name text [not null, unique]
  description text
}

// Темы тестов
Table theme as TM {
  idkart int [pk, increment, not null, PK]
  dttmcr timestamptz [not null]
  dttmup timestamptz
  dttmcl timestamptz
  idispl int [ref: > U.idkart]
  theme text [not null, unique]
  image_id jsonb [not null]
  description text
  order_number int
  is_public boolean
}

// Категории тестов
Table category as C {
  idkart int [pk, increment, not null, PK]
  dttmcr timestamptz [not null]
  dttmup timestamptz
  dttmcl timestamptz
  idispl int [ref: > U.idkart]
  theme_fk int [not null, ref: > TM.idkart]
  category text [not null, unique]
  description text
  order_number int 
  image_id jsonb
  is_public boolean
}

// Тест (набор вопросов)
Table test as T {
  idkart int [pk, increment, not null, PK]
  dttmcr timestamptz [not null]
  dttmup timestamptz
  dttmcl timestamptz
  idispl int [ref: > U.idkart]
  category_fk int [not null, ref: > C.idkart]
  name text [not null, unique] // название теста
  description text // описание
  test_config jsonb
  is_public boolean // показывать всем, если публичный
  state_fk int [not null, ref: > S.idkart]
  amount_for_attempt int [default: 10]
}

// Тип вопроса
Table question_type as QT {
  idkart int [pk, increment, not null, PK]
  dttmcr timestamptz [not null]
  dttmup timestamptz
  dttmcl timestamptz
  idispl int [ref: > U.idkart]
  code text [not null, unique]
  name text [not null, unique]
  description text
  config jsonb
  is_public boolean
}

// Вопросы теста
Table question as Q {
  idkart int [pk, increment, not null, PK]
  dttmcr timestamptz [not null]
  dttmup timestamptz
  dttmcl timestamptz
  idispl int [ref: > U.idkart]
  test_fk int [not null, ref: > T.idkart]
  question_type_fk int [not null, ref: > QT.idkart]
  question text [not null]
  image_id jsonb
  description text
  is_public boolean
}

// Варианты ответов
Table variant as V {
  idkart int [pk, increment, not null, PK]
  dttmcr timestamptz [not null]
  dttmup timestamptz
  dttmcl timestamptz
  idispl int [ref: > U.idkart]
  question_fk int [not null, ref: > Q.idkart]
  number int 
  text_variant text
  image_id jsonb
  is_compair boolean
}

// Правильные варианты ответов
Table right_variant as RV {
  idkart int [pk, increment, not null, PK]
  dttmcr timestamptz [not null]
  dttmup timestamptz
  dttmcl timestamptz
  idispl int [ref: > U.idkart]
  question_fk int [not null, ref: > Q.idkart]
  text_value text 
  variant_fk int [ref: > V.idkart]
}

// Запуски тестов (попытки)
Table attempt as AT {
  idkart int [pk, increment, not null, PK]
  dttmcr timestamptz [not null]
  dttmup timestamptz
  dttmcl timestamptz
  idispl int [ref: > U.idkart]
  finished_at timestamptz
  test_fk int [not null, ref: > T.idkart]
  test_questions_amount smallint [not null, default: 10]
  right_answers_amount smallint [not null, default: 0]
}

// Ответы на тесты
Table attempt_answer as AA {
  idkart int [pk, increment, not null, PK]
  dttmcr timestamptz [not null]
  dttmup timestamptz
  dttmcl timestamptz
  idispl int [ref: > U.idkart]
  attempt_fk int [not null, ref: > AT.idkart]
  question_fk int [not null, ref: > Q.idkart]
  user_answer jsonb
  is_right boolean [not null, default: false]
}

// Логирование изменения данных в таблицах
Table log as LG {
  idkart bigint [pk, increment, not null, PK]
  dttmcr timestamptz [not null]
  idispl int [ref: > U.idkart]
  action text [not null]
  table_name text
  table_idkart int
  data_old jsonb
}

// Изменение данных по полям
Table log_fields as LF {
  idkart bigint [pk, increment, not null, PK]
  dttmcr timestamptz [not null]
  idispl int [ref: > U.idkart]
  log_id bigint [not null, ref: > LG.idkart]
  data_old jsonb
  data_new jsonb
}

// Грейды
Table grade as GR {
  idkart int [pk, increment, not null, PK]
  dttmcr timestamptz [not null]
  dttmup timestamptz
  dttmcl timestamptz
  idispl int [ref: > U.idkart]
  name text [not null, unique]
  description text
}

// Роли
Table role as RO {
  idkart int [pk, increment, not null, PK]
  dttmcr timestamptz [not null]
  dttmup timestamptz
  dttmcl timestamptz
  idispl int [ref: > U.idkart]
  name text [not null, unique]
  description text
}

// Экзамены
Table exam as EX {
  idkart int [pk, increment, not null, PK]
  dttmcr timestamptz [not null]
  dttmup timestamptz
  dttmcl timestamptz
  idispl int [ref: > U.idkart]
  theme_fk int [ref: > TM.idkart]
  grade_fk int [ref: > GR.idkart]
  role_fk int [ref: > RO.idkart]
  code text [not null]
  name text [not null, unique]
  description text
  test_list int[] [not null]
  result smallint [not null]
  image_id jsonb 
  is_active boolean [not null, default: true]
}

// Сессии (аттестации)
Table session as SE {
  idkart int [pk, increment, not null, PK]
  dttmcr timestamptz [not null]
  dttmup timestamptz
  dttmcl timestamptz
  idispl int [ref: > U.idkart]
  exam_fk int [not null, ref: > EX.idkart]
  mentee_fk int [not null, ref: > U.idkart]
  mentor_fk int [not null, ref: > U.idkart]
  date_start date [not null]
  date_end date [not null]
  actual_result smallint [not null, default: 0]
  is_completed boolean [not null, default: false]
}

// Группа конфигов
Table config_group as CG {
  idkart int [pk, increment, not null, PK]
  dttmcr timestamptz [not null]
  dttmup timestamptz
  dttmcl timestamptz
  idispl int [ref: > U.idkart]
  name text [not null, unique]
  description text
}

// Конфиги
Table config as CF {
  idkart int [pk, increment, not null, PK]
  dttmcr timestamptz [not null]
  dttmup timestamptz
  dttmcl timestamptz
  idispl int [ref: > U.idkart]
  config_group_fk int [not null, ref: > CG.idkart]
  key text [not null]
  value text 
  description text
  end_date date
}
