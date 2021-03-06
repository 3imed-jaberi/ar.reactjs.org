---
id: testing
title: نظرة عامة على الاختبارات
permalink: docs/testing.html
redirect_from:
  - "community/testing.html"
next: testing-recipes.html
---

بإمكانك اختبار مكوّنات React بطريقة مشابهة لاختبارك اي كود جافاسكريبت آخر.

هناك عدة طرق لاختبار مكوّنات React. بشكل عام ، يتم تقسيمهم إلى فئتين:

* **تصيير أشجار المكوّنات** في بيئة اختبار مبسطة والتأكيد على مخرجاتها.
* **تشغيل تطبيق كامل** في بيئة متصفح واقعية (تُعرف أيضًا باسم اختبارات  end-to-end).

يُركز قسم المستندات هذا على إستراتيجيات الاختبار للحالة الأولى. على الرغم من أن الاختبارات الكاملة من النوع (end-to-end) يمكن أن تكون مفيدة جدًا لمنع الإنحدارات إلى مهام سير العمل الهامة ،مثل هذه الاختبارات لا تتعلق بمكوّنات React على وجه الخصوص ، وهي خارج نطاق هذا القسم.

### المقايضات {#tradeoffs}

عند إختيار أدوات الاختبار ، يجدر التفكير في بعض المقايضات:
* **سرعة التكرار مقابل البيئة الواقعية:** تقدم بعض الأدوات حلقة ردود فعل سريعة للغاية بين إجراء التغيير ورؤية النتيجة، ولكنها لا تُحاكي سلوك المتصفح بدقة. بعض الأدوات الأخرى تستخدم بيئة متصفح واقعية، لكن ذلك يقلل سرعة التكرار وتكون غير مستقرة على خادم التكامل المستمر.

* **كمية عمليات التقليد:** مع المكوّنات ، يمكن أن يكون الفرق بين اختبار "الوحدة (unit)" و "التكامل (integration)" غير واضح. مثلا إذا كنت تختبر إستمارة ، فهل يجب على الاختبار ان يشمل أيضًا اختبار الأزرار الموجودة بداخلها؟ أم هل يجب أن يكون لمكوّن الزر مجموعة اختبارات خاصة به؟ هل يجب أن تؤدي إعادة هيكلة الزر إلى تعطيل اختبار الإستمارة ؟

تختلف الإجابات بإختلاف فرق العمل والمنتجات.

### الأدوات المُوصى بها{#tools}

**[Jest](https://facebook.github.io/jest/)** هو مشغل اختبارات جافاسكريبت يتيح لك الوصول الى ال DOM بواسطة [`jsdom`](/docs/testing-environments.html#mocking-a-rendering-surface). على الرغم من أن jsdom عبارة عن مجرد صورة تقريبية عن كيفية عمل المتصفح، لكنها غالباً جيدة لاختبار مكوّنات React. يوفر Jest سرعة تكرار رائعة مقترنة بميزات قوية مثل تقليد  [المكتبات](/docs/testing-environments.html#mocking-modules) و [المؤقتات](/docs/testing-environments.html#mocking-timers) بحيث يمكنك التحكم بشكل أكبر في كيفية تنفيذ الكود.

**[مكتبة اختبارات React](https://testing-library.com/react)** هي مجموعة من الأدوات والحزم المساعدة التي تتيح لك  اختبار مكوّنات React دون الإعتماد على تفاصيل تنفيذها. هذا  النهج يجعل عملية إعادة الهيكلة سهلة جدا كما يدفعك نحو إتباع أفضل الممارسات لإتاحة سهولة الوصول. على الرغم من انها لا تُقدم طريقة لتصيير مكوّن بصورة سطحية بدون العناصر الأبناء، يتيح لك مشغل اختبارات مثل Jest ذلك عبر [التقليد](/docs/testing-recipes.html#mocking-modules).

### تعلم أكثر {#learn-more}

ينقسم هذا القسم إلى صفحتين:

- [طرق إجراء الاختبارات](/docs/testing-recipes.html): الأنماط الشائعة عند كتابة اختبارات مكوّنات React.  
- [بيئة و محيط الاختبارات](/docs/testing-environments.html): ما يجب مُراعاته عند إعداد بيئة اختبار لمكوّنات React.
