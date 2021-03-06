# Tatter\Visits
Lightweight traffic tracking for CodeIgniter 4

## Quick Start

1. Install with Composer: `> composer require tatter/visits`
2. Update the database: `> php spark migrate -all`
3. Visits will be recorded automatically by a system event

## Features

Provides automated traffic tracking for CodeIgniter 4

## Installation

Install easily via Composer to take advantage of CodeIgniter 4's autoloading capabilities
and always be up-to-date:
* `> composer require tatter/visits`

Or, install manually by downloading the source files and adding the directory to
`app/Config/Autoload.php`.

Once the files are downloaded and included in the autoload, run any library migrations
to ensure the database is setup correctly:
* `> php spark migrate -all`

**Pro Tip:** You can add the spark command to your composer.json to ensure your database is
always current with the latest release:
```
{
	...
    "scripts": {
        "post-update-cmd": [
            "@composer dump-autoload",
            "php spark migrate -all"
        ]
    },
	...
```

## Configuration (optional)

The library's default behavior can be altered by extending its config file. Copy
**bin/Visits.php** to **app/Config/** and follow the instructions in the
comments. If no config file is found in app/Config the library will use its own.

## Usage

If installed correctly CodeIgniter 4 will detect and autoload the class, service, and
config. The library includes an event listening for `post_controller_constructor` to
record page loads. If you prefer to handle them manually you may use the service to load
the class and record the current visit:
* `service('visits')->record();`

## Accessing data

This library provides a `VisitModel` and a `Visit` entity for convenient access to recorded
entries. Feel free to extend these classes for any additional functionality.

## User tracking

It is not legal nor advisable to track user traffic in all cases. By default `Visits` will
only include user IDs when they are loaded into the specific session variable
`logged_in`. If this session variable is not set access will be anonymous. You can
change the variable used to determine a logged in user by using the Config file and
altering the value (see above).
