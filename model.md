# Описание сущностей базы данных

Ниже приведено описание таблиц базы данных.

Общие принципы:

- Почти в каждой таблице присутствуют служебные поля: idkart, dttmcr, dttmup, dttmcl, idispl. Они стандартные.

## Темы (theme)

Справочник тем тестов. Крупные разделы, на которые могут быть разделены тесты. Название темы небольшое, описание - внутреннее поле, может быть довольно длинным. Для каждой темы задаётся небольшое изображение (иконка). Темы могут быть направлениями деятельности организации (для удобства).

Поле `order_number` позволяет задать произвольный порядок, в котором должен выводиться список тем.

| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | serial | NOT NULL | Идентификатор записи |
| dttmcr | timestamptz | NOT NULL DEFAULT now() | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| theme | text | NOT NULL REFERENCES theme(idkart) | Название темы |
| image_id | jsonb | NOT NULL | ID файла изображения |
| description | text | | Описание |
| is_public | boolean | | Опубликовано ли |
| order_number | integer | | Порядковый № при выводе на страницу |

## Категории (category)

Справочник категорий внутри каждой из тем. Это более мелкое разделение тестов на разделы. У категории должна быть иконка. Поле `order_number` позволяет задать произвольный порядок, в котором должен выводиться список категорий.

| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | serial | NOT NULL | Идентификатор записи |
| dttmcr | timestamptz | NOT NULL DEFAULT now() | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| theme_fk | integer | NOT NULL REFERENCES theme(idkart) | FK на ID темы |
| category | text | NOT NULL | Категория |
| description | text |  | Описание |
| is_public | boolean |  | Опубликовано ли |
| order_number | integer |  | Порядковый № при выводе на страницу |
| image_id | jsonb |  | ID файла изображения |

## Группы статусов (state_group)

Справочник групп статусов.
Статусы нужны для отслеживания состояний каких-либо сущностей. Группы статусов позволяют разделить статусы, которые могут иметь одни и те же названия, по разным сущностям.

| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | serial | NOT NULL | Идентификатор записи |
| dttmcr | timestamptz | NOT NULL DEFAULT now() | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| name | text | NOT NULL UNIQUE | Название группы статусов |
| description | text |  | Описание |

## Статусы (state)

Справочник статусов.
Каждый статус относится к какой-либо группе статусов. Статус обозначает состояние объекта: "Новый", "В процессе", "Опубликован", "Закрыт" и т.д.

| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | serial | NOT NULL | Идентификатор записи |
| dttmcr | timestamptz | NOT NULL DEFAULT now() | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| state_group_fk | integer | NOT NULL REFERENCES state_group(idkart) | FK на ID группы статусов |
| name | text | NOT NULL | Название статуса |
| description | text |  | Описание |

## Професссии (profession)

Справочник профессий. Используется в таблице пользователей.

| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | serial | NOT NULL | Идентификатор записи |
| dttmcr | timestamptz | NOT NULL DEFAULT now() | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| name | text | NOT NULL UNIQUE | Профессия |
| description | text |  | Описание |

## Грейды (grade)

Справочник грейдов - условных уровней, экзамены на достижение которых сдают пользователи, проходя тесты.
Например, для программистов это Junior, Middle, Senior, STO и др.

| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | serial | NOT NULL | Идентификатор записи |
| dttmcr | timestamptz | NOT NULL DEFAULT now() | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| name | text | NOT NULL UNIQUE | Название грейда |
| description | text |  | Описание |

## Роли (role)

Справочник ролей - званий, которые не являются грейдами, а существуют параллельно и для разных профессий. Например: "Наставник", "Тимлид" и др.

| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | serial | NOT NULL | Идентификатор записи |
| dttmcr | timestamptz | NOT NULL DEFAULT now() | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| name | text | NOT NULL UNIQUE | Название роли |
| description | text |  | Описание |

## Типы вопросов (question_type)

Справочник типов вопросов. Тип вопроса определяет, какой будет внешний вид и структура вопроса: будет это или выбор вариантов из предложенных, или сбор правильной последовательности или другой тип выбора правильных ответов.
Поле `config` может содержать настройки, используемые на фронтенде для корректного отображения вопроса.

| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | serial | NOT NULL | Идентификатор записи |
| dttmcr | timestamptz | NOT NULL DEFAULT now() | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| code | text | NOT NULL UNIQUE | Код типа |
| name | text | NOT NULL UNIQUE | Профессия |
| description | text |  | Описание |
| config | jsonb |  | Настройки для фронтенда |
| is_public | boolean |  | Опубликовано ли |

## Пользователи (users)

Список пользователей приложения. Система поддерживает прямое заведение пользователей и репликацию из CRM-системы.
Кроме типичных полей, таблица содержит группу специальных служебных полей, обеспечивающих аутентификацию через социальные сети и связь с данными служебной библиотеки.

| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | serial | NOT NULL | Идентификатор записи |
| dttmcr | timestamptz | NOT NULL DEFAULT now() | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| last_name | text |  | Фамилия |
| first_name | text | NOT NULL | Имя |
| middle_name | text |  | Отчество |
| nick | text |  | Никнейм |
| bdate | date |  | Дата рождения |
| email | text | NOT NULL UNIQUE | E-mail адрес |
| password_hash | text | NOT NULL | Хеш пароля |
| profession_fk | integer | REFERENCES profession(idkart) | FK на запись в таблице `profession` |
| pdb_data | jsonb |  | JSONB данных библиотеки PDB |
| uuid_pdb | uuid |  | Общий UUID пользователя |
| pdb_hash | text |  | Хэш данных библиотеки PDB |
| contract_data | jsonb |  | Данные соцсетей для аутентификации |

## Подразделения (division)

Список подразделений компании. Данные передаются с помощью репликации из базы CRM.

| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | serial | NOT NULL | Идентификатор записи |
| dttmcr | timestamptz | NOT NULL DEFAULT now() | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| code | text | NOT NULL UNIQUE | Код |
| city | text |  | Город |
| name | text | NOT NULL UNIQUE | Название |
| description | text |  | Описание |
| email | text |  | Общий E-mail подразделения |

## Группы (group)

Внутри подразделений могут быть группы сотрудников со своими руководителями.

| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | serial | NOT NULL | Идентификатор записи |
| dttmcr | timestamptz | NOT NULL DEFAULT now() | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| division_fk | int | NOT NULL REFERENCES division(idkart) | FK на запись в таблице `division` |
| name | text | NOT NULL | Название |
| description | text |  | Описание |
| user_fk | int | NOT NULL | Руководитель группы |

## Сотрудники (employee)

Сотрудники компании, относящиеся к определённым подразделениям компании. 
У сотрудника есть рабочий телефон, email и должность в компании.

| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | serial | NOT NULL | Идентификатор записи |
| dttmcr | timestamptz | NOT NULL DEFAULT now() | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| division_fk | int | NOT NULL REFERENCES division(idkart) | FK на запись в таблице `division` |
| group_fk | int | REFERENCES group(idkart) | FK на запись в таблице `group` |
| user_fk | int | NOT NULL REFERENCES users(idkart) | FK на запись в таблице `users` |
| profession_fk | int | NOT NULL REFERENCES profession(idkart) | Должность сотрудника |
| work_email | text |  | Рабочий email |
| email_signature | text |  | Подпись в email |
| work_phone | text |  | Рабочий телефон |

## Тесты (test)

Список тестов, которые должны проходить пользователи. Тесты относятся к определённым категориям, могут иметь свои настройки, статус и др. параметры.

| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | serial | NOT NULL | Идентификатор записи |
| dttmcr | timestamptz | NOT NULL DEFAULT now() | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| category_fk | integer | NOT NULL REFERENCES category(idkart) | FK на запись в таблице `category` |
| name | text | NOT NULL | Профессия |
| description | text |  | Описание |
| test_config | jsonb |  | Настройки теста |
| is_public | boolean |  | Опубликовано ли |
| state_fk | integer | NOT NULL REFERENCES state(idkart) | FK на запись в таблице `state` |
| amount_for_attempt | integer | DEFAULT 10 | Min кол-во вопросов для прохождения |

## Вопросы (question)

