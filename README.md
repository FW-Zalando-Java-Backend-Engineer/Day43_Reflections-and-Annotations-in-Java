## 📚 **Day 43 – Reflections and Annotations in Java**

---

### 🔹 **Topic:**

Understanding and using **Reflection and Annotations** in Java to build dynamic, metadata-driven logic.

---

### 🧠 **What We Learned:**

* **Reflection**: How Java inspects and modifies classes/fields/methods at runtime.
* **Annotations**: Metadata tags to declare rules (like `@NotNull`, `@Min`) used in validation, testing, and frameworks.
* Combined, they allow us to build **flexible, declarative code** – like frameworks do!

---

### 💼 **Real-Life Theme: Mini HR Validator System**

> We built a **validation engine** for `Employee` objects with annotated rules:

* `@NotNull` – Fields must not be null
* `@Min(18)` – Age must be 18+
* `@Length(min=3, max=50)` – Name length must be valid

---

### ✅ **Live Code Example**

#### `Employee.java`

```java
public class Employee {
    @NotNull
    @Length(min = 3, max = 50)
    private String name;

    @NotNull
    private String email;

    @Min(18)
    private int age;

    @Length(max = 100)
    private String position;
    
    // constructor + toString
}
```

#### `Validator.java`

```java
public class Validator {
    public static void validate(Object obj) throws IllegalAccessException {
        for (Field field : obj.getClass().getDeclaredFields()) {
            field.setAccessible(true);
            Object value = field.get(obj);

            if (field.isAnnotationPresent(NotNull.class) && value == null)
                throw new IllegalArgumentException("Field " + field.getName() + " cannot be null");

            if (field.isAnnotationPresent(Min.class)) {
                int min = field.getAnnotation(Min.class).value();
                if ((Integer) value < min)
                    throw new IllegalArgumentException("Field " + field.getName() + " must be >= " + min);
            }

            if (field.isAnnotationPresent(Length.class)) {
                Length len = field.getAnnotation(Length.class);
                String str = (String) value;
                if (str.length() < len.min() || str.length() > len.max())
                    throw new IllegalArgumentException("Field " + field.getName() + " must be between " + len.min() + " and " + len.max());
            }
        }
    }
}
```

#### `Demo.java`

```java
public class Demo {
    public static void main(String[] args) {
        Employee emp = new Employee("Al", "al@example.com", 17, "Developer");
        try {
            Validator.validate(emp);
            System.out.println("VALID");
        } catch (Exception e) {
            System.out.println("❌ INVALID: " + e.getMessage());
        }
    }
}
```


