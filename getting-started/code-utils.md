# Code Utils

1\. To make our code more readable and clean, we'll use following global functions, that will be placed in `utils.php` file.

<details>

<summary>utils.php</summary>

```php
function downloadFile($url, $filePath) {
    $context = stream_context_create(['http' => ['timeout' => 30]]);
    $response = @file_get_contents($url, false, $context);
    if ($response === false) {
        throw new RuntimeException("Failed to download file from $url");
    }
    file_put_contents($filePath, $response);
}
```

</details>

2\. We'll use PrettyPrint library:\
[https://github.com/apphp/pretty-print](https://github.com/apphp/pretty-print)

Pretty print function - `pprint()`  or `pp()`  works like Python's `print().`

**Examples of output:**

Sample 1:

```php
pprint($demo->getWeights(), end:"\n\n");
```

```
// Output
tensor([[[-0.1962, -1.4249, -0.6252],
   [-0.2102, -0.8102,  0.2460],
   ...,
   [-1.1121, -1.0190, -0.3571],
   [ 0.0423, -0.8077, -1.1279],
   [-0.5272, -1.7160,  1.6134]])
```

Sample 2:

```php
echo "Embedding for token 3:\n";
pprint($demo->embedTokenRounded(3), end:"\n\n")
```

```
// Output
Embedding for token 3:
[-1.1121, -1.0190, -0.3571]
```

3\. We're also going to use following libraries: `rubix/tensor` and `rubix/ml`

* `rubix/tensor`  - a library and extension that provides objects for scientific computing in PHP.
* `rubix/ml`  - a high-level machine learning and deep learning library for the PHP language.

