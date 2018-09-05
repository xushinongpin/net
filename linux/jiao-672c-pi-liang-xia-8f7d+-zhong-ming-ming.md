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

备注： 断点续传 要加多个 -C 

```
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/001.mp3 -O 001_1234567.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/002.mp3 -O 002_搬迁.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/003.mp3 -O 003_半斤八两.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/004.mp3 -O 004_保姆.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/005.mp3 -O 005_比你高一点.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/006.mp3 -O 006_补镜头.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/007.mp3 -O 007_裁缝.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/008.mp3 -O 008_超级球迷.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/009.mp3 -O 009_成语集.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/010.mp3 -O 010_打电话.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/011.mp3 -O 011_打假难.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/012.mp3 -O 012_打破常规.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/013.mp3 -O 013_电灯胆.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/014.mp3 -O 014_电脑睇相.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/015.mp3 -O 015_电视迷.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/016.mp3 -O 016_罚得好.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/017.mp3 -O 017_肥仔米.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/018.mp3 -O 018_狗咬狗.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/019.mp3 -O 019_广东各地方言.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/020.mp3 -O 020_广告大王.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/021.mp3 -O 021_广州话趣.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/022.mp3 -O 022_好的研究.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/023.mp3 -O 023_候机室即景.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/024.mp3 -O 024_祸害.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/025.mp3 -O 025_家庭教师.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/026.mp3 -O 026_借电话.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/027.mp3 -O 027_老字的研究.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/028.mp3 -O 028_乐业安居.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/029.mp3 -O 029_旅游会.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/030.mp3 -O 030_怕怕.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/031.mp3 -O 031_如此后生.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/032.mp3 -O 032_生神仙看相.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/033.mp3 -O 033_刷鞋主任.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/034.mp3 -O 034_四代同堂.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/035.mp3 -O 035_特别嘉宾.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/036.mp3 -O 036_特殊约会.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/037.mp3 -O 037_无牌医生.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/038.mp3 -O 038_笑口常开听我唱.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/039.mp3 -O 039_新潮家长.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/040.mp3 -O 040_验视力.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/041.mp3 -O 041_一对一.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/042.mp3 -O 042_有法可依.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/043.mp3 -O 043_诸家语言.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/044.mp3 -O 044_猪年壁合.mp3
wget _C http://down01.pingshu8.com:8000/2/xs/huangjunying/045.mp3 -O 045_自作自受.mp3
```



