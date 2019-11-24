Java - wprowadzenie do programowania obiektowego - klasy i obiekty
---

### struktura klasy:

```java
public class Person {
    
    private String name;                            // pole klasy
    private String surname;                         // pole klasy

    public Person(String name, String surname) {    // konstruktor
        this.name = name;
        this.surname = surname;
    }

    public String getName() {                       // metoda
        return name;
    }

    public void setName(String name) {              // metoda
        this.name = name;
    }   

}
```

---
### Konstruktory

**Nazewnictwo**:

Nazwa klasy musi być taka sama (wielkość liter ma znaczenie) jak nazwa pliku `*.java`. Nazwa klasy powinna być połączenie rzeczownika i opcjonalnie
opisującego go przymiotnika - np. `Person`, `LuxuryCar`, itd.

**Konstruktor bezargumentowy**

```java
public class Person {

    private String name;
    private String surname;

    public Person() {
        this.name = "";
        this.surname = "";
    }
}
```

**Konstruktor domyślny**:

W przypadku, gdy w ciele klasy nie jest zdefiniowany żaden konstruktor, to automatycznie
jest dostępny konstruktor domyślny, którym jest konstruktor bezargumentowy, który nie posiada
żadnej implementacji w ciele konstruktora - ma on za zadanie jedynie powołać nowy obiekt do życia.


**Przeciązanie konstruktorów:**

W obrębie jednej klasy jest mozliwe definiowane wielu konstruktorów, jednakże muszą się one różnić liczbą 
lub typem argumentów. Tak, aby było możliwe jednoznaczne określenie, który konstruktor jest używany na podstawie
przekazanych do niego argumentów.

```java
public class Person {

    private String name;
    private String surname;

    public Person() {
        this.name = "";
        this.surname = "";
    }

    public Person(String name) {
            this.name = name;
            this.surname = "";
    }

    public Person(String name, String surname) {
            this.name = name;
            this.surname = surname;
    }
}
```

**Parametry jawne i niejawne:**

W przypadku konstruktora (analogicznie również w przypadku metod) parametrem jawnym sa argumenty podawane
"w nawiasach", a parametrem niejawnym jest obiekt, na którym wykonujemy dane działanie. Aby odwołać się do parametru
niejawnego, należy użyć słowa kluczowego **this**.

```java
public class Person {

    private String name;                                // na to wskazuje w konstruktorze this.name
    private String surname;                             // na to wskazuje w konstruktorze this.surname

    public Person(String name, String surname) {        // parametry jawne: name i surname
            this.name = name;                           // parametr niejawny: sam obiekt, który został stworzony przy użyciu konstruktora
            this.surname = surname;
    }
}
```


---
### Pola klasy

**nazewnictwo:**

Pola klasy powinno się nazywać zgodnie z ich przeznaczeniem, tzn. pole przechowujące imię powinno się nazywać `name`,
a nie np. `n`, `abc`, itd. - tak aby w późniejszym czasie nie tracić czasu na doszukiwanie się przeznaczenia poszczególnych pól w klasie.

**inicjacja pól**

Sposób 1: konstruktor
```java
public class Person {

    private String name;                                
    private String surname;                             

    public Person(String name, String surname) {    // tutaj inicjalizacja pól  
            this.name = name;                          
            this.surname = surname;
    }
}
```

Sposób 2: wartość domyślna przypisana za pomoca operatora **=**
```java
public class Person {

    private String name = "";                                
    private String surname = "";                           

    public Person() {}                              // pola name i surname mają przypisane pusty łańcuch

    public Person(String name, String surname) {    // pola name i surname mają przypisane wartości  
            this.name = name;                       // z parametrów jawnych   
            this.surname = surname;
    }
}
```

Sposób 3: blok inicjalizacyjny
```java
public class Person {

    private String name;                               
    private String surname;                         

    {
        name = "";
        surname = "";
    }
    
    public Person() {}                              // pola name i surname mają przypisane pusty łańcuch

    public Person(String name, String surname) {    // pola name i surname mają przypisane wartości  
            this.name = name;                       // z parametrów jawnych   
            this.surname = surname;
    }
}
```


---
### Modyfikatory dostępu: