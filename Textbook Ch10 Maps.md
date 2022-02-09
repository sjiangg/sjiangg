#### Maps

a ***map*** is an abstract data type **ADT** designed to efficiently store and retrieve values. A map stores key-value pairs *(k, v)*, which we call ***entires***, where *k* is the kay and *v* is its corresponding value. 

​	Maps are also known as ***associative*** ***arrays***. Unlike a standard array, a key of a map need not to be numeric,and it does not directly designate a position within the structure.

```java
 public interface Map<K,V> { 
     int size( );
	 boolean isEmpty( );
	 V get(K key);
	 V put(K key, V value);
	 V remove(K key);
	 Iterable<K> keySet( );
	 Iterable<V> values( );
	 Iterable<Entry<K,V>> entrySet( );
1 }
```

