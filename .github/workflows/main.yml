
name: Build RR Pay Android APK

on:
  workflow_dispatch:
  push:
    paths:
      - 'RR_Pay_Android_Prototype.zip'
      - '.github/workflows/android-apk.yml'

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Set up Java
        uses: actions/setup-java@v4
        with:
          distribution: temurin
          java-version: '17'

      - name: Set up Gradle
        uses: gradle/actions/setup-gradle@v4
        with:
          gradle-version: '8.7'

      - name: Set up Android SDK
        uses: android-actions/setup-android@v3

      - name: Extract RR Pay source
        run: unzip -o RR_Pay_Android_Prototype.zip

      - name: Build debug APK
        working-directory: RR_Pay_Android_Prototype
        run: gradle assembleDebug

      - name: Upload APK
        uses: actions/upload-artifact@v4
        with:
          name: RR-Pay-Debug-APK
          path: RR_Pay_Android_Prototype/app/build/outputs/apk/debug/app-debug.apk
