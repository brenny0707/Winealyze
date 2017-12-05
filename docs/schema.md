# Schema Information

## users
|    Column          |   Data Type   |    Details               |
| -------------      | ------------- | -------------            |
| id                 | integer       | not null, primary key    |
| fname              | string        | not null                 |
| lname              | string        | not null                 |
| email              | string        | not null, indexed, unique|
| password_digest    | string        | not null                 |
| session_token      | string        | not null, indexed, unique|

* has many wines

## lots

|    Column         |   Data Type   |    Details               |
| -------------     | ------------- | -------------            |
| id                | integer       | not null, primary key    |
| wine_id           | integer        | not null                 |
| house_id          | integer        | not null                 |
| continent         | string        | not null                 |
| date              | string?        | not null                 |
| quantity          | integer        | not null                 |
| hammer/realized?  | integer        | not null               |

## wines


## wineries


## auction houses
