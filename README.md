# Docker image to run tests with Chrome headless

This Docker contains:

* node 8.x
* ruby 2.5.x
* npm and yarn latest
* Google Chrome latest
* codeceptjs latest
* protractor 5.3.1

# Usage

To use this image as is, you might need to build and run your website in another container image or if you are building a webapp, you can serve it in the `beforeLaunch` of `protractor.conf.js`:
```
baseUrl: 'http://localhost:3001',
beforeLaunch: () => {
  require('connect')().use(require('serve-static')('public')).listen(3001);
},
```

## Gitlab CI

To use on gitlab, edit your `.gitlab-ci.yml` test stage:
```
test:
  image: mebibou/docker-node-ruby-chrome
  script:
    - npm install
    - npm test
```
