# Лабораторная работа #1
:shipit: ***Вариант №1006:***
</br>Разработать спецификацию в формате OpenAPI для набора веб-сервисов, реализующего следующую функциональность:
</br></br>**Первый веб-сервис** должен осуществлять управление коллекцией объектов. В коллекции необходимо хранить объекты класса Product, описание которого приведено ниже:</br>
```
public class Product {
    private Integer id; //Поле не может быть null, Значение поля должно быть больше 0, Значение этого поля должно быть уникальным, Значение этого поля должно генерироваться автоматически
    private String name; //Поле не может быть null, Строка не может быть пустой
    private Coordinates coordinates; //Поле не может быть null
    private java.time.ZonedDateTime creationDate; //Поле не может быть null, Значение этого поля должно генерироваться автоматически
    private Long price; //Поле не может быть null, Значение поля должно быть больше 0
    private String partNumber; //Поле может быть null
    private Integer manufactureCost; //Поле не может быть null
    private UnitOfMeasure unitOfMeasure; //Поле может быть null
    private Person owner; //Поле не может быть null
}

public class Coordinates {
    private float x; //Максимальное значение поля: 791
    private Float y; //Поле не может быть null
}
public class Person {
    private String name; //Поле не может быть null, Строка не может быть пустой
    private String passportID; //Длина строки не должна быть больше 40, Поле не может быть null
    private Color eyeColor; //Поле не может быть null
    private Color hairColor; //Поле может быть null
    private Country nationality; //Поле может быть null
    private Location location; //Поле может быть null
}
public class Location {
    private int x;
    private Double y; //Поле не может быть null
    private double z;
}
public enum UnitOfMeasure {
    KILOGRAMS,
    METERS,
    CENTIMETERS,
    SQUARE_METERS,
    MILLILITERS;
}
public enum Color {
    BLACK,
    BLUE,
    ORANGE,
    BROWN;
}
public enum Country {
    RUSSIA,
    SPAIN,
    NORTH_KOREA,
    JAPAN;
}
```

</br>Веб-сервис должен удовлетворять следующим требованиям:
- API, реализуемый сервисом, должен соответствовать рекомендациям подхода RESTful.
- Необходимо реализовать следующий базовый набор операций с объектами коллекции: добавление нового элемента, получение элемента по ИД, обновление элемента, удаление элемента, получение массива элементов.
- Операция, выполняемая над объектом коллекции, должна определяться методом HTTP-запроса.
- Операция получения массива элементов должна поддерживать возможность сортировки и фильтрации по любой комбинации полей класса, а также возможность постраничного вывода результатов выборки с указанием размера и порядкового номера выводимой страницы.
- Все параметры, необходимые для выполнения операции, должны передаваться в URL запроса.
- Информация об объектах коллекции должна передаваться в формате json.
- В случае передачи сервису данных, нарушающих заданные на уровне класса ограничения целостности, сервис должен возвращать код ответа http, соответствующий произошедшей ошибке.

Помимо базового набора, веб-сервис должен поддерживать следующие операции над объектами коллекции:
- Вернуть количество объектов, значение поля owner которых больше заданного.
- Вернуть массив объектов, значение поля name которых содержит заданную подстроку.
- Вернуть массив уникальных значений поля owner по всем объектам.

Эти операции должны размещаться на отдельных URL.</br>
</br>**Второй веб-сервис** должен располагаться на URL $\color{red} /ebay$, и реализовывать ряд дополнительных операций, связанных с вызовом API первого сервиса:
- $\color{red} /filter/manufacturer/{manufacturer-id}$ : выбрать всю продукцию заданного производителя
- $\color{red} /price/decrease/{decrease-percent}$ : снизить цену всей продукции на указанный процент

Эти операции также должны размещаться на отдельных URL.</br>
Для разработанной спецификации необходимо сгенерировать интерактивную веб-документацию с помощью Swagger UI. Документация должна содержать описание всех REST API обоих сервисов с текстовым описанием функциональности каждой операции. Созданную веб-документацию необходимо развернуть на сервере helios.
</br>
### :smiley_cat: Готовая спецификация - [Не нажимать](https://se.ifmo.ru/~s282606/SOA/Lab1/)

### Вопросы к защите лабораторной работы:
1. Подходы к проектированию приложений. "Монолитная" и сервис-ориентированная архитектура.
2. Понятие сервиса. Общие свойства сервисов.
3. Основные принципы SOA. Подходы к реализации SOA, стандарты и протоколы.
4. Общие принципы построения и элементы сервис-ориентированных систем.
5. Понятие веб-сервиса. Определение, особенности, отличия от веб-приложений.
6. Категоризация веб-сервисов. RESTful и SOAP. Сходства и отличия, области применения.
7. RESTful веб-сервисы. Особенности подхода. Понятия ресурса, URI и полезной нагрузки (payload).
8. Виды RESTful-сервисов. Интерпретация методов HTTP в RESTful.
9. Правила именования ресурсов в RESTful сервисах.
10. Спецификация RESTful-сервисов. Стандарт OpenAPI.
11. Автодокументирование RESTful-сервисов. Swagger Editor, Swagger UI (и Swagger Codegen).
12. Архитектурный принцип HATEOAS.
