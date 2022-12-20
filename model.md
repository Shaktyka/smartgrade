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
| last_name | text |  |  |
| first_name | text | NOT NULL |  |
| middle_name | text |  |  |
| nick | text |  |  |
| bdate | date |  |  |
| email | text |  |  |
| password_hash | text |  |  |
| profession_fk | integer |  |  |
| pdb_data | jsonb |  |  |
| uuid_pdb | uuid |  |  |
| pdb_hash | text |  |  |
| contract_data | jsonb |  |  |

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
| category_fk | integer | NOT NULL |  |
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
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |

## Ответы на вопросы тестов (attempt_answer)



| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | integer | | Идентификатор записи |
| dttmcr | timestamptz | | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |



## Экзамены (exam)

| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | integer | | Идентификатор записи |
| dttmcr | timestamptz | | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |



## Сессии (session)

| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | integer | | Идентификатор записи |
| dttmcr | timestamptz | | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |



## Группа конфигураций (config_group)

| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | integer | | Идентификатор записи |
| dttmcr | timestamptz | | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |



## Конфиг (config)

| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | integer | | Идентификатор записи |
| dttmcr | timestamptz | | ДатаВремя создания записи |
| dttmup | timestamptz | | ДатаВремя последнего обновления записи |
| dttmcl | timestamptz | | ДатаВремя закрытия записи |
| idispl | integer | | ID создателя записи |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |

## Лог (log)



| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | bigint | | Идентификатор записи |
| dttmcr | timestamptz | | ДатаВремя создания записи |
| idispl | integer | | ID создателя записи |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |

## Изменение полей (log_fields)



| Поле | Тип | Ограничения | Назначение |
| ------ | ------ | ------ | ------ |
| idkart | bigint | | Идентификатор записи |
| dttmcr | timestamptz | | ДатаВремя создания записи |
| idispl | integer | | ID создателя записи |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
