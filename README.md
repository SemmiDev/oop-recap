# REVIEW OOP

## Scope

- Class & Object
- Fields / Properties / Attributes
- Method
- Recap

---

### Class & Object

- Class adalah blueprint, prototype atau cetakan untuk membuat Object
- Class berisikan deklarasi semua properties dan functions yang dimiliki oleh Object
- Setiap Object selalu dibuat dari Class Dan sebuah Class bisa membuat Object tanpa batas

```java
public class Person {

}

class Person {

}
```

- Object adalah hasil instansiasi dari sebuah class
- Untuk membuat object kita bisa menggunakan kata kunci **new**, dan diikuti dengan nama Class dan kurung ()

```java
Person sammi = new Person();
Person faren = new Person();
```

### Properties / Attributes

- Properties / Attributes adalah data yang bisa kita sisipkan di dalam Object
- Namun sebelum kita bisa memasukkan data di fields, kita harus mendeklarasikan data apa aja yang dimiliki object tersebut di dalam deklarasi class-nya
- Membuat field sama seperti membuat variable, namun ditempatkan di block class

```java
public class Person {
    String name;
    String gender;
    String address;
    final String country = "INDONESIA";
}
```

- Fields yang ada di object, bisa kita manipulasi. Tergantung final atau bukan.
- Jika final, berarti kita tidak bisa mengubah data field nya, namun jika tidak, kita bisa mengubah field nya
- Untuk memanipulasi data field, sama seperti cara pada variable
- Untuk mengakses field, kita butuh kata kunci . (titik) setelah nama object dan diikuti nama fields nya

```java
Person sammi = new Person();
sammi.name = "Sammi";
sammi.gender = "laki-laki";
sammi.address = "pekanbaru";
```

### Method

- Selain menambahkan field, kita juga bisa menambahkan method ke object
- Caranya dengan mendeklarasikan method tersebut di dalam block class
- Sama seperti method biasanya, kita juga bisa menambahkan return value, parameter dan method overloading di method yang ada di dalam block class
- Untuk mengakses method tersebut, kita bisa menggunakan tanda titik (.) dan diikuti dengan nama method nya. Sama seperti mengakses field

```java
public class Person {
    String name;
    String gender;
    String address;
    private int age;
    final String country = "INDONESIA";

    void sayHello(String timesOfDay) {
    	System.out.println("Good " + timesOfDay + " " + this.name);
    }

    int getUmur() {
    	return this.age;
    }
}
```

```java
    Person sammi = new Person();
    sammi.name = "sammidev";
    sammi.setUmur(17);

    sammi.sayHello("Morning");
    System.out.println("Umur " + sammi.name " = " + sammi.getUmur());
```

## Recap

```java
package com.sammidev;

import java.util.ArrayList;
import java.util.UUID;

class Product {
    String id;
    String name;
    int quantity;
    double price;

    public Product(String name, int quantity, double price) {
        this.id = UUID.randomUUID().toString();
        this.name = name;
        this.quantity = quantity;
        this.price = price;
    }
}

class Cart {
    private ArrayList<Product> products = new ArrayList<>();
    private double totalPrice;

    Boolean addToCart(Product product, int quantity) {
        if (product.quantity < quantity) {
            return false;
        }

        product.quantity -= quantity;
        this.products.add(product);
        return true;
    }

    double getTotalPrice() {
        for (Product product : this.products) {
            this.totalPrice += product.price;
        }
        return this.totalPrice;
    }
}

public class App {
    public static void main(String[] args) {
        Product productA = new Product("Product A", 10, 20.000);

        Cart cart = new Cart();
        boolean status =  cart.addToCart(productA, 5);
        if (status) {
            System.out.println("BERHASIL...");
        } else {
            System.out.println("GAGAL...");
        }

        System.out.println("total price = " + cart.getTotalPrice());
    }
}

```
