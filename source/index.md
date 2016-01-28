---
title: Imagify API Reference

language_tabs:
  - shell
  - python
  - php

toc_footers:
  - <a href='https://app.imagify.io'>Sign Up for a Developer Key</a>
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to Imagify API! You can use the API to optimize and resize your images. 

# API Libraries

A few libraries are already available to interact with our API. If you write your own library, we would be very happy to link you on this doc. [Please contact us](mailto:contact@imagify.io).

## Python

You can directly install it with pip: 

`pip install imagify-python`

You can also install it by cloning the [Github Repo](https://github.com/wp-media/imagify-python) and doing a : 

`python setup.py install`

## PHP

You can direclty install it with composer:

`composer install wp-media/imagify-php`

You can also install it by cloning the [Github Repo](https://github.com/wp-media/imagify-php)

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "https://app.imagify.io/api/endpoint/"
  -H "Authorization: token my_api_key"
```

```python
from imagify import Imagify

imagify = Imagify('my_api_key')
```

```php
<?php
require('class-imagify.php');

$imagify = new Imagify\Optimizer('my_api_key');
```


> Make sure to replace `my_api_key` with your API key.

Imagify uses API keys to allow access to the API. You can register for free to get an API key at our [website](https://app.imagify.io).

Imagify expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: token your_api_key`

<aside class="notice">
You must replace <code> your_api_key </code> with your personal API key.
Be sure to add token before your api key.
</aside>

# Upload

## Upload and Optimize an image

```php
<?php
require ('class-imagify.php');

$imagify = new Imagify\Optimizer('my_api_key');
$param = array(
	"level"=> 'ultra',
	"resize"=> array("width"=> 50),
	);
$image = '1.jpg';	

$imagify->Optimize($image, $param);
```

```python
from imagify import Imagify

imagify = Imagify('my_api_key')

param = dict(ultra=True, resize=dict(width=50))
image = '1.jpg'

imagify.optimize(image, param)
```

```shell
curl "https://app.imagify.io/api/upload/"
  -H "Authorization: my_api_key" -H "Content-Type: multipart/form-data" -F "image=@1.jpg" -F "data={"ultra":true, "resize":{"width":50}}"
```

> The above command returns JSON structured like this:

```json
  {
    "code": 200,
    "image": "http://storage.imagify.io/imagify/45dfi7h/1.jpg",
    "new_size": 100,
    "original_size": 200,
    "percent": 50,
    "success": true
  }

```

This endpoint allow you to upload and optimize an image.

### HTTP Request

<div class="api-endpoint">
    <div class="endpoint-data">
        <i class="label label-post">POST</i>
        <h6>https://app.imagify.io/api/upload/</h6>
    </div>
</div>
### Query Parameters

Query parameters should be send as a form-data request

Parameter | Type | Description
--------- | ------- | -----------
image | binary data | Your image file <i class="label label-info">required</i>
data | json | A json with optimization parameters


### Data Parameters

By filling the data parameter you will be able to control the optimization and to resize images.

Parameter | Type | Default | Description
--------- | ------- | ------ | -----------
normal |bool| false | Optimization with a losseless algorithm
aggressive |bool| true | Optimization with Agressive algorithm
ultra | bool|false | Optimization with Ultra algorithm
keep_exif |bool| false | Will allow you to preserve meta data in images
resize | bool|false | Array with resize paramater
resize["width"] |int| false | Will resize the image with the given width
resize["height"] |int| false | Will resize the image with the given height
resize["percentage"] |int| false | Will resize the image with the given percentage


