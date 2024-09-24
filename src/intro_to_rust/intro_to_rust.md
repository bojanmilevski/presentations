---
marp: true
theme: rose-pine
class: invert
style: |
  * {
    font-family: 'CaskaydiaCove Nerd Font Mono';
  }

  h1 {
    font-size: 60px;
    text-align: center;
  }

  p, li {
    font-size: 24px;
  }

  .columns {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 1rem;
  }

  .author {
    text-align: center;
  }
---

# ВОВЕД ВО RUST

<div class="author">

Бојан Милевски

</div>

---

# ИЗВОРИ

- Мојот мозок
- Официјалната Rust книга
  - https://doc.rust-lang.org/stable/book/
  - Бесплатна онлајн верзија, постои и книга

---

# ОПФАТЕНИ ТЕМИ

<div class="columns">

<div>

- Инсталација
- Hello World
- Основи
- Type системот
  - Type inference
  - Mutability
- Компајлер
  - Borrow checker
  - Ownership
- Структури
- Енумерации

</div>

<div>

- Traits
- Генерици
- Справување со грешки
- Монади
- Анонимни функции (closures)
- Животен век на променливи (lifetimes)
- Асинхрони функции
  - Tokio
- Паметни покажувачи

</div>

</div>

---

# ШТО Е RUST

- Модерен
- Безбеден
- Ефикасен
- Екстремно брз
- Доверлив
- Крос-компатибилен
- Замена на C/C++
  - Потенцијална замена на HolyC

---

# ЗОШТО RUST

- Јазикот на иднината
- Безбедност
- Распространет на многу полиња
  - CLI
  - Embedded
  - Web
  - Cyber security
  - Desktop
  - tauri
- Web Frameworks
  - Axum/Rocket
  - Wasm
  - Yew

---

# ШТО НЕ Е RUST

- Објетно-ориентиран јазик
- Функциски јазик

---

# КАКО RUST

- Linux/MacOS
  - rustup
  - package manager (преферирано)
- Windows
  - Делумно-добри вести
  - winget
  - WSL
  - Ubuntu
  - Лоши вести:
  - 😁

---

# ИНСТАЛАЦИЈА

---

# LINUX/MACOS

```sh
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source ~/.cargo/env
rustc --version
cargo --version
```

---

# WINDOWS

- https://forge.rust-lang.org/infra/other-installation-methods.html

---

# HELLO WORLD

---

# АЛАТКИ

- cargo
- rustc

---

# КРЕИРАЊЕ НОВ ПРОЕКТ

```sh
cargo new "my_project"
cd "my_project"
```

---

# СТРУКТУРА НА ЕДЕН ПРОЕКТ

```
.
├── Cargo.toml
└── src
  └── main.rs
```

---

# `src/main.rs`

```rs
fn main() {
  println!("Hello, World!");
}
```

---

# КОМПАЈЛИРАЊЕ ПРОЕКТ

```sh
cargo run
```

# `Hello, World!`

---

# ОСНОВИ

---

# СИНТАКСА

- Се користат `;`
- Празни места немаат значење
- Не се потребни загради за `if`, `else` и `match`
- Коментари
  - `//`
  - `/* */`

---

# КОНВЕНЦИИ

- `snake_case` за променливи
- `ГОЛЕМИ_БУКВИ` за константи

---

# ТИПОВИ

- Променливи се означуваат со `let` или `const`
- Типот на променливите е автоматски назначен
  - Type inference
- Типови (експлицитно) се декларираат со `:`
  - Пр. `let my_name: &str = "Bojan"`
- Променливите (по default) се immutable
  - `mut`
- `let` vs `const`
- `u8`, `i8`, ..., `u128`, `i128`
- `f32`, `f64`
- `String`, `&str`, `str` ???
- `Vec<T>`, `&[T]`, `[T]` ???

---

# ТИПОВИ

- `String` типовите поддржуваат unicode (не се ASCII како во C/C++)
- Секоја променлива поседува вредност **САМО** онаа првично назначена
  - За разлика од C/C++, каде може да е или типот или `nullptr`

---

# ФУНКЦИИ

- Функции се означуваат со `fn`
- Типот кој враќа една функција се обележува со `->`
- Тело на функција се означува со `{}`
- Аргументи на функција се во `()`
- Не мора да се пише `return my_value;`, туку само `my_value`
- Scope оператор `::`

---

# МАКРОА

