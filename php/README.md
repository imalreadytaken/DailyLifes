## PHPUNIT

#### 测试值依赖问题

如果一个测试方法需要依赖另一个方法的返回值，可以使用如下方法

```php
class CosTest extends TestCase
{
    public function testUpload(){
        $cos = new CosService();
        $handler = new TaskHandler(1019, 'a0eb195632c3b3354522f00f2f1f0d24','test_seven');
        $uri = $handler->generateCosUri();
        $url = $cos->uploadData(json_encode(array(
                'name' => 'seven_big_data1',
            )), $uri);
        $this->assertContains($uri, $url);
        return $uri;
    }

    /**
     * @depends testUpload
     * @author sevencheng
     * @param $uri
     * @return
     */
    public function testGet($uri){
        $cos = new CosService();
        $data = json_decode($cos->request($uri), true);
        $this->assertEquals($data['name'], 'seven_big_data1');
        return $uri;
    }

    /**
     * @depends testUpload
     * @depends testGet
     * @author sevencheng
     * @param $uri
     * @param $uriGet
     */
    public function testDelete($uri, $uriGet){
        $cos = new CosService();
        $this->assertEquals($uri, $uriGet);
        $this->assertEquals($cos->delete($uri), true);
        $this->assertEquals($cos->request($uri), false);
    }

}
```



##Tips

- json_decode:
  - 如果assoc不设为true，返回的将是Object而不是array，而在Object中，是无法将数字键设置为属性的，只有通过访问key才能访问到数字key

     <?php
     ​	$json = '{"1":a,"b":2,"c":3,"d":4,"e":5}';
     ​	
     ```php
     $obj = json_decode($json);
     $arr = json_decode($json, true);
     
     array_key_exists('1', $obj); // false
     array_key_exists('1', $arr); // true
     
     ?>
     ```
