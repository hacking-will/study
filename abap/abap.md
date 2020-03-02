## ABAP Branch

### 一、ABAP

 #### 1.语法规范

​		参考博客:https://www.cnblogs.com/wangyingcheng/p/9608197.html

#### 2.内表操作

​	

#### 3. Open SQL



### 二、选择屏幕 - Selection Screen

#### 1. 单值参数 - Parameter

​	`PARAMETERS name TYPE｜LIKE type|dobj`

#### 2. 范围参数 - Selection-Options

​	`SELECT-OPTIONS so_name FOR spfli-carrid`

| 字段   | 类型 | 长度 | 说明                                                  |
| ------ | ---- | ---- | ----------------------------------------------------- |
| SIGN   | C    | 1    | 标志位<br />I  : 包括"Include"<br />E : 排除"Exclude" |
| OPTION | C    | 2    | 运算符，EQ\NE\GT...BT...NB                            |
| LOW    |      |      | 下界                                                  |
| HIGH   |      |      | 上界                                                  |



#### 3. 格式化选择屏幕

| 选项                       | 作用           | 说明                                                         |
| -------------------------- | -------------- | ------------------------------------------------------------ |
| `DEFAULT value`            | 分配默认值     |                                                              |
| `OBLIGATRY`                | 设置必输       |                                                              |
| `LOWER CASE`               | 小写输入       | 若语句中使用`TYPE`或`LIKE`选项从ABAP字典中引用某数据库表字段，不能使用该选项 |
| `VISIBLE LENGTH len`       | 设置可见长度   |                                                              |
| `MATHCHCODE OBJECT s_help` | 分配搜索帮助   | 搜索帮助对象`s_help`必须在数据字典中已经定义                 |
| `NO-DISPLAY`               | 隐藏显示       |                                                              |
| `MODIY ID key`             | 分配修改组代码 | `key`中设定的代码将赋值给系统内表`SCREEN`                    |
| `MEMORY ID pid`            | 使用内存默认值 | 从SAP内存中给参数字段分配默认值，`pid`为内存ID,最多20字节,通过`SET/GET`进行设定与读取 |
| `AS CHECKBOX`              | 创建复选框     | 按长度为1的C类型创建，不允许使用附加选项`TYPE`/`LIKE`        |
| `RADIOBUTTON GROUP radi`   | 创建单选按钮   | 长度为1的C类型，允许使用`TYPE / LIKE `但参照类型必须为`char1`,每组至少两个参数，组名称最大长度为4 |

| 选项           | 作用             | 说明 |
| -------------- | ---------------- | ---- |
| `NO-EXTENSION` | 限制选择表为单行 |      |
| `NO-INTERVALS` | 限制为单值选择   |      |
|                |                  |      |

> `DEFAULT`选项给范围分配默认值时，可在选项中进行选择表首行`LOW`、`HIGH`、`OPTION` 、`SIGH`的设定。
>
> `SELECT-OPTIONS seltab FOR f DEFAULT g TO [h]...`



#### 4.其他选择屏幕元素

| x         | x        | x    |
| --------- | -------- | ---- |
| `SKIP`    | 空行     |      |
| `ULINE`   | 下划线   |      |
| `COMMENT` | 添加注释 |      |

>`SELECTION-SCREEN SKIP [n].`
>
>`SELECTION-SCREEN ULINE [[/]pos(len)] [MODIF ID key].`
>
>`SELECTION-SCREEN COMMENT [[/]pos(len)] comm [FOR FIELD f] [MODIF ID key].`"其中comm为注释文本

#### 5. 组合选择屏幕

##### (1) 多个元素集中在一行输出

```
SELECTION-SCREEN BEGIN OF LINE.
	...
SELECTION-SCREEN END OF LINE.
```

> 屏幕不会自动显示选择屏幕元素的说明文字，必须要和`COMMENT`选择一起使用；
>
> 可以通过`POSITION`附加项把元素按照指定位置输出：`SELECTION-SCREEN POSITION pos.`

