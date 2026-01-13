# بناء التطبيق باستخدام VS Code

## الخطوات:

### 1. تثبيت VS Code (إذا مسموح)
- من: https://code.visualstudio.com/
- أو استخدم Portable Version

### 2. تثبيت Extensions
ابحث في VS Code Extensions عن:
- **Android iOS Emulator** - لتشغيل المحاكي
- **Gradle for Java** - لبناء المشروع

### 3. فتح المشروع
- File → Open Folder
- اختر `d:\Mobile App`

### 4. تشغيل Build من Terminal
في VS Code Terminal:
```powershell
# تأكد من وجود Java
java -version

# بناء المشروع
.\gradlew.bat assembleDebug
```

### 5. استخراج APK
ستجده في: `app\build\outputs\apk\debug\app-debug.apk`
