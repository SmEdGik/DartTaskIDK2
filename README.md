# DartTaskIDK2

# Практическая работа по дисциплине - Разработка мобильных приложений
 - 
```dart


import 'package:flutter/material.dart';

class Dog {
  String bark() {
    return "Dog says: Woof!";
  }
}

class Cat {
  String meow() {
    return "Cat says: Meow!";
  }
}

class Bird {
  String fly() {
    return "Bird is flying";
  }
}

String checkObject(Object object) {
  if (object is Dog) {
    return object.bark();
  } else if (object is Cat) {
    return object.meow();
  } else if (object is Bird) {
    return object.fly();
  } else {
    return "Unknown object";
  }
}

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final result = '''
${checkObject(Dog())}
${checkObject(Cat())}
${checkObject(Bird())}
${checkObject("Hello")}
''';

    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 26')),
        body: Center(
          child: Text(
            result,
            textAlign: TextAlign.center,
            style: const TextStyle(fontSize: 24),
          ),
        ),
      ),
    );
  }
}


[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

class NumberIterator implements Iterator<int> {
  final List<int> numbers;
  int _index = -1;

  NumberIterator(this.numbers);

  @override
  int get current => numbers[_index];

  @override
  bool moveNext() {
    if (_index + 1 < numbers.length) {
      _index++;
      return true;
    }

    return false;
  }
}

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  MyApp({super.key});

  final NumberIterator iterator = NumberIterator([10, 20, 30]);

  @override
  Widget build(BuildContext context) {
    final List<String> results = [];

    while (iterator.moveNext()) {
      results.add(iterator.current.toString());
    }

    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 27')),
        body: Center(
          child: Text(
            results.join('\n'),
            textAlign: TextAlign.center,
            style: const TextStyle(fontSize: 24),
          ),
        ),
      ),
    );
  }
}


[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

abstract class Account {
  String owner;

  Account(this.owner);

  String showInfo();
}

class BankAccount extends Account {
  double balance;

  BankAccount(String owner, this.balance) : super(owner);

  @override
  String showInfo() {
    return "Owner: $owner\nBalance: $balance";
  }
}

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  MyApp({super.key});

  final BankAccount account = BankAccount("Ivan", 1500);

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 28')),
        body: Center(
          child: Text(
            account.showInfo(),
            textAlign: TextAlign.center,
            style: const TextStyle(fontSize: 24),
          ),
        ),
      ),
    );
  }
}



[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

abstract class ErrorHandler {
  String handleError(String error);
}

class NetworkErrorHandler implements ErrorHandler {
  @override
  String handleError(String error) {
    return "Network error: $error";
  }
}

class FileErrorHandler implements ErrorHandler {
  @override
  String handleError(String error) {
    return "File error: $error";
  }
}

class DatabaseErrorHandler implements ErrorHandler {
  @override
  String handleError(String error) {
    return "Database error: $error";
  }
}

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  MyApp({super.key});

  final List<ErrorHandler> handlers = [
    NetworkErrorHandler(),
    FileErrorHandler(),
    DatabaseErrorHandler(),
  ];

  @override
  Widget build(BuildContext context) {
    final result = handlers
        .map((handler) => handler.handleError("Something went wrong"))
        .join('\n');

    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 29')),
        body: Center(
          child: Text(
            result,
            textAlign: TextAlign.center,
            style: const TextStyle(fontSize: 24),
          ),
        ),
      ),
    );
  }
}


[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

abstract class Executable {
  String execute();
}

class Task implements Executable {
  String name;

  Task(this.name);

  @override
  String execute() {
    return "Executing task: $name";
  }
}

class Command implements Executable {
  String command;

  Command(this.command);

  @override
  String execute() {
    return "Running command: $command";
  }
}

class PolymorphicContainer {
  final List<Executable> items = [];

  void add(Executable item) {
    items.add(item);
  }

  String executeAll() {
    return items.map((item) => item.execute()).join('\n');
  }
}

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  MyApp({super.key});

  final PolymorphicContainer container = PolymorphicContainer();

  @override
  Widget build(BuildContext context) {
    container.add(Task("Clean project"));
    container.add(Command("flutter pub get"));
    container.add(Task("Run tests"));

    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 30')),
        body: Center(
          child: Text(
            container.executeAll(),
            textAlign: TextAlign.center,
            style: const TextStyle(fontSize: 24),
          ),
        ),
      ),
    );
  }
}



[06.05.2026 0:04] Zex: Да, сделаю так же: каждое задание — отдельный Flutter-код для DartPad.
В каждом примере уже добавил:
Dart
debugShowCheckedModeBanner: false
чтобы убрать надпись DEBUG.
Задача 31
Dart
import 'package:flutter/material.dart';

abstract class Repository<T> {
  T? findById(int id);
  List<T> findAll();
}

class User {
  int id;
  String name;

  User(this.id, this.name);

  @override
  String toString() => 'User(id: $id, name: $name)';
}

class UserRepository implements Repository<User> {
  final List<User> users = [
    User(1, 'Alice'),
    User(2, 'Bob'),
  ];

  @override
  User? findById(int id) {
    for (var user in users) {
      if (user.id == id) return user;
    }
    return null;
  }

  @override
  List<User> findAll() {
    return users;
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final repository = UserRepository();

    final result = '''
Найден пользователь:
${repository.findById(1)}

Все пользователи:
${repository.findAll().join('\n')}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 31')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 32
Dart
import 'package:flutter/material.dart' hide Container;

abstract class Container<T extends Comparable<dynamic>> {
  List<T> sortItems(List<T> items);
}

class SortedContainer<T extends Comparable<dynamic>> implements Container<T> {
  @override
  List<T> sortItems(List<T> items) {
    final copy = [...items];
    copy.sort((a, b) => a.compareTo(b));
    return copy;
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final container = SortedContainer<int>();
    final result = container.sortItems([5, 2, 9, 1]);

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 32')),
        body: Center(
          child: Text(
            'Отсортированный список:\n$result',
            textAlign: TextAlign.center,
          ),
        ),
      ),
    );
  }
}
Задача 33
Dart
import 'package:flutter/material.dart';

abstract class Printable {
  String printInfo();
}

mixin TimeStamp {
  String getTimeStamp() {
    return 'Created at: 2026';
  }
}

class Report with TimeStamp implements Printable {
  @override
  String printInfo() {
    return '''
Report object
${getTimeStamp()}
''';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final report = Report();

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 33')),
        body: Center(
          child: Text(
            report.printInfo(),
            textAlign: TextAlign.center,
          ),
        ),
      ),
    );
  }
}
Задача 34
Dart
import 'package:flutter/material.dart';

abstract class DataService {
  Future<String> fetchData();
}

class ApiService extends DataService {
  @override
  Future<String> fetchData() async {
    await Future.delayed(const Duration(seconds: 1));
    return 'Data loaded successfully!';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final service = ApiService();

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 34')),
        body: Center(
          child: FutureBuilder<String>(
            future: service.fetchData(),
            builder: (context, snapshot) {
              if (!snapshot.hasData) {
                return const Text('Загрузка...');
              }
[06.05.2026 0:04] Zex: return Text(snapshot.data!);
            },
          ),
        ),
      ),
    );
  }
}
Задача 35
Dart
import 'package:flutter/material.dart';

abstract class SortStrategy {
  List<int> sort(List<int> numbers);
}

class AscendingSort implements SortStrategy {
  @override
  List<int> sort(List<int> numbers) {
    final copy = [...numbers];
    copy.sort();
    return copy;
  }
}

class DescendingSort implements SortStrategy {
  @override
  List<int> sort(List<int> numbers) {
    final copy = [...numbers];
    copy.sort((a, b) => b.compareTo(a));
    return copy;
  }
}

class Sorter {
  SortStrategy strategy;

  Sorter(this.strategy);

  List<int> sort(List<int> numbers) {
    return strategy.sort(numbers);
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final numbers = [5, 1, 9, 3];

    final ascending = Sorter(AscendingSort()).sort(numbers);
    final descending = Sorter(DescendingSort()).sort(numbers);

    final result = '''
Исходный список: $numbers
По возрастанию: $ascending
По убыванию: $descending
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 35')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 36
Dart
import 'package:flutter/material.dart';

abstract class Observer {
  String update(String message);
}

abstract class Subject {
  void addObserver(Observer observer);
  void removeObserver(Observer observer);
  List<String> notifyObservers(String message);
}

class UserObserver implements Observer {
  String name;

  UserObserver(this.name);

  @override
  String update(String message) {
    return '$name получил уведомление: $message';
  }
}

class NewsSubject implements Subject {
  final List<Observer> observers = [];

  @override
  void addObserver(Observer observer) {
    observers.add(observer);
  }

  @override
  void removeObserver(Observer observer) {
    observers.remove(observer);
  }

  @override
  List<String> notifyObservers(String message) {
    return observers.map((observer) => observer.update(message)).toList();
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final subject = NewsSubject();

    subject.addObserver(UserObserver('Alice'));
    subject.addObserver(UserObserver('Bob'));

    final result = subject.notifyObservers('Новая новость!').join('\n');

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 36')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 37
Dart
import 'package:flutter/material.dart';

abstract class Coffee {
  String getDescription();
  double cost();
}

class SimpleCoffee implements Coffee {
  @override
  String getDescription() {
    return 'Simple coffee';
  }

  @override
  double cost() {
    return 5;
  }
}

class MilkDecorator implements Coffee {
  Coffee coffee;

  MilkDecorator(this.coffee);

  @override
  String getDescription() {
    return '${coffee.getDescription()} + milk';
  }

  @override
  double cost() {
    return coffee.cost() + 2;
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final coffee = MilkDecorator(SimpleCoffee());

    final result = '''
Описание: ${coffee.getDescription()}
Цена: ${coffee.cost()}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 37')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 38
Dart
import 'package:flutter/material.dart';
[06.05.2026 0:04] Zex: abstract class Animal {
  String sound();
}

class Dog implements Animal {
  @override
  String sound() => 'Woof!';
}

class Cat implements Animal {
  @override
  String sound() => 'Meow!';
}

class AnimalFactory {
  static Animal createAnimal(String type) {
    if (type == 'dog') {
      return Dog();
    } else if (type == 'cat') {
      return Cat();
    } else {
      throw ArgumentError('Unknown animal');
    }
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final dog = AnimalFactory.createAnimal('dog');
    final cat = AnimalFactory.createAnimal('cat');

    final result = '''
Dog: ${dog.sound()}
Cat: ${cat.sound()}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 38')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 39
Dart
import 'package:flutter/material.dart';

abstract class SettingsProvider {
  String getSetting(String key);
}

class AppSettings implements SettingsProvider {
  static final AppSettings _instance = AppSettings._internal();

  final Map<String, String> _settings = {
    'theme': 'dark',
    'language': 'ru',
  };

  factory AppSettings() {
    return _instance;
  }

  AppSettings._internal();

  @override
  String getSetting(String key) {
    return _settings[key] ?? 'not found';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final settings1 = AppSettings();
    final settings2 = AppSettings();

    final result = '''
Theme: ${settings1.getSetting('theme')}
Language: ${settings2.getSetting('language')}

Один объект: ${identical(settings1, settings2)}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 39')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 40
Dart
import 'package:flutter/material.dart';

class OldPrinter {
  String printOld(String text) {
    return 'Old printer: $text';
  }
}

abstract class ModernPrinter {
  String printDocument(String text);
}

class PrinterAdapter implements ModernPrinter {
  OldPrinter oldPrinter;

  PrinterAdapter(this.oldPrinter);

  @override
  String printDocument(String text) {
    return oldPrinter.printOld(text);
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final printer = PrinterAdapter(OldPrinter());

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 40')),
        body: Center(
          child: Text(printer.printDocument('Hello adapter!')),
        ),
      ),
    );
  }
}
Задача 41
Dart
import 'package:flutter/material.dart';

abstract class Device {
  String turnOn();
  String turnOff();
}

class TV implements Device {
  @override
  String turnOn() => 'TV is on';

  @override
  String turnOff() => 'TV is off';
}

class Radio implements Device {
  @override
  String turnOn() => 'Radio is on';

  @override
  String turnOff() => 'Radio is off';
}

class RemoteControl {
  Device device;

  RemoteControl(this.device);

  String powerOn() => device.turnOn();
  String powerOff() => device.turnOff();
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final tvRemote = RemoteControl(TV());
    final radioRemote = RemoteControl(Radio());

    final result = '''
${tvRemote.powerOn()}
${tvRemote.powerOff()}

${radioRemote.powerOn()}
${radioRemote.powerOff()}
''';
[06.05.2026 0:04] Zex: return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 41')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 42
Dart
import 'package:flutter/material.dart';

class Engine {
  String start() {
    return 'Engine started';
  }
}

class Car {
  Engine engine;

  Car(this.engine);

  String drive() {
    return '''
${engine.start()}
Car is driving
''';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final car = Car(Engine());

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 42')),
        body: Center(
          child: Text(car.drive(), textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 43
Dart
import 'dart:convert';
import 'package:flutter/material.dart';

abstract class Saveable {
  String get id;
  Map<String, dynamic> save();
}

class User implements Saveable {
  @override
  String id;

  String name;

  User(this.id, this.name);

  @override
  Map<String, dynamic> save() {
    return {
      'type': 'User',
      'id': id,
      'name': name,
    };
  }
}

class Product implements Saveable {
  @override
  String id;

  String title;

  Product(this.id, this.title);

  @override
  Map<String, dynamic> save() {
    return {
      'type': 'Product',
      'id': id,
      'title': title,
    };
  }
}

class StateStorage {
  final List<Saveable> items = [];

  void add(Saveable item) {
    items.add(item);
  }

  List<Map<String, dynamic>> saveAll() {
    return items.map((item) => item.save()).toList();
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final storage = StateStorage();

    storage.add(User('1', 'Alice'));
    storage.add(Product('p1', 'Laptop'));

    final result = const JsonEncoder.withIndent('  ').convert(storage.saveAll());

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 43')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 44
Dart
import 'package:flutter/material.dart';

abstract class AppException implements Exception {
  String message;

  AppException(this.message);

  @override
  String toString() => message;
}

class NetworkException extends AppException {
  NetworkException(String message) : super(message);
}

class DatabaseException extends AppException {
  DatabaseException(String message) : super(message);
}

abstract class Operation {
  String execute();

  String safeExecute() {
    try {
      return execute();
    } on AppException catch (error) {
      return 'Ошибка обработана: ${error.message}';
    }
  }
}

class NetworkOperation extends Operation {
  @override
  String execute() {
    throw NetworkException('Нет подключения к интернету');
  }
}

class DatabaseOperation extends Operation {
  @override
  String execute() {
    throw DatabaseException('Ошибка базы данных');
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final operations = [
      NetworkOperation(),
      DatabaseOperation(),
    ];

    final result = operations.map((op) => op.safeExecute()).join('\n');

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 44')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 45
Dart
import 'package:flutter/material.dart';

class Animal {
  String name;

  Animal(this.name);
}

class Dog extends Animal {
  Dog(String name) : super(name);
}
[06.05.2026 0:04] Zex: abstract class Producer<T extends Animal> {
  T produce();
}

class DogProducer implements Producer<Dog> {
  @override
  Dog produce() {
    return Dog('Rex');
  }
}

typedef DogConsumer = String Function(Dog dog);

String animalConsumer(Animal animal) {
  return 'Consumer получил: ${animal.name}';
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    Producer<Animal> producer = DogProducer();

    DogConsumer consumer = animalConsumer;

    final animal = producer.produce();

    final result = '''
Ковариантность:
Producer<Dog> можно использовать как Producer<Animal>
Произведён объект: ${animal.name}

Контравариантность в функции:
${consumer(Dog('Buddy'))}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 45')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 46
Dart
import 'package:flutter/material.dart';

abstract class Cloneable<T> {
  T clone();
}

class Address implements Cloneable<Address> {
  String city;

  Address(this.city);

  @override
  Address clone() {
    return Address(city);
  }
}

class User implements Cloneable<User> {
  String name;
  Address address;

  User(this.name, this.address);

  @override
  User clone() {
    return User(name, address.clone());
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final user1 = User('Alice', Address('Astana'));
    final user2 = user1.clone();

    user2.address.city = 'Almaty';

    final result = '''
Оригинал: ${user1.name}, ${user1.address.city}
Копия: ${user2.name}, ${user2.address.city}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 46')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 47
Dart
import 'package:flutter/material.dart';

abstract class DataProcessor<T> {
  List<T> loadData();
  List<T> filter(List<T> data);
  List<String> transform(List<T> data);
}

class NumberProcessor extends DataProcessor<int> {
  @override
  List<int> loadData() {
    return [1, 2, 3, 4, 5, 6];
  }

  @override
  List<int> filter(List<int> data) {
    return data.where((number) => number > 3).toList();
  }

  @override
  List<String> transform(List<int> data) {
    return data.map((number) => 'Number: $number').toList();
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final processor = NumberProcessor();

    final loaded = processor.loadData();
    final filtered = processor.filter(loaded);
    final transformed = processor.transform(filtered);

    final result = '''
Загружено: $loaded
Фильтр: $filtered

${transformed.join('\n')}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 47')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 48
Dart
import 'package:flutter/material.dart';

abstract class EventListener {
  String onEvent(String event);
}

class ButtonClickListener extends EventListener {
  @override
  String onEvent(String event) {
    return 'Button listener получил событие: $event';
  }
}

class FormSubmitListener extends EventListener {
  @override
  String onEvent(String event) {
    return 'Form listener получил событие: $event';
  }
}

class EventManager {
  final List<EventListener> listeners = [];

  void addListener(EventListener listener) {
    listeners.add(listener);
  }

  List<String> fireEvent(String event) {
    return listeners.map((listener) => listener.onEvent(event)).toList();
  }
}
[06.05.2026 0:04] Zex: void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final manager = EventManager();

    manager.addListener(ButtonClickListener());
    manager.addListener(FormSubmitListener());

    final result = manager.fireEvent('Click').join('\n');

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 48')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 49
Dart
import 'package:flutter/material.dart';

class Request {
  bool isAuthenticated;
  bool hasPermission;

  Request({
    required this.isAuthenticated,
    required this.hasPermission,
  });
}

abstract class Handler {
  Handler? next;

  Handler setNext(Handler handler) {
    next = handler;
    return handler;
  }

  String handle(Request request) {
    if (next != null) {
      return next!.handle(request);
    }

    return 'Запрос обработан';
  }
}

class AuthHandler extends Handler {
  @override
  String handle(Request request) {
    if (!request.isAuthenticated) {
      return 'Ошибка: пользователь не авторизован';
    }

    return super.handle(request);
  }
}

class PermissionHandler extends Handler {
  @override
  String handle(Request request) {
    if (!request.hasPermission) {
      return 'Ошибка: нет прав доступа';
    }

    return super.handle(request);
  }
}

class FinalHandler extends Handler {
  @override
  String handle(Request request) {
    return 'Запрос успешно прошёл всю цепочку';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final auth = AuthHandler();
    final permission = PermissionHandler();
    final finalHandler = FinalHandler();

    auth.setNext(permission).setNext(finalHandler);

    final request = Request(
      isAuthenticated: true,
      hasPermission: true,
    );

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 49')),
        body: Center(
          child: Text(auth.handle(request)),
        ),
      ),
    );
  }
}
Задача 50
Dart
import 'package:flutter/material.dart';

abstract class DataExporter {
  String export() {
    return '''
${openConnection()}
${writeData()}
${closeConnection()}
''';
  }

  String openConnection();
  String writeData();
  String closeConnection();
}

class JsonExporter extends DataExporter {
  @override
  String openConnection() {
    return 'Открываем соединение';
  }

  @override
  String writeData() {
    return 'Записываем JSON данные';
  }

  @override
  String closeConnection() {
    return 'Закрываем соединение';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final exporter = JsonExporter();

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 50')),
        body: Center(
          child: Text(exporter.export(), textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 51
Dart
import 'package:flutter/material.dart';

abstract class Validator<T> {
  String validate(T value);
}

class EmailValidator implements Validator<String> {
  @override
  String validate(String value) {
    if (value.contains('@')) {
      return 'Email корректный';
    }

    return 'Email некорректный';
  }
}

class AgeValidator implements Validator<int> {
  @override
  String validate(int value) {
    if (value >= 18) {
      return 'Возраст подходит';
    }

    return 'Возраст меньше 18';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});
[06.05.2026 0:04] Zex: @override
  Widget build(BuildContext context) {
    final emailValidator = EmailValidator();
    final ageValidator = AgeValidator();

    final result = '''
${emailValidator.validate('test@mail.com')}
${ageValidator.validate(20)}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 51')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 52
Dart
import 'package:flutter/material.dart';

class Computer {
  String cpu = '';
  String ram = '';

  @override
  String toString() {
    return 'Computer(cpu: $cpu, ram: $ram)';
  }
}

abstract class ComputerBuilder {
  void setCpu();
  void setRam();
  Computer build();
}

class GamingComputerBuilder implements ComputerBuilder {
  final Computer computer = Computer();

  @override
  void setCpu() {
    computer.cpu = 'Intel i9';
  }

  @override
  void setRam() {
    computer.ram = '32 GB';
  }

  @override
  Computer build() {
    return computer;
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final builder = GamingComputerBuilder();

    builder.setCpu();
    builder.setRam();

    final computer = builder.build();

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 52')),
        body: Center(
          child: Text(computer.toString()),
        ),
      ),
    );
  }
}
Задача 53
Dart
import 'dart:convert';
import 'package:flutter/material.dart';

abstract class Serializable {
  Map<String, dynamic> toJson();
}

class User implements Serializable {
  String name;
  int age;

  User(this.name, this.age);

  @override
  Map<String, dynamic> toJson() {
    return {
      'type': 'User',
      'name': name,
      'age': age,
    };
  }
}

class Product implements Serializable {
  String title;
  double price;

  Product(this.title, this.price);

  @override
  Map<String, dynamic> toJson() {
    return {
      'type': 'Product',
      'title': title,
      'price': price,
    };
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final objects = <Serializable>[
      User('Alice', 20),
      Product('Phone', 999),
    ];

    final json = const JsonEncoder.withIndent('  ')
        .convert(objects.map((object) => object.toJson()).toList());

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 53')),
        body: Center(
          child: Text(json, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 54
Dart
import 'package:flutter/material.dart';

abstract class StreamProcessor<T> {
  Stream<T> process(Stream<T> input);
}

class DoubleNumberProcessor implements StreamProcessor<int> {
  @override
  Stream<int> process(Stream<int> input) async* {
    await for (final number in input) {
      yield number * 2;
    }
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final processor = DoubleNumberProcessor();

    final future = processor
        .process(Stream.fromIterable([1, 2, 3, 4]))
        .toList();

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 54')),
        body: Center(
          child: FutureBuilder<List<int>>(
            future: future,
            builder: (context, snapshot) {
              if (!snapshot.hasData) {
                return const Text('Обработка потока...');
              }

              return Text('Результат: ${snapshot.data}');
            },
          ),
        ),
      ),
    );
  }
}
Задача 55
Dart
import 'package:flutter/material.dart';
[06.05.2026 0:04] Zex: abstract class FileStorage {
  String write(String fileName, String data);
  String read(String fileName);
}

class JsonFileStorage implements FileStorage {
  final Map<String, String> files = {};

  @override
  String write(String fileName, String data) {
    files[fileName] = '{ "data": "$data" }';
    return 'JSON файл записан';
  }

  @override
  String read(String fileName) {
    return files[fileName] ?? 'Файл не найден';
  }
}

class XmlFileStorage implements FileStorage {
  final Map<String, String> files = {};

  @override
  String write(String fileName, String data) {
    files[fileName] = '<data>$data</data>';
    return 'XML файл записан';
  }

  @override
  String read(String fileName) {
    return files[fileName] ?? 'Файл не найден';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final jsonStorage = JsonFileStorage();
    final xmlStorage = XmlFileStorage();

    jsonStorage.write('user.json', 'Alice');
    xmlStorage.write('user.xml', 'Bob');

    final result = '''
${jsonStorage.read('user.json')}
${xmlStorage.read('user.xml')}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 55')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 56
Dart
import 'package:flutter/material.dart';

abstract class FormValidator {
  String validate(Map<String, String> form);
}

class NameValidator extends FormValidator {
  @override
  String validate(Map<String, String> form) {
    final name = form['name'] ?? '';

    if (name.isEmpty) {
      return 'Имя не заполнено';
    }

    return 'Имя корректное';
  }
}

class EmailFormValidator extends FormValidator {
  @override
  String validate(Map<String, String> form) {
    final email = form['email'] ?? '';

    if (!email.contains('@')) {
      return 'Email некорректный';
    }

    return 'Email корректный';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final form = {
      'name': 'Alice',
      'email': 'alice@mail.com',
    };

    final validators = [
      NameValidator(),
      EmailFormValidator(),
    ];

    final result = validators
        .map((validator) => validator.validate(form))
        .join('\n');

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 56')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 57
Dart
import 'package:flutter/material.dart';

abstract class Logger {
  String log(String message);
}

class ConsoleLogger implements Logger {
  @override
  String log(String message) {
    return 'Console log: $message';
  }
}

class FileLogger implements Logger {
  @override
  String log(String message) {
    return 'File log: $message';
  }
}

class NetworkLogger implements Logger {
  @override
  String log(String message) {
    return 'Network log: $message';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final loggers = [
      ConsoleLogger(),
      FileLogger(),
      NetworkLogger(),
    ];

    final result = loggers
        .map((logger) => logger.log('Hello'))
        .join('\n');

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 57')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 58
Dart
import 'package:flutter/material.dart';

abstract class Cache<K, V> {
  V? get(K key);
  void set(K key, V value);
  void clear();
}
[06.05.2026 0:04] Zex: class MemoryCache<K, V> implements Cache<K, V> {
  final Map<K, V> storage = {};

  @override
  V? get(K key) {
    return storage[key];
  }

  @override
  void set(K key, V value) {
    storage[key] = value;
  }

  @override
  void clear() {
    storage.clear();
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final cache = MemoryCache<String, int>();

    cache.set('age', 25);

    final beforeClear = cache.get('age');

    cache.clear();

    final afterClear = cache.get('age');

    final result = '''
До очистки: $beforeClear
После очистки: $afterClear
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 58')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 59
Dart
import 'package:flutter/material.dart';

abstract class HttpClient {
  String GET(String url);
  String POST(String url, String body);
  String PUT(String url, String body);
  String DELETE(String url);
}

class MockHttpClient implements HttpClient {
  @override
  String GET(String url) {
    return 'GET request to $url';
  }

  @override
  String POST(String url, String body) {
    return 'POST request to $url with body: $body';
  }

  @override
  String PUT(String url, String body) {
    return 'PUT request to $url with body: $body';
  }

  @override
  String DELETE(String url) {
    return 'DELETE request to $url';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final client = MockHttpClient();

    final result = '''
${client.GET('/users')}
${client.POST('/users', 'new user')}
${client.PUT('/users/1', 'updated user')}
${client.DELETE('/users/1')}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 59')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 60
Dart
import 'package:flutter/material.dart';

abstract class Database {
  String connect();
  String insert(String data);
  String read();
}

class SqlDatabase implements Database {
  @override
  String connect() {
    return 'Connected to SQL database';
  }

  @override
  String insert(String data) {
    return 'Inserted into SQL: $data';
  }

  @override
  String read() {
    return 'Reading from SQL database';
  }
}

class NoSqlDatabase implements Database {
  @override
  String connect() {
    return 'Connected to NoSQL database';
  }

  @override
  String insert(String data) {
    return 'Inserted into NoSQL: $data';
  }

  @override
  String read() {
    return 'Reading from NoSQL database';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final databases = [
      SqlDatabase(),
      NoSqlDatabase(),
    ];

    final result = databases
        .map((db) => '''
${db.connect()}
${db.insert('User Alice')}
${db.read()}
''')
        .join('\n');

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 60')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 61
Dart
import 'package:flutter/material.dart';

mixin Cacheable<T> {
  final Map<String, T> _cache = {};

  void cache(String key, T value) {
    _cache[key] = value;
  }

  T? getFromCache(String key) {
    return _cache[key];
  }
}

class UserService with Cacheable<String> {
  String loadUser(String id) {
    final cachedUser = getFromCache(id);

    if (cachedUser != null) {
      return 'Из кэша: $cachedUser';
    }

    final user = 'User with id $id';
    cache(id, user);
[06.05.2026 0:04] Zex: return 'Загружено и сохранено в кэш: $user';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final service = UserService();

    final first = service.loadUser('1');
    final second = service.loadUser('1');

    final result = '''
$first
$second
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 61')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 62
Dart
import 'package:flutter/material.dart';

abstract class Readable<T> {
  T read(String id);
}

abstract class Writable<T> {
  String write(T item);
}

abstract class Deletable {
  String delete(String id);
}

abstract class Repository<T>
    implements Readable<T>, Writable<T>, Deletable {}

class UserRepository implements Repository<String> {
  final Map<String, String> users = {};

  @override
  String write(String item) {
    users['1'] = item;
    return 'Пользователь сохранён: $item';
  }

  @override
  String read(String id) {
    return users[id] ?? 'Пользователь не найден';
  }

  @override
  String delete(String id) {
    users.remove(id);
    return 'Пользователь удалён';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final repository = UserRepository();

    final result = '''
${repository.write('Alice')}
${repository.read('1')}
${repository.delete('1')}
${repository.read('1')}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 62')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 63
Dart
import 'package:flutter/material.dart';

abstract class StrictBox<T> {
  T get value;
  void setValue(T value);
}

class IntBox extends StrictBox<int> {
  int _value;

  IntBox(this._value);

  @override
  int get value => _value;

  @override
  void setValue(int value) {
    _value = value;
  }
}

class StringBox extends StrictBox<String> {
  String _value;

  StringBox(this._value);

  @override
  String get value => _value;

  @override
  void setValue(String value) {
    _value = value;
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final intBox = IntBox(10);
    final stringBox = StringBox('Hello');

    intBox.setValue(20);
    stringBox.setValue('Dart');

    final result = '''
IntBox хранит только int: ${intBox.value}
StringBox хранит только String: ${stringBox.value}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 63')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}Да, сделаю так же: каждое задание — отдельный Flutter-код для DartPad.
В каждом примере уже добавил:
Dart
debugShowCheckedModeBanner: false
чтобы убрать надпись DEBUG.
Задача 31
Dart
import 'package:flutter/material.dart';

abstract class Repository<T> {
  T? findById(int id);
  List<T> findAll();
}

class User {
  int id;
  String name;

  User(this.id, this.name);

  @override
  String toString() => 'User(id: $id, name: $name)';
}

class UserRepository implements Repository<User> {
  final List<User> users = [
    User(1, 'Alice'),
    User(2, 'Bob'),
  ];

  @override
  User? findById(int id) {
    for (var user in users) {
      if (user.id == id) return user;
    }
    return null;
  }

  @override
  List<User> findAll() {
    return users;
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final repository = UserRepository();
[06.05.2026 0:04] Zex: final result = '''
Найден пользователь:
${repository.findById(1)}

Все пользователи:
${repository.findAll().join('\n')}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 31')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 32
Dart
import 'package:flutter/material.dart' hide Container;

abstract class Container<T extends Comparable<dynamic>> {
  List<T> sortItems(List<T> items);
}

class SortedContainer<T extends Comparable<dynamic>> implements Container<T> {
  @override
  List<T> sortItems(List<T> items) {
    final copy = [...items];
    copy.sort((a, b) => a.compareTo(b));
    return copy;
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final container = SortedContainer<int>();
    final result = container.sortItems([5, 2, 9, 1]);

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 32')),
        body: Center(
          child: Text(
            'Отсортированный список:\n$result',
            textAlign: TextAlign.center,
          ),
        ),
      ),
    );
  }
}
Задача 33
Dart
import 'package:flutter/material.dart';

abstract class Printable {
  String printInfo();
}

mixin TimeStamp {
  String getTimeStamp() {
    return 'Created at: 2026';
  }
}

class Report with TimeStamp implements Printable {
  @override
  String printInfo() {
    return '''
Report object
${getTimeStamp()}
''';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final report = Report();

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 33')),
        body: Center(
          child: Text(
            report.printInfo(),
            textAlign: TextAlign.center,
          ),
        ),
      ),
    );
  }
}
Задача 34
Dart
import 'package:flutter/material.dart';

abstract class DataService {
  Future<String> fetchData();
}

class ApiService extends DataService {
  @override
  Future<String> fetchData() async {
    await Future.delayed(const Duration(seconds: 1));
    return 'Data loaded successfully!';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final service = ApiService();

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 34')),
        body: Center(
          child: FutureBuilder<String>(
            future: service.fetchData(),
            builder: (context, snapshot) {
              if (!snapshot.hasData) {
                return const Text('Загрузка...');
              }

              return Text(snapshot.data!);
            },
          ),
        ),
      ),
    );
  }
}
Задача 35
Dart
import 'package:flutter/material.dart';

abstract class SortStrategy {
  List<int> sort(List<int> numbers);
}

class AscendingSort implements SortStrategy {
  @override
  List<int> sort(List<int> numbers) {
    final copy = [...numbers];
    copy.sort();
    return copy;
  }
}

class DescendingSort implements SortStrategy {
  @override
  List<int> sort(List<int> numbers) {
    final copy = [...numbers];
    copy.sort((a, b) => b.compareTo(a));
    return copy;
  }
}

class Sorter {
  SortStrategy strategy;

  Sorter(this.strategy);

  List<int> sort(List<int> numbers) {
    return strategy.sort(numbers);
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final numbers = [5, 1, 9, 3];
[06.05.2026 0:04] Zex: final ascending = Sorter(AscendingSort()).sort(numbers);
    final descending = Sorter(DescendingSort()).sort(numbers);

    final result = '''
Исходный список: $numbers
По возрастанию: $ascending
По убыванию: $descending
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 35')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 36
Dart
import 'package:flutter/material.dart';

abstract class Observer {
  String update(String message);
}

abstract class Subject {
  void addObserver(Observer observer);
  void removeObserver(Observer observer);
  List<String> notifyObservers(String message);
}

class UserObserver implements Observer {
  String name;

  UserObserver(this.name);

  @override
  String update(String message) {
    return '$name получил уведомление: $message';
  }
}

class NewsSubject implements Subject {
  final List<Observer> observers = [];

  @override
  void addObserver(Observer observer) {
    observers.add(observer);
  }

  @override
  void removeObserver(Observer observer) {
    observers.remove(observer);
  }

  @override
  List<String> notifyObservers(String message) {
    return observers.map((observer) => observer.update(message)).toList();
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final subject = NewsSubject();

    subject.addObserver(UserObserver('Alice'));
    subject.addObserver(UserObserver('Bob'));

    final result = subject.notifyObservers('Новая новость!').join('\n');

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 36')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 37
Dart
import 'package:flutter/material.dart';

abstract class Coffee {
  String getDescription();
  double cost();
}

class SimpleCoffee implements Coffee {
  @override
  String getDescription() {
    return 'Simple coffee';
  }

  @override
  double cost() {
    return 5;
  }
}

class MilkDecorator implements Coffee {
  Coffee coffee;

  MilkDecorator(this.coffee);

  @override
  String getDescription() {
    return '${coffee.getDescription()} + milk';
  }

  @override
  double cost() {
    return coffee.cost() + 2;
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final coffee = MilkDecorator(SimpleCoffee());

    final result = '''
Описание: ${coffee.getDescription()}
Цена: ${coffee.cost()}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 37')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 38
Dart
import 'package:flutter/material.dart';

abstract class Animal {
  String sound();
}

class Dog implements Animal {
  @override
  String sound() => 'Woof!';
}

class Cat implements Animal {
  @override
  String sound() => 'Meow!';
}

class AnimalFactory {
  static Animal createAnimal(String type) {
    if (type == 'dog') {
      return Dog();
    } else if (type == 'cat') {
      return Cat();
    } else {
      throw ArgumentError('Unknown animal');
    }
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final dog = AnimalFactory.createAnimal('dog');
    final cat = AnimalFactory.createAnimal('cat');

    final result = '''
Dog: ${dog.sound()}
Cat: ${cat.sound()}
''';
[06.05.2026 0:04] Zex: return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 38')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 39
Dart
import 'package:flutter/material.dart';

abstract class SettingsProvider {
  String getSetting(String key);
}

class AppSettings implements SettingsProvider {
  static final AppSettings _instance = AppSettings._internal();

  final Map<String, String> _settings = {
    'theme': 'dark',
    'language': 'ru',
  };

  factory AppSettings() {
    return _instance;
  }

  AppSettings._internal();

  @override
  String getSetting(String key) {
    return _settings[key] ?? 'not found';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final settings1 = AppSettings();
    final settings2 = AppSettings();

    final result = '''
Theme: ${settings1.getSetting('theme')}
Language: ${settings2.getSetting('language')}

Один объект: ${identical(settings1, settings2)}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 39')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 40
Dart
import 'package:flutter/material.dart';

class OldPrinter {
  String printOld(String text) {
    return 'Old printer: $text';
  }
}

abstract class ModernPrinter {
  String printDocument(String text);
}

class PrinterAdapter implements ModernPrinter {
  OldPrinter oldPrinter;

  PrinterAdapter(this.oldPrinter);

  @override
  String printDocument(String text) {
    return oldPrinter.printOld(text);
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final printer = PrinterAdapter(OldPrinter());

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 40')),
        body: Center(
          child: Text(printer.printDocument('Hello adapter!')),
        ),
      ),
    );
  }
}
Задача 41
Dart
import 'package:flutter/material.dart';

abstract class Device {
  String turnOn();
  String turnOff();
}

class TV implements Device {
  @override
  String turnOn() => 'TV is on';

  @override
  String turnOff() => 'TV is off';
}

class Radio implements Device {
  @override
  String turnOn() => 'Radio is on';

  @override
  String turnOff() => 'Radio is off';
}

class RemoteControl {
  Device device;

  RemoteControl(this.device);

  String powerOn() => device.turnOn();
  String powerOff() => device.turnOff();
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final tvRemote = RemoteControl(TV());
    final radioRemote = RemoteControl(Radio());

    final result = '''
${tvRemote.powerOn()}
${tvRemote.powerOff()}

${radioRemote.powerOn()}
${radioRemote.powerOff()}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 41')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 42
Dart
import 'package:flutter/material.dart';

class Engine {
  String start() {
    return 'Engine started';
  }
}

class Car {
  Engine engine;

  Car(this.engine);

  String drive() {
    return '''
${engine.start()}
Car is driving
''';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final car = Car(Engine());
[06.05.2026 0:04] Zex: return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 42')),
        body: Center(
          child: Text(car.drive(), textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 43
Dart
import 'dart:convert';
import 'package:flutter/material.dart';

abstract class Saveable {
  String get id;
  Map<String, dynamic> save();
}

class User implements Saveable {
  @override
  String id;

  String name;

  User(this.id, this.name);

  @override
  Map<String, dynamic> save() {
    return {
      'type': 'User',
      'id': id,
      'name': name,
    };
  }
}

class Product implements Saveable {
  @override
  String id;

  String title;

  Product(this.id, this.title);

  @override
  Map<String, dynamic> save() {
    return {
      'type': 'Product',
      'id': id,
      'title': title,
    };
  }
}

class StateStorage {
  final List<Saveable> items = [];

  void add(Saveable item) {
    items.add(item);
  }

  List<Map<String, dynamic>> saveAll() {
    return items.map((item) => item.save()).toList();
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final storage = StateStorage();

    storage.add(User('1', 'Alice'));
    storage.add(Product('p1', 'Laptop'));

    final result = const JsonEncoder.withIndent('  ').convert(storage.saveAll());

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 43')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 44
Dart
import 'package:flutter/material.dart';

abstract class AppException implements Exception {
  String message;

  AppException(this.message);

  @override
  String toString() => message;
}

class NetworkException extends AppException {
  NetworkException(String message) : super(message);
}

class DatabaseException extends AppException {
  DatabaseException(String message) : super(message);
}

abstract class Operation {
  String execute();

  String safeExecute() {
    try {
      return execute();
    } on AppException catch (error) {
      return 'Ошибка обработана: ${error.message}';
    }
  }
}

class NetworkOperation extends Operation {
  @override
  String execute() {
    throw NetworkException('Нет подключения к интернету');
  }
}

class DatabaseOperation extends Operation {
  @override
  String execute() {
    throw DatabaseException('Ошибка базы данных');
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final operations = [
      NetworkOperation(),
      DatabaseOperation(),
    ];

    final result = operations.map((op) => op.safeExecute()).join('\n');

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 44')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 45
Dart
import 'package:flutter/material.dart';

class Animal {
  String name;

  Animal(this.name);
}

class Dog extends Animal {
  Dog(String name) : super(name);
}

abstract class Producer<T extends Animal> {
  T produce();
}

class DogProducer implements Producer<Dog> {
  @override
  Dog produce() {
    return Dog('Rex');
  }
}

typedef DogConsumer = String Function(Dog dog);

String animalConsumer(Animal animal) {
  return 'Consumer получил: ${animal.name}';
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    Producer<Animal> producer = DogProducer();

    DogConsumer consumer = animalConsumer;

    final animal = producer.produce();
[06.05.2026 0:04] Zex: final result = '''
Ковариантность:
Producer<Dog> можно использовать как Producer<Animal>
Произведён объект: ${animal.name}

Контравариантность в функции:
${consumer(Dog('Buddy'))}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 45')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 46
Dart
import 'package:flutter/material.dart';

abstract class Cloneable<T> {
  T clone();
}

class Address implements Cloneable<Address> {
  String city;

  Address(this.city);

  @override
  Address clone() {
    return Address(city);
  }
}

class User implements Cloneable<User> {
  String name;
  Address address;

  User(this.name, this.address);

  @override
  User clone() {
    return User(name, address.clone());
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final user1 = User('Alice', Address('Astana'));
    final user2 = user1.clone();

    user2.address.city = 'Almaty';

    final result = '''
Оригинал: ${user1.name}, ${user1.address.city}
Копия: ${user2.name}, ${user2.address.city}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 46')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 47
Dart
import 'package:flutter/material.dart';

abstract class DataProcessor<T> {
  List<T> loadData();
  List<T> filter(List<T> data);
  List<String> transform(List<T> data);
}

class NumberProcessor extends DataProcessor<int> {
  @override
  List<int> loadData() {
    return [1, 2, 3, 4, 5, 6];
  }

  @override
  List<int> filter(List<int> data) {
    return data.where((number) => number > 3).toList();
  }

  @override
  List<String> transform(List<int> data) {
    return data.map((number) => 'Number: $number').toList();
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final processor = NumberProcessor();

    final loaded = processor.loadData();
    final filtered = processor.filter(loaded);
    final transformed = processor.transform(filtered);

    final result = '''
Загружено: $loaded
Фильтр: $filtered

${transformed.join('\n')}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 47')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 48
Dart
import 'package:flutter/material.dart';

abstract class EventListener {
  String onEvent(String event);
}

class ButtonClickListener extends EventListener {
  @override
  String onEvent(String event) {
    return 'Button listener получил событие: $event';
  }
}

class FormSubmitListener extends EventListener {
  @override
  String onEvent(String event) {
    return 'Form listener получил событие: $event';
  }
}

class EventManager {
  final List<EventListener> listeners = [];

  void addListener(EventListener listener) {
    listeners.add(listener);
  }

  List<String> fireEvent(String event) {
    return listeners.map((listener) => listener.onEvent(event)).toList();
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final manager = EventManager();

    manager.addListener(ButtonClickListener());
    manager.addListener(FormSubmitListener());

    final result = manager.fireEvent('Click').join('\n');
[06.05.2026 0:04] Zex: return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 48')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 49
Dart
import 'package:flutter/material.dart';

class Request {
  bool isAuthenticated;
  bool hasPermission;

  Request({
    required this.isAuthenticated,
    required this.hasPermission,
  });
}

abstract class Handler {
  Handler? next;

  Handler setNext(Handler handler) {
    next = handler;
    return handler;
  }

  String handle(Request request) {
    if (next != null) {
      return next!.handle(request);
    }

    return 'Запрос обработан';
  }
}

class AuthHandler extends Handler {
  @override
  String handle(Request request) {
    if (!request.isAuthenticated) {
      return 'Ошибка: пользователь не авторизован';
    }

    return super.handle(request);
  }
}

class PermissionHandler extends Handler {
  @override
  String handle(Request request) {
    if (!request.hasPermission) {
      return 'Ошибка: нет прав доступа';
    }

    return super.handle(request);
  }
}

class FinalHandler extends Handler {
  @override
  String handle(Request request) {
    return 'Запрос успешно прошёл всю цепочку';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final auth = AuthHandler();
    final permission = PermissionHandler();
    final finalHandler = FinalHandler();

    auth.setNext(permission).setNext(finalHandler);

    final request = Request(
      isAuthenticated: true,
      hasPermission: true,
    );

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 49')),
        body: Center(
          child: Text(auth.handle(request)),
        ),
      ),
    );
  }
}
Задача 50
Dart
import 'package:flutter/material.dart';

abstract class DataExporter {
  String export() {
    return '''
${openConnection()}
${writeData()}
${closeConnection()}
''';
  }

  String openConnection();
  String writeData();
  String closeConnection();
}

class JsonExporter extends DataExporter {
  @override
  String openConnection() {
    return 'Открываем соединение';
  }

  @override
  String writeData() {
    return 'Записываем JSON данные';
  }

  @override
  String closeConnection() {
    return 'Закрываем соединение';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final exporter = JsonExporter();

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 50')),
        body: Center(
          child: Text(exporter.export(), textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 51
Dart
import 'package:flutter/material.dart';

abstract class Validator<T> {
  String validate(T value);
}

class EmailValidator implements Validator<String> {
  @override
  String validate(String value) {
    if (value.contains('@')) {
      return 'Email корректный';
    }

    return 'Email некорректный';
  }
}

class AgeValidator implements Validator<int> {
  @override
  String validate(int value) {
    if (value >= 18) {
      return 'Возраст подходит';
    }

    return 'Возраст меньше 18';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final emailValidator = EmailValidator();
    final ageValidator = AgeValidator();

    final result = '''
${emailValidator.validate('test@mail.com')}
${ageValidator.validate(20)}
''';
[06.05.2026 0:04] Zex: return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 51')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 52
Dart
import 'package:flutter/material.dart';

class Computer {
  String cpu = '';
  String ram = '';

  @override
  String toString() {
    return 'Computer(cpu: $cpu, ram: $ram)';
  }
}

abstract class ComputerBuilder {
  void setCpu();
  void setRam();
  Computer build();
}

class GamingComputerBuilder implements ComputerBuilder {
  final Computer computer = Computer();

  @override
  void setCpu() {
    computer.cpu = 'Intel i9';
  }

  @override
  void setRam() {
    computer.ram = '32 GB';
  }

  @override
  Computer build() {
    return computer;
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final builder = GamingComputerBuilder();

    builder.setCpu();
    builder.setRam();

    final computer = builder.build();

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 52')),
        body: Center(
          child: Text(computer.toString()),
        ),
      ),
    );
  }
}
Задача 53
Dart
import 'dart:convert';
import 'package:flutter/material.dart';

abstract class Serializable {
  Map<String, dynamic> toJson();
}

class User implements Serializable {
  String name;
  int age;

  User(this.name, this.age);

  @override
  Map<String, dynamic> toJson() {
    return {
      'type': 'User',
      'name': name,
      'age': age,
    };
  }
}

class Product implements Serializable {
  String title;
  double price;

  Product(this.title, this.price);

  @override
  Map<String, dynamic> toJson() {
    return {
      'type': 'Product',
      'title': title,
      'price': price,
    };
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final objects = <Serializable>[
      User('Alice', 20),
      Product('Phone', 999),
    ];

    final json = const JsonEncoder.withIndent('  ')
        .convert(objects.map((object) => object.toJson()).toList());

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 53')),
        body: Center(
          child: Text(json, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 54
Dart
import 'package:flutter/material.dart';

abstract class StreamProcessor<T> {
  Stream<T> process(Stream<T> input);
}

class DoubleNumberProcessor implements StreamProcessor<int> {
  @override
  Stream<int> process(Stream<int> input) async* {
    await for (final number in input) {
      yield number * 2;
    }
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final processor = DoubleNumberProcessor();

    final future = processor
        .process(Stream.fromIterable([1, 2, 3, 4]))
        .toList();

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 54')),
        body: Center(
          child: FutureBuilder<List<int>>(
            future: future,
            builder: (context, snapshot) {
              if (!snapshot.hasData) {
                return const Text('Обработка потока...');
              }

              return Text('Результат: ${snapshot.data}');
            },
          ),
        ),
      ),
    );
  }
}
Задача 55
Dart
import 'package:flutter/material.dart';

abstract class FileStorage {
  String write(String fileName, String data);
  String read(String fileName);
}

class JsonFileStorage implements FileStorage {
  final Map<String, String> files = {};
[06.05.2026 0:04] Zex: @override
  String write(String fileName, String data) {
    files[fileName] = '{ "data": "$data" }';
    return 'JSON файл записан';
  }

  @override
  String read(String fileName) {
    return files[fileName] ?? 'Файл не найден';
  }
}

class XmlFileStorage implements FileStorage {
  final Map<String, String> files = {};

  @override
  String write(String fileName, String data) {
    files[fileName] = '<data>$data</data>';
    return 'XML файл записан';
  }

  @override
  String read(String fileName) {
    return files[fileName] ?? 'Файл не найден';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final jsonStorage = JsonFileStorage();
    final xmlStorage = XmlFileStorage();

    jsonStorage.write('user.json', 'Alice');
    xmlStorage.write('user.xml', 'Bob');

    final result = '''
${jsonStorage.read('user.json')}
${xmlStorage.read('user.xml')}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 55')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 56
Dart
import 'package:flutter/material.dart';

abstract class FormValidator {
  String validate(Map<String, String> form);
}

class NameValidator extends FormValidator {
  @override
  String validate(Map<String, String> form) {
    final name = form['name'] ?? '';

    if (name.isEmpty) {
      return 'Имя не заполнено';
    }

    return 'Имя корректное';
  }
}

class EmailFormValidator extends FormValidator {
  @override
  String validate(Map<String, String> form) {
    final email = form['email'] ?? '';

    if (!email.contains('@')) {
      return 'Email некорректный';
    }

    return 'Email корректный';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final form = {
      'name': 'Alice',
      'email': 'alice@mail.com',
    };

    final validators = [
      NameValidator(),
      EmailFormValidator(),
    ];

    final result = validators
        .map((validator) => validator.validate(form))
        .join('\n');

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 56')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 57
Dart
import 'package:flutter/material.dart';

abstract class Logger {
  String log(String message);
}

class ConsoleLogger implements Logger {
  @override
  String log(String message) {
    return 'Console log: $message';
  }
}

class FileLogger implements Logger {
  @override
  String log(String message) {
    return 'File log: $message';
  }
}

class NetworkLogger implements Logger {
  @override
  String log(String message) {
    return 'Network log: $message';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final loggers = [
      ConsoleLogger(),
      FileLogger(),
      NetworkLogger(),
    ];

    final result = loggers
        .map((logger) => logger.log('Hello'))
        .join('\n');

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 57')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 58
Dart
import 'package:flutter/material.dart';

abstract class Cache<K, V> {
  V? get(K key);
  void set(K key, V value);
  void clear();
}

class MemoryCache<K, V> implements Cache<K, V> {
  final Map<K, V> storage = {};

  @override
  V? get(K key) {
    return storage[key];
  }

  @override
  void set(K key, V value) {
    storage[key] = value;
  }

  @override
  void clear() {
    storage.clear();
  }
}
[06.05.2026 0:04] Zex: void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final cache = MemoryCache<String, int>();

    cache.set('age', 25);

    final beforeClear = cache.get('age');

    cache.clear();

    final afterClear = cache.get('age');

    final result = '''
До очистки: $beforeClear
После очистки: $afterClear
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 58')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 59
Dart
import 'package:flutter/material.dart';

abstract class HttpClient {
  String GET(String url);
  String POST(String url, String body);
  String PUT(String url, String body);
  String DELETE(String url);
}

class MockHttpClient implements HttpClient {
  @override
  String GET(String url) {
    return 'GET request to $url';
  }

  @override
  String POST(String url, String body) {
    return 'POST request to $url with body: $body';
  }

  @override
  String PUT(String url, String body) {
    return 'PUT request to $url with body: $body';
  }

  @override
  String DELETE(String url) {
    return 'DELETE request to $url';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final client = MockHttpClient();

    final result = '''
${client.GET('/users')}
${client.POST('/users', 'new user')}
${client.PUT('/users/1', 'updated user')}
${client.DELETE('/users/1')}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 59')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 60
Dart
import 'package:flutter/material.dart';

abstract class Database {
  String connect();
  String insert(String data);
  String read();
}

class SqlDatabase implements Database {
  @override
  String connect() {
    return 'Connected to SQL database';
  }

  @override
  String insert(String data) {
    return 'Inserted into SQL: $data';
  }

  @override
  String read() {
    return 'Reading from SQL database';
  }
}

class NoSqlDatabase implements Database {
  @override
  String connect() {
    return 'Connected to NoSQL database';
  }

  @override
  String insert(String data) {
    return 'Inserted into NoSQL: $data';
  }

  @override
  String read() {
    return 'Reading from NoSQL database';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final databases = [
      SqlDatabase(),
      NoSqlDatabase(),
    ];

    final result = databases
        .map((db) => '''
${db.connect()}
${db.insert('User Alice')}
${db.read()}
''')
        .join('\n');

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 60')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 61
Dart
import 'package:flutter/material.dart';

mixin Cacheable<T> {
  final Map<String, T> _cache = {};

  void cache(String key, T value) {
    _cache[key] = value;
  }

  T? getFromCache(String key) {
    return _cache[key];
  }
}

class UserService with Cacheable<String> {
  String loadUser(String id) {
    final cachedUser = getFromCache(id);

    if (cachedUser != null) {
      return 'Из кэша: $cachedUser';
    }

    final user = 'User with id $id';
    cache(id, user);

    return 'Загружено и сохранено в кэш: $user';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final service = UserService();
[06.05.2026 0:04] Zex: final first = service.loadUser('1');
    final second = service.loadUser('1');

    final result = '''
$first
$second
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 61')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 62
Dart
import 'package:flutter/material.dart';

abstract class Readable<T> {
  T read(String id);
}

abstract class Writable<T> {
  String write(T item);
}

abstract class Deletable {
  String delete(String id);
}

abstract class Repository<T>
    implements Readable<T>, Writable<T>, Deletable {}

class UserRepository implements Repository<String> {
  final Map<String, String> users = {};

  @override
  String write(String item) {
    users['1'] = item;
    return 'Пользователь сохранён: $item';
  }

  @override
  String read(String id) {
    return users[id] ?? 'Пользователь не найден';
  }

  @override
  String delete(String id) {
    users.remove(id);
    return 'Пользователь удалён';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final repository = UserRepository();

    final result = '''
${repository.write('Alice')}
${repository.read('1')}
${repository.delete('1')}
${repository.read('1')}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 62')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
Задача 63
Dart
import 'package:flutter/material.dart';

abstract class StrictBox<T> {
  T get value;
  void setValue(T value);
}

class IntBox extends StrictBox<int> {
  int _value;

  IntBox(this._value);

  @override
  int get value => _value;

  @override
  void setValue(int value) {
    _value = value;
  }
}

class StringBox extends StrictBox<String> {
  String _value;

  StringBox(this._value);

  @override
  String get value => _value;

  @override
  void setValue(String value) {
    _value = value;
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final intBox = IntBox(10);
    final stringBox = StringBox('Hello');

    intBox.setValue(20);
    stringBox.setValue('Dart');

    final result = '''
IntBox хранит только int: ${intBox.value}
StringBox хранит только String: ${stringBox.value}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 63')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: Задача 100: Мегазадача: Фреймворк для управления сущностями
Создайте фреймворк с интерфейсом Entity, Repository<T>, Service<T>, включающий:
Создайте фреймворк с интерфейсом Entity, Repository<T>, import 'package:flutter/material.dart';

abstract class Function1<T, R> {
  R call(T value);
}

class Square implements Function1<int, int> {
  @override
  int call(int value) {
    return value * value;
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final square = Square();

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 64')),
        body: Center(
          child: Text(
            'Square(5) = ${square(5)}',
            style: const TextStyle(fontSize: 24),
          ),
        ),
      ),
    );
  }
}, включающий::
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

class Cache<T extends Comparable<dynamic>> {
  final List<T> items = [];

  void add(T value) {
    items.add(value);
  }

  List<T> sorted() {
    final copy = [...items];
    copy.sort((a, b) => a.compareTo(b));
    return copy;
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final cache = Cache<int>();

    cache.add(5);
    cache.add(1);
    cache.add(9);
    cache.add(3);

    final result = '''
До сортировки: ${cache.items}
После сортировки: ${cache.sorted()}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 65')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

abstract class Shape {
  String info();
}

class Circle implements Shape {
  @override
  String info() {
    return 'Это Circle';
  }
}

class Rectangle implements Shape {
  @override
  String info() {
    return 'Это Rectangle';
  }
}

String reflectObject(Object object) {
  return '''
Тип объекта: ${object.runtimeType}
Строковое представление: $object
''';
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final shape = Circle();

    final result = '''
dart:mirrors не работает во Flutter/DartPad.

Рабочий аналог:
${reflectObject(shape)}

Метод объекта:
${shape.info()}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 66')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

abstract class CanRead {
  String read();
}

abstract class CanWrite {
  String write();
}

abstract class CanDelete {
  String delete();
}

class Guest implements CanRead {
  @override
  String read() {
    return 'Guest может читать';
  }
}

class Editor implements CanRead, CanWrite {
  @override
  String read() {
    return 'Editor может читать';
  }

  @override
  String write() {
    return 'Editor может писать';
  }
}

class Admin implements CanRead, CanWrite, CanDelete {
  @override
  String read() {
    return 'Admin может читать';
  }

  @override
  String write() {
    return 'Admin может писать';
  }

  @override
  String delete() {
    return 'Admin может удалять';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final admin = Admin();

    final result = '''
${admin.read()}
${admin.write()}
${admin.delete()}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 67')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

class Product implements Comparable<Product> {
  String name;
  double price;

  Product(this.name, this.price);

  @override
  int compareTo(Product other) {
    return price.compareTo(other.price);
  }

  @override
  String toString() {
    return '$name: $price';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final products = [
      Product('Phone', 900),
      Product('Book', 20),
      Product('Laptop', 1500),
    ];

    products.sort();

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 68')),
        body: Center(
          child: Text(
            products.join('\n'),
            textAlign: TextAlign.center,
          ),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

abstract class AsyncWorker<T> {
  Future<T> loadFuture();
  Stream<T> loadStream();
}

class NumberWorker implements AsyncWorker<int> {
  @override
  Future<int> loadFuture() async {
    await Future.delayed(const Duration(seconds: 1));
    return 100;
  }

  @override
  Stream<int> loadStream() async* {
    yield 1;
    yield 2;
    yield 3;
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final worker = NumberWorker();

    final futureResult = worker.loadFuture();
    final streamResult = worker.loadStream().toList();

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 69')),
        body: Center(
          child: FutureBuilder(
            future: Future.wait([futureResult, streamResult]),
            builder: (context, snapshot) {
              if (!snapshot.hasData) {
                return const Text('Загрузка...');
              }

              final data = snapshot.data!;

              return Text(
                '''
Future результат: ${data[0]}
Stream результат: ${data[1]}
''',
                textAlign: TextAlign.center,
              );
            },
          ),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

abstract class Plugin {
  String get name;
  String run();
}

class AuthPlugin implements Plugin {
  @override
  String get name => 'Auth Plugin';

  @override
  String run() {
    return '$name запущен';
  }
}

class PaymentPlugin implements Plugin {
  @override
  String get name => 'Payment Plugin';

  @override
  String run() {
    return '$name запущен';
  }
}

class PluginManager {
  final List<Plugin> plugins = [];

  void register(Plugin plugin) {
    plugins.add(plugin);
  }

  String runAll() {
    return plugins.map((plugin) => plugin.run()).join('\n');
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final manager = PluginManager();

    manager.register(AuthPlugin());
    manager.register(PaymentPlugin());

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 70')),
        body: Center(
          child: Text(manager.runAll(), textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

abstract class Converter<From, To> {
  To convert(From value);
}

class StringToIntConverter implements Converter<String, int> {
  @override
  int convert(String value) {
    return int.parse(value);
  }
}

class IntToStringConverter implements Converter<int, String> {
  @override
  String convert(int value) {
    return 'Number: $value';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final stringToInt = StringToIntConverter();
    final intToString = IntToStringConverter();

    final result = '''
String в int: ${stringToInt.convert('123')}
int в String: ${intToString.convert(456)}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 71')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

abstract class Report {
  String generate(String data);
}

class PdfReport implements Report {
  @override
  String generate(String data) {
    return 'PDF отчет: $data';
  }
}

class ExcelReport implements Report {
  @override
  String generate(String data) {
    return 'Excel отчет: $data';
  }
}

class CsvReport implements Report {
  @override
  String generate(String data) {
    return 'CSV отчет: $data';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final reports = [
      PdfReport(),
      ExcelReport(),
      CsvReport(),
    ];

    final result = reports
        .map((report) => report.generate('Продажи за месяц'))
        .join('\n');

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 72')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

abstract class StateMachine {
  String get currentState;
  String next();
  String previous();
}

class OrderStateMachine extends StateMachine {
  int index = 0;

  final List<String> states = [
    'Создан',
    'Оплачен',
    'Отправлен',
    'Доставлен',
  ];

  @override
  String get currentState => states[index];

  @override
  String next() {
    if (index < states.length - 1) {
      index++;
    }
    return currentState;
  }

  @override
  String previous() {
    if (index > 0) {
      index--;
    }
    return currentState;
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final machine = OrderStateMachine();

    final result = '''
Начальное состояние: ${machine.currentState}
После next: ${machine.next()}
После next: ${machine.next()}
После previous: ${machine.previous()}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 73')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

abstract class Optimizer<T> {
  T optimize(T data);
}

class TextOptimizer implements Optimizer<String> {
  @override
  String optimize(String data) {
    return data.trim().replaceAll('  ', ' ');
  }
}

class NumberListOptimizer implements Optimizer<List<int>> {
  @override
  List<int> optimize(List<int> data) {
    final result = data.toSet().toList();
    result.sort();
    return result;
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final textOptimizer = TextOptimizer();
    final numberOptimizer = NumberListOptimizer();

    final result = '''
Текст: "${textOptimizer.optimize('  Hello  Dart  ')}"
Числа: ${numberOptimizer.optimize([3, 1, 2, 3, 1])}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 74')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

abstract class Resource {
  String use();
  String dispose();
}

class FileResource implements Resource {
  @override
  String use() {
    return 'Файл используется';
  }

  @override
  String dispose() {
    return 'Файл закрыт';
  }
}

class NetworkResource implements Resource {
  @override
  String use() {
    return 'Сеть используется';
  }

  @override
  String dispose() {
    return 'Сетевое соединение закрыто';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final resources = [
      FileResource(),
      NetworkResource(),
    ];

    final result = resources
        .map((resource) => '${resource.use()}\n${resource.dispose()}')
        .join('\n\n');

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 75')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

abstract class PaymentGateway {
  String payByCard(double amount);
  String payByWallet(double amount);
}

class StripeGateway implements PaymentGateway {
  @override
  String payByCard(double amount) {
    return 'Stripe: оплата картой $amount';
  }

  @override
  String payByWallet(double amount) {
    return 'Stripe: оплата кошельком $amount';
  }
}

class PayPalGateway implements PaymentGateway {
  @override
  String payByCard(double amount) {
    return 'PayPal: оплата картой $amount';
  }

  @override
  String payByWallet(double amount) {
    return 'PayPal: оплата кошельком $amount';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final gateways = [
      StripeGateway(),
      PayPalGateway(),
    ];

    final result = gateways
        .map((gateway) => gateway.payByCard(100))
        .join('\n');

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 76')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

abstract class ApiClient {
  String get(String url);
  String post(String url, String body);
  String put(String url, String body);
  String delete(String url);
}

class RestApiClient implements ApiClient {
  @override
  String get(String url) => 'GET $url';

  @override
  String post(String url, String body) => 'POST $url, body: $body';

  @override
  String put(String url, String body) => 'PUT $url, body: $body';

  @override
  String delete(String url) => 'DELETE $url';
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final api = RestApiClient();

    final result = '''
${api.get('/users')}
${api.post('/users', 'Alice')}
${api.put('/users/1', 'Bob')}
${api.delete('/users/1')}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 77')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

class CacheItem<V> {
  V value;
  DateTime expiresAt;

  CacheItem(this.value, this.expiresAt);
}

abstract class TtlCache<K, V> {
  void set(K key, V value, Duration ttl);
  V? get(K key);
}

class MemoryTtlCache<K, V> implements TtlCache<K, V> {
  final Map<K, CacheItem<V>> storage = {};

  @override
  void set(K key, V value, Duration ttl) {
    storage[key] = CacheItem(value, DateTime.now().add(ttl));
  }

  @override
  V? get(K key) {
    final item = storage[key];

    if (item == null) {
      return null;
    }

    if (DateTime.now().isAfter(item.expiresAt)) {
      storage.remove(key);
      return null;
    }

    return item.value;
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final cache = MemoryTtlCache<String, String>();

    cache.set('token', 'ABC123', const Duration(seconds: 10));

    final result = '''
Кэш с TTL:
token = ${cache.get('token')}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 78')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

abstract class BusinessRule<T> {
  String check(T value);
}

class MinimumAgeRule implements BusinessRule<int> {
  @override
  String check(int value) {
    if (value >= 18) {
      return 'Возраст подходит';
    }

    return 'Возраст меньше 18';
  }
}

class PositiveBalanceRule implements BusinessRule<double> {
  @override
  String check(double value) {
    if (value >= 0) {
      return 'Баланс положительный';
    }

    return 'Баланс отрицательный';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final ageRule = MinimumAgeRule();
    final balanceRule = PositiveBalanceRule();

    final result = '''
${ageRule.check(20)}
${balanceRule.check(150.5)}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 79')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

abstract class AuditLog {
  String record(String action);
}

class ConsoleAuditLog implements AuditLog {
  @override
  String record(String action) {
    return 'Console audit: $action';
  }
}

class DatabaseAuditLog implements AuditLog {
  @override
  String record(String action) {
    return 'Database audit: $action';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final logs = [
      ConsoleAuditLog(),
      DatabaseAuditLog(),
    ];

    final result = logs
        .map((log) => log.record('User logged in'))
        .join('\n');

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 80')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

abstract class Config {
  String getValue(String key);
}

class FileConfig implements Config {
  final Map<String, String> data = {
    'theme': 'dark',
    'lang': 'ru',
  };

  @override
  String getValue(String key) {
    return data[key] ?? 'not found';
  }
}

class EnvConfig implements Config {
  final Map<String, String> data = {
    'apiUrl': 'https://example.com',
  };

  @override
  String getValue(String key) {
    return data[key] ?? 'not found';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final configs = [
      FileConfig(),
      EnvConfig(),
    ];

    final result = '''
FileConfig theme: ${configs[0].getValue('theme')}
EnvConfig apiUrl: ${configs[1].getValue('apiUrl')}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 81')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

abstract class Migration {
  String up();
  String down();
}

class CreateUsersTableMigration implements Migration {
  @override
  String up() {
    return 'Создана таблица users';
  }

  @override
  String down() {
    return 'Удалена таблица users';
  }
}

class AddEmailColumnMigration implements Migration {
  @override
  String up() {
    return 'Добавлена колонка email';
  }

  @override
  String down() {
    return 'Удалена колонка email';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final migrations = [
      CreateUsersTableMigration(),
      AddEmailColumnMigration(),
    ];

    final result = migrations
        .map((migration) => '${migration.up()}\n${migration.down()}')
        .join('\n\n');

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 82')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

class Request {
  String path;

  Request(this.path);
}

abstract class Middleware {
  String handle(Request request);
}

class AuthMiddleware implements Middleware {
  @override
  String handle(Request request) {
    return 'Auth проверен для ${request.path}';
  }
}

class LoggingMiddleware implements Middleware {
  @override
  String handle(Request request) {
    return 'Запрос записан в лог: ${request.path}';
  }
}

class MiddlewarePipeline {
  final List<Middleware> middlewares = [];

  void add(Middleware middleware) {
    middlewares.add(middleware);
  }

  String execute(Request request) {
    return middlewares
        .map((middleware) => middleware.handle(request))
        .join('\n');
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final pipeline = MiddlewarePipeline();

    pipeline.add(AuthMiddleware());
    pipeline.add(LoggingMiddleware());

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 83')),
        body: Center(
          child: Text(
            pipeline.execute(Request('/profile')),
            textAlign: TextAlign.center,
          ),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart' hide Notification;

abstract class Notification {
  String send(String message);
}

class EmailNotification implements Notification {
  @override
  String send(String message) {
    return 'Email отправлен: $message';
  }
}

class SmsNotification implements Notification {
  @override
  String send(String message) {
    return 'SMS отправлен: $message';
  }
}

class PushNotification implements Notification {
  @override
  String send(String message) {
    return 'Push отправлен: $message';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final notifications = [
      EmailNotification(),
      SmsNotification(),
      PushNotification(),
    ];

    final result = notifications
        .map((notification) => notification.send('Hello!'))
        .join('\n');

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 84')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

abstract class Job {
  Future<String> execute();
}

class EmailJob implements Job {
  @override
  Future<String> execute() async {
    await Future.delayed(const Duration(milliseconds: 500));
    return 'Email job выполнен';
  }
}

class ReportJob implements Job {
  @override
  Future<String> execute() async {
    await Future.delayed(const Duration(milliseconds: 500));
    return 'Report job выполнен';
  }
}

class JobQueue {
  final List<Job> jobs = [];

  void add(Job job) {
    jobs.add(job);
  }

  Future<String> process() async {
    final results = <String>[];

    for (final job in jobs) {
      results.add(await job.execute());
    }

    return results.join('\n');
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final queue = JobQueue();

    queue.add(EmailJob());
    queue.add(ReportJob());

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 85')),
        body: Center(
          child: FutureBuilder<String>(
            future: queue.process(),
            builder: (context, snapshot) {
              if (!snapshot.hasData) {
                return const Text('Очередь выполняется...');
              }

              return Text(snapshot.data!, textAlign: TextAlign.center);
            },
          ),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

abstract class PasswordHasher {
  String hash(String password);
}

class SimpleHasher implements PasswordHasher {
  @override
  String hash(String password) {
    return password.codeUnits.fold(0, (sum, code) => sum + code).toString();
  }
}

class ReverseHasher implements PasswordHasher {
  @override
  String hash(String password) {
    return password.split('').reversed.join();
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final hashers = [
      SimpleHasher(),
      ReverseHasher(),
    ];

    final result = hashers
        .map((hasher) => hasher.hash('password'))
        .join('\n');

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 86')),
        body: Center(
          child: Text(
            'Учебные хеши:\n$result',
            textAlign: TextAlign.center,
          ),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

class Permission {
  String name;

  Permission(this.name);
}

class User {
  String name;
  List<Permission> permissions;

  User(this.name, this.permissions);
}

abstract class PermissionChecker {
  bool hasPermission(User user, String permission);
}

class SimplePermissionChecker implements PermissionChecker {
  @override
  bool hasPermission(User user, String permission) {
    return user.permissions.any((p) => p.name == permission);
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final user = User('Alice', [
      Permission('read'),
      Permission('write'),
    ]);

    final checker = SimplePermissionChecker();

    final result = '''
Can read: ${checker.hasPermission(user, 'read')}
Can delete: ${checker.hasPermission(user, 'delete')}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 87')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

abstract class SearchEngine<T> {
  List<T> search(List<T> items, String query);
}

class NameSearchEngine implements SearchEngine<String> {
  @override
  List<String> search(List<String> items, String query) {
    return items.where((item) => item.contains(query)).toList();
  }
}

class StartsWithSearchEngine implements SearchEngine<String> {
  @override
  List<String> search(List<String> items, String query) {
    return items.where((item) => item.startsWith(query)).toList();
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final items = ['Alice', 'Bob', 'Alex', 'Maria'];

    final containsSearch = NameSearchEngine();
    final startsWithSearch = StartsWithSearchEngine();

    final result = '''
Contains "A": ${containsSearch.search(items, 'A')}
Starts with "A": ${startsWithSearch.search(items, 'A')}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 88')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

abstract class Filter<T> {
  bool apply(T item);
}

class EvenFilter implements Filter<int> {
  @override
  bool apply(int item) {
    return item % 2 == 0;
  }
}

class GreaterThanFilter implements Filter<int> {
  int min;

  GreaterThanFilter(this.min);

  @override
  bool apply(int item) {
    return item > min;
  }
}

class AndFilter<T> implements Filter<T> {
  Filter<T> first;
  Filter<T> second;

  AndFilter(this.first, this.second);

  @override
  bool apply(T item) {
    return first.apply(item) && second.apply(item);
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final numbers = [1, 2, 3, 4, 5, 6, 7, 8];

    final filter = AndFilter<int>(
      EvenFilter(),
      GreaterThanFilter(4),
    );

    final result = numbers.where(filter.apply).toList();

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 89')),
        body: Center(
          child: Text(
            'Результат фильтрации: $result',
            textAlign: TextAlign.center,
          ),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart' hide Container;

abstract class Container {
  void register<T>(T instance);
  T resolve<T>();
}

class DIContainer implements Container {
  final Map<Type, Object> services = {};

  @override
  void register<T>(T instance) {
    services[T] = instance as Object;
  }

  @override
  T resolve<T>() {
    return services[T] as T;
  }
}

class UserService {
  String getUser() {
    return 'User Alice';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final container = DIContainer();

    container.register<UserService>(UserService());

    final service = container.resolve<UserService>();

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 90')),
        body: Center(
          child: Text(service.getUser()),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

abstract class ErrorHandler {
  String logError(Object error);
  String recover();
}

class NetworkErrorHandler implements ErrorHandler {
  @override
  String logError(Object error) {
    return 'Логируем сетевую ошибку: $error';
  }

  @override
  String recover() {
    return 'Повторяем запрос';
  }
}

class DatabaseErrorHandler implements ErrorHandler {
  @override
  String logError(Object error) {
    return 'Логируем ошибку БД: $error';
  }

  @override
  String recover() {
    return 'Открываем резервную БД';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final handlers = [
      NetworkErrorHandler(),
      DatabaseErrorHandler(),
    ];

    final result = handlers
        .map((handler) => '${handler.logError('Ошибка')}\n${handler.recover()}')
        .join('\n\n');

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 91')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

abstract class Metrics {
  void record(String name, double value);
  double average(String name);
}

class AppMetrics implements Metrics {
  final Map<String, List<double>> data = {};

  @override
  void record(String name, double value) {
    data.putIfAbsent(name, () => []);
    data[name]!.add(value);
  }

  @override
  double average(String name) {
    final values = data[name] ?? [];

    if (values.isEmpty) {
      return 0;
    }

    return values.reduce((a, b) => a + b) / values.length;
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final metrics = AppMetrics();

    metrics.record('loadTime', 100);
    metrics.record('loadTime', 200);
    metrics.record('loadTime', 300);

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 92')),
        body: Center(
          child: Text(
            'Среднее loadTime: ${metrics.average('loadTime')}',
          ),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'dart:collection';
import 'package:flutter/material.dart';

abstract class Cache<K, V> {
  void set(K key, V value);
  V? get(K key);
  String info();
}

class FifoCache<K, V> implements Cache<K, V> {
  final int capacity;
  final LinkedHashMap<K, V> storage = LinkedHashMap();

  FifoCache(this.capacity);

  @override
  void set(K key, V value) {
    if (storage.length >= capacity) {
      storage.remove(storage.keys.first);
    }
    storage[key] = value;
  }

  @override
  V? get(K key) => storage[key];

  @override
  String info() => 'FIFO: $storage';
}

class LruCache<K, V> implements Cache<K, V> {
  final int capacity;
  final LinkedHashMap<K, V> storage = LinkedHashMap();

  LruCache(this.capacity);

  @override
  void set(K key, V value) {
    if (storage.containsKey(key)) {
      storage.remove(key);
    }

    if (storage.length >= capacity) {
      storage.remove(storage.keys.first);
    }

    storage[key] = value;
  }

  @override
  V? get(K key) {
    final value = storage.remove(key);

    if (value != null) {
      storage[key] = value;
    }

    return value;
  }

  @override
  String info() => 'LRU: $storage';
}

class LfuCache<K, V> implements Cache<K, V> {
  final int capacity;
  final Map<K, V> storage = {};
  final Map<K, int> frequency = {};

  LfuCache(this.capacity);

  @override
  void set(K key, V value) {
    if (storage.length >= capacity && !storage.containsKey(key)) {
      final leastUsedKey = frequency.entries
          .reduce((a, b) => a.value <= b.value ? a : b)
          .key;

      storage.remove(leastUsedKey);
      frequency.remove(leastUsedKey);
    }

    storage[key] = value;
    frequency[key] = 0;
  }

  @override
  V? get(K key) {
    if (storage.containsKey(key)) {
      frequency[key] = frequency[key]! + 1;
    }

    return storage[key];
  }

  @override
  String info() => 'LFU: $storage, частота: $frequency';
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final fifo = FifoCache<String, int>(2);
    fifo.set('a', 1);
    fifo.set('b', 2);
    fifo.set('c', 3);

    final lru = LruCache<String, int>(2);
    lru.set('a', 1);
    lru.set('b', 2);
    lru.get('a');
    lru.set('c', 3);

    final lfu = LfuCache<String, int>(2);
    lfu.set('a', 1);
    lfu.set('b', 2);
    lfu.get('a');
    lfu.set('c', 3);

    final result = '''
${fifo.info()}

${lru.info()}

${lfu.info()}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 93')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

class SimpleImage {
  String name;

  SimpleImage(this.name);
}

abstract class ImageProcessor {
  SimpleImage applyFilter(SimpleImage image);
  SimpleImage transform(SimpleImage image);
}

class BlackWhiteProcessor implements ImageProcessor {
  @override
  SimpleImage applyFilter(SimpleImage image) {
    return SimpleImage('${image.name} + black-white filter');
  }

  @override
  SimpleImage transform(SimpleImage image) {
    return SimpleImage('${image.name} + resized');
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final processor = BlackWhiteProcessor();

    final image = SimpleImage('photo.png');

    final filtered = processor.applyFilter(image);
    final transformed = processor.transform(filtered);

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 94')),
        body: Center(
          child: Text(
            'Результат: ${transformed.name}',
            textAlign: TextAlign.center,
          ),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

abstract class Graph<T> {
  void addVertex(T vertex);
  void addEdge(T from, T to);
  List<T> neighbors(T vertex);
}

class AdjacencyListGraph<T> implements Graph<T> {
  final Map<T, List<T>> adjacencyList = {};

  @override
  void addVertex(T vertex) {
    adjacencyList.putIfAbsent(vertex, () => []);
  }

  @override
  void addEdge(T from, T to) {
    addVertex(from);
    addVertex(to);
    adjacencyList[from]!.add(to);
  }

  @override
  List<T> neighbors(T vertex) {
    return adjacencyList[vertex] ?? [];
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final graph = AdjacencyListGraph<String>();

    graph.addEdge('A', 'B');
    graph.addEdge('A', 'C');
    graph.addEdge('B', 'D');

    final result = '''
Соседи A: ${graph.neighbors('A')}
Соседи B: ${graph.neighbors('B')}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 95')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

abstract class ValidationRule<T> {
  String? validate(T value);
}

class NotEmptyRule implements ValidationRule<String> {
  @override
  String? validate(String value) {
    if (value.isEmpty) {
      return 'Поле не должно быть пустым';
    }

    return null;
  }
}

class MinLengthRule implements ValidationRule<String> {
  int min;

  MinLengthRule(this.min);

  @override
  String? validate(String value) {
    if (value.length < min) {
      return 'Минимальная длина: $min';
    }

    return null;
  }
}

class RuleValidator<T> {
  final List<ValidationRule<T>> rules;

  RuleValidator(this.rules);

  List<String> validate(T value) {
    return rules
        .map((rule) => rule.validate(value))
        .whereType<String>()
        .toList();
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final validator = RuleValidator<String>([
      NotEmptyRule(),
      MinLengthRule(5),
    ]);

    final errors = validator.validate('abc');

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 96')),
        body: Center(
          child: Text(
            errors.join('\n'),
            textAlign: TextAlign.center,
          ),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

abstract class Period {
  DateTime get start;
  DateTime get end;
  int get lengthInDays;
}

class DayPeriod implements Period {
  @override
  final DateTime start;

  DayPeriod(this.start);

  @override
  DateTime get end => start.add(const Duration(days: 1));

  @override
  int get lengthInDays => 1;
}

class WeekPeriod implements Period {
  @override
  final DateTime start;

  WeekPeriod(this.start);

  @override
  DateTime get end => start.add(const Duration(days: 7));

  @override
  int get lengthInDays => 7;
}

class MonthPeriod implements Period {
  @override
  final DateTime start;

  MonthPeriod(this.start);

  @override
  DateTime get end => DateTime(start.year, start.month + 1, start.day);

  @override
  int get lengthInDays => end.difference(start).inDays;
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final periods = [
      DayPeriod(DateTime(2026, 5, 5)),
      WeekPeriod(DateTime(2026, 5, 5)),
      MonthPeriod(DateTime(2026, 5, 5)),
    ];

    final result = periods
        .map((period) => '${period.runtimeType}: ${period.lengthInDays} дней')
        .join('\n');

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 97')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

abstract class AsyncOperation<T> {
  Future<T?> execute();
  void cancel();
}

class DownloadOperation implements AsyncOperation<String> {
  bool _isCanceled = false;

  @override
  Future<String?> execute() async {
    await Future.delayed(const Duration(seconds: 1));

    if (_isCanceled) {
      return 'Операция отменена';
    }

    return 'Файл загружен';
  }

  @override
  void cancel() {
    _isCanceled = true;
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final operation = DownloadOperation();

    operation.cancel();

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 98')),
        body: Center(
          child: FutureBuilder<String?>(
            future: operation.execute(),
            builder: (context, snapshot) {
              if (!snapshot.hasData) {
                return const Text('Выполнение...');
              }

              return Text(snapshot.data!);
            },
          ),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'dart:convert' as convert;
import 'package:flutter/material.dart';

abstract class Codec<T> {
  String encode(T value);
  T decode(String value);
}

class JsonMapCodec implements Codec<Map<String, dynamic>> {
  @override
  String encode(Map<String, dynamic> value) {
    return convert.jsonEncode(value);
  }

  @override
  Map<String, dynamic> decode(String value) {
    return convert.jsonDecode(value);
  }
}

class Base64TextCodec implements Codec<String> {
  @override
  String encode(String value) {
    return convert.base64Encode(convert.utf8.encode(value));
  }

  @override
  String decode(String value) {
    return convert.utf8.decode(convert.base64Decode(value));
  }
}

class CaesarCipherCodec implements Codec<String> {
  @override
  String encode(String value) {
    return value.codeUnits.map((code) => String.fromCharCode(code + 1)).join();
  }

  @override
  String decode(String value) {
    return value.codeUnits.map((code) => String.fromCharCode(code - 1)).join();
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final jsonCodec = JsonMapCodec();
    final base64Codec = Base64TextCodec();
    final cipherCodec = CaesarCipherCodec();

    final json = jsonCodec.encode({'name': 'Alice'});
    final base64 = base64Codec.encode('Hello');
    final cipher = cipherCodec.encode('Secret');

    final result = '''
JSON: $json
Base64: $base64
Шифр: $cipher

Base64 decode: ${base64Codec.decode(base64)}
Шифр decode: ${cipherCodec.decode(cipher)}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 99')),
        body: Center(
          child: Text(result, textAlign: TextAlign.center),
        ),
      ),
    );
  }
}
[06.05.2026 0:04] Zex: import 'package:flutter/material.dart';

abstract class Entity {
  int get id;
}

class User implements Entity {
  @override
  int id;

  String name;

  User(this.id, this.name);

  @override
  String toString() {
    return 'User(id: $id, name: $name)';
  }
}

abstract class Repository<T extends Entity> {
  void create(T entity);
  T? findById(int id);
  List<T> findAll();
  void update(T entity);
  void delete(int id);
}

class MemoryRepository<T extends Entity> implements Repository<T> {
  final Map<int, T> storage = {};

  @override
  void create(T entity) {
    storage[entity.id] = entity;
  }

  @override
  T? findById(int id) {
    return storage[id];
  }

  @override
  List<T> findAll() {
    return storage.values.toList();
  }

  @override
  void update(T entity) {
    storage[entity.id] = entity;
  }

  @override
  void delete(int id) {
    storage.remove(id);
  }
}

abstract class Service<T extends Entity> {
  String create(T entity);
  String getById(int id);
  String getAll();
  String update(T entity);
  String delete(int id);
}

class UserService implements Service<User> {
  final Repository<User> repository;

  UserService(this.repository);

  @override
  String create(User entity) {
    repository.create(entity);
    return 'Создан: $entity';
  }

  @override
  String getById(int id) {
    return repository.findById(id)?.toString() ?? 'Не найден';
  }

  @override
  String getAll() {
    return repository.findAll().join('\n');
  }

  @override
  String update(User entity) {
    repository.update(entity);
    return 'Обновлен: $entity';
  }

  @override
  String delete(int id) {
    repository.delete(id);
    return 'Удалён id: $id';
  }
}

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final repository = MemoryRepository<User>();
    final service = UserService(repository);

    final result = '''
${service.create(User(1, 'Alice'))}
${service.create(User(2, 'Bob'))}

Все пользователи:
${service.getAll()}

Поиск id 1:
${service.getById(1)}

${service.update(User(1, 'Alice Updated'))}

После обновления:
${service.getAll()}

${service.delete(2)}

После удаления:
${service.getAll()}
''';

    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(title: const Text('Задача 100')),
        body: SingleChildScrollView(
          child: Padding(
            padding: const EdgeInsets.all(16),
            child: Center(
              child: Text(
                result,
                textAlign: TextAlign.center,
              ),
            ),
          ),
        ),
      ),
    );
```
  }
}
