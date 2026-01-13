# خطوات رفع ملف Workflow

## الطريقة السريعة:

1. **في صفحة GitHub، اضغط "Add file" → "Create new file"**

2. **اكتب في اسم الملف:**
   ```
   .github/workflows/android-build.yml
   ```

3. **انسخ والصق المحتوى التالي:**

```yaml
name: Android Build

on:
  push:
    branches: [ main, master ]
  pull_request:
    branches: [ main, master ]
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout code
      uses: actions/checkout@v4

    - name: Set up JDK 17
      uses: actions/setup-java@v4
      with:
        java-version: '17'
        distribution: 'temurin'
        cache: gradle

    - name: Grant execute permission for gradlew
      run: chmod +x gradlew

    - name: Build Debug APK
      run: ./gradlew assembleDebug --stacktrace

    - name: Upload APK
      uses: actions/upload-artifact@v4
      with:
        name: voice-assistant-debug
        path: app/build/outputs/apk/debug/app-debug.apk
        retention-days: 30
```

4. **اضغط "Commit changes"**

5. **روح على تبويب Actions**

6. **الـ Build هيبدأ تلقائياً!**
