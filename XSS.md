# XSS1
---------
## Code analysis

Vulnerability code is located `destoon\admin\setting.inc.php` 64 to 139 lines 
First looking at `destoon\admin.php` 56 to 60 lines
![](https://github.com/AvaterXXX/DESTOON/blob/master/image/XSS1-1.png)
When the module parameter is not POST, the default is destoon. it will inclusion a file, and the file is derived from the file parameter, so we go to the POST package to view it.
![](https://github.com/AvaterXXX/DESTOON/blob/master/image/XSS1-2.png)
You can see that the POST file parameter is set, and the splicing with the source code can get the include file as `/admin/setting.inc.php`
![](https://github.com/AvaterXXX/DESTOON/blob/master/image/XSS1-3.png)

## Vulnerability display
![](https://github.com/AvaterXXX/DESTOON/blob/master/image/XSS1-4.png)
![](https://github.com/AvaterXXX/DESTOON/blob/master/image/XSS1-5.png)

# XSS2
---------
Do not do too much explanation, the source code is not filtered
![](https://github.com/AvaterXXX/DESTOON/blob/master/image/XSS2-1.png)
![](https://github.com/AvaterXXX/DESTOON/blob/master/image/XSS2-2.png)
Visit the homepage
![](https://github.com/AvaterXXX/DESTOON/blob/master/image/XSS2-3.png)
Click below for details（详细介绍）
![](https://github.com/AvaterXXX/DESTOON/blob/master/image/XSS2-4.png)


# XSS3
---------
## Code analysis

Also in file `destoon\admin.php` 
![](https://github.com/AvaterXXX/DESTOON/blob/master/image/XSS3-1.png)
When the module parameter is not POST, the default is destoon. it will inclusion a file, and the file is derived from the file parameter, so we go to the POST package to view it.
![](https://github.com/AvaterXXX/DESTOON/blob/master/image/XSS3-2.png)
You can see that the POST file parameter is category, and the splicing with the source code can get the include file as `/admin/category.inc.php`
![](https://github.com/AvaterXXX/DESTOON/blob/master/image/XSS3-3.png)
You can see the case operation of the incoming action here. The action in the current data packet is edit, but after analyzing add or copy, there is also a problem. I will not analyze it here, only analyze the edit branch.
Code in 76 to 90 lines
![](https://github.com/AvaterXXX/DESTOON/blob/master/image/XSS3-4.png)
It can be seen that when the action is edit, the judgment is first made to determine whether the classification name is empty and equal to catid, and the judgment based on category[catname] and category[parentid] are both incoming data.
![](https://github.com/AvaterXXX/DESTOON/blob/master/image/XSS3-5.png)

## Vulnerability display
![](https://github.com/AvaterXXX/DESTOON/blob/master/image/XSS3-6.png)
![](https://github.com/AvaterXXX/DESTOON/blob/master/image/XSS3-7.png)
