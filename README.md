# OctoberCMS Agent Plugin

[日本語版はこちら](./README_ja.md)

[OctoberCMS](http://octobercms.com/) plugin to detect user's browser, OS, and device.
This is available not only from PHP but also from Twig templates.

This is a wrapper plugin of [jenssegers/agent](https://github.com/jenssegers/agent).
Thanks to jenssegers, and also serbanghita created it's base [serbanghita/Mobile-Detect](https://github.com/serbanghita/Mobile-Detect).


## API
Please refer [jenssegers/agent](https://github.com/jenssegers/agent) for available APIs.


## Usage
### Installation
#### With Composer
Add below to the composer.json of your project. (`repositories` section is required because I have not registered it to [packagist](https://packagist.com))
```
{
    "require": [
        ...
        "pikanji/oc-agent-plugin": "dev-master"
    ],
...
    "repositories": [
        ...
        {
            "url": "git@github.com:pikanji/oc-agent-plugin.git",
            "type": "git"
        }
}
```

Execute below at the root of your project.
```
composer update
```

#### With OctoberCMS UI
This does not support OctoberCMS's plugin installation UI, because this is not registered there yet.


### Using in Twig Templates
Agent object will be available after Agent component is added to pages or layouts.
I recommend to add the component to your layout, so that you don't have to add every page.

Preparation is to add `[Agent]` to the configuration section of page or layout files. There is no parameter needed for Agent component.
```
description = "Default layout"

[Agent]
==
<!DOCTYPE html>
...

```

Then you can use this Agent object to call [jenssegers/agent](https://github.com/jenssegers/agent) APIs.
```
...
{% if Agent.isFireFox() %}
...
```

### Using in PHP Code
It is just using [jenssegers/agent](https://github.com/jenssegers/agent) directly. Please refer to its documentation.
You don't need to install it since it is installed as the dependency of this plugin.

Basically, the usage looks like this.
```php
use Jenssegers\Agent\Agent;
...

$agent = new Agent();
if ($agent->isFireFox()) {
...

```
