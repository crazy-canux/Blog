---
layout: post
title: Django之Module
comments: true
date: 2016-10-04 04:20:31
updated:
tags:
- python
- django
categories:
- Python
- Django
permalink:
---

# models.py

    from django.db import models

django模型是和数据库关联的，代码放在models.py，数据库信息在settings.py中统一配置即可。

每个模型对应数据库唯一的一张表，是django.db.models.Model的子类。

模型的每个属性都表示为数据库中的一个字段。

* 在项目的settings.py中激活应用，并设置数据库相关参数。

* 让django包含你的应用：

    告诉django你对模型做了更改，并且将这些更改存储为迁移文件polls/migrations/0001_initial.py:

        $python manage.py makemigrations polls

    可以查看迁移文件执行了哪些sql语句,并不真的在数据库执行：

        $python manage.py sqlmigrate polls 0001

    可以检查项目中的模型是否存在问题：

        $python manage.py check

    在数据库中创建模型,查找还没有被应用的迁移文件然后和数据库同步：

        $python manage.py migrate

# 模型的字段类型和字段选项

模型的每个属性都表示为数据库的一个字段,是Field子类的某个实例。

模型的字段还有一些选项。

模型字段类型和选项参考：

<http://python.usyiyi.cn/documents/django_182/ref/models/fields.html#common-model-field-options>

字段命名规则：
1. 不能是python的保留关键字。
2. 字段名中连续的下划线不能超过一个。

字段的类型都是Field类的子类：

每个字段都接受一个可选的位置参数(一般是第一个），叫字段的自述名,如果不指定就默认是字段名字（下划线换成空格）。

    AutoField
    # 默认django会每个模型添加一个自增主键字段,如果你显示设置一个自增主键字段就不会默认再添加,每个模型只能有一个主键字段。
    # id = models.AutoField(primary_key=True)
    BigIntegerField
    BinaryField
    BooleanField
    CharField
    CommaSeparatedIntegerField
    DateField
    DateTimeField
    DecimalField
    DurationField
    EmailField
    FileField
    FilePathField
    FloatField
    GenericIPAddressField
    IPAddressField
    ImageField
    IntegerField
    NullBooleanField
    PositiveIntegerField
    PositiveSmallIntegerField
    SlugField
    SmallIntegerField
    TextField
    TimeField
    URLField
    UUIDField

django定义了一系列字段类型描述数据库之间的关联:

这三个字段要求第一个参数是模型类，用verbose_name选项才能指定自述名。

    ForeignKey 定义多对一关系
    OneToOneField 定义一对一关系
    ManyToManyField 定义多对多关系

django定义的字段的通用的选项：

每个字段都有特定的选项，也有通用的选项,特定参数参考文档。

    null
    blank
    choices
    default
    help_text
    primary_key
    unique
    db_column
    db_index
    db_tablespace
    editable
    error_messages
    unique_for_date
    unique_for_month
    unique_for_year
    verbose_name
    validators

访问其它应用的模型,导入即可：

    from <other-aplication>.models import <module-name>

# 模型元数据

使用内部class Meta定义模型的元数据。

模型元数据是任何不是字段的数据，比如排序选项等。

模型的元数据选项：

<http://python.usyiyi.cn/translate/django_182/ref/models/options.html>

    from django.db import models
    class Ox(models.Model):
        horn_length = models.IntegerField()
        ...
        class Meta:
            ordering = ["horn_length"]
            verbose_name_plural = "oxen"

    abstract = True # 表示模型是抽象基类，数据库不会创建这个表.
    ordering # 对象的默认顺序。
    ...

# 模型的属性

每个类都要添加一个Manager实例，如果不显示添加，django就会默认添加objects属性，包含Manager实例。

Manager或object属性是模型进行数据库查询操作的接口,并用于从数据库获取实例。

    from django.db import models
    class Foo(models.Model):
        bar = models.Manager()

DoesNotExist属性：

django为每个类提供这个异常属性，可以捕获这个异常。

# 模型的方法

模型中可以自定义方法，可以使用预定义的自动生成的方法，也可以覆盖预定义的方法。

预定义方法参考：

<http://python.usyiyi.cn/translate/django_182/ref/models/instances.html#model-instance-methods>

预定义方法__str__()和__unicode__():

python3中所有字段都是unicode，只需要str方法，python2中用unicode方法。

这段代码兼容python2和python3.

python_2_unicode_compatible是一个用于类的装饰器，在类中定义__str__并返回文本.

    # -*- encoding: utf-8 -*-
    from __future__ import unicode_literals
    from django.db import models
    from django.utils.encoding import python_2_unicode_compatible

    @python_2_unicode_compatible
    class Question(models.Model):
        title = models.CharField('title', max_length=256)
        ...
        def __str__(self):
            return self.title

# 查询集

查询集参考QuerySet类的方法：

<http://python.usyiyi.cn/translate/django_182/ref/models/querysets.html#queryset-api>

查询集求值：
1. 迭代
2. 切片
3. 序列化
4. repr()
5. len()
6. list()
7. bool()

创建一个对象：

    q = Question(question_text='content', pub_date='date')
    q.save()

    q = Question(question_text='content')
    q.pub_date='date'
    q.save()

    Question.objects.create(question_text="content", pub_date='date')

    # 防止重复,不存在就创建，返回(object, True),存在返回(object, False)
    Question.objects.get_or_create(question_text='content', pub_date='date')

获取对象：

    # 获取所有
    Question.objects.all()
    # 切片获取部分
    Question.objects.all()[:10]
    # 获取单个
    Question.objects.get(question_text='content')
    # 过滤
    Question.objects.filter(**kwargs)
    Question.objects.exclude(**kwargs)

查询集的链式处理：

    Question.objects.all().exists()
    Question.objects.all().order_by('name')
    Question.objects.filter(**kwargs).filter(**kwargs)