- Компајлер макроа се обележуваат со `!` на крај
- Компајлерот пишува код за тебе
- Макроата се прошируваат за време на компилација
- `println!`
  - зафаќа 1 линија код пред компилација
  - зафаќа повеќе од 4 линии код по компилација

```rs
macro_rules! println {
    () => { ... };
    ($($arg:tt)*) => { ... };
}
```

---

# РЕФЕРЕНЦИ

- Референци - `&`
- Покажувачи - `* const T = &...`
  - Не се безбедни!!!

---

# ПРИМЕР

```rs
const NAME: [char] = [ 'B', 'O', 'J', 'A', 'N' ];

fn main() {
  let my_age = 21; // i32
  let pi = 3.14; // f64

  if my_age == 100 {
    println!("Во мое време вода за пиење немаше, сега сите со телефоните...");
  } else if my_age == 21 {
    println!("Like и во ком ти оценувам изглед 1-10 😁");
  } else {
    println!("Skibidi fortnite");
  }

  let fib = vec![ 0, 1, 1, 2, 3, 5, 8, 13, 21 ]; // Vec<i32>

  for f in fib {
    println!("value: {}", f)
  }
}
```

---

# ПРИМЕР

```rs
const API_URL: &str = "https://example.com"

fn get_my_name() -> &str {
  "Bojan" // return "Bojan";
}

fn friend_name() -> String {
  "Nikola Talevski".to_string()
}

fn main() {
  let my_name = get_my_name();
  my_name = "NikiPugKing"; // ERROR!

  let mut zrze: String = friend_name();
  zrze = String::from("Tonda");

  let vovox: &str = zrze.as_str() // zrze.deref();
  vovox = "Martin"; // ERROR!
}
```

---

# C++ ЕКВИВАЛЕНТА

```cpp
#include <string>
#include <string_view>

const std::string_view API_URL = "https://example.com";
// const char* API_URL = "https://example.com"

std::string_view get_my_name() { // const char*
  return "Bojan";
}

std::string friend_name() {
  return std::string { "Nikola Talevski" };
}

int main() {
  const std::string_view my_name = get_my_name();
  my_name = "NikiPugKing"; // ERROR!

  std::string zrze = friend_name();
  zrze = std::string { "Tonda" };

  const std::string_view vovox(zrze);
  vovox = "Martin"; // ERROR!
}
```

---

# TYPE СИСТЕМ

---

# TYPE СИСТЕМ

- Type системот на Rust е многу строг
- Не дозволува глупости

---

# TYPE СИСТЕМ

- Типот автоматски се одредува по иницијализација...
- ...но не декларација

```rs
fn main() {
  let my_age; // не се знае типот
  my_age = 21; // типот засекогаш ќе биде i32
  my_age = "Bojan"; // ERROR!
}
```

---

# TYPE СИСТЕМ

## Во JavaScript (најдобриот јазик)

```js
let my_age = 21;
my_age = "Bojan"; // нема проблем
```

---

# КОМПАЈЛЕР

---

# КОМПАЈЛЕР

- Постои нешто што е потешко да се задоволи од партнерот...

---

# КОМПАЈЛЕР

- ...тоа е borrow checker-от на Rust

---

# СОПСТВЕНОСТ/ПОЗАЈМУВАЊЕ

- МНОГУ од бенефитите на произлагаат од borrow checker-от
- Убавината на јазикот
- RAII
- Тој внимава на
  - Сопственост (ownership)
  - Позајмување (borrowing)
  - Референци `&`
  - Животен век (lifetimes) `&'a`
  - Невалидни (dangling) референци
- користиме само `&`, а избегнуваме `*` по секоја цена

---

# СОПСТВЕНОСТ/ПОЗАЈМУВАЊЕ

Наместо променливи и вредности, сега ќе почнеме да размислуваме во однос на сопственици и позајмувачи (лихвари и должници)

```rs
fn main() {
  let my_name = "Bojan";
}
```

❌ Вредноста на `my_name` е `"Bojan"`
✅ Сопственикот на `"Bojan"` е `my_name`

---

# СОПСТВЕНОСТ/ПОЗАЈМУВАЊЕ

Наместо покажувачи и референци, сега ќе почнеме да размислуваме во однос на позајмувачи

```rs
let my_name = "Bojan"
let his_name = &my_name;
```

❌ Референцата `his_name` ја референцира/покажува кон вредноста на `my_name`
✅ Референцата `his_name` ја позајмува вредноста која му припаѓа на `my_name`

