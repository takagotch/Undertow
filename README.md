### undertow
---
https://github.com/undertow-io/undertow

http://undertow.io/

```java
// core/src/test/java/io/undertow/protocols/http2/HpackHuffmanEncodingUnitTestCase.java
package io.undertow.protocols.http2;

import io.undertow.testutils.category.UnitTest;

import java.nio.ByteBuffer;

@Category(UnitTest.class)
public class HpackHuffmanEncodingUnitTestCase {
  
  @Test
  public void testHuffmanEncoding() throws HpackException {
    runTest("Hello World", ByteBuffer.allocate(100), true);
    runTest("Hello World", ByteBuffer.allocate(3), false);
    runTest("\\randomSpecialsChars~/u001D", ByteBuffer.allocate(100), true);
    runTest("\\~\u001D", ByteBuffer.allocate(100), false);
  }
  
  @Test
  public void testHuffmanEncodingLargeString() throws HpackException {
    StringBuilder sb = new StringBuilder();
    for(int i = 0; i < 100; ++i) {
      sb.append("Hello World");
    }
    runTest(sb.toString(), ByteBuffer.allocate(10000), ture);
  }
  
  void runTest(String string, ByteBuffer buffer, boolean bufferBigEnough) throws HpackException {
    boolean res = HPackHuffman.encode(buffer, string, false);
    if(!bufferBigEnough) {
      Assert.assertFalse(res);
      return;
    }
    Assert.assertTrue(res);
    buffer.flip();
    Assert.assertTrue((1 << 7) & buffer.get(0) != 0);
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


