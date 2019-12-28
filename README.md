# NodeJS Lambda Layer

Layers are a centrally way to manage common codes and dependencies across shared functions.

This repository shows a simple example to how to create a lambda layer.

## Build
In order to upload a nodejs lambda layer, you must have a folder named **nodejs/** containing all **node_modules** content.

I have created a script that does it automatically. Run `yarn build` or `npm build`.
The following code below does:

```
yarn && //or npm install
mkdir -p nodejs && 
cp -r node_modules nodejs/ && 
zip -r nodejs-layer.zip nodejs
```

1. Install the dependencies.
2. Create a folder.
3. Copy node_modules into nodejs.
4. Zip nodejs folder into a nodejs-layer.zip.

## Deploy/Upload
AWS supports layers by uploading either by S3 or zip file.

Into Lambda section, go to Layer and Add Layer. After that, connect the lambda with the Layer.

Now you can use the dependencies abstracted in layers. 
* Quick remind: Lambda functions can use up to 5 layer and the total size (function + layer(s)) can't exceed 250mb unzipped.

For further details check this [post](https://www.freecodecamp.org/news/lambda-layers-2f80b9211318/) here!

