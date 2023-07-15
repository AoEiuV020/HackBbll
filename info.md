
activity只有一个，  
com.xx.blbl.ui.MainActivity  
其他都是fragment，  
设置保存在 /data/data/com.xx.blbl/shared_prefs/BLBL.xml  

弹幕使用的库是，KwaiAppTeam/AkDanmaku  
弹幕大小的处理是switch，这，有必要吗，  

### 改弹幕大小，让不同设备显示效果尽量接近，  
jadx-gui打开直接搜“ > 25.0f) {”，定位到最终渲染弹幕的位置，  
改成自己算，getHeight, 1080p算三倍，其他按比例算，  


### 改字幕大小，直接翻倍，  
jadx-gui打开搜索字幕控件id, text_subtitle,  
得到fragment,  
设置字幕大小后加上，读取字幕大小乘以2f再设置进去，
这一步读取不必要，主要是旧版没有设置字幕大小时用的，现在复制沿用，

### 改字幕重力，居中，
在上面改字幕大小后加上重力设置就好，

### 生成patch文件，
使用git format-patch命令生成，  
反编译后先git init初始化一个git项目，后续修改生成patch再用脚本script/apply导入就可以编译，  

