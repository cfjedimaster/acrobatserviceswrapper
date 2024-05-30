# Acrobat Services Wrapper

This is a simple, lightweight wrapper to the [Acrobat Services](https://developer.adobe.com/document-services/) REST API. To use this, you will need a set of credentials (a client ID and secret) which can be gotten for free.

## Usage

Initialize the library with your credentials:

```js
let sw = new ServicesWrapper(process.env.CLIENTID, process.env.CLIENTSECRET);
```

Upload assets by path and media type:

```js
let filePath = '../source_pdfs/schoolcalendar.pdf';
let mediaType = 'application/pdf';

let asset = await sw.upload(filePath, mediaType);
```

Note that this wraps the 2 step REST process of creating the asset and uploading the bits.

Call an endpoint:

```js
let job = await sw.createExtractJob(asset);
console.log('Extract job started.');
```

You can `pollJob`, which will hit the job status until done. 

You can `downloadFile` to get the result.

And you can `downloadWhenDone(job, path)` to simplify the above.
