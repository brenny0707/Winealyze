# Schema Information

## users
|    Column          |   Data Type   |    Details               |
| -------------      | ------------- | -------------            |
| id                 | integer       | not null, primary key    |
| fname              | string        | not null                 |
| lname              | string        | not null                 |
| email              | string        | not null, index, unique|
| password_digest    | string        | not null                 |
| session_token      | string        | not null, index, unique|

#### associations
* has many wines

## lots

|    Column         |   Data Type   |    Details               |
| -------------     | ------------- | -------------            |
| id                | integer       | not null, primary key    |
| wine_id           | integer        | not null, index           |
| house_id          | integer        | not null, index         |
| continent_id      | integer        | not null, index           |
| date              | string?        | not null                 |
| quantity          | integer        | not null                 |
| hammer/realized?  | integer        | not null               |

#### associations
* belongs to house
* belongs to wine?
* belongs to continent?

## wines

|    Column         |   Data Type   |    Details               |
| -------------     | ------------- | -------------            |
| id                | integer       | not null, primary key    |
| winery_id           | integer        | not null, index            |
| country_id           | integer        | not null, index       |
| region_id           | integer        | not null, index           |
| grape_id           | integer        | not null, index          |
| name              | string        | not null            |
| size         | string        | not null                 |
| quantity          | integer        | not null                 |
| hammer/realized?  | integer        | not null               |

#### associations
* belongs to user
* belongs to winery
* belongs to region
* belongs to country (through region)
* belongs to grape
* has many lots?

## wineries

|    Column         |   Data Type   |    Details               |
| -------------     | ------------- | -------------            |
| id                | integer       | not null, primary key    |
| name              | string        | not null            |
| country_id           | integer        | not null, index      |
| region_id           | integer        | not null, index     |

#### associations
* has many wines
* belongs to country
* belongs to region

## (auction) houses

|Column         |   Data Type   |    Details               |
| -------------     | ------------- | -------------            |
| id                | integer       | not null, primary key    |
| name              | string        | not null            |

#### associations
* has many lots
* has many wines (through lots)?

## continents
Continents refer to the sale location of an auction (Auction House 1 has a sale in Asia).

Currently set so they also contain wine countries.

|Column         |   Data Type   |    Details               |
| -------------     | ------------- | -------------            |
| id                | integer       | not null, primary key    |
| name              | string        | not null            |

#### associations
* has many lots

## countries
Countries refer to the country a wine/winery is present.

|    Column         |   Data Type   |    Details               |
| -------------     | ------------- | -------------            |
| id                | integer       | not null, primary key    |
| name              | string        | not null            |
| continent_id           | integer        | not null, index     |

#### associations
* has many regions
* has many wines (through regions)
* has many wineries (through regions)

## regions
Regions refer to wine regions.

|    Column         |   Data Type   |    Details               |
| -------------     | ------------- | -------------            |
| id                | integer       | not null, primary key    |
| name              | string        | not null            |
| country_id        | integer        | not null, index     |

#### associations
* belongs to country
* has many wines
* has many wineries

## grapes
Can include blends (ex: Bordeaux blend).

|    Column         |   Data Type   |    Details               |
| -------------     | ------------- | -------------            |
| id                | integer       | not null, primary key    |
| name              | string        | not null            |
| color              | string        | not null            |

#### associations
* has many regions
* has many wines
