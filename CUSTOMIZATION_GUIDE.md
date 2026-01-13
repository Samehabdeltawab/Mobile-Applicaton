# دليل التخصيص والتطوير 🎨

## إضافة كلمات وجمل جديدة

### الطريقة السهلة (بدون برمجة)

#### تعديل الجمل الموجودة
افتح الملف: `app/src/main/res/values/strings.xml`

```xml
<!-- غير النصوص اللي عايزها -->
<string name="water">عايز أشرب مية</string>
<string name="food">عايز آكل</string>
```

#### إضافة جمل جديدة
افتح الملف: `app/src/main/java/com/voiceassist/MainActivity.kt`

```kotlin
// ابحث عن القائمة اللي عايز تضيف فيها واكتب جمل جديدة

// مثال: إضافة جمل للاحتياجات الأساسية
private val basicNeedsPhrases = listOf(
    "عايز أشرب مية",
    "عايز آكل",
    "عايز أشرب شاي",        // جملة جديدة
    "عايز أشرب قهوة",       // جملة جديدة
    "عايز أكل فاكهة"        // جملة جديدة
)

// مثال: إضافة جمل للمشاعر
private val feelingsPhrases = listOf(
    "عندي وجع",
    "تعبان",
    "حاسس بدوخة",          // جملة جديدة
    "حاسس بصداع"           // جملة جديدة
)
```

---

## تغيير الألوان 🎨

افتح الملف: `app/src/main/res/values/colors.xml`

```xml
<resources>
    <!-- الألوان الأساسية -->
    <color name="primary">#2196F3</color>          <!-- أزرق -->
    <color name="primary_dark">#1976D2</color>
    <color name="accent">#FF9800</color>           <!-- برتقاني -->
    
    <!-- ألوان الفئات -->
    <color name="category_basic">#4CAF50</color>      <!-- أخضر للاحتياجات -->
    <color name="category_feelings">#2196F3</color>   <!-- أزرق للمشاعر -->
    <color name="category_responses">#FF9800</color>  <!-- برتقاني للردود -->
    <color name="category_questions">#9C27B0</color>  <!-- بنفسجي للأسئلة -->
    
    <!-- زر التحدث -->
    <color name="success">#4CAF50</color>          <!-- أخضر -->
    <!-- زر المسح -->
    <color name="error">#F44336</color>            <!-- أحمر -->
</resources>
```

### أمثلة لألوان مختلفة:
```xml
<!-- ألوان دافئة -->
<color name="primary">#FF5722</color>     <!-- برتقاني محمر -->
<color name="accent">#FFC107</color>      <!-- أصفر ذهبي -->

<!-- ألوان باردة -->
<color name="primary">#00BCD4</color>     <!-- سماوي -->
<color name="accent">#3F51B5</color>      <!-- نيلي -->

<!-- ألوان طبيعية -->
<color name="primary">#8BC34A</color>     <!-- أخضر فاتح -->
<color name="accent">#FF9800</color>      <!-- برتقاني -->
```

---

## تغيير حجم النصوص والأزرار 📏

افتح الملف: `app/src/main/res/values/themes.xml`

```xml
<!-- حجم أزرار الجمل -->
<style name="PhraseButton" parent="Widget.Material3.Button.OutlinedButton">
    <item name="android:layout_height">80dp</item>    <!-- غير الرقم ده -->
    <item name="android:textSize">20sp</item>         <!-- غير الرقم ده -->
</style>

<!-- حجم أزرار الإجراءات (اتكلم/امسح) -->
<style name="ActionButton" parent="Widget.Material3.Button.ElevatedButton">
    <item name="android:layout_height">70dp</item>    <!-- غير الرقم ده -->
    <item name="android:textSize">20sp</item>         <!-- غير الرقم ده -->
</style>
```

### أحجام مقترحة:

**للشاشات الصغيرة:**
- حجم الزر: `70dp`
- حجم النص: `18sp`

**للشاشات المتوسطة (افتراضي):**
- حجم الزر: `80dp`
- حجم النص: `20sp`

**للشاشات الكبيرة:**
- حجم الزر: `100dp`
- حجم النص: `24sp`

---

## إضافة فئة جديدة كاملة 📋

