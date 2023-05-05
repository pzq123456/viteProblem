# cornerstone3D-vite config problem and one possible solution
> Thanks for the help from [sedghi](https://github.com/sedghi)
> There must be some more elegant solutions, but this is the one worked for me. If you have any better ideas, please let me know in the issue or PR.

- find the `dynamic-import` folder in the `dicom-image-loader` package and copy it to the `src` folder.
- add the following code in the `vite.config.js` file:
```js
server: {
    headers: {
        'Cross-Origin-Embedder-Policy': 'require-corp',
        'Cross-Origin-Opener-Policy': 'same-origin'
    }
  }
```
> - see the [issue](https://github.com/cornerstonejs/cornerstone3D-beta/issues/594)
> - If you meet the `304` problem, you can try "CTRL + F5" to refresh the page.

## Background
> see the related [issue](https://github.com/cornerstonejs/cornerstone3D-beta/issues/594) in [cornerstone3D-beta](https://github.com/cornerstonejs/cornerstone3D-beta).
When we use vite to run the example code, we can't get the webworker-file and the error is like this:
```sh
:5173/src/index.worker.ea71efba2ce63c499055.worker.js:1 
        Failed to load resource: the server responded with a status of 404 (Not Found)
:5173/src/index.worker.ea71efba2ce63c499055.worker.js:1 
```
It looks like the `vite` can't find the webworker-file. In the `dicom-image-loader` package, we can find that the worker files have been built in the `dynamic-import` folder. 

> correct [config](https://cn.vitejs.dev/guide/features.html#web-workers) in vite may help us to solve this problem.

## New problem after solving the first one
When I find those missing files, I put them in the `src` folder and run the code again. The error is like this:
```sh
decodeImageFrame.ts:266  Uncaught (in promise) ReferenceError: SharedArrayBuffer is not defined
    at decodeImageFrame.ts:266:51
    at U (decodeImageFrame.ts:154:25)
    at async Object.handler (decodeTask.ts:51:9)
```



## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```
