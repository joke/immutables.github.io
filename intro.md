---
title: 'Intro'
layout: page
---

Introduction
------------

To get benefits of immutability in Java we created the annotation processor
to easily create simple and consistent value objects. You can think of it as
[Guava's Immutable Collections](https://code.google.com/p/guava-libraries/wiki/ImmutableCollectionsExplained)
but for regular objects.

The core of _Immutables_ is modeling. Good modelling is at heart of creating good application,
services and good design in general. We feel proud to fill a gap in modelling on the Java programming language, where usage of conventional JavaBeans just insufficient.

* Immutable object constructed once, in consistent state and can be safely shared
  - Will fail if mandatory attribute is missing
  - No sneaky modification when passed to other code
* Immutable objects are naturally thread-safe and can be safely shared among threads
  - No excessive copying
  - No excessive synchronization
* Object definitions are pleasant to write and read
  - No boilerplate setter and getters
  - No ugly IDE-generated `hashCode`, `equals` and `toString` methods that are stored in source control.

[Get started!](/getstarted.html) create an _abstract value class_ and then add annotation to generate _immutable implementation class_!

See [sample generated code](/generated.html) for an example of what kind of code is being generated by the processor.

Or jump straight to the [features](/immutable.html#features) implemented!

* Read "Item 15: Minimize mutability" [Effective Java, Second Edition](http://www.amazon.com/Effective-Java-Edition-Joshua-Bloch/dp/0321356683)
  book for classic summary on immutability.
* See Google's attempt on this with [AutoValue](https://docs.google.com/presentation/d/14u_h-lMn7f1rXE1nDiLX0azS3IkgjGl5uxp5jGJ75RE).
* Watch ["Power Use of Value Objects" presentation](http://www.infoq.com/presentations/Value-Objects-Dan-Bergh-Johnsson) for examples of how useful value objects are.
* Watch ["Simple made easy" presentation](http://www.infoq.com/presentations/Simple-Made-Easy) about some insights on simplicity of immutability.

_Immutables_ have been in development since early 2012 counting from earliest prototypes.
Currently, toolkit is being successfully used in production applications:
it's used for development of airline inventory systems, travel deal aggregators and other application that take advantages of efficient in-memory storage and concurrent computations on JVM.

[Guava](https://code.google.com/p/guava-libraries) is used as utility library for generated classes,
but in addition we employ API style popularized by "Effective Java, Second Edition" book and Guava Library.
Usage of `null` as attribute values is rigorously prohibited ([Using and avoiding null explained](https://code.google.com/p/guava-libraries/wiki/UsingAndAvoidingNullExplained)).

The solution do not require compiler hacks with AST transformation or companion languages. Annotation processing is a part of standard Java compiler. Classes are being generated during compilation are not stored in source control, however, generated sources are easily inspectable if needed. Generated code extends user written code, but never mixed in one file!

It may seem that usage _Immutables_ may result in some sort of [anemic domain model](http://www.martinfowler.com/bliki/AnemicDomainModel.html),
however, this impression is false and we see great benefits of proper domain modelling. But we need solid building blocks — value objects,
a [smart data](http://immutables.github.com/immutable.html#smart-data) objects,
immutable values that have methods that compute other values and reduce complexity of services and entities.
Other aspect of modelling is representation of system state and domain entities as sequences of _events_ or _snapshots_.
The techniques like [event sourcing](http://martinfowler.com/eaaDev/EventSourcing.html) employs
benefits of immutable object graphs, allow sub-graphs to be shared between snapshots, transform system states,
or even reconstruct full system state at some point in time.
For that kind of systems we just made writing immutable objects a whole lot easier. 

Immutables annotation processor may be very useful if you wish to increase safety and consistency at application boundaries as well as in internal data structures,
create expressive data objects for your java API.