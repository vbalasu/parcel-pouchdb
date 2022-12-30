# parcel-pouchdb

Use the following steps to quickly get a PouchDB project up and running

Note that it uses the "json" command line tool to edit package.json inline to add the necessary steps for the ParcelJS bundler. You can install it using `npm install -g json`

[src/index.html](src/index.html)

[package.json](package.json)

```
npm init -y
npm i --save-dev parcel
npm i pouchdb
mkdir src
touch src/index.html
code . #Launch Visual Studio Code to edit src/index.html
### Use the Emmet abbreviation ! to create barebones html
json -f package.json -I -e 'this.scripts.dev="parcel src/index.html"'
json -f package.json -I -e 'this.targets={"default":{"publicUrl": "./"}}'
### Now you can run the development server as follows:
npm run dev
json -f package.json -I -e 'this.scripts.build="parcel build src/index.html"'
### Remove the following line from package.json: 
#### "main": "index.js",
npm run build
python -m http.server
### DEPLOY TO S3
json -f package.json -I -e 'this.scripts.deploy="aws s3 sync dist s3://cloudmatica/parcel-pouchdb --acl public-read"'
npm run deploy
# Get the presigned url as follows:
aws s3 presign s3://cloudmatica/parcel-pouchdb/index.html
```