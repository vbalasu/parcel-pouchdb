# parcel-pouchdb

Use the following steps to quickly get a PouchDB project up and running

Note that it uses the "json" command line tool to edit package.json inline to add the necessary steps for the ParcelJS bundler. You can install it using `npm install -g json`

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
```

[src/index.html](src/index.html)

[package.json](package.json)
