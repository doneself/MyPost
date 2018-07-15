# [.NET-ORM框架EF-Code First代码优先](https://www.cnblogs.com/SmileIven/p/9140442.html)

<div class="clear">

</div>

<div class="postBody">

<div id="cnblogs_post_body" class="blogpost-body">

### 前言

Code
First顾名思义，通告代码创建实体与数据库。示例中我们会创建表，分表是Studen,Teacher。

### Code First实战示例

打开VS2013,创建一个项目我这里是用的MVC框架来做的示例搞麻烦了，小伙伴们可用控制台一样的。命名为EFCodeFirst,如下图： 

![](https://images2018.cnblogs.com/blog/814205/201806/814205-20180605144729617-205152970.png)

选中解决方案资源管理器中的项目，点击右键，选择”管理NuGet程序包”
添加EF

![](https://images2018.cnblogs.com/blog/814205/201806/814205-20180605145120644-1485962114.png)

![](https://images2018.cnblogs.com/blog/814205/201806/814205-20180605145132435-1669900866.png)

 

准备工作结束，接下来我们创建实体类，添加代码如下：

![](https://images2018.cnblogs.com/blog/814205/201806/814205-20180605145352956-648076945.png)![](https://images2018.cnblogs.com/blog/814205/201806/814205-20180605145406314-137461970.png)

    Studen：

<div class="cnblogs_code">

``` 
    public class Studen
    {
        public Studen() { }
        [Key]
        public int Id { get; set; }

        public string Name { get; set; }

        public int Age { get; set; }

        public Studen(string name, int age)
        {
            this.Name = name;
            this.Age = age;
        }
    }
```

</div>

    Teacher：

<div class="cnblogs_code">

``` 
    public class Teacher
    {
        public Teacher() { }
        [Key]
        public int Id { get; set; }

        public string Name { get; set; }

        public int Age { get; set; }

        public Teacher(string name, int age)
        {
            this.Name = name;
            this.Age = age;
        }
    }
```

</div>

接下来我们设置数据库上下文Context,它继承于DbContext类。构造一个函数base中是设置数据库连接的驱动地址，要注意其中的对应关系Context代码如下：

![](https://images2018.cnblogs.com/blog/814205/201806/814205-20180605150059470-9554394.png)

学习C\#的同学应该都知道DbContext是EF关联上下文所用的驱动，真对DbContext的解释如下：

<span style="color: #ff0000">DbContext： DbContext
实例表示工作单元和存储库模式的组合，可用来查询数据库并将更改组合在一起，这些更改稍后将作为一个单元写回存储区中。</span>

然后我们开始往下增加数据表的操作如下示例：

    DbSet：表示上下文中给定类型的所有实体的集合或可从数据库中查询的给定类型的所有实体的集合。

<div class="cnblogs_code">

``` 
    public class Context : DbContext
    {
        //base与Config中数据库连接字符串名称一样
        public Context() : base("name=MyStrConn") { }
        public DbSet<Studen> studen { get; set; }
        public DbSet<Teacher> seacher { get; set; }
    }
```

</div>

到目前映射数据库就添加完了（很简单吧）接下来让我们从程序处理，这大家应该都看得懂我是简历的MVC 所以方便省事直接仔仔action里面了
，其中using里面就是EF对数据库的操作，创建实体然后然后db添加到student里面，执行

    SaveChanges（）方法添加到数据库

<div class="cnblogs_code">

    public ActionResult Index()
            {
                using (var db = new Context())
                {
                    Studen stu = new Studen("123", 11);
                    db.studen.Add(stu);
                    db.SaveChanges();
                }
                return View();
            }

</div>

![](https://images2018.cnblogs.com/blog/814205/201806/814205-20180605152437896-21784794.png)

 接下来让我们进行查询,大家可以看到下面是读取到了这样我们添加表和数据就完成了。

![](https://images2018.cnblogs.com/blog/814205/201806/814205-20180605152657889-417129440.png)

### EF添加新表-迁移苦

 在上面我们添加了数据库，但是在项目中两个表肯定是不用够用的。那我们在添加一个表。我们添加一个Car类，然后吧Car添加到Context上下文读取中。

<div class="cnblogs_code">

``` 
  public class Car
    {
        public Car() { }
        [Key]
        public int Id { get; set; }

        public string Name { get; set; }

        public string Color { get; set; }

        public Car(string name, string color)
        {
            this.Name = name;
            this.Color = Color;
        }
    }
```

</div>

<div class="cnblogs_code">

``` 
  public class Context : DbContext
    {
        //base与Config中数据库连接字符串名称一样
        public Context() : base("name=MyStrConn") { }
        public DbSet<Studen> studen { get; set; }
        public DbSet<Teacher> seacher { get; set; }
        public DbSet<Car> car { get; set; }

    }
```

</div>

添加完之后，然后吧添加信息的字段改成Car类的字段

<div class="cnblogs_code">

``` 
 public ActionResult Index()
        {
            using (var db = new Context())
            {
                Car car = new Car("123", "RED");
                db.car.Add(car);
                db.SaveChanges();
            }
            return View();
        }
```

</div>

 

当我们再次执行启动上下文执行文件，可以看到以下提示：

![](https://images2018.cnblogs.com/blog/814205/201806/814205-20180605153350998-1257339821.png)

为毛？接下来看怎么解决

<span style="color: #ff0000">PM\> Enable-Migrations -Force</span>  
在程序集“EFCodeFirst”中找到多个上下文类型。  
要允许“EFCodeFirst.Models.Context”的迁移，请使用 Enable-Migrations
-ContextTypeName EFCodeFirst.Models.Context。  
要允许“EFCodeFirst.Models.ApplicationDbContext”的迁移，请使用 Enable-Migrations
-ContextTypeName EFCodeFirst.Models.ApplicationDbContext。  
<span style="color: #ff0000">PM\> Enable-Migrations -ContextTypeName
EFCodeFirst.Models.Context</span>  
正在检查上下文的目标是否为现有数据库...  
检测到使用数据库初始值设定项创建的数据库。已搭建与现有数据库对应的迁移“201806050721085\_InitialCreate”的基架。若要改用自动迁移，请删除
Migrations 文件夹并重新运行指定了 -EnableAutomaticMigrations 参数的
Enable-Migrations。  
已为项目 EFCodeFirst 启用 Code First 迁移。  
<span style="color: #ff0000">PM\> Add-Migration
AddSocialNameAndRefreshToken</span>  
正在为迁移“AddSocialNameAndRefreshToken”搭建基架。  
此迁移文件的设计器代码包含当前 Code First
模型的快照。在下一次搭建迁移基架时，将使用此快照计算对模型的更改。如果对要包含在此迁移中的模型进行其他更改，则您可通过再次运行“Add-Migration
AddSocialNameAndRefreshToken”重新搭建基架。  
<span style="color: #ff0000">PM\> Update-Database</span>  
指定“-Verbose”标志以查看应用于目标数据库的 SQL 语句。  
正在应用显式迁移: \[201806050824112\_AddSocialNameAndRefreshToken\]。  
正在应用显式迁移: 201806050824112\_AddSocialNameAndRefreshToken。  
正在运行 Seed
方法。

问题解决刷新下数据库看看我们的Car表存在否？

![](https://images2018.cnblogs.com/blog/814205/201806/814205-20180605162651302-598687921.png)

启动程序然后进行添加看看是否可以添加上数据，到这步就可以看到数据添加完成了。

![](https://images2018.cnblogs.com/blog/814205/201806/814205-20180605162738772-1152898408.png)

![](https://images2018.cnblogs.com/blog/814205/201806/814205-20180605162802987-2098984431.png)

 

如果小伙伴在测试过程中遇到了下面这个问题重启下SQL服务就好了。

![](https://images2018.cnblogs.com/blog/814205/201806/814205-20180605163125163-1748541462.png)

写了半天手累的狠，觉得觉得有用小伙伴们就点个赞吧。

 

