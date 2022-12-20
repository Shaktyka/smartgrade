# Описание сущностей базы данных

Ниже приведено описание таблиц базы данных.

## Темы (theme)

Темы для главной страницы приложения. Крупные разделы, на которые могут быть разделены тесты. Название темы небольшое, описание - внутреннее поле, может быть довольно длинным. Для каждой темы задаётся изображение. Темы могут быть направлениями деятельности организации (для удобства).

| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | integer | | Идентификатор записи |
| dttmcr | timestamptz | | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| theme | text | | Название темы |
| image_id | jsonb | | ID файла изображения |
| description | text | | Описание |
| is_public | boolean | | Опубликовано ли |
| order_number | integer | | Порядковый № при выводе на страницу |

## Категории (category)



| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | integer | | Идентификатор записи |
| dttmcr | timestamptz | | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| theme_fk | integer | NOT NULL | FK на ID темы |
| category | text | NOT NULL | Категория |
| description | text |  | Описание |
| is_public | boolean |  | Опубликовано ли |
| order_number | integer |  | Порядковый № при выводе на страницу |
| image_id | jsonb |  | ID файла изображения |

## Группы статусов (state_group)



| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | integer | | Идентификатор записи |
| dttmcr | timestamptz | | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| name | text | NOT NULL UNIQUE | Название группы статусов |
| description | text |  | Описание |

## Статусы (state)



| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | integer | | Идентификатор записи |
| dttmcr | timestamptz | | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| state_group_fk | integer | NOT NULL | FK на ID группы статусов |
| name | text | NOT NULL | Название статуса |
| description | text |  | Описание |

## Пользователи (users)



| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | integer | | Идентификатор записи |
| dttmcr | timestamptz | | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| last_name | text |  | Фамилия |
| first_name | text | NOT NULL | Имя |
| middle_name | text |  | Отчество |
| nick | text |  | Никнейм |
| bdate | date |  | Дата рождения |
| email | text |  | E-mail адрес |
| password_hash | text |  | Хеш пароля |
| profession_fk | integer |  | FK на запись в таблице `profession` |
| pdb_data | jsonb |  | JSONB данных библиотеки PDB |
| uuid_pdb | uuid |  | Общий UUID пользователя |
| pdb_hash | text |  | Хэш данных библиотеки PDB |
| contract_data | jsonb |  | Данные соцсетей для аутентификации |

## Професссии (profession)



| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | integer | | Идентификатор записи |
| dttmcr | timestamptz | | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| name | text | NOT NULL | Профессия |
| description | text |  | Описание |

## Роли (role)



| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | integer | | Идентификатор записи |
| dttmcr | timestamptz | | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| name | text | NOT NULL | Профессия |
| description | text |  | Описание |

## Грейды (grade)



| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | integer | | Идентификатор записи |
| dttmcr | timestamptz | | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| name | text | NOT NULL | Профессия |
| description | text |  | Описание |

## Типы вопросов (question_type)



| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | integer | | Идентификатор записи |
| dttmcr | timestamptz | | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| code | text | NOT NULL | Код типа |
| name | text | NOT NULL | Профессия |
| description | text |  | Описание |
| config | jsonb |  | Настройки для фронтенда |
| is_public | boolean |  | Опубликовано ли |

## Тесты (test)



| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | integer | | Идентификатор записи |
| dttmcr | timestamptz | | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| category_fk | integer | NOT NULL | FK на запись в таблице category |
| name | text | NOT NULL | Профессия |
| description | text |  | Описание |
| test_config | jsonb |  | Настройки теста |
| is_public | boolean |  | Опубликовано ли |
| state_fk | integer | NOT NULL | Статус |
| amount_for_attempt | integer | DEFAULT 10 | Min кол-во вопросов для прохождения |

## Вопросы (question)



| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | integer | | Идентификатор записи |
| dttmcr | timestamptz | | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| test_fk | integer | NOT NULL | FK на ID теста |
| question_type_fk | integer | NOT NULL | FK на ID типа вопроса |
| question | text | NOT NULL | Текст вопроса |
| image_id | jsonb |  | ID файла изображения |
| description | text |  | Описание |
| is_public | boolean |  | Опубликовано ли |

