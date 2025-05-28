# 📚 Day 43 – Reflections and Annotations in Java

Welcome to **Day 43** of your Java adventure! Today we dove into the **meta-magical world of Java Reflection and Annotations** — the secret sauce behind frameworks like Spring, Hibernate, and your favorite test runners.

---

## 🧠 What We Learned

### ✅ Key Topics:

* **Reflection API** – Inspect and manipulate classes, fields, and methods at runtime.
* **Custom Annotations** – Add metadata to your code using `@interface` definitions.
* **Combining Reflection + Annotations** – Write reusable, declarative logic that scans your classes for rules.
* **Annotation Meta-Annotations**: `@Target`, `@Retention` — the annotation *for* annotations.
* **Real use case**: Data validation logic inspired by frameworks like Bean Validation.

---

### 💼 Real-Life Project: **HR Validator System** 👩‍💼👨‍💼

A lightweight validation framework built using **reflection and custom annotations**:

* `@NotNull` – Field must not be `null`.
* `@Min(value)` – For numeric validation (e.g., age ≥ 18).
* `@Length(min, max)` – Validate string length (e.g., position title ≤ 25 chars).

🧠 You now understand how **frameworks validate objects without hardcoding rules** – just by scanning annotations!

---

## 🎥 Zoom Recording

📺 Rewatch the lesson:
👉 [**Zoom Recording Link**](https://us06web.zoom.us/rec/share/BxsM2cUhZRm0i6266i0DlSRA383A_tZ3MDBgAsqLTIb5x5b7bUY0-fpCbA_2PXXQ.qTJ1qekHsOEgoRax?startTime=1748330339000)

---

## 💻 Live Coding Demo

Check out the demo code:
🧑‍💻 [**GitHub Repo – HR Validator System**](https://github.com/FW-Zalando-Java-Backend-Engineer/HR-Validator-System)

---

## 🧪 Exercises for Practice

1. **Mini Survey Validator**:

   * Create a `SurveyResponse` class with fields like `name`, `email`, `age`, `feedback`.
   * Annotate fields with `@NotNull`, `@Min`, and `@Length`.
   * Write a `SurveyValidator` that reads these annotations and prints errors if present.

🔗 [**GitHub Exercises Repo: Survey Validator**](https://github.com/FW-Zalando-Java-Backend-Engineer/surveyvalidator)

---

## ❓ Recap Questions

* What does `@Retention(RUNTIME)` enable?
* Why is reflection powerful but potentially dangerous?
* What’s the purpose of `@Target(ElementType.FIELD)`?
* When would you use a custom annotation vs. a standard one?

---

## 🎯 Deep Dive: `@Override` Annotation

Ever wonder how Java knows when you're trying to override a method?

### Key Points:

| Concept              | Meaning                                                                 |
| -------------------- | ----------------------------------------------------------------------- |
| `@Target(METHOD)`    | Can only be used on methods.                                            |
| `@Retention(SOURCE)` | Only exists in source code; removed during compilation.                 |
| Purpose              | Compile-time check that you're actually overriding a superclass method. |

✅ Helps catch bugs like:

```java
@Override
public String Speak() {  // ❌ typo! should be speak()
    return "WOOF!";
}
```

Without `@Override`, that typo silently creates a new method instead of overriding. With it — compiler to the rescue. 🚓

---

## 📚 References

* [Reflection API Overview – Oracle](https://docs.oracle.com/javase/tutorial/reflect/)
* [Creating Custom Annotations](https://www.baeldung.com/java-custom-annotation)


* *Java tried reflection once, but it just reflected back `¯\\_(ツ)_/¯`* 😅


