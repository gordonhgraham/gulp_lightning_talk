Install `gulp` globally so you can run it from the terminal:

```sh
$ npm install -g gulp
```

Now install `gulp` locally for your project:

```sh
$ npm install -D gulp
```

Create a `gulpfile.js`
```sh
$ touch gulpfile.js
```
Lets make a task. Add this text to your `gulpfile.js`:

```js
var gulp = require(`gulp`);

gulp.task(`default`, () => {
  console.log(`The gulp default task ran!`)
});
```
Now run `gulp`
```sh
$ gulp
```
Wahoo! We installed and configured gulp.

Lets add another task to our `gulpfile.js`
```js
gulp.task(`pipeStuff`, () => {
  gulp
    .src(`./src/**/*.js`)
    .pipe(gulp.dest(`./build`))
})
```

Now, to run our task `pipeStuff` lets add it to the default task.

```js
gulp.task(`default`, [`pipeStuff`], () => {
  console.log(`The gulp default task ran!`)
})
```
A build directory should have been created containing everything we piped in there.

Lets make this pipe more useful. We'll use it to minify our code.

First, we need to install node module to help us, `UglifyJS`

```sh
$ npm i -D gulp-uglify
```

Remember to require it in your `gulpfile.js`
```js
const uglify = require(`gulp-uglify`)
```

Now, we'll add another task to our `gulpfile.js`
```js
gulp.task(`minify`, () => {
	return gulp.src(`./src/**/*.js`)
		.pipe(uglify())
		.pipe(gulp.dest(`./min`))
})
```

Lets check to see that a `min` directory has been created. What's in the files?

Yay gulp!
