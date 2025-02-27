# 📌 **`EXISTS` في SQL – التحقق من وجود بيانات في استعلام فرعي**

## 🔹 **ما هو `EXISTS` في SQL؟**

🚀 **`EXISTS`** هو **عامل منطقي (`Boolean Operator`) يُستخدم للتحقق مما إذا كان استعلام فرعي (`Subquery`) يُرجع أي صفوف**.  
✅ **يُعيد `TRUE` إذا وجد صفًا واحدًا على الأقل، و `FALSE` إذا لم يجد شيئًا**.  
✅ **يُستخدم عادةً مع `WHERE` للتحقق من وجود بيانات في جدول مرتبط**.

---

## 🔹 **الصيغة العامة (`Syntax`)**

```sql
SELECT column_name(s)  
FROM table_name  
WHERE EXISTS (subquery);
```

📌 **`subquery` هو استعلام داخلي يُرجع مجموعة بيانات لفحصها.**  
📌 **إذا أرجع الاستعلام الفرعي أي صف، فإن `EXISTS` يُعيد `TRUE`، وإلا يُعيد `FALSE`**.

---

## 🔹 **مثال عملي على `EXISTS`**

### 🗄️ **جدول `customers` (العملاء)**

|customer_id|name|
|---|---|
|1|Ali|
|2|Sara|
|3|Omar|

### 🗄️ **جدول `orders` (الطلبات)**

|order_id|customer_id|amount|
|---|---|---|
|101|1|200|
|102|2|150|
|103|1|300|

---

### 🎯 **1️⃣ إظهار العملاء الذين لديهم طلبات (`EXISTS`)**

```sql
SELECT name  
FROM customers  
WHERE EXISTS (SELECT 1 FROM orders WHERE orders.customer_id = customers.customer_id);
```

🔹 **النتيجة:**

|name|
|---|
|Ali|
|Sara|

📌 **تم إرجاع العملاء الذين لديهم طلبات فقط، بينما لم يظهر `Omar` لأنه ليس لديه طلبات في جدول `orders`.**  
📌 **الاستعلام الفرعي `SELECT 1 FROM orders ...` يُعيد صفًا واحدًا على الأقل إذا وجد طلبًا للعميل، مما يجعل `EXISTS` تُرجع `TRUE`.**

---

### 🎯 **2️⃣ البحث عن العملاء الذين ليس لديهم طلبات (`NOT EXISTS`)**

```sql
SELECT name  
FROM customers  
WHERE NOT EXISTS (SELECT 1 FROM orders WHERE orders.customer_id = customers.customer_id);
```

🔹 **النتيجة:**

|name|
|---|
|Omar|

📌 **تم عرض العملاء الذين ليس لديهم أي طلبات فقط (`NOT EXISTS`).**

---

### 🎯 **3️⃣ استخدام `EXISTS` مع شرط إضافي**

**إظهار العملاء الذين لديهم طلبات بقيمة أكبر من 250:**

```sql
SELECT name  
FROM customers  
WHERE EXISTS (SELECT 1 FROM orders WHERE orders.customer_id = customers.customer_id AND amount > 250);
```

🔹 **النتيجة:**

|name|
|---|
|Ali|

📌 **تم عرض `Ali` فقط لأنه العميل الوحيد الذي لديه طلب بقيمة أكبر من 250.**

---

## 🏆 **ملخص سريع عن `EXISTS`**

|الميزة|التفاصيل|
|---|---|
|**يُستخدم للتحقق من وجود صفوف في استعلام فرعي**|✅|
|**يُعيد `TRUE` إذا وجد بيانات، وإلا `FALSE`**|✅|
|**أسرع من `IN` في بعض الحالات، خاصة مع جداول كبيرة**|✅|
|**`NOT EXISTS` يُستخدم للتحقق من عدم وجود بيانات**|✅|

---

## 🎯 **الخلاصة**

- **`EXISTS`** يُستخدم **للتحقق مما إذا كان استعلام فرعي يُرجع أي بيانات**.
- **يُعيد `TRUE` إذا وجد بيانات، وإلا يُعيد `FALSE`**.
- **`NOT EXISTS` يُستخدم للبحث عن الصفوف التي لا تحقق شرط معين**.
- **فعال في تحسين الأداء عند التعامل مع جداول كبيرة مقارنة بـ `IN` في بعض الحالات**.

---


## Connect Me :

- https://github.com/foefvjfev33
- https://t.me/It_auf
- https://www.youtube.com/@IT_red-j9b
- https://www.linkedin.com/in/mohamed-auf-860537353/