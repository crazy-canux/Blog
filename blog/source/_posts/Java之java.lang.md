---
layout: post
title: Java之java.lang
comments: true
date: 2016-04-28 22:36:57
updated:
tags:
- jvaa
- lang
categories:
- Java
permalink:
---

# java.lang

> Provides classes that are fundamental to the design of the Java programming
language. The most important classes are Object, which is the root of the class
hierarchy, and Class, instances of which represent classes at run time.
Frequently it is necessary to represent a value of primitive type as if it were
an object. The wrapper classes Boolean, Character, Integer, Long, Float, and
Double serve this purpose. An object of type Double, for example, contains a
field whose type is double, representing that value in such a way that a
reference to it can be stored in a variable of reference type. These classes
also provide a number of methods for converting among primitive values, as well
as supporting such standard methods as equals and hashCode. The Void class is a
non-instantiable class that holds a reference to a Class object representing the
type void.

java的基础类，不需要用import导入。

# java.lang.Object

Object类是所有类的基类。

Constructor:

    Object()

Method:

    protected Object clone()
    boolean equals(Object obj)
    protected void finalize()
    Class<?> getClass()
    int hashCode()
    void notify()
    void notifyAll()
    String toString()
    void wait()
    void wait(long timeout)
    void wait(long timeout, int nanos)

# java.lang.String

Fields:

    static Comparator<String>    CASE_INSENSITIVE_ORDER

Constructor:

    String()
    String(byte[] bytes)
    String(byte[] bytes, Charset charset)
    String(byte[] bytes, int offset, int length)
    String(byte[] bytes, int offset, int length, Charset charset)
    String(byte[] bytes, int offset, int length, String charsetName)
    String(byte[] bytes, String charsetName)
    String(char[] value)
    String(char[] value, int offset, int count)
    String(int[] codePoints, int offset, int count)
    String(String original)
    String(StringBuffer buffer)
    String(StringBuilder builder)

Method:

    char charAt(int index)
    int codePointAt(int index)
    int codePointBefore(int index)
    int codePointCount(int beginIndex, int endIndex)
    int compareTo(String anotherString)
    int compareToIgnoreCase(String str)
    String concat(String str)
    boolean contain(CharSequence s)
    boolean contentEquals(CharSequence cs)
    boolean contentEquals(StringBuffer sb)
    static String copyValueOf(char[] data)
    static String copyValueOf(char[] data, int offset, int count)
    boolean endsWith(String suffix)
    boolean equals(Object anObject)
    boolean equalsIgnoreCase(String anotherString)
    static String format(Locale l, String format, Object... args)
    static String format(String format, Object... args)
    byte[] getBytes()
    byte[] getBytes(Charset charset)
    void getBytes(int srcBegin, int srcEnd, byte[] dst, int dstBegin)
    byte[] getBytes(String charsetName)
    void getChars(int srcBegin, int srcEnd, char[] dst, int dstBegin)
    int hashCode()
    int indexOf(int ch)
    int indexOf(int ch, int fromIndex)
    int indexOf(String str)
    int indexOf(String str, int fromIndex)
    String intern()
    boolean isEmpty()
    static String join(CharSequence delimiter, CharSequence... elements)
    static String join(CharSequence delimiter, Iteable<? extends CharSequence> elements)
    int lastIndexOf(int ch)
    int lastIndexOf(int ch, int fromIndex)
    int lastIndexOf(String str)
    int lastIndexOf(String str, int fromIndex)
    int length()
    boolean matches(String regex)
    int offsetByCodePoints(int index, int codePointOffset)
    boolean regionMatched(boolean ignoreCase, int toffset, String other, int ooffset, int len)
    boolean regionMatches(int toffset, String other, int ooffset, int len)
    String replace(char oldChar, char newChar)
    String replace(CharSeuqence target, CharSequence replacement)
    String replaceAll(String regex, String replacement)
    String replaceFirst(String regex, String replacement)
    String[] split(String regex)
    String[] split(String regex, int limit)
    boolean startsWith(String prefix)
    boolean startsWith(String prefix, int toffset)
    CharSequence subSequence(int beginIndex, int endIndex)
    String substring(int beginIndex)
    String substring(int beginIndex, int endIndex)
    char[] toCharArray()
    String toLowerCase()
    String toLowerCase(Locale locale)
    Strint toString()
    String toUpperCase()
    String toUpperCase(Locale locale)
    String trim()
    static String valueOf(boolean b)
    static String valueOf(char c)
    static String valueOf(char[] data)
    static String valueOf(char[] data, int offset, int count)
    static String valueOf(double d)
    static String valueOf(float f)
    static String valueOf(int i)
    static String valueOf(long l)
    static String valueOf(Object obj)

