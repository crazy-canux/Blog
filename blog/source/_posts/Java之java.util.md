---
layout: post
title: Java之java.util
comments: true
date: 2016-04-28 22:36:47
updated:
tags:
- java
- util
categories:
- Java
permalink:
---

# java.util

> Contains the collections framework, legacy collection classes, event model,
date and time facilities, internationalization, and miscellaneous utility
classes (a string tokenizer, a random-number generator, and a bit array

# java.util.Scanner

Constructor:

    Scanner(File source)
    Scanner(File source, String charsetName)
    Scanner(InputStream source)
    Scanner(InputStream source, String charsetName)
    Scanner(Path source)
    Scanner(Path source, String charsetName)
    Scanner(Readable source)
    Scanner(ReadableByteChannel source)
    Scanner(ReadableByteChannel source)
    Scanner(String source)

Method:

    void close()
    Pattern delimiter()
    String findInLine(Pattern pattern)
    String findInLine(String pattern)
    String findWithinHorizon(Pattern pattern, int horizon)
    String findWithinHorizon(String pattern, int horizon)
    boolean hasNext()
    boolean hasNext(Pattern pattern)
    boolean hasNext(String pattern)
    boolean hasNextBigDecimal()
    boolean hasNextBigInteger()
    boolean hasNextBigInteger(int radix)
    boolean hasNextBoolean()
    boolean hasNextByte()
    boolean hasNextByte(int radix)
    boolean hasNextDouble()
    boolean hasNextFloat()
    boolean hasNextInt()
    boolean hasNextInt(int radix)
    boolean hasNextLine()
    boolean hasNextLong()
    boolean hasNextLong(int radix)
    boolean hasNextShort()
    boolean hasNextShort(int radix)
    IOException ioException()
    Locale locale()
    MatchResult match()
    String next()
    String next(Pattern pattern)
    String next(String pattern)
    BigDecimal nextBigDecimal()
    BigDecimal nextBigInteger()
    BigDecimal nextBigInteger(int radix)
    boolean nextBoolean()
    byte nextByte()
    byte nextByte(int radix)
    double nextDouble()
    float nextFloat()
    int nextInt()
    int nextInt(int radix)
    String nextLine()
    long nextLong()
    long nextLong(int radix)
    short nextShort()
    short nextShort(int radix)
    int radix()
    void remove()
    Scanner reset()
    Scanner skip(Pattern pattern)
    Scanner skip(String pattern)
    String toString()
    Scanner useDelimiter(Pattern pattern)
    Scanner useDelimiter(String pattern)
    Scanner useLocale(Locale locale)
    Scanner useRadix(int radix)

