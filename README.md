# Sanitizer EasySlugger

A module for ProcessWire CMS/CMF. Allows the use of the [EasySlugger](https://github.com/javiereguiluz/EasySlugger) library as Sanitizer methods.

## Installation

[Install](http://modules.processwire.com/install-uninstall/) the Sanitizer EasySlugger module.

## Usage

The module adds four new sanitizer methods.

###slugger($string, $options)

Similar to `$sanitizer->pageName()` - I'm not sure if there are any advantages over that method. Included because it is one of the methods offered by EasySlugger.
```php
$slug = $sanitizer->slugger('Lorem Ipsum');
// Result: lorem-ipsum
```

###utf8Slugger($string, $options)

Creates slugs from non-latin alphabets.

```php
$slug = $sanitizer->utf8Slugger('这个用汉语怎么说');
// Result: zhe-ge-yong-han-yu-zen-me-shuo
```

###seoSlugger($string, $options)

Augments the strings before turning them into slugs. The conversions are related to numbers, currencies, email addresses and other common symbols.

```php
$slug = $sanitizer->seoSlugger('The price is $5.99');
// Result: the-price-is-5-dollars-99-cents
```
See the [EasySlugger readme](https://github.com/javiereguiluz/EasySlugger) for some more examples.

###seoUtf8Slugger($string, $options)

A combination of utf8Slugger() and seoSlugger().

```php
$slug = $sanitizer->seoUtf8Slugger('价钱是 $5.99');
// Result: jia-qian-shi-5-dollars-99-cents
```

###$options argument

Each of the methods can take an `$options` array as second argument.
* `separator` (string): the character that separates the part of the slug. Default: `-`
* `unique` (bool): Determines whether a random suffix is added at the end of the slug. Default: `false`

```php
$slug = $sanitizer->utf8Slugger('这个用汉语怎么说', ['separator' => '_', 'unique' => true]);
// Result: zhe_ge_yong_han_yu_zen_me_shuo_3ad66c4
```