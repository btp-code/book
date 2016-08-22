#第一個網頁
首先我們先打```jonah1005:~/workspace (master) $ ls```
會看到```README.md  clhs_web_workshop/  db.sqlite3  manage.py*``` 因為我project取的名子叫做clhs_web_workshop所以我看到的是這個。
```$ python manage.py startapp pages```
這個指令是請django幫忙新增一個新的app，我們取名叫做pages用來放一些雜七雜八的網頁（任何沒有明確分類的網頁，我們都放在這裡）。
其實只是幫忙開一個新資料夾，再放一些檔案進去。
接著我們進去這個資料夾新增一個叫做templates的資料夾。
```cd pages
mkdir templates```也可以直接在cloud9左邊那個格子按右鍵新增資料夾。然後在pages/templates這個資料夾裡新增一個home.html。至於這個html要放什麼就請大家先回去複習一下[html](../html_basic_guide.md)
如果你還沒有看可以先隨便放一個，我們先學要怎麼把它放到server上，**但是記得這篇看完要回去學html。**

```html
<!DOCTYPE html>
<html>
  <head>
    <!-- BootStrap-->
    
    <link rel="stylesheet" href="http://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css">
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css" integrity="sha384-1q8mTJOASx8j1Au+a5WDVnPi2lkFfwwEAa8hDDdjZlpLegxhjVME1fgjWPGmkzs7" crossorigin="anonymous">
    <title>Home Page</title>
  </head>
  
  <body>
    <div class="container-fluid">
      <div class="row content">
	<div class="col-sm-3 sidenav">
	  <h4>Learning by Doing</h4>
	  <ul class="nav nav-pills nav-stacked">
            <li><a>HI</a></li>

	  </ul><br>
	</div>
  </body>
</html>
```

接下來，我們還要跟django說我們現在有一個新的app，所以我們打開clhs_web_workshop/settings.py 找到INSTALLED_APPS 這邊。

```python
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
] ```

這些是django裡面預設已經安裝好的app，先不要去改它。我們新增'pages'在裡面，如果你剛剛startspp的時候不是叫pages那要記得自己換名子。
```python
LED_APPS = [
    'pages',
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]
```
記得前後面要用單引號框住，還要加逗點。

接著在打開pages/views.py  _view是什麼下一章會說_
應該會看到一個幾乎是空空的檔案。我們直接換成

```python
from django.shortcuts import render
def home(request):
    return render(request,'home.html')

# Create your views here.

```
到底這在做什麼有點複雜，我們下次再說，總而言之它做的就是把home.html這個檔案丟出去。（django預設會在templates這個資料夾裡面找）

存檔之後，接著我們打開clhs_web_workshop/urls.py，找到

```python
urlpatterns = [
    url(r'^admin/', admin.site.urls),
]
```
這代表如果連到網址/admin會交給（admin.site.urls）處理，這是django預設的後台管理網站，是很好用的東西，不過暫時用不到，先不管它。
我們先在這個之上加上

```python
from pages.views import home

```

這是要從pages/views找到 home這個函數。
接著我們要把連到我們網址的人指向home這個view。
我們在urlpatterns裡面新增home，變成

```python
urlpatterns = [
    url(r'^admin/', admin.site.urls),
    url(r'^$',home),
]

```
稍微解釋一下，django會把網址是 '^$'的人指向home這個view. 這個 ＄ 符號代表這個字串已經結束了。
_試試看把＄拿掉，跑起網站試試看，改改網址試試看_
存檔之後，把server跑起來（要用run project 或是 ```python manage.py runserver 0.0.0.0:8080```)都可以，現在在連去我的網址 https://clhs-web-workshop-jonah1005.c9users.io/。


雖然我們現在對DJANGO還是一知半解，但反正他已經可以跑了，接下來就是認真寫html (?!)就可以讓大家看到你的網頁拉！
我們下一章會解釋DJANGO，剛剛的app，views，urls，templates到底發生什麼事，可能會有點複雜，可以先跳過，等學完javascript對寫程式有更了解再回來看。
~~~~

