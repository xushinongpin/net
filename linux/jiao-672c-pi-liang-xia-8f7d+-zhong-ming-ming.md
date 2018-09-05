最近想听黄俊英的相声，网上找下下载，然后遇到国内叽叽歪歪的渣渣文章看的一脸懵逼，最后在国外找到了好文章好建议

一： 建立下载脚本并写入下载内容

```
文件： huangjunying.sh
内容：

wget http://down01.pingshu8.com:8000/2/xs/huangjunying/021.mp3 -O 广州话趣.mp3
wget http://down01.pingshu8.com:8000/2/xs/huangjunying/022.mp3 -O 好的研究.mp3
wget http://down01.pingshu8.com:8000/2/xs/huangjunying/023.mp3 -O 候机室即景.mp3
wget http://down01.pingshu8.com:8000/2/xs/huangjunying/024.mp3 -O 祸害.mp3
wget http://down01.pingshu8.com:8000/2/xs/huangjunying/025.mp3 -O 家庭教师.mp3
wget http://down01.pingshu8.com:8000/2/xs/huangjunying/026.mp3 -O 借电话.mp3
wget http://down01.pingshu8.com:8000/2/xs/huangjunying/027.mp3 -O 老字的研究.mp3
wget http://down01.pingshu8.com:8000/2/xs/huangjunying/028.mp3 -O 乐业安居.mp3
wget http://down01.pingshu8.com:8000/2/xs/huangjunying/029.mp3 -O 旅游会.mp3
wget http://down01.pingshu8.com:8000/2/xs/huangjunying/030.mp3 -O 怕怕.mp3
wget http://down01.pingshu8.com:8000/2/xs/huangjunying/031.mp3 -O 如此后生.mp3
wget http://down01.pingshu8.com:8000/2/xs/huangjunying/032.mp3 -O 生神仙看相.mp3
wget http://down01.pingshu8.com:8000/2/xs/huangjunying/033.mp3 -O 刷鞋主任.mp3
wget http://down01.pingshu8.com:8000/2/xs/huangjunying/034.mp3 -O 四代同堂.mp3
wget http://down01.pingshu8.com:8000/2/xs/huangjunying/035.mp3 -O 特别嘉宾.mp3
wget http://down01.pingshu8.com:8000/2/xs/huangjunying/036.mp3 -O 特殊约会.mp3
wget http://down01.pingshu8.com:8000/2/xs/huangjunying/037.mp3 -O 无牌医生.mp3
wget http://down01.pingshu8.com:8000/2/xs/huangjunying/038.mp3 -O 笑口常开听我唱.mp3
wget http://down01.pingshu8.com:8000/2/xs/huangjunying/039.mp3 -O 新潮家长.mp3
wget http://down01.pingshu8.com:8000/2/xs/huangjunying/040.mp3 -O 验视力.mp3
wget http://down01.pingshu8.com:8000/2/xs/huangjunying/041.mp3 -O 一对一.mp3
wget http://down01.pingshu8.com:8000/2/xs/huangjunying/042.mp3 -O 有法可依.mp3
wget http://down01.pingshu8.com:8000/2/xs/huangjunying/043.mp3 -O 诸家语言.mp3
wget http://down01.pingshu8.com:8000/2/xs/huangjunying/044.mp3 -O 猪年壁合.mp3
wget http://down01.pingshu8.com:8000/2/xs/huangjunying/045.mp3 -O 自作自受.mp3
```

二： 给文件拥有执行权限 775

```
chmod 775 huangjunying.sh
```

三：执行文件 ./huangjunying.sh

等待下载完成即可

