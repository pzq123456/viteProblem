# vue-project
> This respository just foucs on the problem.
> - Thanks for your help.


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
