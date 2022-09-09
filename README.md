### Chapter 13.1.1

# An Overview of the Collections Framework

**Chapter Goals 13.1.1**
* To learn how to use the collection classes supplied in the Java library
* To use iterators to traverse collections
* To choose appropriate collections for solving programming problems
* To study applications of stacks and queues

![](https://zytools.zybooks.com/zyAuthor/BigJavaLateObjects/3/IMAGES/embedded_image_1_02056871-9946-49ca-a6e5-c74283968632_0SbYWohbgKnCkRCWRqdZ.png)

If you want to write a program that collects objects (such as the stamps to the left), you have a number of choices. Of course, you can use an array list, but computer scientists have invented other mechanisms that may be better suited for the task. In this chapter, we introduce the collection classes and interfaces that the Java library offers. You will learn how to use the Java collection classes, and how to choose the most appropriate collection type for a problem.

When you need to organize multiple objects in your program, you can place them into a collection. The `ArrayList` class that was introduced in Chapter 6 is one of many collection classes that the standard Java library supplies. In this chapter, you will learn about the Java collections framework, a hierarchy of interface types and classes for collecting objects. Each interface type is implemented by one or more classes (see Figure 13.1.1). (Definition of **_collection_**: A data structure that provides a mechanism for adding, removing, and locating elements.)

## Figure 13.1.1: Interfaces and Classes in the Java Collections Framework.
![](https://zytools.zybooks.com/zyAuthor/BigJavaLateObjects/3/IMAGES/embedded_image_1_dee6f249-7877-4fff-88ba-bb4de6f69633_0SbYWohbgKnCkRCWRqdZ.png)

At the root of the hierarchy is the `Collection` interface. That interface has methods for adding and removing elements, and so on. Table 13.1.1 shows all the methods. Because all collections implement this interface, its methods are available for all collection classes. For example, the `size` method reports the number of elements in any collection.

## Table 13.1.1: The Methods of the Collection Interface.
| Collection<String> coll = new ArrayList<>(); | The ArrayList class implements the Collection interface. |
| :--- | :--- |
| coll = new TreeSet<>(); | The TreeSet class (Section 13.4) also implements the Collection interface. |
| int n = coll.size(); | Gets the size of the collection. n is now 0. |
| coll.add("Harry"); <br /> coll.add("Sally"); | Adds elements to the collection. |
| String s = coll.toString(); | Returns a string with all elements in the  ollection. s is now [Harry, Sally]. |
| System.out.println(coll); | Invokes the toString method and prints [Harry, Sally]. |
| coll.remove("Harry"); <br /> boolean b = coll.remove("Tom"); | Removes an element from the collection, returning false if the element is not present. b is false. |
| b = coll.contains("Sally"); | Checks whether this collection contains a given element. b is now true. |
| for (String s : coll)  { <br />   System.out.println(s); <br />} <br /> | You can use the “for each” loop with any collection. This loop prints the elements on separate lines. |
| Iterator<String> iter = coll.iterator(); | You use an iterator for visiting the elements in the collection (see Section 13.2). |

The `List` interface describes an important category of collections. In Java, a list is a collection that remembers the order of its elements (see Figure 13.1.2). The `ArrayList` class implements the `List` interface. An `ArrayList` is simply a class containing an array that is expanded as needed. **_If you are not concerned about efficiency, you can use the `ArrayList` class whenever you need to collect objects_**. However, several common operations are inefficient with array lists. In particular, if an element is added or removed, the elements at larger positions must be moved.

## Figure 13.1.2: A List of Books.
![](https://zytools.zybooks.com/zyAuthor/BigJavaLateObjects/3/IMAGES/embedded_image_1_85220027-a1c4-4997-a5f2-929372f1c797_0SbYWohbgKnCkRCWRqdZ.png)

The Java library supplies another class, `LinkedList`, that also implements the `List` interface. Unlike an array list, a linked list allows efficient insertion and removal of elements in the middle of the list. We will discuss that class in the next section.

You use a list whenever you want to retain the order that you established. For example, on your bookshelf, you may order books by topic. A list is an appropriate data structure for such a collection because the ordering matters to you.

However, in many applications, you don’t really care about the order of the elements in a collection. Consider a mail-order dealer of books. Without customers browsing the shelves, there is no need to order books by topic. Such a collection without an intrinsic order is called a set—see Figure 13.1.3. (Definition of **_set_**: An unordered collection that allows efficient addition, location, and removal of elements.)

## Figure 13.1.3: A Set of Books.
![](https://zytools.zybooks.com/zyAuthor/BigJavaLateObjects/3/IMAGES/embedded_image_1_a6dd0ab4-9802-4c7f-bcea-0c18551c1abe_0SbYWohbgKnCkRCWRqdZ.png)

Because a set does not track the order of the elements, it can arrange the elements so that the operations of finding, adding, and removing elements become more efficient. Computer scientists have invented mechanisms for this purpose. The Java library provides classes that are based on two such mechanisms (called hash tables and binary search trees). You will learn in this chapter how to choose between them.

Another way of gaining efficiency in a collection is to reduce the number of operations. A stack remembers the order of its elements, but it does not allow you to insert elements in every position. You can add and remove elements only at the top—see Figure 13.1.4. (Definition of **stack**: A data structure with “last-in, first-out” retrieval. Elements can be added and removed only at one position, called the top of the stack.)

## Figure 13.1.4: A Stack of Books.
![](https://zytools.zybooks.com/zyAuthor/BigJavaLateObjects/3/IMAGES/embedded_image_1_a9b5120f-a8b8-47be-8a7e-fd2823596f87_0SbYWohbgKnCkRCWRqdZ.png)

In a queue, you add items to one end (the tail) and remove them from the other end (the head). For example, you could keep a queue of books, adding required reading at the tail and taking a book from the head whenever you have time to read another one. A priority queue is an unordered collection that has an efficient operation for removing the element with the highest priority. You might use a priority queue for organizing your reading assignments. Whenever you have some time, remove the book with the highest priority and read it. We will discuss stacks, queues, and priority queues in Section 13.10. (Definition of **queue**: A collection of items with “first in, first out” retrieval. ) (Definition of **priority queue**: An abstract data type that enables efficient insertion of elements and efficient removal of the smallest element. )

Finally, a map manages associations between keys and values. Every key in the map has an associated value (see Figure 13.1.5). The map stores the keys, values, and the associations between them. (Definition of **map**: A data structure that keeps associations between key and value objects.)

## Figure 13.1.5: A Map from Bar Codes to Books.
![](https://zytools.zybooks.com/zyAuthor/BigJavaLateObjects/3/IMAGES/embedded_image_1_c678e553-3094-48aa-b960-b7ccdede21ce_0SbYWohbgKnCkRCWRqdZ.png)

For an example, consider a library that puts a bar code on each book. The program used to check books in and out needs to look up the book associated with each bar code. A map associating bar codes with books can solve this problem. We will discuss maps in Section 13.5.

Starting with this chapter, we will use the “diamond syntax” for constructing instances of generic classes (see Special Topic 6.18). For example, when constructing an array list of strings, we will use
```java
ArrayList<String> coll = new ArrayList<>();
```
Note that there is an empty pair of brackets `<>` after `new ArrayList` on the right-hand side. The compiler infers from the left-hand side that an array list of strings is constructed.

Here is a sample program that demonstrates several collection classes.

<details><summary><Strong>CollectionsDemo.java. by Fabian Zelaya<Strong/></summary>
<p>

#### We can hide anything, even code!

```java
import java.util.Collection;
import java.util.ArrayList;
import java.util.TreeSet;

/**
 * @author Fabian Zelaya
 * @version Fri Sep 9, 2022
 * @description CollectionsDemo.java.
 * 
 */

/**
   This program demonstrates classes from the Java collections framework.
*/
public class CollectionsDemo
{
   public static void main(String[] args)
   {
      System.out.println("Working with an ArrayList");
      workWith(new ArrayList<>());
      System.out.println("Working with a TreeSet");
      workWith(new TreeSet<>());
   }

   /**
      Shows how to work with a collection of strings.
      @param coll a collection from the Java collections framework
   */
   public static void workWith(Collection<String> coll)
   {
      coll.add("Harry");
      coll.add("Sally");
      coll.add("Fred");
      coll.add("Wilma");
      coll.add("Harry");
      System.out.println(coll);
      System.out.print("Removing Harry and Tom: ");
      System.out.print(coll.remove("Harry") + " ");
      System.out.println(coll.remove("Tom"));
      System.out.print("Looking for Harry and Sally: ");
      System.out.print(coll.contains("Harry") + " ");
      System.out.println(coll.contains("Sally"));
      for (String s : coll) 
      {
         System.out.println(s);
      }
   }
}
// FZ

/**
 * Working with an ArrayList
 * [Harry, Sally, Fred, Wilma, Harry]
 * Removing Harry and Tom: true false
 * Looking for Harry and Sally: true true
 * Sally
 * Fred
 * Wilma
 * Harry
 * Working with a TreeSet
 * [Fred, Harry, Sally, Wilma]
 * Removing Harry and Tom: true false
 * Looking for Harry and Sally: false true
 * Fred
 */
```
</p>
</details>


**Important websites:**
https://www.pluralsight.com/guides/working-tables-github-markdown