# java.lang.StringBuffer

Constructor:

    StringBuffer()
    StringBuffre(charSequence seq)
    StringBuffer(int capacity)
    StringBuffer(String str)

Method:

    StringBuffer append(...)
    int capacity()
    char charAt()
    int codePointAt(int index)
    int codePointBefore(int index)
    int codePointCount(int beginIndex, int endIndex)
    StringBuffer delete(int start, int end)
    StringBuffer deleteCharAt(int index)
    void ensureCapacity(int ninimumCapacity)
    void getChars(int srcBegin, int srcEnd, char[] dst, int dstBegin)
    int indexOf(String str)
    int indexOf(String str, int formIndex)
    StringBuffer insert(...)
    int lastIndexOf(String str)
    int lastindexOf(String str, int formIndex)
    int length()
    int offsetByCodePoints(int index, int codePointOffset)
    StringBuffer replace(int start, int end, String str)
    StringBuffer reverse()
    void setCharAt(int index, char ch)
    void setLength(int index, char ch)
    CharSequence subSequence(int start, int end)
    String substring(int start)
    String substring(int start, int end)
    String toString()
    void trimToSize()

# java.lang.StringBuilder

Constructor:

    StringBuilder() /* 构建一个空的字符串构建器 */
    StringBuilder(charSequence seq)
    StringBuilder(int capacity)
    StringBuilder(String str)

Method:

    StringBuilder append(...)
    StringBuilder appendCodePoint(int codePoint)
    int capacity()
    char charAt(int index)
    int codePointAt(int index)
    int codePointBefore(int index)
    int codePointCount(int beginIndex, int endIndex)
    StringBuilder delete(int start, int end)
    StringBuilder deleteCharAt(int index)
    void ensureCapacity(int minimumCapacity)
    void getChars(int srcBegin, int srcEnd)
    int indexOf(String str)
    int indexOf(String str, int formIndex)
    StringBuilder insert(...)
    int lastIndexOf(String str)
    int lastIndexOf(String str, int formIndex)
    int length()
    int offsetByCodePoints(int index, int codePointOffset)
    StringBuilder replace(int start, int end, String str)
    StringBuilder reverse()
    void setCharAt(int index, char ch)
    void setLength(int newLength)
    CharSequence subSequence(int start, int end)
    String substring(int start)
    String substring(int start, int end)
    String toString()
    void trimToSize()

# java.lang.System

Fields:

    public static final InputStream    in
    /* 标准输入流 */

    public static final PrintStream    out
    /* 标准输出流 */

    public static final PrintStream    err
    /* 标准错误输出流 */

Method:

    static void arraycopy(Object src, int srcPos, Object dest, int destPos, int length)
    static String clearProperty(String key)
    static Console console()
    static long currentTimeMillis()
    static void exit(int status)
    static void gc()
    static Map<String, String> getenv()
    static String getenv(String name)
    static Properties getProperty()
    static String getProperty(String key)
    static String getProperty(String key, String def)
    static SecurityManager getSecurityManager()
    static int indentityHashCode(Object x)
    ...

