# Graphqloquent
Graphql javascript model based - inspired by Laravel Eloquent

## Ideas
Graphql provide us very fast way to get data from backend. Laravel Eloquent provide model base working with database. The idea is provide a way to query data like Eloquent for javascript.
And this package was born to provide fatest way to define model

## Requrements
- Postgresql
- Hasura or an api for backend
- Apollo client for graphql
- Static method of javascript from [ECMAScript 2015](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/static)


## Basic usage
### Defining model
#### Define Model
```
import Model from 'graphqloquent';

export default class Flight extends Model {
}
```
#### Table name
```
import Model from 'graphqloquent';

export default class Flight extends Model {
  /**
   * table: is the table associated with model
   */

  constructor() {
    this.table = 'my_flights';
  }
}
```
#### Primary key
```
import Model from 'graphqloquent';

export default class Flight extends Model {

  /**
   * key: is the table primary key
   */
  constructor() {
    this.key = 'my_flights_id';
  }
}
```
#### Timestamps
By default, Graphloquent expects created_at and updated_at columns exist on your tables
```
import Model from 'graphqloquent';

export default class Flight extends Model {

  /**
   * key: is the table primary key
   */
  constructor() {
    this.key = 'my_flights_id';
  }
}
```

### Retrieving Models

#### Get all flights
```
import Flight from '@/models/Fligt';
$flights = Flight.all();
```

#### With conditions
```
import Flight from '@/models/Flight';
$flight = Flight.where('active', 1)
                .orderBy('name', 'desc')
                .take(10)
                .get();
```

### Retrieving Single Model

#### Get Single Model
```
import Flight from '@/models/Fligt';
$flight = Flight.find(1);
```

#### With conditions
```
import Flight from '@/models/Flight';
$flight = Flight.where('active', 1).first();
```

#### Notfound exception
```
import Flight from '@/models/Flight';
$flight = Flight.findOrFail(1);
$flight = Flight.where('leg', '>', 1).findOrFail();
```

#### Retrieving Aggregates
```
import Flight from '@/models/Flight';
$flight = Flight.where('active', 1).count();
```

### Inserting and Updating model

#### Insert
```
import Flight from '@/models/Flight';
$flight = new Flight();
$flight.name = 'Airbus 320';
$flight.save();
```
#### Update
```
import Flight from '@/models/Flight';
$flight = Flight.find(1);
$flight.name = 'New Airbus 320';
$flight.save();
```
#### Delete
```
import Flight from '@/models/Flight';
$flight = Flight.find(1);
$flight.delete();
```
