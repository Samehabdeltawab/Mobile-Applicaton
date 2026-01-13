# رفع المشروع على GitHub - الحل النهائي

## المشكلة:
Git محتاج تسجيل دخول

## الحل الأسهل: GitHub Desktop

### الخطوات:

1. **حمل GitHub Desktop**
   https://desktop.github.com/

2. **سجل دخول بحسابك**
   - File → Options → Sign in

3. **أضف المشروع:**
   - File → Add Local Repository
   - اختر: `d:\Mobile App`
   - إذا قال "not a git repository":
     - اختار "Create Repository" بدلاً من Add
     - Repository path: `d:\Mobile App`
     - اضغط Create

4. **ارفع على GitHub:**
   - اكتب Commit message: "Complete Android project"
   - اضغط **Commit to main**
   - اضغط **Publish repository**
   - أو اضغط **Push origin**

5. **تأكد من الرفع:**
   - روح على: https://github.com/Samehabdeltawab/Contact-Mobile-App
   - تأكد من وجود مجلد `app/`

6. **شغل GitHub Actions:**
   - تبويب Actions
   - هيشتغل تلقائياً
   - أو اضغط "Run workflow"

---

## بديل: استخدام Personal Access Token

إذا كنت تريد استخدام Command Line:

1. روح على GitHub → Settings → Developer settings
2. Personal Access Tokens → Generate new token
3. اختار: repo (كل الصلاحيات)
4. انسخ التوكن

في Terminal:
```powershell
cd "d:\Mobile App"
git push https://TOKEN@github.com/Samehabdeltawab/Contact-Mobile-App.git main --force
```
(استبدل TOKEN بالتوكن الحقيقي)

---

## التوصية: 
**استخدم GitHub Desktop - أسهل وأسرع! ✅**
