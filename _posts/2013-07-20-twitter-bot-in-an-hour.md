---
layout: post
title:  "Write a Twitter Bot in an Hour (or less)"
date:   2013-07-20
---

1. Carve out some space on a public server of yours (you'll need PHP 5.3+ and curl).
2. Register your "app" with Twitter. This might be the hardest part. See: [https://dev.twitter.com/docs/auth](https://dev.twitter.com/docs/auth) Scribble down the various keys you create.
3. Grab [https://github.com/themattharris/tmhOAuth](https://github.com/themattharris/tmhOAuth) and place that on your server space
4. Write a simple script. A sample basic skeleton is shown below.
5. Call this script on a cron, as desired.
6. Best of luck!

~~~
require 'twitter/tmhOAuth.php';
require 'twitter/tmhUtilities.php';
$tmhOAuth = new tmhOAuth(array(
  'consumer_key' => 'foo',
  'consumer_secret' => 'bar',
  'user_token' => 'boo',
  'user_secret' => 'far',
));

// Magic code that generates an interesting and unique $status
// Grabs a random line from a text file
// Makes an API call to somewhere else
// Etc.
$status = 'foo';

$code = $tmhOAuth->request(
    'POST',
    $tmhOAuth->url('1.1/statuses/update'),
    array(
         'status' => $status
    ),
);

// Add some useful output
echo "code=$code<br/>";
if ($code == 200) {
  echo "response OK<br/>";
  var_dump(json_decode($tmhOAuth->response['response']));
  echo "<br/>";
}
else {
  echo "response KO<br/>";
  echo $tmhOAuth->response['response'];
  echo "<br/>";
}
~~~