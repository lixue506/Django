- Django path()可以接受四个函数，两个必选参数route，view和两个可选参数 kwargs,name

- path(route, view, kwargs=None, name=None)
  - route:字符串，表示url规则，与之匹配的url会执行对应的第二个参数view
  - view:用于执行与正则表达式匹配的url请求
  - kwargs:视图使用的字典类型的参数
  - name用来反向获取url

# Django模板标签

### if/else 标签

---

**case1:**

{% if condition %}

​	... display

{% endif %}

**case2:**

{% if condition1 %}

​	... display 1

{% elif condition2 %}

​	... display 2

{% else %}

​	... display 3

{% endif %}

**case 3:**

{% if %}标签接收 and， or 或者 not关键字来说对多个变量做判断， 或者对变量取反（not）。

if/else支持嵌套。

{% if athlete_list and coach_list %}

​	athletes 和 coaches 变量都是可用的。

{% endif %}

### for 标签

---

{% for %}允许同一个序列上迭代。

循环句法for X in Y, Y是要迭代的序列而X是在每一个特定的循环中使用的变量名称。

每次循环模板系统会渲染在{% for %}和{% endfor %}之间的所有内容

```
<ul>
{% for athlete in athlete_list %}
    <li>{{ athlete.name }}</li>
{% endfor %}
</ul>
```

给标签增加一个 reversed 使得该列表被反向迭代：

```
{% for athlete in athlete_list reversed %}
...
{% endfor %}
```

可以嵌套使用 {% for %} 标签：（双重for循环）

```
{% for athlete in athlete_list %}
    <h1>{{ athlete.name }}</h1>
    <ul>
    {% for sport in athlete.sports_played %}
        <li>{{ sport }}</li>
    {% endfor %}
    </ul>
{% endfor %}
```

**注释标签**

Django注释使用{# #}。

```py
{# 这是一个注释 #}
```

**过滤器**

模板过滤器可以在变量被显示前修改它，过滤器使用管道字符，如下所示：

```
{{ name|lower }}
```

{{ name }} 变量被过滤器 lower 处理后，文档大写转换文本为小写。

过滤管道可以被* 套接* ，既是说，一个过滤器管道的输出又可以作为下一个管道的输入：

```
{{ my_list|first|upper }}
```

以上实例将第一个元素并将其转化为大写。

有些过滤器有参数。 过滤器的参数跟随冒号之后并且总是以双引号包含。 例如：

```
{{ bio|truncatewords:"30" }}
```

这个将显示变量 bio 的前30个词。

其他过滤器：

- addslashes : 添加反斜杠到任何反斜杠，单引号或者双引号前面。

- date : 按指定的格式字符串参数格式化 date 或者 datetime 对象，实例：

  ```
  {{ pub_date|date:"F j, Y" }}
  ```

- length : 返回变量的长度。

**include 标签**

{% include %} 标签允许在模板中包含其它的模板的内容。

下面这个例子都包含了 nav.html 模板：

```
{% include "nav.html" %}
```







