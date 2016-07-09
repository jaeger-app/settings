# Jaeger Settings

[![Build Status](https://travis-ci.org/jaeger-app/settings.svg?branch=master)](https://travis-ci.org/jaeger-app/settings)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/jaeger-app/settings/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/jaeger-app/settings/?branch=master)
[![Author](http://img.shields.io/badge/author-@mithra62-blue.svg?style=flat-square)](https://twitter.com/mithra62)
[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/jaeger-app/bootstrap/master/LICENSE) 

Jaeger Settings is an abstract object to manage storage of your plugin settings. 

> Note that you're NOT meant to instantiate this object; you have to extend it and apply your specific settings before you can get started.

## Installation

Add `jaeger-app/settings` as a requirement to your `composer.json`:

```bash
$ composer require jaeger-app/settings
```

Once that's done, you'll have to install the database schema located at data\settings_table.sql

## Simple Example

In your parent object, ensure you extend have 2 properties, `$table` and `$_defaults`. `$table` should be the name of your settings table, and `$_defaults` is a key => value array of your plugin's settings and a default value for each. 

You'll also have to define a method named `validate(array $data, array $extra = array())` that accepts the settings data and returns a boolean.

```php
class MyPluginSettings extends \JaegerApp\Settings
{
    /**
     * The name of the settings storage table
     * 
     * @var string
     */
    protected $table = 'my_plugin_settings';

    /**
     * The accepted settings with a default value
     * 
     * @var array
     */
    protected $_defaults = array(
        'key1' => 'value1',
        'key2' => 'value2',
	);

    public function __construct($db, $lang)
    {
        parent::__construct($db, $lang);
		$this->setTable($this->table);
		$this->setTable($this->table);
    }

    public function validate(array $data, array $extra = array())
    {}
}
```

