# Lims__report_uploader’s documentation

## 简介
*Lims_report_uploader*是用于将结题报告从天津或南京集群传到lims系统的工具.

## 集群路径

天津集群
```
/PUBLIC/software/MICRO/Anaconda/anaconda3/bin/python /TJPROJ1/MICRO/lidanqing/lims_report_upload/Lims_report_uploader -h
```
南京集群
```
/NJPROJ2/MICRO/share/software/Anaconda/anaconda3/bin/python  /NJPROJ2/MICRO/PROJ/lidanqing/lims_report_upload/Lims_report_uploader -h
```

## 使用方法

* 首先,需要通过’init’命令初始化配置自己的lims账号和密码,此后,使用不需要再重新配置.
* 使用’upload’命令来上传结题报告;
* 如果不清楚SOP编号,可通过’search’命令查询可选SOP

```
$ /PUBLIC/software/MICRO/Anaconda/anaconda3/bin/python /TJPROJ1/MICRO/lidanqing/lims_report_upload/Lims_report_uploader -h
usage: Lims_report_uploader [-h] [-V] {init,search,upload} ...

Description:
这个脚本用于将结题报告从集群传到lims系统中.
    1 首先,需要通过’init’命令初始化配置lims账号和密码;
    2 上传结题报告使用’upload’命令;
    3 如果不清楚SOP编号,可通过’search’命令查询可选SOP

author: lidanqing@novogene.com
version:  1.1.1

positional arguments:
  {init,search,upload}  sub-command
    init                开始初始化lims账户信息
    search              查询项目SOP
    upload              上传报告

optional arguments:
  -h, --help            show this help message and exit
  -V, --version         show program's version number and exit

Example:
            Lims_report_uploader init -h
            Lims_report_uploader search -h
            Lims_report_uploader upload -h

```


### 初始化lims账号信息
初始化lims账号信息直接使用*init*命令
```
/PUBLIC/software/MICRO/Anaconda/anaconda3/bin/python /TJPROJ1/MICRO/lidanqing/lims_report_upload/Lims_report_uploader init
```
查看帮助信息可加上`-h`参数:
```
$ /PUBLIC/software/MICRO/Anaconda/anaconda3/bin/python /TJPROJ1/MICRO/lidanqing/lims_report_upload/Lims_report_uploader init -h 
usage: Lims_report_uploader init [-h]

Description:
    ’init’命令用于初始化配置lims账号和密码等信息.命令行中不用给其他任何参数.

optional arguments:
  -h, --help  show this help message and exit

Example:
    Lims_report_uploader init

```


### SOP编号查询

通过项目分期编号,可以使用`search`命令查询可选的SOP

```
$ /PUBLIC/software/MICRO/Anaconda/anaconda3/bin/python /TJPROJ1/MICRO/lidanqing/lims_report_upload/Lims_report_uploader search -s P101SC18072239-01-F002 
	SOP_code	SOP方法
############################################################
	SOPMC00038	ANI分析（每株）
	SOPMC00039	cgMLST
	SOPMC00040	QC
	SOPMC00041	比较基因组分析（SNP／InDel／SV检测及注释）
	SOPMC00042	比较基因组分析（共线性）
	SOPMC00043	标准分析
	SOPMC00044	群体进化分析（core-pan基因分析）
	SOPMC00045	群体进化分析（基因家族）
	SOPMC00046	群体进化分析（进化选择压力分析）
	SOPMC00047	群体进化分析（群体地理传播途径预测）
	SOPMC00048	群体进化分析（群体进化分歧时间预测）
	SOPMC00049	群体进化分析（群体进化树分析）
	SOPMC00050	转座子分析（基于蛋白+核酸序列）
	SOPMC00051	转座子分析（基于蛋白序列）
	SOPMC00052	转座子分析（基于核酸序列）

```
查看帮助信息可使用`-h`参数:
```
$ /PUBLIC/software/MICRO/Anaconda/anaconda3/bin/python /TJPROJ1/MICRO/lidanqing/lims_report_upload/Lims_report_uploader search -h
usage: Lims_report_uploader search [-h] -s STAGECODE

Description:
    提供项目分期编号,使用'search'命令,可查询此产品可选SOP.

optional arguments:
  -h, --help            show this help message and exit
  -s STAGECODE, --stage_code STAGECODE
                        分期编号

Example:
    Lims_report_uploader search -s  P101SC18072239-01-F002
    Lims_report_uploader search --stage_code  P101SC18072239-01-F002
```


### 报告上传

