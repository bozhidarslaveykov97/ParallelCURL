# ParallelCURL
[![GitHub release](https://img.shields.io/github/release/selfworks/ParallelCURL.svg)](https://github.com/selfworks/ParallelCURL/releases)
[![GitHub stars](https://img.shields.io/github/stars/selfworks/ParallelCURL.svg)](https://github.com/selfworks/ParallelCURL/stargazers)
[![Github All Releases](https://img.shields.io/github/downloads/selfworks/ParallelCURL/total.svg)](https://github.com/selfworks/ParallelCURL)
[![GitHub issues](https://img.shields.io/github/issues/selfworks/ParallelCURL.svg)](https://github.com/selfworks/ParallelCURL/issues)
[![GitHub license](https://img.shields.io/github/license/selfworks/ParallelCURL.svg)](https://github.com/selfworks/ParallelCURL/blob/master/LICENSE)

A PHP class providing an easy interface for running multiple concurrent CURL requests

```
<?php
$maxRequests = 2;
$curlOptions = array(
    CURLOPT_SSL_VERIFYPEER => FALSE,
    CURLOPT_SSL_VERIFYHOST => FALSE,
    CURLOPT_FOLLOWLOCATION => 1,
    CURLOPT_VERBOSE => 0,
    CURLOPT_TIMEOUT => 15,
    CURLOPT_ENCODING => 'gzip, deflate',
);

$parallelCurl = new ParallelCurl($maxRequests, $curlOptions);
$parallelCurl->startRequest("https://google.com", 
    array(
        'class'=>'MyClass',
        'function'=>'onRequestDone'
    ));

$parallelCurl->startRequest("https://youtube.com", array(
        'class'=>'MyClass',
        'function'=>'onRequestDone'
));
$parallelCurl->finishAllRequests();

class MyClass {

  // Request is done
  public function onRequestDone($content) {
    echo $content;
  }
}
?>
```
