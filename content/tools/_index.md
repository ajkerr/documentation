---
date: 2016-03-08T21:07:13+01:00
title: About GraphQL Java Tools
weight: 1
type: index
menu:
  main:
    parent: Tools
---

[![Maven Central](https://maven-badges.herokuapp.com/maven-central/com.graphql-java-kickstart/graphql-java-tools/badge.svg)](https://maven-badges.herokuapp.com/maven-central/com.graphql-java-kickstart/graphql-java-tools)

This library allows you to use the GraphQL schema language to build your [graphql-java](https://github.com/graphql-java/graphql-java) schema.
Inspired by [graphql-tools](https://github.com/apollographql/graphql-tools), it parses the given GraphQL schema and allows you to BYOO (bring your own object) to fill in the implementations.
GraphQL Java Tools works extremely well if you already have domain POJOs that hold your data (e.g. for RPC, ORM, REST, etc) by allowing you to map these magically to GraphQL objects.

GraphQL Java Tools aims for seamless integration with Java, but works for any JVM language.  Try it with Kotlin!

## Why GraphQL Java Tools?

* **Schema First**:  GraphQL Java Tools allows you to write your schema in a simple, portable way using the [GraphQL schema language](http://graphql.org/learn/schema/) instead of hard-to-read builders in code.
* **Minimal Boilerplate**:  It takes a lot of work to describe your GraphQL-Java objects manually, and quickly becomes unreadable.
A few libraries exist to ease the boilerplate pain, including [GraphQL-Java's built-in schema-first wiring](http://graphql-java.readthedocs.io/en/latest/schema.html), but none (so far) do type and datafetcher discovery.
* **Stateful Data Fetchers**:  If you're using an IOC container (like Spring), it's hard to wire up datafetchers that make use of beans you've already defined without a bunch of fragile configuration.  GraphQL Java Tools allows you to register "Resolvers" for any type that can bring state along and use that to resolve fields.
* **Generated DataFetchers**:  GraphQL Java Tools automatically creates data fetchers for your fields that call the appropriate method on your java class.  This means all you have to do to create a new field is add the field definition to your schema and add a corresponding method on your class.
* **Type → Class Discovery**:  GraphQL Java Tools starts from your root objects (Query, Mutation) and, as it's generating data fetchers for you, starts to learn about the classes you use for a certain GraphQL type.
* **Class Validation**:  Since there aren't any compile-time checks of the type → class relationship, GraphQL Java Tools will warn you if you provide classes/types that you don't need to, as well as throwing errors if you use the wrong Java class for a certain GraphQL type when it builds the schema.
* **Unit Testing**:  Since your GraphQL schema is independent of your data model, this makes your classes simple and extremely testable.
