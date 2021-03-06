# Office 365 Graph API Connection Oauth2 Laravel 5

[![Latest Version on Packagist][ico-version]][link-packagist]
[![Software License][ico-license]](LICENSE.md)
[![Build Status][ico-travis]][link-travis]
[![Coverage Status][ico-scrutinizer]][link-scrutinizer]
[![Quality Score][ico-code-quality]][link-code-quality]
[![Total Downloads][ico-downloads]][link-downloads]


This is the first test of a package to Laravel 5 , actually is already working, is getting the connection to the Microsoft Graph api correctly, as soon as i can i will document this file better, The purpose of the project is getting bigger and extends the classes with all the options of their API (send emails, read emails, control the calendar, create events, create users, etc).

## Install

Via Composer

``` bash
$ composer require miguel_costa/office365api
```


Add the provider in the file <i>app.php</i> at folder config

``` php
Miguel_Costa\Office365API\Office365APIServiceProvider::class,
```

Publish the config file in your folder <i>config/Office365API.php</i>

``` bash
$ php artisan vendor:publish
```

Finally, configure the file <i>Office365API.php</i> at config folder with your credentials of your API at Microsoft Dev Portal </br>
<a href="https://apps.dev.microsoft.com/">App Registration Portal</a>

``` php
    'CLIENT_ID' => 'your id string goes here...',
    'CLIENT_SECRET' => 'your secret key goes here...',
    'REDIRECT_URI' => 'your redirect url, Should be the route of laravel where will redirect once the connection is finished',
```

## Usage

``` php
//use the namespace corretly on your controller
use Miguel_Costa\Office365API\ConnectAPI;

//example of function to make the connection
public function redirect_connect() {
ConnectAPI::connect_officeAPI();
}

//get the connection and redirect the user to the intended page
public function get_connection() {
ConnectAPI::get_connection();
return view('home');
}
```
Get the connection at the blade view:
The connection saves an Session variable of the username and email, so after making the connection you can access the variables like that:
``` php
@if(Session::has('office365_name'))
<p>Welcome, <b>{{Session::get('office365_name')}}</b></p>
<p>You are logged in with the Office365 Account:<b>{{Session::get('office365_email')}}</b></p>
@endif
```

## Change log

Please see [CHANGELOG](CHANGELOG.md) for more information what has changed recently.


## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) and [CONDUCT](CONDUCT.md) for details.

## Security

If you discover any security related issues, please email "tga_miguel_tga@hotmail.com" instead of using the issue tracker.

## Credits

- [Miguel Costa][https://github.com/killmi]
- [All Contributors][link-contributors]

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.

[ico-version]: https://img.shields.io/packagist/v/miguel_costa/office365api.svg?style=flat-square
[ico-license]: https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square
[ico-travis]: https://img.shields.io/travis/miguel_costa/office365api/master.svg?style=flat-square
[ico-scrutinizer]: https://img.shields.io/scrutinizer/coverage/g/miguel_costa/office365api.svg?style=flat-square
[ico-code-quality]: https://img.shields.io/scrutinizer/g/miguel_costa/office365api.svg?style=flat-square
[ico-downloads]: https://img.shields.io/packagist/dt/miguel_costa/office365api.svg?style=flat-square

[link-packagist]: https://packagist.org/packages/miguel_costa/office365api
[link-travis]: https://travis-ci.org/miguel_costa/office365api
[link-scrutinizer]: https://scrutinizer-ci.com/g/miguel_costa/office365api/code-structure
[link-code-quality]: https://scrutinizer-ci.com/g/miguel_costa/office365api
[link-downloads]: https://packagist.org/packages/miguel_costa/office365api
[link-author]: https://github.com/killmi
[link-contributors]: ../../contributors
