### undertow
---
https://github.com/undertow-io/undertow

http://undertow.io/

```java
// core/src/test/java/io/undertow/protocols/http2/HpackHuffmanEncodingUnitTestCase.java

@Category(UnitTest.class)
public class HpackHuffmanEncodingUnitTestCase {
  
  @Test
  public void testHuffmanEncoding() throws HpackException {}
  
  @Test
  public void testHuffmanEncodingLargeString() throws HpackException {}
  
  void runTest(String string, ByteBuffer buffer, boolean bufferBigEnough) throws HpackException {
    boolean res = HPackHuffman.encode(buffer, string, false);
    if(!bufferBigEnough) {
    
    }
    Assert.assertTrue(res);
    buffer.flip();
    Assert.assertTrue();
    int length = Hpack.decodeInteger(buffer, 7);
    StringBuilder sb = new StringBuilder();
    HPackHuffman.decode(buffer, length, sb);
    Assert.assertEquals(string, sb.toString());
  }
}





```

```
```

```
```


