# Ember Attrs Validations

Gone are the days where you forgot to pass an attribute from a parent to a child component.
This addon will throw an error *only* in your test runs whenever a required attribute is undefined or its type is invalid.

## Compatibility

Supports Ember CLI v2.4 LTS.

I'm planning to support only the latest [LTS](http://emberjs.com/blog/2016/02/25/announcing-embers-first-lts.html) versions of Ember. I won't be doing tests for any versions other than that.

## Usage

To install this addon using Ember CLI, use this command:

```bash
$ ember install ember-attrs-validations
```

Then in your component.js:

```js
import Ember from 'ember';
import AttrsValidationsMixin from 'ember-attrs-validations/mixins/validations';

const {
  Component
} = Ember;

export default Component.extend(AttrsValidationsMixin, {
  attrValidations: {
    firstName: {
      isRequired: true,
      type: 'string'
    },
    lastName: {
      isRequired: true,
      type: 'string'
    },
    age: {
      isRequired: true,
      type: 'number'
    }
  }
});
```

Currently only supports validations for required fields and data type. To see what types are available, see [Ember.typeOf](http://emberjs.com/api/classes/Ember.html#method_typeOf).

## Caveat

When your data is async, the `isRequired` will fail since the data originally will be undefined
until it resolves and passes the correct value.

Current workarounds:

* Make sure async data resolves first before rendering component (e.g. use handlebar `if` helper).
* Make `isRequired` to false since in essence, you're allowing the attr to be undefined if you use async.

I don't have any plans as of the moment to seemlessly support async data. I'm open to PRs if anyone
has a good idea on how to handle it.

## Installation

* `git clone` this repository
* `npm install`
* `bower install`

## Running

* `ember server`
* Visit your app at http://localhost:4200.

## Running Tests

* `npm test` (Runs `ember try:testall` to test your addon against multiple Ember versions)
* `ember test`
* `ember test --server`

## Building

* `ember build`

For more information on using ember-cli, visit [http://www.ember-cli.com/](http://www.ember-cli.com/).
