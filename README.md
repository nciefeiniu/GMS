# GMS
Django框架开发的垃圾管理统计系统

## 二.功能列表:

### 1.用户投放垃圾
	 1.用户扫描二维码
	 2.用户投放垃圾时,选择垃圾种类,垃圾袋规格,数量
	 3.用户可输入积分凭证,领取积分

### 2.点位地图
	 1.导入腾讯地图,在地图上根据经纬度进行点位标注,并设置点位点击事件
	 2.添加点位:管理员可以直接在地图上点击点然后得到经纬度,输入点位名称即可添加点位
	 3.点位管理:可以删除点位和生成点位二维码
	 4.阈值设置:管理员可以设置点位的阈值,当实时数据超过阈值后,地图点位将变为红色报警

### 3.实时数据
	 1.根据地图的点位,管理员可以任意点击点位查看实时数据
	 2.数据展示:数据将以柱状图显示,JS库的为百度开源的echarts
	 3.实时数据页面,管理员可以清理点位数据,汇总到当天该点位的数据历史记录中
	 4.可以根据下拉框选择其他点位,自动跳转至其他点位实时数据

### 4.历史数据
	 1.历史数据页面默认为前一天的所有点位的数据总和,以柱状图显示
	 2.日期选择:可以选择指定日期段数据,默认为前一天
	 3.数据视化:可以选择柱状图,折线图,饼图,默认为柱状图
	 4.点位选择:可以选择各个点位的历史数据,默认为所有点位
	 5.以上三种选项可以随意搭配

### 5.管理员
	 1.系统可以游客访问,但若涉及到数据的改动,则需要管理员登录
	 2.管理员可以删除,添加点位,设置点位阈值.
	 3.管理可清理垃圾,将点位数据清空汇总到当天点位历史数据


## 三. 项目启动

### 1. 安装依赖

```shell
pip install -r requirements.txt
```

### 2. 创建数据库，并修改数据库配置

请先自行创建数据库，用你熟悉的方式！！！(注意：Mysql请使用 5.7及其以上的版本)

请修改 `mycompetition/settings.py` 文件中的 76 到85行

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',  
        'NAME': 'competition',  # 数据库名
        'HOST': '127.0.0.1',  # 数据库地址
        'PASSWORD': '123456',  # 数据库密码
        'PORT': 3306,  # 数据库端口
        'USER': 'root',  # 数据库账号
    }
}
```

### 3. 同步数据库

```shell
python manage.py makemigrations
python manage.py migrate
```

### 4. 运行服务

```shell
python manage.py runserver 
```

用浏览器打开即可