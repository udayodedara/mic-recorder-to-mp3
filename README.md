# Microphone Recorder to Mp3

Record your microphone audio input and get an ```audio/mp3``` file in the end.

# Install

## Yarn

```bash
yarn add github:udayodedara/mic-recorder-to-mp3
```

## npm

```bash
npm install github:udayodedara/mic-recorder-to-mp3
```

## CDN Usage

You can add via CDN using the address: [https://unpkg.com/mic-recorder-to-mp3@2.2.1](https://unpkg.com/mic-recorder-to-mp3@2.2.1). You can find the minified version in the same address, ex: [https://unpkg.com/mic-recorder-to-mp3@2.2.1/dist/index.min.js](https://unpkg.com/mic-recorder-to-mp3@2.2.1/dist/index.min.js)

**About the version in URL**: Change the URL version to any of our releases, or use https://unpkg.com/mic-recorder-to-mp3 to automatically use the latest version.

# Development

- Watch for changes:

```bash
npm run watch
```

- Regular build:

```bash
npm run build
```

# How to use

```js
const MicRecorder = require('mic-recorder-to-mp3');

// New instance
const recorder = new MicRecorder({
  bitRate: 128
});

// if you are already using stream from navigator then you can directly add stream to recorder which can save 200ms of time.
recorder.startWithStream(stream).then(() => {
  // something else
}).catch((e) => {
  console.error(e);
});

// Start recording. Browser will request permission to use your microphone.
recorder.start().then(() => {
  // something else
}).catch((e) => {
  console.error(e);
});

// Once you are done singing your best song, stop and get the mp3.
recorder
.stop()
.getMp3().then(([buffer, blob]) => {
  // do what ever you want with buffer and blob
  // Example: Create a mp3 file and play
  const file = new File(buffer, 'me-at-thevoice.mp3', {
    type: blob.type,
    lastModified: Date.now()
  });

  const player = new Audio(URL.createObjectURL(file));
  player.play();

}).catch((e) => {
  alert('We could not retrieve your message');
  console.log(e);
});
```

- Check the [samples](https://github.com/closeio/mic-recorder-to-mp3/tree/master/samples) folder for more examples.

- [Live example on jsfiddle](https://jsfiddle.net/8u5fbpx6/1/)

## Lamejs Notice

This library uses lamejs as a direct dependency. We build our releases with [lamejs](https://github.com/zhuker/lamejs/) built-in, so you don't need to add another dependency.

Thanks to **@zhuker** for writing the lamejs library.

# License

MIT
