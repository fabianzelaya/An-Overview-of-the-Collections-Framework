### Chapter 13.1.1

# An Overview of the Collections Framework

**Chapter Goals 13.1.1**
* To learn how to use the collection classes supplied in the Java library
* To use iterators to traverse collections
* To choose appropriate collections for solving programming problems
* To study applications of stacks and queues

![](https://zytools.zybooks.com/zyAuthor/BigJavaLateObjects/3/IMAGES/embedded_image_1_02056871-9946-49ca-a6e5-c74283968632_0SbYWohbgKnCkRCWRqdZ.png)

If you want to write a program that collects objects (such as the stamps to the left), you have a number of choices. Of course, you can use an array list, but computer scientists have invented other mechanisms that may be better suited for the task. In this chapter, we introduce the collection classes and interfaces that the Java library offers. You will learn how to use the Java collection classes, and how to choose the most appropriate collection type for a problem.

When you need to organize multiple objects in your program, you can place them into a collection. The ArrayList class that was introduced in Chapter 6 is one of many collection classes that the standard Java library supplies. In this chapter, you will learn about the Java collections framework, a hierarchy of interface types and classes for collecting objects. Each interface type is implemented by one or more classes (see Figure 13.1.1). (Definition of **_collection_**: A data structure that provides a mechanism for adding, removing, and locating elements.)

## Figure 13.1.1: Interfaces and Classes in the Java Collections Framework.
![](https://zytools.zybooks.com/zyAuthor/BigJavaLateObjects/3/IMAGES/embedded_image_1_dee6f249-7877-4fff-88ba-bb4de6f69633_0SbYWohbgKnCkRCWRqdZ.png)

At the root of the hierarchy is the Collection interface. That interface has methods for adding and removing elements, and so on. Table 13.1.1 shows all the methods. Because all collections implement this interface, its methods are available for all collection classes. For example, the size method reports the number of elements in any collection.

## Table 13.1.1: The Methods of the Collection Interface.
| Collection<String> coll = new ArrayList<>(); | The ArrayList class implements the Collection interface. |
| --- | --- |
| coll = new TreeSet<>(); | The TreeSet class (Section 13.4) also implements the Collection interface. |
| int n = coll.size(); | Gets the size of the collection. n is now 0. |
| coll.add("Harry"); <br /> coll.add("Sally"); | Adds elements to the collection. |
| String s = coll.toString(); | Returns a string with all elements in the  ollection. s is now [Harry, Sally]. |
| System.out.println(coll); | Invokes the toString method and prints [Harry, Sally]. |
| coll.remove("Harry"); <br /> boolean b = coll.remove("Tom"); | Removes an element from the collection, returning false if the element is not present. b is false. |
| b = coll.contains("Sally"); | Checks whether this collection contains a given element. b is now true. |
| for (String s : coll)  { <br /> System.out.println(s); <br />} <br /> | You can use the “for each” loop with any collection. This loop prints the elements on separate lines. |
| Iterator<String> iter = coll.iterator(); | You use an iterator for visiting the elements in the collection (see Section 13.2). |

The **List** interface describes an important category of collections. In Java, a list is a collection that remembers the order of its elements (see Figure 13.1.2). The **ArrayList** class implements the List interface. An **ArrayList** is simply a class containing an array that is expanded as needed. **_If you are not concerned about efficiency, you can use the ArrayList class whenever you need to collect objects_**. However, several common operations are inefficient with array lists. In particular, if an element is added or removed, the elements at larger positions must be moved.

## Figure 13.1.2: A List of Books.
![](https://zytools.zybooks.com/zyAuthor/BigJavaLateObjects/3/IMAGES/embedded_image_1_85220027-a1c4-4997-a5f2-929372f1c797_0SbYWohbgKnCkRCWRqdZ.png)

The Java library supplies another class, **LinkedList**, that also implements the **List** interface. Unlike an array list, a linked list allows efficient insertion and removal of elements in the middle of the list. We will discuss that class in the next section.

You use a list whenever you want to retain the order that you established. For example, on your bookshelf, you may order books by topic. A list is an appropriate data structure for such a collection because the ordering matters to you.

However, in many applications, you don’t really care about the order of the elements in a collection. Consider a mail-order dealer of books. Without customers browsing the shelves, there is no need to order books by topic. Such a collection without an intrinsic order is called a set—see Figure 13.1.3. (Definition of **_set_**: An unordered collection that allows efficient addition, location, and removal of elements. )


**Important websites:**
https://www.pluralsight.com/guides/working-tables-github-markdown