# tumblr.php

The official PHP client for the
[Tumblr API](http://www.tumblr.com/docs/en/api/v2).

## Usage

### Basic Usage

The first step is setting up a Client:

``` php
$client = new Tumblr\Client($consumerKey, $consumerSecret);
$client->setToken($token, $tokenSecret);
```

And then you can do anything you'd like:

``` php
foreach ($client->getUserInfo()->user->blogs as $blog) {
	echo $blog->name . "\n";
}
```

### User Methods

``` php
$client->getUserInfo();

$client->getDashboardPosts($options = null);
$client->getLikedPosts($options = null);
$client->getFollowedBlogs($options = null);

$client->follow($blogName);
$client->unfollow($blogName);

$client->like($blogName, $postId, $reblogKey);
$client->unlike($blogName, $postId, $reblogKey);
```

### Blog Methods

``` php
$client->blogInfo($blogName);

$client->blogAvatar($blogName, $size = null);

$client->blogPosts($blogName, $options = null);
$client->blogLikes($blogName, $options = null);
$client->blogFollowers($blogName, $options = null);

$client->blogQueuedPosts($blogName, $options = null);
$client->blogDraftPosts($blogName, $options = null);
$client->blogSubmissionPosts($blogName, $options = null);
```

### Post Methods

``` php
$client->deletePost($blogName, $id, $reblogKey);
```

### Tagged Methods

``` php
$client->taggedPosts($tag, $options = null);
```

-
## Running tests

tumblr.php has full unit tests that can be run with PHPUnit like this:

``` bash
$ phpunit
```

That will also generate a coverage report into `./coverage`

## Copyright and license

Copyright 2013 Tumblr, Inc.

Licensed under the Apache License, Version 2.0 (the "License"); you may not
use this work except in compliance with the License. You may obtain a copy of
the License in the LICENSE file, or at:

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS, WITHOUT
WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the
License for the specific language governing permissions and limitations.