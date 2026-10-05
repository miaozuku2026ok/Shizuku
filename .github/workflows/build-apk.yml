name: Build Miaozuku APK
on:
  push:
    branches: [ "master" ]
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout source
        uses: actions/checkout@v4
        with:
          submodules: recursive
          fetch-depth: 0

      - name: Setup JDK 21
        uses: actions/setup-java@v4
        with:
          java-version: '21'
          distribution: 'temurin'

      - name: Make gradlew executable
        run: chmod +x gradlew

      - name: Build release APK
        run: ./gradlew assembleRelease

      - name: Upload built APK
        uses: actions/upload-artifact@v4
        with:
          name: Shizuku-ReleaseAPK
          path: app/build/outputs/apk/release/app-release-unsigned.apk
