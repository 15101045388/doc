# 主模块
### 一、提供用户对数据表增删改查的接口
### 二、模型(主模块无模型)
### 三、服务接口

<table>
  <tr>
    <th>接口详情：</th>
    <th>api地址</th>
    <th>提交方法</th>
    <th>参数格式：</th>
    <th>参数示例</th>
  </tr>
  <tr>
    <td>1</td>
    <td>http://localhost:8083/data/{dbName}/{tableName}/_delete</td>
    <td>POST</td>
    <td>json对象</td>
    <td>{"id":"1"}</td>
  </tr>
  <tr>
    <td>2</td>
    <td>http://localhost:8083/data/{dbName}/{tableName}/_add</td>
    <td>POST</td>
    <td>json数组</td>
    <td>[{"name":"mazi"},{"name":"lisi"}]</td>
  </tr>
  <tr>
    <td>3</td>
    <td>http://localhost:8083/data/{dbName}/{tableName}/_update</td>
    <td>POST</td>
    <td>json对象</td>
    <td>{"id":"1","name":"mazi","age":"16"}</td>
  </tr>
  <tr>
    <td>4</td>
    <td>http://localhost:8083/data/{dbName}/{tableName}/_data</td>
    <td>GET</td>
    <td>直接在url后面拼接</td>
    <td>?id=1</td>
  </tr>
</table>


<table>
  <tr>
    <th>查询参数：</th>
    <th>参数描述</th>
  </tr>
  <tr>
    <td>1</td>
    <td>等于 XX=aaa，如id=1，或者name=Db_1，此处及以下“XX”为列名</td>
  </tr>
  <tr>
    <td>2</td>
    <td>大于 XX_start=aaa，如createdate_start=20160101</td>
  </tr>
  <tr>
    <td>3</td>
    <td>小于 XX_end=aaa，如createdate_end=20150202</td>
  </tr>
  <tr>
    <td>4</td>
    <td>范围 XX_start=aaa&XX_end=bbb</td>
  </tr>
  <tr>
    <td>5</td>
    <td>逻辑且 上述条件使用’&’符号相连</td>
  </tr>
  <tr>
    <td>6</td>
    <td>同一条件逻辑或 XX=aaa&XX=bbb，即为XX等于aaa或XX=bbb，返回并集</td>
  </tr>
</table>

<table>
  <tr>
    <th>另外的全局参数：</th>
    <th>参数描述</th>
  </tr>
  <tr>
    <td>1</td>
    <td>_order _order=<列名>，以列排序</td>
  </tr>
  <tr>
    <td>2</td>
    <td>_desc _order=<col_1>&_desc，排序方向，不加上此参数默认是正向</td>
  </tr>
  <tr>
    <td>3</td>
    <td>_skip 结果集的offset，如_skip=10表示跳过前10项</td>
  </tr>
  <tr>
    <td>4</td>
    <td>_take _take=N，取结果集的前N项，一般和排序及offset一期使用</td>
  </tr>
</table>

<table>
  <tr>
    <th>GET方法查询示例：</th>
    <th>api地址</th>
    <th>api描述</th>
  </tr>
  <tr>
    <td>1</td>
    <td>http://localhost:8083/data/test/student/_data?id=1</td>
    <td>查询test表中id为1的数据</td>
  </tr>
  <tr>
    <td>2</td>
    <td>http://localhost:8083/data/test/student/_data?age_start=18&age_end=20</td>
    <td>查询年龄段在18到20岁之间</td>
  </tr>
   <tr>
    <td>3</td>
    <td>http://localhost:8083/data/test/student/_data?age=18&age=20</td>
    <td>查询年龄段是 18和20岁的</td>
  </tr>
  <tr>
    <td>4</td>
    <td>http://localhost:8083/data/test/student/_data?_order=name</td>
    <td>查询结果根据name排序</td>
  </tr>
  <tr>
    <td>5</td>
    <td>http://localhost:8083/data/test/student/_data? _order=name&_desc    </td>
    <td>_desc 与_order组合使用，按Name倒排</td>
  </tr>
  <tr>
    <td>6</td>
    <td>http://localhost:8083/data/test/student/_data?_skip=5&_take=15    </td>
    <td>从5往后面取15个数据。如果数据不够15条，取5后面的所有数据</td>
  </tr>
</table>
