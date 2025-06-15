# Rust - Лабораторная работа №1
## Задача №1
### Постановка задачи
Напишите программу, которая запрашивает у пользователя имя и выводит на экран приветственное сообщение с использованием этого имени.

### Список идентификаторов 

| Имя переменной  | Тип данных     | Описание          |
| --------------- | -------------- | ------------------|
| name            | String         | Имя пользователя  |

### Код программы

```Rust
use std::io;

fn main() {
    let mut name = String::new();

    println!("Enter your name:");

    let _ = io::stdin().read_line(&mut name);
    let name = name.trim();

    println!("Hello, {}!", name);
}
```

### Результат работы программы 

![](https://i.yapx.ru/ZcfA3.png)

## Задача №2
### Постановка задачи 
Создайте переменную типа целое беззнаковое число и выведите ее значение на экран. Явно укажите тип переменной. Затем измените значение переменной и снова выведите его.

### Список идентификаторов 

| Имя переменной  | Тип данных     | Описание          |
| --------------- | -------------- | ------------------|
| a               | u32            | Переменная        |

### Код программы 

```Rust
fn main() {
    let mut a: u32;
    a = 5;
    println!("{}", a);

    a = 7;
    println!("{}", a);
}
```

### Результат работы программы

![](https://i.yapx.ru/ZcfMe.png)

## Задача №3
### Постановка задачи 
Напишите функцию, которая принимает строку и возвращает ее длину (количество символов). Затем вызовите эту функцию с различными строками.

### Список идентификаторов 

| Имя переменной  | Тип данных     | Описание          |
| --------------- | -------------- | ------------------|
| -               | -              | -                 |

### Код программы 

```Rust
fn str_len(s: &str) -> usize {
    s.chars().count()
}

fn main() {
    println!("{}", str_len("Hello!"));
    println!("{}", str_len(""));
    println!("{}", str_len("123"));
}
```

### Результат работы программы

![](https://i.yapx.ru/ZcfYB.png)

## Задача №4
### Постановка задачи 
Задайте структуру Car с полями brand, model и year, и создайте несколько экземпляров этой структуры. Выведите информацию о каждой машине на экран.

### Список идентификаторов 

| Имя переменной  | Тип данных     | Описание          |
| --------------- | -------------- | ------------------|
| bmw             | Car            | Машина            |
| priora          | Car            | Машина            |
| camry           | Car            | Машина            |

### Код программы 

```Rust
struct Car {
    brand: String, 
    model: String,
    year: u32
}

fn main() {
    let bmw = Car {
        brand: "BMW".to_string(),
        model: "5-series".to_string(),
        year: 1995
    };

    println!("First car: {}, {}, {}", bmw.brand, bmw.model, bmw.year);

    let priora = Car {
        brand: "LADA".to_string(),
        model: "priora".to_string(),
        year: 2017
    };

    println!("Second car: {}, {}, {}", priora.brand, priora.model, priora.year);

    let camry = Car {
        brand: "TOYOTA".to_string(),
        model: "camry".to_string(),
        year: 2016
    };

    println!("Third car: {}, {}, {}", camry.brand, camry.model, camry.year);
}
```

### Результат работы программы

![](https://i.yapx.ru/Zcfq7.png)

## Задача №5
### Постановка задачи 
Напишите программу, которая запрашивает у пользователя число N и выводит на экран N-ное число Фибоначчи. Используйте рекурсию для решения этой задачи.

### Список идентификаторов 

| Имя переменной  | Тип данных     | Описание          |
| --------------- | -------------- | ------------------|
| input           | String         | Ввод              |
| n               | u32            | Входное число     |

### Код программы 

```Rust
use std::io;

fn fibonacci(n: u32) -> u32 {
    if n == 0 {
        return 0;
    }

    if n == 1 {
        return 1;
    }

    fibonacci(n - 1) + fibonacci(n - 2)
}

fn main() {
    let mut input = String::new();

    println!("Enter number:");

    let _ = io::stdin().read_line(&mut input);

    let n: u32 = input.trim().parse::<u32>().expect("Error");

    println!("Result: {}", fibonacci(n));
}
```

### Результат работы программы

![](https://i.yapx.ru/ZcgJ0.png)

## Задача №6
### Постановка задачи 
Реализуйте перечисление DayOfWeek для дней недели. Напишите функцию, которая принимает день недели и возвращает следующий день. Обработайте случаи перехода на следующий день недели, если текущий день – воскресенье.

### Список идентификаторов 

| Имя переменной  | Тип данных     | Описание          |
| --------------- | -------------- | ------------------|
| input           | String         | Ввод              |
| day             | DayOfWeek      | Текущий день      |
| next            | DayOfWeek      | Следующий день    |

### Код программы 

```Rust
use std::io;

enum DayOfWeek {
    Monday, 
    Tuesday,
    Wednesday,
    Thursday,
    Friday,
    Saturday,
    Sunday
}

fn next_day(day: DayOfWeek) -> DayOfWeek {
    match day {
        DayOfWeek::Monday => DayOfWeek::Tuesday,
        DayOfWeek::Tuesday => DayOfWeek::Wednesday,
        DayOfWeek::Wednesday => DayOfWeek::Thursday,
        DayOfWeek::Thursday => DayOfWeek::Friday,
        DayOfWeek::Friday => DayOfWeek::Saturday,
        DayOfWeek::Saturday => DayOfWeek::Sunday,
        DayOfWeek::Sunday => DayOfWeek::Monday
    }
}

fn main() {
    println!("Введите день недели (на английском языке, с заглавной буквы):");

    let mut input = String::new();
    let _ = io::stdin().read_line(&mut input);

    let day = match input.trim() {
        "Monday" => DayOfWeek::Monday,
        "Tuesday" => DayOfWeek::Tuesday,
        "Wednesday" => DayOfWeek::Wednesday,
        "Thursday" => DayOfWeek::Thursday,
        "Friday" => DayOfWeek::Friday,
        "Saturday" => DayOfWeek::Saturday,
        "Sunday" => DayOfWeek::Sunday,
        _ => {
            println!("Incorrect input");
            return;
        }
    };

    let next = next_day(day);

    match next {
        DayOfWeek::Monday => println!("Next day: Monday"),
        DayOfWeek::Tuesday => println!("Next day: Tuesday"),
        DayOfWeek::Wednesday => println!("Next day: Wednesday"),
        DayOfWeek::Thursday => println!("Next day: Thursday"),
        DayOfWeek::Friday => println!("Next day: Friday"),
        DayOfWeek::Saturday => println!("Next day: Saturday"),
        DayOfWeek::Sunday => println!("Next day: Sunday")
    }
}
```

### Результат работы программы

![](https://i.yapx.ru/Zcgc0.png)

## Задача №7
### Постановка задачи 
Создайте структуру Product с полями name, price и category, а также перечисление (enum) Category для категорий товаров. Напишите метод для вывода информации о продукте и ассоциированную функцию для подсчета общей суммы товаров в заданной категории из
массива продуктов.

### Список идентификаторов 

| Имя переменной  | Тип данных     | Описание          |
| --------------- | -------------- | ------------------|
| apple           | Product        | Food              |
| bread           | Product        | Food              |
| book            | Product        | Education         |
| sofa            | Product        | House             |
| shirt           | Product        | Clothes           |
| aspirin         | Product        | Medicine          |

### Код программы 

```Rust
struct Product {
    name: String,
    price: u32,
    category: Category
}

#[derive(PartialEq)]
enum Category {
    House,
    Food,
    Clothes,
    Education,
    Medicine
}

impl Product {
    fn print(&self) {
        let category_name = match &self.category {
            Category::House => "House",
            Category::Food => "Food",
            Category::Clothes => "Clothes",
            Category::Education => "Education",
            Category::Medicine => "Medicine"
        };

        println!("Name: {}, Price: {}, Category: {}", &self.name, &self.price, category_name);
    }

    fn total_price(products: &[Product], category: Category) -> u32 {
        let mut result: u32 = 0;

        for product in products {
            if product.category == category {
                result += product.price;
            }
        }

        result
    }
}

fn main() {
    let apple = Product {
        name: "Apple".to_string(),
        price: 50,
        category: Category::Food
    };

    let bread = Product {
        name: "Bread".to_string(),
        price: 60,
        category: Category::Food
    };

    let book = Product {
        name: "Book".to_string(),
        price: 200,
        category: Category::Education
    };

    let sofa = Product {
        name: "Sofa".to_string(),
        price: 50000,
        category: Category::House
    };

    let shirt = Product {
        name: "Shirt".to_string(),
        price: 5000,
        category: Category::Clothes
    };

    let aspirin = Product {
        name: "Aspirin".to_string(),
        price: 100,
        category: Category::Medicine
    };

    apple.print();
    bread.print();
    book.print();
    sofa.print();
    shirt.print();
    aspirin.print();

    let products: [Product; 6] = [apple, bread, book, sofa, shirt, aspirin];

    println!("");
    println!("Total price in category Food: {}", Product::total_price(&products, Category::Food));
    println!("Total price in category Education: {}", Product::total_price(&products, Category::Education));
    println!("Total price in category House: {}", Product::total_price(&products, Category::House));
    println!("Total price in category Clothes: {}", Product::total_price(&products, Category::Clothes));
    println!("Total price in category Medicine: {}", Product::total_price(&products, Category::Medicine));
}
```

### Результат работы программы

![](https://i.yapx.ru/Zcg6c.png)

## Задача №8
### Постановка задачи 
Создайте структуру Employee с полями name, position, salary, а также перечисление Position для должностей сотрудников. Напишите функцию, которая принимает вектор сотрудников и возвращает вектор сотрудников заданной должности.

### Список идентификаторов 

| Имя переменной  | Тип данных     | Описание             |
| --------------- | -------------- | ---------------------|
| andrey          | Employee       | Developer            |
| sergey          | Employee       | Developer            |
| oleg            | Employee       | Tester               |
| aleksandr       | Employee       | Analyst              |
| ivan            | Employee       | Analyst              |
| maxim           | Employee       | Manager              |
| artem           | Employee       | SystemAdministrator  |
| maria           | Employee       | Designer             |
| employees       | Vec(Employee)  | all employees        |
| developers      | Vec(Employee)  | all developers       |
| testers         | Vec(Employee)  | all testers          |
| analysts        | Vec(Employee)  | all analysts         |
| managers        | Vec(Employee)  | all managers         |
| administrators  | Vec(Employee)  | all administrators   |
| designers       | Vec(Employee)  | all designers        |


### Код программы 

```Rust
struct Employee {
    name: String,
    position: Position,
    salary: u32
}

impl Employee {
    fn print(&self) {
        let position = match &self.position {
            Position::Developer => "Developer",
            Position::Tester => "Tester",
            Position::Analyst => "Analyst",
            Position::Manager => "Manager",
            Position::SystemAdministrator => "System Administrator",
            Position::Designer => "Designer"
        };

        println!("{}, {}, {}", &self.name, position, &self.salary);
    }
}

#[derive(PartialEq)]
enum Position {
    Developer,
    Tester,
    Analyst,
    Manager,
    SystemAdministrator,
    Designer
}

fn get_employees_by_position(employees: &Vec<Employee>, position: Position) -> Vec<&Employee> {
    let mut result: Vec<&Employee> = Vec::new();

    for employee in employees {
        if employee.position == position {
            result.push(employee);
        }
    }

    result
}

fn main() {
    let andrey = Employee {
        name: "Andrey".to_string(),
        position: Position::Developer,
        salary: 150000
    };

    let sergey = Employee {
        name: "Sergey".to_string(),
        position: Position::Developer,
        salary: 170000
    };

    let oleg = Employee {
        name: "Oleg".to_string(),
        position: Position::Tester,
        salary: 100000
    };

    let aleksandr = Employee {
        name: "Aleksandr".to_string(),
        position: Position::Analyst,
        salary: 200000
    };

    let ivan = Employee {
        name: "Ivan".to_string(),
        position: Position::Analyst,
        salary: 180000
    };

    let maxim = Employee {
        name: "Maxim".to_string(),
        position: Position::Manager,
        salary: 140000
    };

    let artem = Employee {
        name: "Artem".to_string(),
        position: Position::SystemAdministrator,
        salary: 130000
    };

    let maria = Employee {
        name: "Maria".to_string(),
        position: Position::Designer,
        salary: 120000
    };

    let employees: Vec<Employee> = vec![andrey, sergey, oleg, aleksandr, ivan, maxim, artem, maria];

    let developers = get_employees_by_position(&employees, Position::Developer);

    println!("Developers:");
    for developer in developers {
        developer.print();
    }
    println!();

    let testers = get_employees_by_position(&employees, Position::Tester);

    println!("Testers:");
    for tester in testers {
        tester.print();
    }
    println!();

    let analysts = get_employees_by_position(&employees, Position::Analyst);

    println!("Analysts:");
    for analyst in analysts {
        analyst.print();
    }
    println!();

    let managers = get_employees_by_position(&employees, Position::Manager);

    println!("Managers:");
    for manager in managers {
        manager.print();
    }
    println!();

    let administrators = get_employees_by_position(&employees, Position::SystemAdministrator);

    println!("System Administrators:");
    for administrator in administrators {
        administrator.print();
    }
    println!();

    let designers = get_employees_by_position(&employees, Position::Designer);

    println!("Designers:");
    for designer in designers {
        designer.print();
    }
}
```

### Результат работы программы

![](https://i.yapx.ru/ZciYz.png)

## Информация о студенте 

Болгов Александр, 1 курс, ИВТ-2.