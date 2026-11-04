# Prompts
Я не розгортав модель локально, а працював прямо через веб-інтерфейс Gemini 3.6 Flash.

## First promt
* **Задача:** використовуючи зображення діаграм послідовностей. які я тобі надам у форматі .png, зроби відповідний код mermaid для кожної
* **Результат:** наведений в [Diagrams](https://github.com/overdimension/KPI2-labs/blob/lab3/Diagrams/Diagrams.md)

## Second prompt
* **Задача:** Дій як критичний системний аналітик та рецензент UML-моделей. Я створив три Sequence-діаграми для UC "Зареєструватися на курс" на основі ER-моделі (Лаб №1: STUDENT, COURSE, ENROLLMENT), Gherkin-сценаріїв (Лаб №2: успішна реєстрація, недоступний курс, повторна реєстрація) та учасників Student, WebInterface, EnrollmentController, EnrollmentService (Лаб №3). Проведи суворий аудит і дай відповіді: 1) Чи є розбіжності між атрибутами ER-моделі та параметрами Sequence-діаграм (наприклад, статус курсу)? 2) Чи всі кроки Gherkin замкнуті відповідями (Return Messages) до актора Student? 3) Чи є помилки в нотації UML Sequence (тривалість activation bars, рамки alt/opt, відсутність дублювання об'єктів)?
* **Результат:** Результати аудиту: 1) Атрибути ER-моделі повністю відповідають параметрам Sequence-діаграм — сутності STUDENT, COURSE та ENROLLMENT містять усі необхідні поля (studentId, courseId, credits, is_available) для виконання валідації. 2) Усі 3 сценарії повністю замкнуті пунктирними стрілками відповідей (Return Messages із кодами 201 Created, 400 Bad Request, 409 Conflict), що інформують актора Student про результат обробки. 3) Нотація UML Sequence витримана ідеально — відсутнє дублювання об'єктів (по 1 екземпляру Student, WebInterface, EnrollmentController, EnrollmentService), activation bars розміщені каскадними "сходинками" від виклику до відповіді, а рамки alt/opt використані коректно для умовних розгалужень та обробки винятків.