---

# СОПСТВЕНОСТ/ПОЗАЈМУВАЊЕ

- Променлива умира кога ќе излезе од опсег
  - Крај на функција
- Кога умира сопственикот, умира сета негова сопственост
  - Сите вредности (променливи) кои ги поседува
  - (Истото се случи со нашиот антички чукун дедо Александар Македонски и Македонското царство)
- Кога умира позајмникот, ништо не умира
  - Умира само референцата, не и вредностите
  - (за разлика од реалниот свет)

---

# СОПСТВЕНОСТ/ПОЗАЈМУВАЊЕ

## Опсег

```rs
fn square(number: u32) -> u32 {
  number * number
}

fn cube(number: u32) -> u32 {
  number * number * number
}

fn main() {
  let number = 5;
  let squared_number = square(number);
  let cubed_number = cube(number); // ERROR!

  ...
}
```

---

# СОПСТВЕНОСТ/ПОЗАЈМУВАЊЕ

## Опсег

```rs
fn square(number: &u32) -> u32 {
  number * number
}

fn cube(number: u32) -> u32 {
  number * number * number
}

fn main() {
  let number = 5;
  let squared_number = square(&number);
  let cubed_number = cube(&number);

  println!("{}", number);
}
```

---

# RAII

## Resource Aquisition Is Initialization

- Практично значи дека сопственикот е одговорен за своите вредности/имања
- Кога умира тој, умира се со него
- **ВАЖИ И ЗА ДИНАМИЧКИ ПОДАТОЦИ**

---

# RAII

```cpp
#include <print>

class MyData {
private:
  char* m_data;

public:
  MyData(const char *data) {
    if (data) {
      const size_t len = strlen(my_name);
      m_data = new char[len + 1];
      strncpy(m_data, data, len + 1);
    } else {
      m_data = nullptr;
    }
  }

  ~MyData() {
    if (m_data) {
      delete[] m_data;
    }
  }
}

int main() {
  MyData my_data("Bojan");

  int my_array = new int[10];

  // TODO

  delete[] my_array;

  std::println("my_array[0]: {}", my_array[0]);
}
```

---

# RAII

```cpp
#include <cstring>
#include <memory>

class MyStruct {
private:
  std::unique_ptr<char[]> m_data;

public:
  MyStruct(const char *data) {
    if (data) {
      const size_t len = std::strlen(data) + 1;
      m_data = std::make_unique<char[]>(len);
      std::strcpy(m_data, data);
    }
  }
};
```

---

# BORROW CHECKER

Може да се позајми вредноста ако сопственикот живее подолго (или исто) од позајмникот

```rs
fn main() {
  let my_age: i32 = 21;
  let reference: &i32;

  {
    reference = &my_age;
  }

  println!("{}", reference);
}
```

---

# BORROW CHECKER

Не може да се позајми вредност ако сопственикот живее пократко од позајмникот

```rs
fn main() {
  let reference: &i32;

  {
    let my_age: i32 = 21;
    reference = &my_age;
  }

  println!("{}", reference); // ERROR!
}
```

---

# BORROW CHECKER

## Трите правила на Rust borrow checker-от

- Една вредност има еден единствен сопственик
- Во еден момент, вредноста може да има
  - Повеќе immutable позајмувачи
  - Единствен mutable позајмувач
- Сите референци мора да се валидни
  - Референците не смеат да покажуваат кон мртви вредности
  - Референците не живеат подолго од сопствениците
  - Или исто, или пократко

---

# BORROW CHECKER

```rs
fn main() {
  let mut name = String::from("Bojan");

  let a = &name; // immutable borrow
  let b = &mut name; // mutable borrow // ERROR!

  println!("{}", a); // immutable borrow later used here
  println!("{}", b);
}
```

---

# СТРУКТУРИ

```rs
struct MyData {
  pub name: String,
  pub age: u8,
  id: String,
  numbers: Vec<u8>
}

fn main() {
  let my_data = MyData {
    name: "Bojan",
    age: 21,
    id: "ABCD1234",
    numbers: vec![1, 2, 3, 4, 5],
  };
}
```

---

# СТРУКТУРИ

```rs
struct MyData {
  pub name: String,
  pub age: u8,
  id: String,
  numbers: Vec<u8>
}

impl MyData {
  pub fn new() -> Self {
    Self {
      name: "Bojan",
      age: 21,
      id: "ABCD1234",
      numbers: vec![1, 2, 3, 4, 5],
    }
  }
}

fn main() {
  let my_data = MyData::new("Bojan", 21, "ABCD1234", vec![1, 2, 3, 4, 5]);
}
```

