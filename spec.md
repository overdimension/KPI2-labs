## UC Scenarios
Обраний UC: "Реєстрація на курс" з другої лабораторної

1. **Main Scenario:** Успішна реєстрація на доступний курс
2. **Alt Scenario:** Відмова у реєстрації, якщо курс недоступний
3. **Exception Scenario:** Блокування спроби повторної реєстрації на той самий курс

---

## Components of systemic interaction

1. **`Student` (Actor):** Користувач, який ініціює запит на реєстрацію
2. **`WebInterface` (Boundary):** UI, що приймає дії користувача та відображає статуси й повідомлення про помилки
3. **`EnrollmentController` (Control):** REST-контролер, що приймає HTTP-запити та керує оркестрацією обробки
4. **`EnrollmentService` (Service/Domain):** Сервіс бізнес-логіки, де виконуються перевірки доступності курсу, перевірка повторної реєстрації та розрахунок кредитів ECTS

---

## Notice
* Всі діаграми у форматах png та mermaid зняходяться у папці [Diagrams](https://github.com/overdimension/KPI2-labs/tree/lab3/Diagrams) 
