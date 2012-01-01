# A Behat+WebApiContext Demo

## Installation

### Requirements:

You need a valid PHPUnit 3.5 installation:

``` bash
pear channel-discover pear.phpunit.de
pear channel-discover components.ez.no
pear channel-discover pear.symfony-project.com

pear install phpunit/PHPUnit
```

Behat doesn't care what you use to validate your steps. But
WebApiContext uses PHPUnit assertions internally!

## Usage 

Clone this repo:

``` bash
git clone https://github.com/KnpLabs/behat-webapi-demo
```

Now install Behat, CommonContexts and their dependencies:

``` bash
wget -nc http://getcomposer.org/composer.phar
php composer.phar install
```

Now to launch Behat, just run:

``` bash
bin/behat
```

you should see an output like:

``` gherkin
Feature: Labels
  In order to distinguish issues
  As a GitHub user
  I need to be able to label them

  Scenario: List repository labels
    When I send a GET request to "/repos/behat/mink/labels"
    Then the response code should be 200
    And response should contain json:
      """
      [
          {
              "url":   "BASE_URL/repos/Behat/Mink/labels/feature",
              "name":  "feature",
              "color": "02e10c"
          },
          {
              "url":   "BASE_URL/repos/Behat/Mink/labels/bug",
              "name":  "bug",
              "color": "e10c02"
          },
          {
              "url":    "BASE_URL/repos/Behat/Mink/labels/proposal",
              "name":   "proposal",
              "color":  "d7e102"
          }
      ]
      """

1 scenario (1 passed)
3 steps (3 passed)
```
