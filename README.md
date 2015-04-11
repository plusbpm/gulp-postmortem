gulp-postmortem
=========

Execute Gulp tasks when exiting a gulp task (useful for watchers).


#Basic Usage

```javascript
var gulp = require('gulp'),
	postMortem = require('gulp-postmortem');


gulp.task('stop-server', function () {
	// Do something amazing
});

gulp.task('sass', function () {
	gulp.src('./scss/*.scss')
	    .pipe(postMortem({gulp: gulp, tasks: ['stop-server']}))
		.pipe(sass())
		.pipe(watch('web/static/sass/**/*.scss', {verbose: true}))
		.pipe(gulp.dest('./css'));
});
```