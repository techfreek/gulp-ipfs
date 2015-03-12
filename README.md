# gulp-ipfs
A gulp plugin to add files to ipfs and update links to an ipfs gateway

###This will probably involve having ipfs installed on your dev machine. We will see.

One thing I need to figure out is if people try to add their index.html to the cdn. This is one reason why I haven't started to write any code yet. I've just been trying to figure things like that out.	

#intended implementation

```javascript
	gulp.src('public')
		.pipe(ipfs({
			files: ['public/html/*.html'],
			root: 'public/',
			gateway: 'http://gateway.ipfs.io/'
		}))

```

This example will accomplish:
* replacing root with gateway in all files
* Adding public to ipfs 'ipfs add -r public'

So if you have the following folder structure under public
```
.
|- css
|  |
|  - main.css
|
|- scripts
|  |
|  | - something.js
|  | - whatever.js
|
|- html
   | - index.html

```
and index.html had the following:
```html
<html>
	<head>
		<link rel="stylesheet" href="public/css/main.css">
	</head>
	<body>
		<!-- some content here -->
		<script src="public/scripts/something.js"></script>
		<script src="public/scripts/whatever.js"></script>
	</body>
</html>

```
it would conver that to
```html
<html>
	<head>
		<link rel="stylesheet" href="http://gateway.ipfs.io/(long hash)/css/main.css">
	</head>
	<body>
		<!-- some content here -->
		<script src="http://gateway.ipfs.io/(long hash)/scripts/something.js"></script>
		<script src="http://gateway.ipfs.io/(long hash)/scripts/whatever.js"></script>
	</body>
</html>

#Progress
[] Fully tested
[] Add files to ipfs
[] Update links in files

