
#要怎用DJANGO寫網頁
在了解網頁框架之後，我們來動手做一個自己的範例。不過在此之前讓我們先來介紹一下*model*。
##DJANGO model
還記得上一章```View```那邊說過有很多東西都是存在資料庫裡的嗎？譬如說你FB發文之後會送到後端伺服器存起來。View的工作是把網頁的資料接（存）起來或找出來。而model的就是決定要怎麼存，以及存在哪裡。

##瀏覽人次
先讓我們做第一個model。請先打開pages裡面的models.py，如果沒錯應該會看到

```python
from __future__ import unicode_literals

from django.db import models


# Create your models here.

```
我們在裡面新增一個新的model，改成這樣

```python
from __future__ import unicode_literals

from django.db import models
class Visit(models.Model):
    times = models.IntegerField()


# Create your models here.

```

現在我們有一個叫做Visit的model裡面有一筆資料叫做 ```times```了。這裡的```models.IntegerField()```表示這個times的資料要用```integer```存，代表這筆資料會是整數。假如```models.CharField(max_length=30)```就代表要存一個不超過30個字的字串。

##規則
剛剛說models決定要存什麼，存在哪，而我們寫的models.py寫完只是把規則寫好，接下來我們要讓django按照這個規則建立一筆資料。
我們回到command line那邊打
```python manage.py makemigrations```
然後再打
```python manage.py migrate```
現在，在你的資料庫裡面有一欄可以存```Visit```了。

##資料庫
如果搞不太懂存資料就存資料，為什麼這麼麻煩還要makemigrations，我們在這邊稍微解釋一下，如果沒有疑惑的人（或現在不想知道太多）可以直接跳到下面去。

大家可以把資料庫想成一個倉庫，或是圖書館。裡面有很多櫃子，櫃子裡面又有很多書。剛剛那個例子用瀏覽人數這種東西，一個網頁只需要一個值，所以大家可能不是很能理解為什麼要這麼麻煩。大家可以想像一下FB，用戶有這麼多，如果你就只有一個很大的箱子，把所有資料都丟在裡面，那效率一定會很差。```model```是DJANGO跟資料庫溝通的地方。*用資料庫這個字可能會有點混淆，或說是資料庫管理系統，它是一個獨立的程式*。DJANGO，你什麼設定都不改，預設是用```sqlite```，是一個輕量化的資料庫，用來測試網頁，或是寫小網頁很適合，要怎麼有快速的存資料找資料其實是很大的學問，每一種資料庫有自己的優缺點，但這邊就先不深究。

上一步```python manage.py makemigrations```就像是在這個圖書館放一個書櫃，以後DJANGO要用這個資料就會去```Visit```這個櫃子找，當然現在這個櫃子是空的我們下一步要放資料進去
##DJANGO shell
我們要在visit那個櫃子裡放第一筆資料，現在請在terminal那邊打```python manage.py shell```，進到django的shell。
再來輸入
```python
from pages.models import Visit
first=Visit()
first.times=0
first.save()
```
[](first_model_01.png)
[](first_model_02.png)
這邊是先新增一個資料，把```times```設成0，然後存起來。現在你已經有第一筆```Visit```的資料了，以後就可以用這個當作計數器了。

現在要離開DJANGO shell只要按Ctrl+D就可以了。
##瀏覽人數
現在前置作業算是做好了，現在開始幫網站加瀏覽人數了。
我們先到pages/views.py裡面改一下我們的view。

```python
def home(request):
    visit_model=Visit.objects.get(pk=1)
    visit_model.times+=1
    visit_model.save()
    return render(request,'home.html',{"visit_template":visit_model.times});

```
這裡我們幫home加上瀏覽次數，每次有人呼叫的這個view時，它會從Visit這個書櫃裡面拿第一本書，把裡面的times加一，再把它傳給template。這裡注意一下 ```render(request,'home.html',{"visit_template":visit_model.times})```代表，你要傳給template的東西是```visit_model.times```而template可以用```"visit_template"```就可以拿到這個值。
接這再改一下```pages/templates/home.html``` 

```html
 <head>
    <!-- BootStrap-->
    
    <link rel="stylesheet" href="http://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css">
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css" integrity="sha384-1q8mTJOASx8j1Au+a5WDVnPi2lkFfwwEAa8hDDdjZlpLegxhjVME1fgjWPGmkzs7" crossorigin="anonymous">
    <title>Home Page --{{visit_template}}</title>
  </head>
  
```
把head換成這個。可以注意一下title那邊的```{{visit_template}}```剛剛view傳過來就是這個名子，之後在只要用兩個大括弧刮起來，就可以拿到這個值。
[](first_model_03.png)
現在runserver之後，打開首頁就能看到標題有數字了對吧，重整幾次看到它有往上跑，就對囉。