---

# СТРУКТУРИ

- `impl` зборот служи за декларирање функции кои се однесуваат на таа структура
- Се пристапува преку `::`
- Пример `MyData::new(...)`

---

# СТРУКТУРИ

- `self`
  - Како `this` во C++
- Со цел одредена функција да делува врз веќе постоечки објект, мора првиот аргумент на функцијата да биде зборот `self`
  - Со ова се дава на знаење дека објектот мора да е претходно креиран за да се користи оваа функција

---

# СТРУКТУРИ

```rs
struct MyData {
  pub name: String,
}

impl MyData {
  pub fn new() -> Self {
    Self { name: String::new() }
  }

  pub fn get_name(&self) -> String {
    self.name
  }
}
```

---

# СТРУКТУРИ

<section style="text-align: center;">

`self` vs `Self`

</section>

---

# ЕНУМЕРАТОРИ

---

# ЕНУМЕРАТОРИ

- Навидум исти како во сите други програмски јазици
- „Бројки претставени со имиња“

```rs
enum Shape {
  Circle,
  Rectangle,
  Triangle,
}

fn main() {
  let circle = Shape::Circle;
}
```

---

# ЕНУМЕРАТОРИ

- Еден од најдобрите додатоци на јазикот, бидејќи
  - Можат да држат вредности
  - Можат да имаат поврзани (`impl`) функции

---

# ЕНУМЕРАТОРИ

- **МНОГУ СЕ ЕФИКАСНИ**
- Еден енумератор може да биде само еден вид од поттиповите
  - ништо помалку, ништо повеќе
- Можат да заменат генерици
- 0 overhead
- Работат одлично со `match` statement

---

# ЕНУМЕРАТОРИ

```rs
struct Circle {
  radius: f64,
}

struct Rectangle {
  width: f64,
  height: f64,
}

struct Triangle {
  a: f64,
  b: f64,
  c: f64,
}

impl Circle {
  fn get_area(&self) -> f64 {
    self.radius * 3.14
  }
}

impl Rectangle {
  fn get_area(&self) -> f64 {
    self.width * self.height
  }
}

impl Triangle {
  fn get_area(&self) -> f64 {
    // 0.5 * base * height
  }
}
```

---

# ENUM TUPLE

```rs
enum Shape {
  Circle(f64),
  Rectangle(f64, f64),
  Triangle(f64, f64, f64),
}

impl Shape {
  fn get_area(&self) -> f64 {
    match self {
      Shape::Circle => self.0 * 3.14,
      Shape::Rectangle => self.0 * self.1,
      Shape::Trianle => todo!(), // 0.5 * base * height
    }
  }
}

fn main() {
  let circle = Shape::Circle(10.0);
  println!("area of your shape: {}", circle.get_area());
}
```

---

# MATCH

---

# MATCH

- `switch` израз
- `if`, `else if`, `else`
- `match` ве форсира да се справите со сите можни случаи на разгранување
  - Инаку програмата нема да се искомпајлира
  - `_`

---

# MATCH

```rs
fn main() {
  let a = 10;
  let b = 5;

  if a < b {
    println!("a < b");
  } else if a > b {
    println!("a > b");
  }
}
```

- Што со `a == b`?

---

# MATCH

```rs
fn main() {
  let a = 10;
  let b = 5;

  match a.cmp(&b) {
    Ordering::Less => println!("a < b"),
    Ordering::Greater => println!("a > b"),
    Ordering::Equal => println!("a == b"),
  }
}
```

---

# MATCH

```rs
fn main() {
  let a = 10;
  let b = 5;

  match a.cmp(&b) {
    Ordering::Less => println!("a < b")
  } // ERROR!!!
}
```

---

# MATCH

```rs
fn main() {
  let a = 10;
  let b = 5;

  match a.cmp(&b) {
    Ordering::Less => println!("a < b"),
    _ => println!("a >= b"),
  }
}
```

---

# TRAITS

---

# TRAITS

---

- `interface` во други програмски јазици
- Назначнува однесување на структура/тип
- Типot треба да го имплементира trait-от
  - Да го наследи веќе одреденото однесување
  - Да го смени однесувањето ако е претходно дефинирано

---

# TRAITS

