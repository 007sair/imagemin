# imagemin-input [![Build Status](https://travis-ci.org/imagemin/imagemin.svg?branch=master)](https://travis-ci.org/imagemin/imagemin)

> Minify images seamlessly

Fork自[https://github.com/imagemin/imagemin](https://github.com/imagemin/imagemin)

## Install

```
$ npm install imagemin-input
```


## Usage

```js
const imagemin = require('imagemin');
const imageminJpegtran = require('imagemin-jpegtran');
const imageminPngquant = require('imagemin-pngquant');

(async () => {
	const files = await imagemin(['images/*.{jpg,png}'], 'build/images', {
		input: true, // 如果有这个字段，返回结果中就会新增 input 字段
		plugins: [
			imageminJpegtran(),
			imageminPngquant({
				quality: [0.6, 0.8]
			})
		]
	});

	console.log(files);
	//=> [{data: <Buffer 89 50 4e …>, path: 'build/images/foo.jpg'}, …]
})();
```


## API

### imagemin(input, [output], [options])

Returns `Promise<Object[]>` in the format `{data: Buffer, path: string}`.

#### input

Type: `string[]`

Files to be optimized. See supported `minimatch` [patterns](https://github.com/isaacs/minimatch#usage).

#### output

Type: `string`

Set the destination folder to where your files will be written. If no destination is specified no files will be written.

#### options

Type: `Object`

##### input

Type: `boolean`

为 true 时返回的数据中会携带 input 属性，值为源文件path，字符串类型。默认为`false`。

##### log

Type: `boolean`

为 true 时会在控制台输出 压缩信息，格式：`[源文件]: 大小(kb) -> [压缩后的文件]: 大小(kb)`，默认为`false`。

##### plugins

Type: `Array`

[Plugins](https://www.npmjs.com/browse/keyword/imageminplugin) to use.

### imagemin.buffer(buffer, [options])

Returns `Promise<Buffer>`.

#### buffer

Type: `Buffer`

Buffer to optimize.

#### options

Type: `Object`

##### plugins

Type: `Array`

[Plugins](https://www.npmjs.com/browse/keyword/imageminplugin) to use.


## Related

- [imagemin-cli](https://github.com/imagemin/imagemin-cli) - CLI for this module
- [imagemin-app](https://github.com/imagemin/imagemin-app) - GUI app for this module
- [gulp-imagemin](https://github.com/sindresorhus/gulp-imagemin) - Gulp plugin
- [grunt-contrib-imagemin](https://github.com/gruntjs/grunt-contrib-imagemin) - Grunt plugin


## License

MIT © [imagemin](https://github.com/imagemin)
