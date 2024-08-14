# s3-glob

Retrieve object list entries in S3 using minimatch-style globbing.

Forked from unmaintained [izaakschroeder/s3-glob](https://github.com/izaakschroeder/s3-glob).

Features:
 * Full support for minimatch-style syntax,
 * Streaming output,
 * Ready for piping into S3.getObject or S3.headObject.

```javascript
var GlobStream = require('s3-glob');

var stream = new GlobStream([ 's3://my-bucket/*.jpg', '!test*' ]);

stream.on('readable', function() {
	var entry;
	while (null !== (entry = this.read())) {
		console.log(entry);
	}
});
```

```javascript
var GlobStream = require('s3-glob');

var stream = GlobStream([ 's3://my-bucket/*.jpg' ], { format: 'query' });
//...
```
