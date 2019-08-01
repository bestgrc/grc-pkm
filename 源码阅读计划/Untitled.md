## 一、默认容量为什么用位移运算而不直接赋值？？百度也有人有这个疑惑，然后有人说不要纠结这个点。

static final int DEFAULT_INITIAL_CAPACITY = 1 << 4; // aka 16

## 二、内部类

static class Node<K,V> implements Map.Entry<K,V>