لو عايز تضيف فئة جديدة زي "طلبات" أو "أماكن":

### 1. أضف الجمل في `MainActivity.kt`

```kotlin
// بعد الفئات الموجودة، أضف:
private val placesPhrases = listOf(
    "عايز أروح المستشفى",
    "عايز أروح الصيدلية",
    "عايز أقعد في البلكونة",
    "عايز أنزل",
    "عايز أطلع"
)
```

### 2. أضف لون للفئة في `colors.xml`

```xml
<color name="category_places">#FF5722</color>
```

### 3. أضف عنوان الفئة في `strings.xml`

```xml
<string name="category_places">أماكن</string>
```

### 4. أضف الفئة للواجهة في `activity_main.xml`

```xml
<!-- بعد Questions Category -->
<TextView
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:text="@string/category_places"
    android:textSize="20sp"
    android:textStyle="bold"
    android:textColor="@color/category_places"
    android:padding="8dp" />

<GridLayout
    android:id="@+id/placesGrid"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:columnCount="2"
    android:rowCount="3"
    android:layout_marginBottom="16dp">
</GridLayout>
```

### 5. اربط الفئة بالأزرار في `MainActivity.kt`

```kotlin
// في دالة setupPhraseButtons()، أضف:
placesPhrases.forEach { phrase ->
    addPhraseButton(binding.placesGrid, phrase, R.color.category_places)
}
```

---

## تخصيص سرعة ونبرة الصوت 🔊

افتح الملف: `app/src/main/java/com/voiceassist/TextToSpeechManager.kt`

```kotlin
// ابحث عن الكود ده:
tts?.setPitch(1.0f)           // النبرة: 0.5 (منخفض) → 2.0 (عالي)
tts?.setSpeechRate(0.9f)      // السرعة: 0.5 (بطيء) → 2.0 (سريع)

// جرب قيم مختلفة:
tts?.setPitch(1.2f)           // صوت أعلى شوية
tts?.setSpeechRate(0.7f)      // أبطأ للوضوح
```

---

## إضافة ميزة حفظ الجمل المفضلة ⭐

### الخطوات الأساسية:

1. **إنشاء SharedPreferences للحفظ**
2. **إضافة زر "حفظ كمفضل"**
3. **إضافة قسم للجمل المحفوظة**

الكود الكامل متاح في التحديثات القادمة!

---

## بناء APK للتوزيع 📦

### طريقة 1: من Android Studio

1. **Build** → **Build Bundle(s) / APK(s)** → **Build APK(s)**
2. انتظر لحد ما البناء يخلص
3. هتلاقي الملف في: `app/build/outputs/apk/debug/app-debug.apk`

### طريقة 2: من Terminal

```powershell
cd "d:\Mobile App"
.\gradlew.bat assembleDebug
```

الملف هيكون في: `app\build\outputs\apk\debug\app-debug.apk`

### بناء نسخة Release (موقعة):

```powershell
.\gradlew.bat assembleRelease
```

**ملاحظة:** النسخة Release تحتاج keystore للتوقيع

---

## نصائح للتطوير 💡

### 1. اختبر كل تغيير
- اعمل تغيير صغير
- شغل التطبيق واختبره
- لو شغال كويس، كمل

### 2. احفظ نسخ احتياطية
- اعمل Git repository
- أو انسخ المجلد قبل التعديلات الكبيرة

### 3. استخدم Logcat
- في Android Studio: **View** → **Tool Windows** → **Logcat**
- هتشوف كل رسائل التطبيق والأخطاء

### 4. اقرأ الأخطاء
- لو في خطأ، اقرأه كويس
- عادة بيقول المشكلة فين بالظبط

---

## موارد مفيدة 📚

- **Android Developers**: https://developer.android.com/
- **Kotlin Documentation**: https://kotlinlang.org/docs/
- **Material Design**: https://m3.material.io/
- **Stack Overflow**: https://stackoverflow.com/

---

## محتاج مساعدة؟ 🆘

1. شوف ملف `README.md` للتفاصيل العامة
2. شوف ملف `QUICK_START.md` لبدء التشغيل
3. افتح Issue في المشروع للأسئلة

---

**بالتوفيق في التطوير! 🚀**