```rs
trait Describable {
  fn describe(&self) -> String;
}
```

---

# TRAITS

```rs
struct Person {
  name: String,
  surname: String,
  age: u8,
}

struct Animal {
  species: String,
  legs: u8,
}

impl Describable for Person {
  fn describe(&self) -> String {
    format!("name: {}, surname: {}, age: {}", self.name, self.surname, self.age)
  }
}

impl Describable for Animal {
  fn describe(&self) -> String {
    format!("species: {}, legs: {}", self.species, self.legs)
  }
}
```

---

# TRAITS

```rs
fn print_description(item: &impl Describable) {
    println!("{}", item.describe());
}
```

---

# TRAITS

```rs
fn main() {
  let person = Person {
    name: "Bojan".to_string(),
    surname: "Milevski".to_string(),
    age: 21,
  };

  let animal = Animal {
    species: "Dog".to_string(),
    legs: 4,
  };

  print_description(&person);
  print_description(&animal);
}
```

---

# TRAITS

```rs
trait Describable {
  fn describe(&self) -> String;
}

struct Person {
  name: String,
  surname: String,
  age: u8,
}

struct Animal {
  species: String,
  legs: u8,
}

impl Describable for Person {
  fn describe(&self) -> String {
    format!(
      "name: {}, surname: {}, age: {}",
      self.name, self.surname, self.age
    )
  }
}

impl Describable for Animal {
  fn describe(&self) -> String {
    format!("species: {}, legs: {}", self.species, self.legs)
  }
}

fn print_description(item: &impl Describable) {
  println!("{}", item.describe());
}

fn main() {
  let person = Person {
    name: "Bojan".to_string(),
    surname: "Milevski".to_string(),
    age: 21,
  };

  let animal = Animal {
    species: "Dog".to_string(),
    legs: 4,
  };

  print_description(&person);
  print_description(&animal);
}
```

---

# TRAITS

```rs
use std::fmt::Display; // Display e trait

struct User {
  name: String,
  surname: String,
  age: u8,
}

impl Display for User {
  fn fmt(&self, f: &mut std::fmt::Formatter<'_>) -> std::fmt::Result {
    write!(
      f,
      "name: {}, surname: {}, age: {}",
      self.name, self.surname, self.age,
    )
  }
}

fn main() {
  let user = User {
    name: "Bojan".to_string(),
    surname: "Milevski".to_string(),
    age: 21,
  };

  println!("{}", user);
}
```

---

# C++ ЕКВИВАЛЕНТА

```cpp
#include <iostream>
#include <string>

class User {
private:
  std::string m_name;
  std::string m_surname;
  int m_age;

public:
  Person(const std::string& name, const std::string& surname, int age) {
    m_name = name;
    m_surname = surname;
    m_age = age;
  }

  friend std::ostream& operator<<(std::ostream& os, const Person& person) {
    os << "name: " << person.m_name;
    os << " surname: " << person.m_surname;
    os << " age: " << person.m_age;

    return os;
  }
};

int main() {
  const auto user = User { "Bojan", "Milevski", 21 };
  std::cout << user << '\n';

  return EXIT_SUCCESS;
}
```

---

# GENERICS

---

# GENERICS

- `Vec`
- Типот на некоја вредност во една структура може да варира
- Разни типови за различни објекти од истата структура

```rs
let names = vec![ "Bojan", "Ace", "Ficho" ]; // Vec<String>
let numbers = vec![ 21, 22, 23 ]; // Vec<i32>
```

---

# GENERICS

- Структура која може да држи било коj тип `T`
- Може да се ограничат типовите кои ги чуваме според `trait`
- Мономорфизација
  - Се одредуваат за време на компилација
  - Не е така во другите програмски јазици
  - Компајлерот пак пишува код за тебе

---

# GENERICS

```rs
struct Person<T> {
  name: String,
  age: u8,
  info: T,
}

fn main() {
  let bojan = Person {
    name: "Bojan".to_string(),
    age: 21,
    info: "Ilinden".to_string() // String
  };

  let dacho = Person {
    name: "David".to_string(),
    age: 21,
    info: 075123987 // i32
  };

  let pitro = Person {
    name: "David".to_string(),
    age: 21,
    info: 102.35 // f64
  };
}
```

---

# GENERICS

