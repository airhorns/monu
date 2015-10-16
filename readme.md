
##### Developing

```bash
npm install # installs electron and all the deps needed for monu
npm run app # runs the app in the electron wrapper
npm run build # builds the mac app
```

##### Publishing

Before publishing, make sure that your repo is clean, and that you've created a tag for the latest commit. `npm version [major|minor|patch]` will do this for you, increasing the package.json version, creating a commit and adding a tag.

You should see something like this:

```
🐈  make publish
rm -rf Monu.app Monu.zip # prevent duplicates in the final bundle
npm run build

> monu@1.0.4 build /Users/maxogden/src/js/monu
> electron-packager . Monu --platform=darwin --arch=x64 --version=0.26.0 --ignore=node_modules/electron

Wrote new app to /Users/maxogden/src/js/monu/Monu.app
ditto -c -k --sequesterRsrc --keepParent Monu.app Monu.zip
npm run publish

> monu@1.0.4 publish /Users/maxogden/src/js/monu
> publish-release --template notes.md --assets Monu.zip

? Git Tag: v1.0.4
? Github repository owner: maxogden
? Github repository name: monu
? Release Name: Monu v1.0.4 Alpha

Uploading Monu.zip
[=================================================>] 100.0% (1.17 MB/s)
Done! Published at: https://github.com/maxogden/monu/releases/tag/v1.0.4
```