##### (2)多个元素组合在一个区域

```
SELECTION-SCREEN BEGIN OF BLOCK block [WITH FRAME [TITLE title]] [NO INTERVALS]. 
	...
SELECTION-SCREEN END OF BLOCK block.
```

### 三、Alv列表

#### 1. 标准ALV

See: [form.md](./alv/form.md)

#### 2. OOALV



#### 3. Layout

See: [layout.md](./alv/layout.md)

#### 4. Fieldcatalog

See: [fieldcatalog.md](./alv/fieldcatalog.md)

### 四、对话程序 - Dialog



### 五、智能表格 - Smart Forms



### 六、数据导出 - Excel、Pdf



### 七、BAPI



### 八、其他

#### 1. R/3业务模块

|     模块名     |    简称     |              英文               |
| :------------: | :---------: | :-----------------------------: |
| 生产计划与控制 |     PP      | Production Planning And Control |
|    物料管理    |     MM      |      Materials Management       |
|   销售与分销   |     SD      |     Sales And Distribution      |
|    财务会计    |     FI      |      Financial Accounting       |
|    管理会计    |     CO      |           Controlling           |
|    人力资源    |     HR      |         Human Resources         |
|      其他      | CA\BC\QM\AM |                                 |

#### 2. 程序调用

##### (1) 直接运行 

​		- 事务码、SE38/SA38

##### (2) 内部调用

​		SUBMIT的使用  - 参考博客：https://www.cnblogs.com/mingdashu/p/5609503.html

#### 3. 数学函数

##### (1) 任意类型参数的函数列表

| 函数名 | 说明                                          |
| :----- | --------------------------------------------- |
| ABS    | 返回输入参数的**绝对值**                      |
| SIGN   | 返回输入参数的**符号**：正数1、0返回0、负数-1 |
| TRUNC  | 返回输入参数的**整数部分**                    |
| FRAC   | 返回输入参数的**小数部分**                    |
| CEIL   | 返回**不小于**输入参数的**最小整数值**        |
| FLOOR  | 返回**不大于**输入参数的**最大整数值**        |

##### (2) F类型参数的函数列表

| 函数名           | 说明               |
| ---------------- | ------------------ |
| COS、SIN、TAN    | 三角函数           |
| ACOS、ASIN、ATAN | 反三角函数         |
| COSH、SINH、TANH | 双曲函数           |
| EXP              | 底数为e的幂函数    |
| LOG              | 底数为2的自然对数  |
| LOG10            | 底数为10的自然对数 |
| SQRT             | 平方根             |

#### 4. 字符串处理

##### (1) 连接

`CONCATENATE s1 ... sn INTO s_dest [SEPARATED BY sep]`

##### (2) 拆分

`SPLIT s_source AT sep INTO s1 ... sn | INTO TABLE itab`

##### (3) 查找子串

`SEARCH s_source FOR str`

如果找到`SY-SUBRC = 0 && SY-FDPOS = pos` ，否则`SY-SUBRC = 4 `

其中`str`有几种**通配符模式**:

| 模式   | 说明           |
| ------ | -------------- |
| `str`  | 忽略尾部空格   |
| `.str` | 不忽略尾部空格 |
| `*str` | 以`str`结尾    |
| `str*` | 以`str`开头    |

##### (4) 替换

`REPLACE str1 WITH str2 INTO s_dest [LENGTH len]`

##### (5) 长度

`len = STRLEN( str )`

##### (6) 其他

+ SHIFT 移位
+ CONDENSE 删除多余空格
+ TRANSLATE 大小写转换
+ CONVERT TEXT
+ OVERLAY 覆盖

##### (7) 定位子串

`s[+off][(len)]`

> ```ABAP
> DATA: str(8) VALUE '12345678'
> 	  str_dest(10).
> str_dest = str + 3(5). "off = 3, len = 5, result = '45678'
> ```









