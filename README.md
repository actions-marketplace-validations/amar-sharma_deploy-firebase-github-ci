# Deploy to Firebase

A GitHub Action to deploy to Firebase Functions, Storage, and Firestore

- Make sure you have the `firebase.json` file in the repository
- Get the Firebase token by running `firebase login:ci` and [store it](https://help.github.com/en/actions/configuring-and-managing-workflows/creating-and-storing-encrypted-secrets) as the `FIREBASE_TOKEN` secret

Example workflow

```
name: Firebase
on:
  push:
    branches:
    - master
jobs:
  main:
    name: Deploy
    runs-on: ubuntu-latest
    steps:
    - name: Check out code
      uses: actions/checkout@main
    - name: Deploy to Firebase
      uses: amar-sharma/deploy-firebase-github-ci@latest
      env:
        FIREBASE_TOKEN: ${{ secrets.FIREBASE_TOKEN }}
        FIREBASE_PROJECT: 'YOUR_FIREBASE_PROJECT'
        FIREBASE_OPTIONS: '--only functions // Any command that needs to be passed to firebase deploy'
```