Список вопросов для тестов, определённых в таблице `test`. 
У каждого вопроса есть тип и текст, может быть изображение и описание.

| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | serial | NOT NULL | Идентификатор записи |
| dttmcr | timestamptz | NOT NULL DEFAULT now() | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| test_fk | integer | NOT NULL REFERENCES test(idkart) | FK на ID теста |
| question_type_fk | integer | NOT NULL REFERENCES question_type(idkart) | FK на ID типа вопроса |
| question | text | NOT NULL | Текст вопроса |
| image_id | jsonb |  | ID файла изображения |
| description | text |  | Описание |
| is_public | boolean |  | Опубликовано ли |

## Варианты (variant)

Списки вариантов ответов для вопросов из таблицы `question`. Список вариантов зависит от типа вопроса. У вариантов может быть номер (поле `number`), текст, изображение. Для типа игры "Сопоставление пар" используется флаг `is_compair`, который указывает на то, что этот вариант является сопроставляемым.

| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | serial | NOT NULL | Идентификатор записи |
| dttmcr | timestamptz | NOT NULL DEFAULT now() | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| question_fk | integer | NOT NULL REFERENCES question(idkart) | FK на ID вопроса |
| number | integer |  | № среди вариантов |
| text_variant | text |  | Текст варианта |
| image_id | jsonb |  | ID файла изображения |
| is_compair | boolean |  | Является ли этот вариант сопоставлением |

## Правильные варианты (right_variant)

Таблица, куда сохраняются правильные варианты из таблицы вариантов для конкретных вопросов. Ввод правильных вариантов зависит от типа вопроса. Такая структура облегчает проверку правильности ответов пользователей.

| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | serial | NOT NULL | Идентификатор записи |
| dttmcr | timestamptz | NOT NULL DEFAULT now() | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| question_fk | integer | NOT NULL REFERENCES question(idkart) | FK на ID вопроса |
| text_value | text |  | Текст варианта |
| variant_fk | integer | NOT NULL REFERENCES variant(idkart) | FK на ID варианта |

## Попытки (attempt)

Попытки - это запуски тестов пользователями, "игры". Во время прохождения теста данные записи обновляются, а именно поля `finished_at` и `right_answers_amount`. 

| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | serial | NOT NULL | Идентификатор записи |
| dttmcr | timestamptz | NOT NULL DEFAULT now() | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| finished_at | timestamptz |  | Момент завершения теста |
| test_fk | integer | NOT NULL REFERENCES test(idkart) | FK на запись в таблице `test` |
| test_questions_amount | smallint | NOT NULL DEFAULT 10 | Кол-во вопросов в тесте |
| right_answers_amount | smallint | NOT NULL DEFAULT 0 | Кол-во правильных ответов на вопросы |

## Ответы на вопросы тестов (attempt_answer)

В таблице фиксируются ответы пользователей на каждый из вопросов тестов. Данные используются для обновления таблицы `attempt`.

| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | serial | NOT NULL | Идентификатор записи |
| dttmcr | timestamptz | NOT NULL DEFAULT now() | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| attempt_fk | integer | NOT NULL REFERENCES atempt(idkart) | FK на запись в таблице `attempt` |
| question_fk | integer | NOT NULL REFERENCES question(idkart) | FK на запись в таблице `question` |
| user_answer | jsonb |  | Ответ пользователя |
| is_right | boolean | DEFAULT false | Правильный ли ответ |

## Экзамены (exam)

Справочник экзаменов или квалификаций, которые должны проходить пользователи во время сессий. 
Экзамены относятся к определённым темам и создаются на конкретный грейд или роль. Экзамен имеет краткий код, название и список тестов, закреплённых для прохождения пользователями. В поле `result` записывается % вопросов, на которые пользователи должны ответить правильно, чтобы экзамен считался пройденным.

Экзамены могут иметь бейджики - иконки для списка достижений, которые выводятся на страницу прогресса пользователя.

| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | serial | NOT NULL | Идентификатор записи |
| dttmcr | timestamptz | NOT NULL DEFAULT now() | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| grade_fk | integer | REFERENCES grade(idkart) | FK на запись в таблице `grade` |
| role_fk | integer | REFERENCES role(idkart) | FK на запись в таблице `role` |
| code | text | NOT NULL | Буквенно-цифровой код экзамена |
| name | text | NOT NULL | Название экзамена |
| description | text |  | Описание |
| test_list | integer[] |  | Список ID тестов |
| result | smallint | NOT NULL DEFAULT 100 | Значение в % для успеха прохождения |
| is_active | boolean | DEFAULT true | Действующий ли экзамен |
| theme_fk | integer | REFERENCES theme(idkart) | FK на запись в таблице `theme` |
| image_id | jsonb |  | ID файла бейджа за экзамен |

## Сессии (session)

Сессии - это экзамены, назначенние определённым пользователям для прохождения в заданный период времени. Если пользователь успевает успешно пройти заданные тесты в указанный период на нужный уровень, то считается, что он выполнил грейд или роль. За каждой сессией закрепляется ментор - пользователь-руководитель.

| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | serial | NOT NULL | Идентификатор записи |
| dttmcr | timestamptz | NOT NULL DEFAULT now() | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| exam_fk | integer | NOT NULL REFERENCES exam(idkart) | FK на запись в таблице `exam` |
| mentee_fk | integer | NOT NULL REFERENCES users(idkart) | FK на запись в таблице `users` (кто проходит сессию) |
| date_start | date | NOT NULL | Дата начала сессии |
| date_end | date | NOT NULL | Дата окончания сессии |
| actual_result | smallint | NOT NULL DEFAULT 0 | Текущий результат пользователя |
| is_completed | boolean | NOT NULL DEFAULT false | Выполнена ли сессия |
| mentor_fk | integer | REFERENCES users(idkart) | FK на запись в таблице `users` (наставник) |

## Группа конфигураций (config_group)

Группы, объединяющие отдельные настройки (конфигурации) по отношению к чему-либо.

| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | serial | NOT NULL | Идентификатор записи |
| dttmcr | timestamptz | NOT NULL DEFAULT now() | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| name | text | NOT NULL UNIQUE | Название группы |
| description | text |  | Описание |

## Конфигурации (config)

Непосредственно конфигурации - параметры, состоящие из пары "ключ" - "значение". Это могут быть токены аутентификации, константы для приложения идругие общие настройки. В поле `end_date` может быть записана дата, когда истекает срок годности параметра, что позволяет своевременно отслеживать этот момент.

| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | serial | NOT NULL | Идентификатор записи |
| dttmcr | timestamptz | NOT NULL DEFAULT now() | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| config_group_fk | integer | REFERENCES config_group(idkart) | FK на запись в таблице `config_group` |
| key | text | NOT NULL | Название параметра |
| value | text |  | Значение параметра |
| description | text |  | Описание |
| end_date | date |  | Дата окончания действия параметра |

## Лог (log)

Таблица для логирования изменений в таблицах: UPDATE, DELETE. В данной таблице записывается JSONB-объект исходной строки с данными. По триггеру планируется фиксировать в таблицу log_fields конкретные изменения данных в сравнении с данными в таблице в момент изменения.

| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | bigserial | NOT NULL | Идентификатор записи |
| dttmcr | timestamptz | NOT NULL DEFAULT now() | ДатаВремя создания записи |
| idispl | integer | | ID создателя записи |
| data_old | jsonb |  | JSONB-объект исходных данных |
| action | text | NOT NULL | Действие с данными |
| table_name | text | NOT NULL | Название таблицы |
| table_idkart | int | DEFAULT 0 | ID записи в таблице |

## Изменение полей (log_fields)

Таблица, в которой фиксируются поля конкретной записи таьлицы, указанной в таблице `log`. Записывается предыдущее значение поля и новое, что позволяет отслеживать изменения значений в таблицах пользователями.

| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | bigserial | NOT NULL | Идентификатор записи |
| dttmcr | timestamptz | NOT NULL DEFAULT now() | ДатаВремя создания записи |
| idispl | integer | | ID создателя записи |
| log_id | bigint | NOT NULL REFERENCES log(idkart) | ID записи в таблице `log` |
| data_old | jsonb |  | Предыдущее значение поля |
| data_new | jsonb |  | Новое значение поля |
