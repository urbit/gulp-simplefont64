# gulp-simplefont64

This is a fork of [gulp-simplefont64](https://github.com/joshblack/gulp-simplefont64) which changes the order of the `@font-face` properties. We needed to do this in order to make the output valid for some reason.

For `gulp-simplefont64`, just name your fonts in the following format:

> FontFamily-Style1-Style2...

For example:

> PlayfairDisplay-Black-Italic.otf

And `gulp-simplefont64` will give it the appropriate rulesets underneath the PlayfairDisplay font family (`font-weight: 800;` and `font-style: italic;`).

## Example

#### gulpfile.js

```js
var gulp = require('gulp');
var font64 = require('gulp-simplefont64');

gulp.task('fonts', function() {
    return gulp.src(['src/fonts/**/*.otf', 'src/fonts/**/*.ttf'])
        .pipe(font64())
        .pipe(gulp.dest('dist/stylesheets/'));
});
```

#### Contents of "src/fonts":

```bash
    +-- src
    |   +--fonts
    |      +-- PlayfairDisplay-Black-Italic.otf
```

#### Result of plugin (fork):

```css
@font-face {
  font-family: Inter;
  src: url("inter/data: font/opentype;charset=utf-8; base64,T1RUTwAMAIAAAwBAQ0ZGICNw7jIAABE8AAFw1UdERUYSkBS7AAGPSAAAAERHUE9TXJ5OgwABqaAAAJDYR1NVQmMeE9EAAY+MAAAaFE9TLzJuRIYyAAABMAAAAGBjbWFw5kH1tQAACbgAAAdkaGVhZANwzXwAAADMAAAANmhoZWERJQwdAAABBAAAACRobXR4PCvh+gABghQAAA00bWF4cANNUAAAAAEoAAAABm5hbWUD6eGxAAABkAAACCdwb3N0/zwAKQAAERwAAAAgAAEAAAABAQbN9rJqXw889QADCAAAAAAAzmtAdgAAAADOa0B2/Qr9/);
  font-weight: 800;
  font-style: italic;
};
```
