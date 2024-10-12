# Clean Code für Java-Entwickler: Übungen

Hier sind drei einfache und spaßige Übungen zum Thema **Clean Code für Java-Entwickler**, die speziell für Anfänger geeignet sind und in einem unterhaltsamen Kontext stehen:

---

## Übung 1: Der sprechende Roboter
### Kontext:
Du bist ein Entwickler in einem Team, das Roboter programmiert. Dein Roboter soll verschiedene Befehle wie "Gehen", "Sprechen" und "Licht anschalten" ausführen. Leider gibt es einige Überraschungen im Verhalten des Roboters, die du beheben sollst.

### Aufgabe:
- Du hast eine Klasse `Robot`, aber manchmal führt der Roboter unvorhergesehene Aktionen aus. Refaktoriere den Code, damit er vorhersehbar und "überraschungsfrei" funktioniert.

### Ausgangscode:
```java
class Robot {
    public void walk() {
        System.out.println("Walking...");
    }

    public void talk() {
        System.out.println("Beep Beep! I am talking!");
    }

    public void lightOn() {
        System.out.println("Turning on the light...");
    }

    public void dance() {
        System.out.println("Dancing! But wait... I wasn't asked to dance!");
    }
}
```

### Aufgabe:
- Entferne unerwartetes Verhalten (wie das Tanzen) und sorge dafür, dass der Roboter nur das tut, was von ihm erwartet wird.

## Übung 2: Die Bücherei
### Kontext:
Du baust eine digitale Bibliothek, in der Nutzer Bücher ausleihen können. Jedes Buch hat eine Information über den Autor und das Jahr der Veröffentlichung. Leider musst du immer sehr viele Methoden aufrufen, um die Informationen über ein Buch zu erhalten. Du sollst die Klassen so umbauen, dass sie dem Law of Demeter folgen.

### Ausgangscode:
```java
class Author {
    private String name;
    public String getName() { return name; }
}

class Book {
    private Author author;
    private String title;
    public Author getAuthor() { return author; }
    public String getTitle() { return title; }
}

class Library {
    public void printBookDetails(Book book) {
        System.out.println("Title: " + book.getTitle());
        System.out.println("Author: " + book.getAuthor().getName());
    }
}
```

### Aufgabe:
- Refaktoriere den Code, sodass die Library-Klasse nicht direkt auf die Author-Objekte zugreift. Verwende das Law of Demeter und ändere die Book-Klasse entsprechend, damit sie nur notwendige Informationen nach außen gibt.

## Übung 2: Die Tierwelt
### Kontext:
Du baust eine Anwendung, die verschiedene Tiere simuliert. Dabei gibt es einige Tiere, die fliegen können, und andere, die nicht fliegen können. Du hast bemerkt, dass ein Pinguin, der von der Klasse Bird erbt, eine fly() Methode hat, obwohl er nicht fliegen kann. Deine Aufgabe ist es, den Code so zu refaktorisieren, dass er dem Liskovschen Substitutionsprinzip (LSP) folgt.

### Ausgangscode:
```java
class Bird {
    public void fly() {
        System.out.println("Flying...");
    }
}

class Penguin extends Bird {
    @Override
    public void fly() {
        throw new UnsupportedOperationException("Penguins can't fly");
    }
}
```

### Aufgabe:
- Refaktoriere den Code, sodass Pinguine nicht mehr von Bird erben und die fly() Methode nicht aufgerufen werden kann. Überlege, wie du das Verhalten von Vögeln und Pinguinen richtig modellierst, ohne das Liskovsche Substitutionsprinzip zu verletzen.