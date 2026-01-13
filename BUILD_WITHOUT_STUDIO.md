# بناء التطبيق بدون Android Studio

## المتطلبات الأساسية:
1. Java JDK (يمكن تحميله portable)
2. Gradle (موجود في المشروع)

## الخطوات:

### 1. تحميل JDK Portable
حمل من: https://adoptium.net/temurin/releases/
- اختر Windows x64
- اختر ZIP (بدون تثبيت)
- فك الضغط في مجلد مثل `C:\Java`

### 2. تعيين JAVA_HOME
```powershell
# في PowerShell
$env:JAVA_HOME = "C:\Java\jdk-17.0.9"  # غير المسار حسب موقع Java
$env:PATH = "$env:JAVA_HOME\bin;$env:PATH"
```

### 3. بناء التطبيق
```powershell
cd "d:\Mobile App"

# تنظيف
.\gradlew.bat clean

# بناء Debug APK
.\gradlew.bat assembleDebug
```

### 4. العثور على APK
الملف سيكون في:
```
d:\Mobile App\app\build\outputs\apk\debug\app-debug.apk
```

### 5. نقل APK للموبايل
- انسخ الملف على الموبايل عبر USB
- أو ارفعه على Google Drive/OneDrive
- ثبته مباشرة على الموبايل

## ملاحظات:
- Debug APK يعمل مباشرة بدون توقيع
- لا يحتاج Play Store
- يمكن تثبيته مباشرة (قد تحتاج تفعيل "مصادر غير معروفة")
