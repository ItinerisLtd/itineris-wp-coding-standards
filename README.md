# Itineris WP Coding Standards

[![Packagist Version](https://img.shields.io/packagist/v/itinerisltd/itineris-wp-coding-standards.svg)](https://packagist.org/packages/itinerisltd/itineris-wp-coding-standards)
[![PHP from Packagist](https://img.shields.io/packagist/php-v/itinerisltd/itineris-wp-coding-standards.svg)](https://packagist.org/packages/itinerisltd/itineris-wp-coding-standards)
[![Packagist Downloads](https://img.shields.io/packagist/dt/itinerisltd/itineris-wp-coding-standards.svg)](https://packagist.org/packages/itinerisltd/itineris-wp-coding-standards)
[![GitHub License](https://img.shields.io/github/license/itinerisltd/itineris-wp-coding-standards.svg)](https://github.com/ItinerisLtd/itineris-wp-coding-standards/blob/master/LICENSE)
[![Hire Itineris](https://img.shields.io/badge/Hire-Itineris-ff69b4.svg)](https://www.itineris.co.uk/contact/)

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Goal](#goal)
- [Installation](#installation)
- [Usage](#usage)
- [Required Readings](#required-readings)
- [FAQs](#faqs)
  - [Will you add support for older PHP versions?](#will-you-add-support-for-older-php-versions)
  - [It looks awesome. Where can I find some more goodies like this?](#it-looks-awesome-where-can-i-find-some-more-goodies-like-this)
  - [This isn't on wp.org. Where can I give a :star::star::star::star::star: review?](#this-isnt-on-wporg-where-can-i-give-a-starstarstarstarstar-review)
- [Feedback](#feedback)
- [Security](#security)
- [Credits](#credits)
- [License](#license)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Goal

[Itineris WP Coding Standards](https://github.com/ItinerisLtd/itineris-wp-coding-standards) is a project with rulesets for code style and quality tools to be used in Itineris WordPress projects.

It is a mix with [PSR-1](https://www.php-fig.org/psr/psr-1/), [PSR-2](https://www.php-fig.org/psr/psr-2), [PSR-4](https://www.php-fig.org/psr/psr-4/), [PSR-12](https://github.com/php-fig/fig-standards/blob/master/proposed/extended-coding-style-guide.md) and [WordPress Coding Standards](https://github.com/WordPress-Coding-Standards/WordPress-Coding-Standards).

Whenever there's a conflict between PSR and WPCS, always prefer PSR.

Currently, it works for WordPress plugins.
Using it on [Bedrock](https://github.com/roots/bedrock) or [Sage](https://github.com/roots/sage) requires some tweaking.

## Installation

```sh-session
$ composer require --dev itinerisltd/itineris-wp-coding-standards
```

## Usage

First, create [`phpcs.xml`](https://github.com/squizlabs/PHP_CodeSniffer/wiki/Annotated-Ruleset) on project root:

```xml
<?xml version="1.0"?>
<ruleset name="Plugin">
    <!-- Check all files under project root -->
    <file>./</file>

    <!-- Show colors in console -->
    <arg value="-colors"/>

    <!-- Show progress and sniff codes in all reports; Show progress of the run -->
    <arg value="sp"/>

    <!-- Scan only PHP files -->
    <arg name="extensions" value="php"/>

    <!-- Use Itineris WP Coding Standards -->
    <rule ref="Itineris"/>

    <!-- TODO: Change everything below! -->
    <!-- TODO: Exclude specific rules if necessary -->

    <!-- TODO: Exclude some files -->
    <exclude-pattern>/my-awesome-plugin.php</exclude-pattern>
    <exclude-pattern>/tests/*</exclude-pattern>
    <exclude-pattern>/vendor/*</exclude-pattern>

    <!-- TODO: Define minimum supported WordPress version -->
    <config name="minimum_supported_wp_version" value="5.2"/>

    <!-- TODO: Define expected text domains -->
    <rule ref="WordPress.WP.I18n">
        <properties>
            <property name="text_domain" type="array" value="my-plugin,my-theme,woocommerce,sage"/>
        </properties>
    </rule>
</ruleset>
```

Then, define [composer scripts](https://getcomposer.org/doc/articles/scripts.md):

```json
# composer.json
{
  "scripts": {
    "style:check": "phpcs",
    "style:fix": "phpcbf"
  }
}
```

Run the commands:

```sh-session
$ composer style:check
$ composer style:fix
```

## Required Readings

- [Whitelisting code which flags errors](https://github.com/WordPress-Coding-Standards/WordPress-Coding-Standards/wiki/Whitelisting-code-which-flags-errors)
- [Flagged superglobal usage in WordPress VIP](https://github.com/WordPress-Coding-Standards/WordPress-Coding-Standards/wiki/Flagged-superglobal-usage-in-WordPress-VIP)
- [Fixing errors for input data](https://github.com/WordPress-Coding-Standards/WordPress-Coding-Standards/wiki/Fixing-errors-for-input-data)
- [Sanitizing array input data](https://github.com/WordPress-Coding-Standards/WordPress-Coding-Standards/wiki/Sanitizing-array-input-data)
- [Customizable sniff properties](https://github.com/WordPress-Coding-Standards/WordPress-Coding-Standards/wiki/Customizable-sniff-properties)

## FAQs

### Will you add support for older PHP versions?

Never! This plugin will only work on [actively supported PHP versions](https://secure.php.net/supported-versions.php).

Don't use it on **end of life** or **security fixes only** PHP versions.

### It looks awesome. Where can I find some more goodies like this?

- Articles on [Itineris' blog](https://www.itineris.co.uk/blog/)
- More projects on [Itineris' GitHub profile](https://github.com/itinerisltd)
- More plugins on [Itineris](https://profiles.wordpress.org/itinerisltd/#content-plugins) and [TangRufus](https://profiles.wordpress.org/tangrufus/#content-plugins) wp.org profiles
- Follow [@itineris_ltd](https://twitter.com/itineris_ltd) and [@TangRufus](https://twitter.com/tangrufus) on Twitter
- Hire [Itineris](https://www.itineris.co.uk/services/) to build your next awesome site

### This isn't on wp.org. Where can I give a :star::star::star::star::star: review?

Thanks! Glad you like it. It's important to let my boss knows somebody is using this project. Please consider:

- tweet something good with mentioning [@itineris_ltd](https://twitter.com/itineris_ltd) and [@TangRufus](https://twitter.com/tangrufus)
- :star: star this [Github repo](https://github.com/ItinerisLtd/itineris-wp-coding-standards)
- :eyes: watch this [Github repo](https://github.com/ItinerisLtd/itineris-wp-coding-standards)
- write blog posts
- submit [pull requests](https://github.com/ItinerisLtd/itineris-wp-coding-standards)
- [hire Itineris](https://www.itineris.co.uk/services/)

## Feedback

**Please provide feedback!** We want to make this library useful in as many projects as possible.
Please submit an [issue](https://github.com/ItinerisLtd/itineris-wp-coding-standards/issues/new) and point out what you do and don't like, or fork the project and make suggestions.
**No issue is too small.**

## Security

If you discover any security related issues, please email [dev@itineris.co.uk](mailto:dev@itineris.co.uk) instead of using the issue tracker.

## Credits

[Itineris WP Coding Standards](https://github.com/ItinerisLtd/itineris-wp-coding-standards) is a [Itineris Limited](https://www.itineris.co.uk/) project created by [Tang Rufus](https://typist.tech).

Full list of contributors can be found [here](https://github.com/ItinerisLtd/itineris-wp-coding-standards/graphs/contributors).

## License

[Itineris WP Coding Standards](https://github.com/ItinerisLtd/itineris-wp-coding-standards) is released under the [MIT License](https://opensource.org/licenses/MIT).
