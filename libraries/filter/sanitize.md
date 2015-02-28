# Aura.Filter Rules To Sanitize Fields

## alnum

Sanitizes to leave only alphanumeric characters.

```php
<?php
$filter->sanitize('field')->to('alnum');
?>
```

## alpha

Sanitizes to leave only alphabetic characters.

```php
<?php
$filter->sanitize('field')->to('alpha');
?>
```

## between

Sanitizes so that values lower than the range are forced up to the minimum, and
values higher than the range are forced down to the maximum.

```php
<?php
$filter->sanitize('field')->to('between', $min, $max);
?>
```

## bool

Sanitizes to a strict PHP boolean.
Pseudo-true values include the strings '1', 'y', 'yes', and 'true';
pseudo-false values include the strings '0', 'n', 'no', and 'false'.

```php
<?php
$filter->sanitize('field')->to('bool');
?>
```

## closure

Sanitizes the value using a closure. The closure should take two arguments,
`$subject` and `$field` to indicate the subject (either an array or object)
and the field within that subject. It should return `true` to pass, or `false`
to fail.

```php
<?php
$filter->validate('field')->is('closure', function ($subject, $field) {
    // always force the field to 'foo'
    $subject->$field = 'foo';
    return true;
});
?>
```

## dateTime

Sanitizes the value to a specified date/time format, default `'Y-m-d H:i:s'`.

```php
<?php
$filter->sanitize('field', $filter::FIX, 'dateTime', $format);
?>
```

## equalToField

Sanitizes to the value of another field in the subject.

```php
<?php
$filter->sanitize('field')->to('equalToField', 'other_field_name');
?>
```

## equalToValue

Sanitizes to the specified value.

```php
<?php
$filter->sanitize('field')->to('equalToValue', $other_value);
?>
```

## float

Sanitizes the value to transform it into a float; for weird strings, this may
not be what you expect.

```php
<?php
$filter->sanitize('field')->to('float');
?>
```

## int

Sanitizes the value to transform it into an integer; for weird strings, this may
not be what you expect.

```php
<?php
$filter->sanitize('field')->to('int');
?>
```

## isbn

Sanitizes the value to an ISBN (International Standard Book Number).

```php
<?php
$filter->sanitize('field')->to('isbn');
?>
```

## max

Sanitizes so that values higher than the maximum are forced down to the maximum.

```php
<?php
$filter->sanitize('field')->to('max', $max);
?>
```

## min

Sanitizes so that values lower than the minimum are forced up to the minimum.

```php
<?php
$filter->sanitize('field')->to('min', $min);
?>
```

## regex

Sanitizes the value using `preg_replace()`.

```php
<?php
$filter->sanitize('field')->to('regex', $expr);
?>
```

## strictEqualToField

Sanitizes to the value of another field in the subject.

```php
<?php
$filter->sanitize('field')->to('strictEqualToField', 'other_field_name');
?>
```

## strictEqualToValue

Sanitizes to the specified value.

```php
<?php
$filter->sanitize('field')->to('strictEqualToValue', $other_value);
?>
```

## string

Sanitizes the value by casting to a string and optionally using `str_replace()`
to find and replace within the string.

```php
<?php
$filter->sanitize('field')->to('string', $find, $replace);
?>
```

## strlen

Validates the value has a specified length. Sanitizes the value
to cut off longer values at the right, and `str_pad()` shorter ones.

```php
<?php
$filter->sanitize('field')->to('strlen', $len);
?>
```

## strlenBetween

Sanitizes the value to truncate values longer than the maximum, and `str_pad()`
shorter ones.

```php
<?php
$filter->sanitize('field')->to('strlenBetween', $min, $max, $pad_string, $pad_type);
?>
```

## strlenMax

Sanitizes the value to truncate values longer than the maximum.

```php
<?php
$filter->sanitize('field')->to('strlenMax', $max);
?>
```

## strlenMin

Sanitizes the value to `str_pad()` values shorter than the minimum.

```php
<?php
$filter->sanitize('field')->to('strlenMin', $min, $pad_string, $pad_type);
?>
```

## trim

Sanitizes the value to `trim()` it. Optionally specify characters to trim.

```php
<?php
$filter->sanitize('field')->to('trim', $chars);
?>
```

## word

Sanitizes the value to remove non-word characters.

```php
<?php
$filter->sanitize('field')->to('word');
?>
```