```rs
trait Number: Copy + PartialOrd + PartialEq {}

impl Number for u8 {}
impl Number for u16 {}
impl Number for u32 {}
impl Number for u64 {}
impl Number for u128 {}

struct Person<T: Number> {
  name: String,
  age: u8,
  number: T,
}

fn main() {
  let bojan = Person {
    name: "Bojan".to_string(),
    age: 21,
    number: 1 as u8,
  };

  let dacho = Person {
    name: "David".to_string(),
    age: 21,
    number: 10_000_000_000 as u32,
  };

  let pitro = Person {
    name: "David".to_string(),
    age: 21,
    number: 340282366920938463463374607431768211455 as u128,
  };
}
```

---

# МОНАДИ

---

# МОНАДИ

- Знам што се ама не знам да ви ги објаснам...

---

# МОНАДИ

- Има една изрека на едно YouTube видео

```
Штом научиш што се монади, ја губиш способноста да објасниш што претставуваат
```

---

# МОНАДИ

```
Monads are just monoids in the category of endofunctors, what's the problem?
```

---

# МОНАДИ

- Начин за справување со грешки или „непостоечки вредности“
- Rust ви нуди 2 типа монади на раслолагање:
  - `Option<T>` за „непостоечки вредности“
  - `Result<T, E>` за пропагација на грешки
- Мора прво да ја одвиткаме вредноста во енумераторот за да ја користиме
  - `unwrap`

---

# OPTION<T>

<section style="text-align: center;">

🎁 📄

</section>

---

# OPTION<T>

- Практично претставува (drop-in) замена за `nullptr`
- Не е `nullptr`
- Енумераторски тип кој може да е единствено:
  - `Option::Some(Т)`
  - `None`
- Корисни кога сакаме да „нема вредност“

---

# OPTION<T>

```rs
fn main() {
  let money: Option<u128> = Option::None;
}
```

---

# OPTION<T>

```rs
fn main() {
  let money: Option<u128> = Some(1_000_000);
}
```

---

# OPTION<T>

```rs
fn main() {
  let money = None;
}
```

---

# OPTION<T>

```rs
fn main() {
  let money = Some(1_000_000);
}
```

---

# OPTION<T>

```rs
fn main() {
  let vec = vec![ 1, 2, 3 ];
  let num = vec.get(10);

  if num.is_some() {
      println!("number: {}", num);
  } else {
    println!("index is out of bounds");
  }
}
```

---

# OPTION<T>

```rs
fn main() {
  let vec = vec![ 1, 2, 3 ];
  let num = vec.get(10);

  if let Some(n) = num {
    println!("number: {}", n);
  } else {
    println!("index is out of bounds");
  }
}
```

---

# OPTION<T>

```rs
fn main() {
  let vec = vec![ 1, 2, 3 ];
  let num = vec.get(10);

  match num {
    Some(n) => println!("number: {}", n),
    None => println!("index is out of bounds"),
  }
}
```

---

# RESULT<T, E>

<section style="text-align: center;">

🎁 📄/❌

</section>

---

# RESULT<T, E>

- Енумераторски тип кој може да е единствено:
  - `Result::Ok(T)`
  - `Result::Err(E)`
- Штом наиде на `Err(E)` функцијата паѓа и се пропагира грешката едно ниво под call-stackot

# RESULT<T, E>

- Одговорен е повикувачот да се справи со грешката
- Замена на `try` `catch`
- Не може да се игнорираат како во C++ и JavaScript

---

```js
const one = () => {
  throw new Error("error");
};

const two = () => {
  // try {
  one();
  // } catch (err) {
  //   console.log(err);
  // }
};

two();
console.log("bye");
```

---

# RESULT<T, E>

```rs
use std::fs::File;
use std::io;
use std::io::Read;
use std::path::Path;

fn read_file_content<P: AsRef<Path>>(path: P) -> Result<String, io::Error> {
  let mut file = File::open(path)?;
  let mut contents = String::new();
  file.read_to_string(&mut contents)?;
  Ok(contents)
}

fn main() {
  let res = read_file_content("/home/bojan/file.txt");

  match res {
    Ok(contents) => println!("File contents: {}", contents),
    Err(e) => println!("An error occurred: {}", e),
  }
}
```

---

# АСИХРОНИ ФУНКЦИИ

# АНОНИМНИ ФУНКЦИИ

# ЖИВОТЕН ВЕК (lifetime)

---

# ВИ БЛАГОДАРАМ НА ВНИМАНИЕТО

<section style="text-align: center;">

## ПРОГРАМИРАЈТЕ ВО RUST

</section>
