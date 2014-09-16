Redmine api
===============

`Fiv\Redmine\Client` allow you to pass HTTP Server Authorization and use redmine with API key
```php
<?php

  require_once 'vendor/autoload.php';

  $url = 'http://redmine.funivan.com';
  $apiKey = '458854444dd5f4r87r9as4df5645as1df1c24f7f664f2';
  $httpAuthString = 'funivan:utHF04759f';

  $client = new Fiv\Redmine\Client($url, $apiKey, $httpAuthString);
  $issueList = $client->api('issue')->all(array(
    'limit' => 3
  ));

  foreach ($issueList['issues'] as $issue) {

    $fullIssue = $client->api('issue')->show($issue['id'], ['include' => 'journals']);
    print_r($fullIssue);

  }
?>
```