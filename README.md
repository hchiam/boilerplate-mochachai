# Learning `mocha` `chai`

Created from <https://github.com/freeCodeCamp/boilerplate-mochachai>

Just one of the things I'm learning. <https://github.com/hchiam/learning>

You can see from the [`tests`](https://github.com/hchiam/boilerplate-mochachai/tree/gomix/tests) folder that this repo's setup can do both [unit tests](https://github.com/hchiam/boilerplate-mochachai/blob/gomix/tests/1_unit-tests.js) (function input/output) and [functional tests](https://github.com/hchiam/boilerplate-mochachai/blob/gomix/tests/1_unit-tests.js) (user inputs/clicks/etc.).

```bash
npm run test-u # unit tests
npm run test-f # functional tests
```

<https://glitch.com/edit/#!/boilerplate-mochachai-hchiam>

<https://boilerplate-mochachai-hchiam.glitch.me>

```js
var chai = require('chai');
var assert = chai.assert;
var server = require('../server'); // import the Express app
var chaiHttp = require('chai-http');
chai.use(chaiHttp);
```

```js
assert.equal(1, 1);
```

```js
chai.request(server)
  .get('/hello?name=Your Name')
  .end(function(err, res) {
    assert.equal(res.status, 200);
    assert.equal(res.text, 'hello Your Name');
    done();
  });
```

```js
chai.request(server)
  .put('/travellers')
  .send({surname: 'Polo'})
  .end(function(err, res) {
    assert.equal(res.status, 200);
    assert.equal(res.text, 'hello Your Name');
    done();
  });
```

```js
// headless test of page at URL: https://boilerplate-mochachai-hchiam.glitch.me
Browser.site = 'https://boilerplate-mochachai-hchiam.glitch.me';
...
const browser = new Browser();
...
browser
  .fill('surname', 'Polo')
  .then(() => browser.pressButton('submit', function() {
    browser.assert.success();
    browser.assert.text('span#name', 'Marco');
    browser.assert.text('span#surname', 'Polo');
    browser.assert.element('span#dates', 1); // element has count = 1
    done(); // since async test, must call done()
  }));
```
