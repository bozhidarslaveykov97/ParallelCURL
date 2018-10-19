# ParallelCURL

[![GitHub stars](https://img.shields.io/github/stars/selfworks/ParallelCURL.svg)](https://github.com/selfworks/ParallelCURL/stargazers)
[![Github All Releases](https://img.shields.io/github/downloads/selfworks/ParallelCURL/total.svg)](https://github.com/selfworks/ParallelCURL)
[![GitHub issues](https://img.shields.io/github/issues/selfworks/ParallelCURL.svg)](https://github.com/selfworks/ParallelCURL/issues)
[![GitHub license](https://img.shields.io/github/license/selfworks/ParallelCURL.svg)](https://github.com/selfworks/ParallelCURL/blob/master/LICENSE)

A PHP class providing an easy interface for running multiple concurrent CURL requests

<?php
$parallel_curl = new ParallelCurl($max_requests, $curl_options);
$parallel_curl->startRequest("https://google.com", 
    array(
        'class'=>'MyClass',
        'function'=>'onRequestDone'
    ));

$parallel_curl->startRequest("https://youtube.com", array(
        'class'=>'MyClass',
        'function'=>'onRequestDone'
));
$parallel_curl->finishAllRequests();

class MyClass {

  // Request is done
  public function onRequestDone($content) {
    echo $content;
  }
}
