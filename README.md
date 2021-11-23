# Book_List_api
Simple Rest API with Flask of to get list and data of top 100 Arabic Novels in all times

## Code-Dependencies

All Dependencies in requirements.txt file to install all of them using pip just

1. go to the directory where script and requirements.txt is located.

2. activate your virtualenv.

3. run in `pip install -r requirements.txt` in your shell.

   

## CRUD Operations 

**Note1:** this API return JSON format so if you test it using browser you will need **JSONView extension**: [Chrome](https://chrome.google.com/webstore/detail/jsonview/chklaanhfefbnpoihckbnefhakgolnmc/related) - [Firefox](https://addons.mozilla.org/en-US/firefox/addon/jsonview/) or use **POSTMAN** like examples

**Note2:** This API uploaded on **[heroku](https://editxl.herokuapp.com/novels)** which i will use in this **Examples**



## Use `./novels`  [GET, POST]

#### GET

#### https://editxl.herokuapp.com/novels

```json
[
    {
        "order": 1,
        "novel_name": "الثلاثية ",
        "novel_url": "https://ar.wikipedia.org/wiki/الثلاثية_(نجيب_محفوظ)",
        "author_name": "نجيب محفوظ ",
        "author_url": "https://ar.wikipedia.org/wiki/نجيب_محفوظ",
        "country_name": " مصر ",
        "country_url": "https://ar.wikipedia.org/wiki/مصر"
    },
    {
        "order": 2,
        "novel_name": "البحث عن وليد مسعود ",
        "novel_url": "https://ar.wikipedia.org/wiki/البحث_عن_وليد_مسعود_(رواية)",
        "author_name": "جبرا إبراهيم جبرا ",
        "author_url": "https://ar.wikipedia.org/wiki/جبرا_إبراهيم_جبرا",
        "country_name": " فلسطين ",
        "country_url": "https://ar.wikipedia.org/wiki/فلسطين"
    },
    .
    .
    {
    {
        "order": 106,
        "novel_name": "مدن الملح خماسية ",
        "novel_url": "https://ar.wikipedia.org/wiki/مدن_الملح",
        "author_name": "عبد الرحمن منيف ",
        "author_url": "https://ar.wikipedia.org/wiki/عبد_الرحمن_المنيف",
        "country_name": " السعودية ",
        "country_url": "https://ar.wikipedia.org/wiki/السعودية"
    }
]
```



#### POST : `["order : 0" to append the list], ["order : num" to insert in this order]  `

```json
{
    "order": 12,
    "novel_name": "كتابي",
    "novel_url": "https://www.mybook.com",
    "author_name": "محمد هاشم",
    "author_url": "https://ar.wikipedia.org/wiki/محمدهاشم",
    "country_name": " فلسطين ",
    "country_url": "https://ar.wikipedia.org/wiki/فلسطين"
}
```

When **POST new novel** to the list it if **order != 0** the new novel will take **the old place** and all **Novels below** will increase it's **order +1**.

![screen](/readme_screens/screen.png)

## Use `./novels/<order:int>`  [GET, PUT, DELETE]

#### GET 

#### https://editxl.herokuapp.com/novels/1

```json
{
    "order": 1,
    "novel_name": "الثلاثية ",
    "novel_url": "https://ar.wikipedia.org/wiki/الثلاثية_(نجيب_محفوظ)",
    "author_name": "نجيب محفوظ ",
    "author_url": "https://ar.wikipedia.org/wiki/نجيب_محفوظ",
    "country_name": " مصر ",
    "country_url": "https://ar.wikipedia.org/wiki/مصر"
}
```



#### PUT : edit by order

#### https://editxl.herokuapp.com/novels/1

**EX**: if you want to edit order 1 Novel data 

```json
{
    "order": 1,	 //you can't edit order here even if edited will still = the URL novels/<order>
    "novel_name": "الايام",
    "novel_url": "https://ar.wikipedia.org/wiki/الايام",
    "author_name": "طه حسين",
    "author_url": "https://ar.wikipedia.org/wiki/طه_حسين",
    "country_name": " مصر ",
    "country_url": "https://ar.wikipedia.org/wiki/مصر"
}
```



#### DELETE: Delete Novel by it's Order

#### https://editxl.herokuapp.com/novels/1

**Note :** list will reorder itself after deleting to be correct

