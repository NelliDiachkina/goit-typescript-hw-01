## goit-typescript-hw-01

### Базові типи

Метою цього блоку завдань є закріплення ваших навичок роботи з базовими типами **TypeScript**.

**Завдання 1**

Виконуйте це завдання у файлі src/basic/1.ts.
Є наступний JavaScript код:

```js
const age = 50;
const username = 'Max';
const toggle = true;
const empty = null;
const callback = (a) => {
  return 100 + a;
};
```

Перетворіть цей код на TypeScript, вказавши відповідні типи для всіх змінних.

**Завдання 2**

Виконуйте це завдання у файлі src/basic/2.ts.
У вас є наступний JavaScript масив:

```js
let person = ['Max', 21];
```

Як переписати його в TypeScript, використовуючи концепцію кортежів, щоб гарантувати, що перший елемент завжди буде рядком, а другий числом?

**Завдання 3**

Виконуйте це завдання у файлі src/basic/3.ts.

Створіть змінну, яка може містити або рядок, або число (union type)? Також, оголосіть змінну, яка може містити лише одне з двох можливих рядкових значень: 'enable' або 'disable' (literal type).

**Завдання 4**

Виконуйте це завдання у файлі src/basic/4.ts.
У вас є такі функції JavaScript:

```js
function showMessage(message) {
  console.log(message);
}

function calc(num1, num2) {
  return num1 + num2;
}

function customError() {
  throw new Error('Error');
}
```

Як ви вкажете типи для аргументів і значень цих функцій, що повертаються?

**Завдання 5**

Виконуйте це завдання у файлі src/basic/5.ts.
Типізуйте функцію isWeekend яка приймає день тижня з enumDayOfWeek і повертає boolean значення, що вказує, чи це день робочий чи вихідний.

```js
enum DayOfWeek {
  Monday,
  Tuesday,
  Wednesday,
  Thursday,
  Friday,
  Saturday,
  Sunday
}

const isWeekend = (day) => {
}
```

**Завдання 6**

Виконуйте це завдання у файлі src/basic/6.ts.
Створіть інтерфейс User для типізації об'єктів, які містять такі властивості. Зверніть увагу, що адреса є необов'язковою властивістю.

```js
const mango = {
  name: 'Mango',
  age: 30,
  email: 'john@example.com',
  address: {
    city: 'New York',
    country: 'USA',
  },
};

const poly = {
  name: 'Mango',
  age: 30,
  email: 'john@example.com',
};
```

**Завдання 7**

Виконуйте це завдання у файлі src/basic/7.ts.
У вас є два об'єкти:

```js
const page1 = {
  title: 'The awesome page',
  likes: 100,
  accounts: ['Max', 'Anton', 'Nikita'],
  status: 'open',
  details: {
    createAt: new Date('2021-01-01'),
    updateAt: new Date('2021-05-01'),
  },
};

const page2 = {
  title: 'Python or Js',
  likes: 5,
  accounts: ['Alex'],
  status: 'close',
};
```

Створіть новий тип даних, який підходить для цих двох об'єктів.

### Generic типи

Мета цього блоку допомогти зрозуміти та застосувати generics у **TypeScript**. Ви працюватимете з функціями, що повертають проміси, використовувати вбудований тип Pick, об'єднувати об'єкти за допомогою generics, а також вирішувати проблеми типів у класах.

**Завдання 1**

Виконуйте це завдання у файлі src/generics/1.ts.
Типізуйте асинхронну функцію fetchData, яка приймає URL ресурсу та повертає об'єкт з даними. Використовуйте Generics для типізації повернутих даних.

```js
import axios from 'axios';

async function fetchData(url) {
  try {
    const response = await axios.get(url);
    return response.data;
  } catch (error) {
    throw new Error(`Error fetching from ${url}: ${error}`);
  }
}
```

**Завдання 2**

Виконуйте це завдання у файлі src/generics/2.ts.
У вас є тип AllType. Існує функція compare, яка приймає два об'єкти. Ці об'єкти містять поля AllType. Ваше завдання - використовувати Pick та generics для вказівки, що поля цих параметрів належать AllType. Функція compare повинна повертати AllType.

```js
type AllType = {
  name: string,
  position: number,
  color: string,
  weight: number,
};

function compare(top, bottom): AllType {
  return {
    name: top.name,
    color: top.color,
    position: bottom.position,
    weight: bottom.weight,
  };
}
```

**Завдання 3**

Виконуйте це завдання у файлі src/generics/3.ts.
У вас є функція merge, яка поєднує два об'єкти. Використовуйте generics, щоб вказати, що ці об'єкти можуть бути будь-якого типу.

```js
function merge(objA, objB) {
  return Object.assign(objA, objB);
}
```

**Завдання 4**

Виконуйте це завдання у файлі src/generics/4.ts.
Ви маєте форму реєстрації користувачів. Іноді потрібно попередньо заповнити форму даними користувача для оновлення його профілю. Однак вам не завжди потрібно заповнити всі поля. Наприклад, користувач може хотіти оновити лише свій email та пароль, залишивши ім'я та прізвище без змін.

Використовуючи утиліту Partial та generics, виправте тип параметра функції так, щоб уникнути помилок типізації.

```js
type User = {
  name: string,
  surname: string,
  email: string,
  password: string,
};

function createOrUpdateUser(initialValues: User) {
  // Оновлення користувача
}

createOrUpdateUser({
  email: 'user@mail.com',
  password: 'password123',
});
```

**Завдання 5**

Виконуйте це завдання у файлі src/generics/5.ts.
У вас є перелік UserRole, який використовується для класифікації користувачів у вашому додатку. Ви хочете створити об'єкт RoleDescription, який зіставлятиме кожну роль користувача з її описом.

```js
export enum UserRole {
  admin = 'admin',
  editor = 'editor',
  guest = 'guest',
}

// Замініть наступний код на версію за допомогою Record
const RoleDescription = {
  admin: 'Admin User',
  editor: 'Editor User',
  guest: 'Guest User',
};
```

**Завдання 6**

Виконуйте це завдання у файлі src/generics/6.ts.
У вас є тип Form, який містить інформацію про форму, включаючи поле errors. Ви хочете створити новий тип Params, який включає всі поля з Form, крім errors.

```js
type Errors = {
  email?: string[],
  firstName?: string[],
  lastName?: string[],
  phone?: string[],
};

type Form = {
  email: string | null,
  firstName: string | null,
  lastName: string | null,
  phone: string | null,
  errors: Errors,
};

// Реалізуйте Params так,
// щоб унеможливити поле 'errors' з типу Form
type Params = Form;
```
