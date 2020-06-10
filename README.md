# Speech-AI-Transcribe Tool

## About

Speech-AI-Transcribe is a powerful tool for converting spoken language to written text directly in the browser. It uses advanced speech recognition technology and is easy to integrate into many types of projects. This tool is especially useful for those needing transcription of media files or real-time audio streams.

## Examples

Click on the images below to watch the videos:

### Example Video

https://content.jwplatform.com/videos/PeDseSR6-vRNXRpvq.mp4

## Video On Demand (VOD) Content or Streams

In the [main example](examples), you can see how to create movies where the word being said is highlighted. 
### Additional Examples



## How to Install

### Preparation Steps

First, make sure Node.js is installed on your computer.

Next, add the module to your project by running:

```bash
npm install speech-ai-transcribe
```

## How to Use It

The Speech-AI-Transcribe offers two main ways to work: **FileTranscriber** for files and **StreamTranscriber** for live audio.

### Server Setup

Make sure your web server is set to handle files correctly:

- `"Cross-Origin-Embedder-Policy": "require-corp"`
- `"Cross-Origin-Opener-Policy": "same-origin"`

### NPM Way

If you use npm, install the package and move needed files to your project folder:

```bash
npm install --save speech-ai-transcribe
cp node_modules/speech-ai-transcribe/dist/* /your/project
```

### Manual Way

If not using a package manager, download and copy the `dist/` files from the repository to your project manually:

```html
<script type="importmap">
{
  "imports": {
    "speech-ai-transcribe": "/path/to/speech-ai-transcribe.js"
  }
}
</script>
<script type="module">
  import { FileTranscriber } from "speech-ai-transcribe";
  ...
</script>
```

## Example to Follow

To make your audio or video files into text, setup the transcriber with model and worker path:

```js
import { FileTranscriber } from "speech-ai-transcribe";

const myTranscriber = new FileTranscriber({
  model: "/path/to/model.bin",
  workerPath: "/path/to/worker"
});

await myTranscriber.init();

const result = await myTranscriber.transcribe("/path/to/file.mp3");
console.log(result);
```

You get a JSON object with text parts, times, and chance scores.

## How to Develop

For those interested in contributing or tweaking:

```bash
git clone https://github.com/aresobus/speech-ai-transcribe
cd speech-ai-transcribe
npm install
npm run dev
```

Open `http://localhost:9876/examples/index.html` to see your changes in a local development setup.


## Testing

Run unit tests and functional tests with:

```bash
npm run test:unit
npm run test:e2e
```

Create TypeScript definitions from JSDoc:

```bash
npm run generate-types
```

## Thanks

Big thanks to many open source projects and contributors that help make Speech-AI-Transcribe possible.

## License

This project is shared under the MIT License, allowing everyone to use, change, and share within the license terms.