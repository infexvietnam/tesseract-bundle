TesseractBundle: a wrapper of the Tesseract OCR engine for Symfony
================================================

A small bundle that makes working with the open source [Tesseract OCR engine](https://github.com/tesseract-ocr/tesseract/) 
easier.

Installation
------------

You need a working Tesseract installation. For more information about 
installation and adding language support, see Tesseract's [README](https://github.com/tesseract-ocr/tesseract/blob/master/README.md).

Then install this library, which is available on [Packagist](http://packagist.org/packages/infexvietnam/tesseract-bundle),
through [Composer](http://getcomposer.org/):

    $ composer require infexvietnam/tesseract-bundle
    
Config tesseract's path:

```
# app/config/config.yml
infex_tesseract:
    path: /usr/bin/tesseract
```

Usage
-----

Get `tesseract` from service container:

```php
$tesseract = $this->container->get('infex_tesseract.tesseract_service');
```

Get version and supported languages information:

```php
$version = $tesseract->getVersion();

$languages = $tesseract->getSupportedLanguages();
```

Perform OCR on an image file:

```php
$text = $tesseract->recognize('myfile.tif');
```

Optionally, specify the language(s) as second argument:

```php
$text = $tesseract->recognize('myfile.tif', array('nld', 'eng'));
```

And specify Tesseract’s page seg mode as third argument:

```php
$text = $tesseract->recognize('myfile.tif', null, Tesseract::PAGE_SEG_MODE_AUTOMATIC_OSD);
```

Credit
------

Forked [ddeboer/tesseract](https://github.com/ddeboer/tesseract), updated and made it to Symfony bundle.