## Варианты (variant)
    


| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | integer | | Идентификатор записи |
| dttmcr | timestamptz | | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| question_fk | integer | NOT NULL | FK на ID вопроса |
| number | integer |  | № среди вариантов |
| text_variant | text |  | Текст варианта |
| image_id | jsonb |  | ID файла изображения |
| is_compair | boolean |  | Является ли этот вариант сопоставлением |

## Правильные варианты (right_variant)



| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | integer | | Идентификатор записи |
| dttmcr | timestamptz | | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| question_fk | integer | NOT NULL | FK на ID вопроса |
| text_value | text |  | Текст варианта |
| variant_fk | integer |  | FK на ID варианта |

## Попытки (attempt)



| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | integer | | Идентификатор записи |
| dttmcr | timestamptz | | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| finished_at | timestamptz |  |  |
| test_fk | integer | NOT NULL |  |
| test_questions_amount | smallint | NOT NULL DEFAULT 10 |  |
| right_answers_amount | smallint | NOT NULL DEFAULT 0 |  |

## Ответы на вопросы тестов (attempt_answer)



| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | integer | | Идентификатор записи |
| dttmcr | timestamptz | | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| attempt_fk | integer | NOT NULL |  |
| question_fk | integer | NOT NULL |  |
| user_answer | jsonb |  |  |
| is_right | boolean | DEFAULT false |  |

## Экзамены (exam)



| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | integer | | Идентификатор записи |
| dttmcr | timestamptz | | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| grade_fk | integer |  | FK на запись в таблице grade |
| role_fk | integer |  | FK на запись в таблице role |
| code | text | NOT NULL | Буквенно-цифровой код экзамена |
| name | text | NOT NULL | Название экзамена |
| description | text |  | Описание |
| test_list | integer[] |  | Список ID тестов |
| result | smallint | NOT NULL | Значение в % для успеха прохождения |
| is_active | boolean | DEFAULT true | Действующий ли экзамен |
| theme_fk | integer |  | FK на запись в таблице theme |
| image_id | jsonb |  | ID файла бейджа за экзамен |

## Сессии (session)



| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | integer | | Идентификатор записи |
| dttmcr | timestamptz | | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| exam_fk | integer | NOT NULL |  |
| mentee_fk | integer | NOT NULL |  |
| date_start | date | NOT NULL |  |
| date_end | date | NOT NULL |  |
| actual_result | smallint | NOT NULL DEFAULT 0 |  |
| is_completed | boolean | NOT NULL DEFAULT false |  |
| mentor_fk | integer |  |  |



## Группа конфигураций (config_group)



| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | integer | | Идентификатор записи |
| dttmcr | timestamptz | | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| name | text | NOT NULL | Название группы |
| description | text |  | Описание |

## Конфиг (config)



| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | integer | | Идентификатор записи |
| dttmcr | timestamptz | | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
| config_group_fk | integer |  | FK на запись в таблице `config_group` |
| key | text | NOT NULL | Название параметра |
| value | text |  | Значение параметра |
| description | text |  | Описание |
| end_date | date |  | Дата окончания действия параметра |

## Лог (log)

Таблица для логирования изменений в таблицах: UPDATE, DELETE. В данной таблице записывается JSONB-объект исходной строки с данными. По триггеру планируется фиксировать в таблицу log_fields конкретные изменения данных в сравнении с данными в таблице в момент изменения.

| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | bigint | | Идентификатор записи |
| dttmcr | timestamptz | | ДатаВремя создания записи |
| idispl | integer | | ID создателя записи |
| data_old | jsonb |  | JSONB-объект исходных данных |
| action | text | NOT NULL | Действие с данными |
| table_name | text | NOT NULL | Название таблицы |
| table_idkart | int | DEFAULT 0 | ID записи в таблице |

## Изменение полей (log_fields)



| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | bigint | | Идентификатор записи |
| dttmcr | timestamptz | | ДатаВремя создания записи |
| idispl | integer | | ID создателя записи |
| log_id | bigint | NOT NULL | ID записи в таблице `log` |
| data_old | jsonb |  | Предыдущее значение поля |
| data_new | jsonb |  | Новое значение поля |
