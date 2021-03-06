twig-htmlstrip
==============

Filter for Twig to convert a small subset of html into something reasonable you can put in plain text email, or SMS.

[![Build Status](https://travis-ci.org/PurpleBooth/twig-htmlstrip.svg?branch=master)](https://travis-ci.org/PurpleBooth/twig-htmlstrip)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/PurpleBooth/twig-htmlstrip/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/PurpleBooth/twig-htmlstrip/?branch=master)
[![Coverage Status](https://coveralls.io/repos/github/PurpleBooth/twig-htmlstrip/badge.svg?branch=master)](https://coveralls.io/github/PurpleBooth/twig-htmlstrip?branch=master)
[![Dependency Status](https://www.versioneye.com/user/projects/57952479b4e86c004c3338f7/badge.svg?style=flat-square)](https://www.versioneye.com/user/projects/57952479b4e86c004c3338f7)
[![Latest Stable Version](https://poser.pugx.org/purplebooth/twig-htmlstrip/v/stable)](https://packagist.org/packages/purplebooth/twig-htmlstrip)
[![Total Downloads](https://poser.pugx.org/purplebooth/twig-htmlstrip/downloads)](https://packagist.org/packages/purplebooth/twig-htmlstrip)
[![License](https://poser.pugx.org/purplebooth/twig-htmlstrip/license)](https://packagist.org/packages/purplebooth/twig-htmlstrip)

How To Use
----------

Add the dependency to your composer.json
```bash
php composer.phar require purplebooth/twig-htmlstrip:^1.0.0
```

Add a service which points to the class, and tag it with the twig.extension tag.
```yaml
# src/Acme/DemoBundle/Resources/config/services.yml
services:
    purplebooth.twig.html_stripper_extension:
        class: PurpleBooth\HtmlStripperExtension
        tags:
            - { name: twig.extension }
```

And use it
```twig
{{ yourhtml|html_strip }}
```

Examples
--------
Input:
```html
<p>Hello, world.</p>
```

Output:
```
Hello, world.
```

Input:
```html
<a href="http://pleasestopbeingsad.tumblr.com/">Quote source</a>
```

Output:
```
Quote source (http://pleasestopbeingsad.tumblr.com/)
```

Input:
```html
<ul>
    <li>You're a good person</li>
    <li>Don't be too hard on yourself</li>
    <li>Enjoy the little things</li>
</ul>
```

Output:
```
* You're a good person
* Don't be too hard on yourself
* Enjoy the little things
```

Input:
```html
<div>Tomorrow will be better.</div>
You're doing your best, and I'm proud of you.
```

Output:
```
Tomorrow will be better.


You're doing your best, and I'm proud of you.
```

Input:
```html
<blockquote>It's always good to read a good book.</blockquote>
You are not here, <i>but I am thinking of you.</i>
```

Output:
```
It's always good to read a good book. You are not here, but I am thinking of you.
```

Input:
```html
<div>
    <p>If she wants to <i>dance</i> and drink all night.</p>
    <ul>
        <li>Well theres no one that can stop her</li>
        <li>Shes going until the house lights come up or her stomach spills on to the floor</li>
        <li>This night is gonna end when we're damn well ready for it to be over</li>
        <li>Worked all week long now the music is playing on our time</li>
    </ul>
    <div><div>Hello</div><div>Fin.</div></div>
</div>
```

Output
```
If she wants to dance and drink all night.

* Well theres no one that can stop her
* Shes going until the house lights come up or her stomach spills on to the floor
* This night is gonna end when we're damn well ready for it to be over
* Worked all week long now the music is playing on our time


Hello


Fin.
```

Related
-------

* [Stand alone library](https://github.com/PurpleBooth/htmlstrip)

Versioning
----------

We use [semver](http://semver.org/). See the [releases](https://github.com/PurpleBooth/twig-htmlstrip/releases) for a changelog and versions
