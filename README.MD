# mongo-bundle

Bundle service integration of official [mongodb/mongo-php-library](https://github.com/mongodb/mongo-php-library) driver library, ([mongodb/mongodb](https://packagist.org/packages/mongodb/mongodb) on packagist)

[![PHP Version](https://img.shields.io/badge/PHP-%3E%3D7.0-blue.svg)](https://img.shields.io/badge/PHP-%3E%3D7.0-blue.svg) [![StyleCI](https://styleci.io/repos/61825783/shield)](https://styleci.io/repos/61825783) [![Build Status](https://travis-ci.org/Algatux/mongo-bundle.svg?branch=master)](https://travis-ci.org/Algatux/mongo-bundle) [![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/Algatux/mongo-bundle/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/Algatux/mongo-bundle/?branch=master) [![Code Coverage](https://scrutinizer-ci.com/g/Algatux/mongo-bundle/badges/coverage.png?b=master)](https://scrutinizer-ci.com/g/Algatux/mongo-bundle/?branch=master)
[![Latest Stable Version](https://poser.pugx.org/algatux/mongo-bundle/v/stable)](https://packagist.org/packages/algatux/mongo-bundle) [![Latest Unstable Version](https://poser.pugx.org/algatux/mongo-bundle/v/unstable)](https://packagist.org/packages/algatux/mongo-bundle) [![License](https://poser.pugx.org/algatux/mongo-bundle/license)](https://packagist.org/packages/algatux/mongo-bundle)

### Installation

First of all, you need to require this library through composer:

```bash
composer require algatux/mongo-bundle
```

Then, enable the bundle on the `AppKernel` class:

```php
// app/AppKernel.php

public function registerBundles()
{
    $bundles = array(
        // ...
        new MongoBundle\MongoBundle(),
    );

    // ...

    return $bundles
}
```

### Configuration

Here is the configuration reference:

```yaml
mongo_bundle:

    # If not defined, the first connection will be taken.
    default_connection:   ~
    connections:

        # Prototype
        name:

            # Your MongoDB host address
            host:                 ~ # Required

            # Your MongoDB database name
            database:             ~ # Required

            port:                 27017
            username:             ''
            password:             ''
```

If you have only one connection to configure, this can be simplified to this:

```yaml
mongo_bundle:
    # Your MongoDB host address
    host:                 ~ # Required

    # Your MongoDB database name
    database:             ~ # Required
    
    port:                 27017
    username:             ''
    password:             ''
```

### Services

You can directly access to the `MongoDB\Database` with those services:

```php
$this->get('mongo.connection'); // Default connection
$this->get('mongo.connection.{connectionName}'); // default if not specified
```

To manipulate the database, please read the official [documentation](http://mongodb.github.io/mongo-php-library/classes/database/)