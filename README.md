# Lims__report_uploader’s documentation

## 简介
`Lims_report_uploader`是用于将结题报告从天津或南京集群传到lims系统的工具.

## 集群路径

天津集群
```
/TJPROJ1/MICRO/lidanqing/lims_report_upload/Lims_report_uploader -h
或
/PUBLIC/software/MICRO/Anaconda/anaconda3/bin/python /TJPROJ1/MICRO/lidanqing/lims_report_upload/Lims_report_uploader -h
```
南京集群
```
/NJPROJ2/MICRO/PROJ/lidanqing/lims_report_upload/Lims_report_uploader -h
或
/NJPROJ2/MICRO/share/software/Anaconda/anaconda3/bin/python  /NJPROJ2/MICRO/PROJ/lidanqing/lims_report_upload/Lims_report_uploader -h
```

## 使用方法

* 首先,需要通过`init`命令初始化配置自己的lims账号和密码,此后,使用不需要再重新配置.
* 使用`upload`命令来上传结题报告;
* 如果不清楚SOP编号,可通过`search`命令查询可选SOP

```
$ /TJPROJ1/MICRO/lidanqing/lims_report_upload/Lims_report_uploader -h
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
初始化lims账号信息直接使用`init`命令
```
/TJPROJ1/MICRO/lidanqing/lims_report_upload/Lims_report_uploader init
```
查看帮助信息可加上`-h`参数:
```
$ /TJPROJ1/MICRO/lidanqing/lims_report_upload/Lims_report_uploader init -h 
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
$ /TJPROJ1/MICRO/lidanqing/lims_report_upload/Lims_report_uploader search -s P101SC18072239-01-F002 
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
$ /TJPROJ1/MICRO/lidanqing/lims_report_upload/Lims_report_uploader search -h
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
报告上传是此程序的主要功能. 需要配置的参数相对较多:
*  -i file, --input file                    集群中报告文件的路径,'.zip', '.tar.gz', '.tar', '.gz', '.rar'等类型的压缩文件
*  -s STAGECODE, --stage_code STAGECODE     项目分期编号
*  -r {Q,M,R}, --report_type {Q,M,R}        结题报告类型,例如:QC报告、mapping报告、结题报告.分别对应于{Q,M,R}.
*  -n int, --sample_num int                 样本个数
*  -d num, --total_data num                 总数据量
*  --SOP SOP                                SOP编号,多个SOP编号的话以英文字符逗号分开,like:"SOPMC00038,SOPMC00039".配置前可以用过'search'命令查询可选SOP.
*  -m REMARK, --remark REMARK               备注信息.可为空.

Example:
```
    Lims_report_uploader upload -i P101SC18072239-01-B1-3.zip -s P101SC18072239-01-F002 -r Q -n 4 -d 2 --SOP SOPMC00039,SOPMC00040 -m "正常"
    
    Lims_report_uploader upload --input P101SC18072239-01-B1-3.zip --stage_code P101SC18072239-01-F002 --report_type Q --sample_num 4 --total_data 2 --SOP SOPMC00039,SOPMC00040 --remark "正常"

```

查看帮助信息可使用`-h`参数:
```
$ /TJPROJ1/MICRO/lidanqing/lims_report_upload/Lims_report_uploader  upload -h
usage: Lims_report_uploader.py upload [-h] -i file -s STAGECODE -r {Q,M,R} -n
                                      int -d num --SOP SOP [-m REMARK]

Description:
    'upload'是本脚本最核心的功能,用于上传结题报告.

optional arguments:
  -h, --help            show this help message and exit
  -i file, --input file
                        集群中报告文件的路径,'.zip', '.tar.gz', '.gz', '.rar'等类型的压缩文件
  -s STAGECODE, --stage_code STAGECODE
                        分期编号
  -r {Q,M,R}, --report_type {Q,M,R}
                        结题报告类型,例如:QC报告、mapping报告、结题报告
  -n int, --sample_num int
                        样本个数
  -d num, --total_data num
                        总数据量,以G为单位
  --SOP SOP             SOP编号,多个SOP编号的话以英文字符逗号分开,like:"SOPMC00038,SOPMC00039".
                        配置前可以用过'search'命令查询可选SOP.
  -m REMARK, --remark REMARK
                        备注信息.可为空

Example:
    Lims_report_uploader upload -i P101SC18072239-01-B1-3.zip -s P101SC18072239-01-F002 -r Q -n 4 -d 2 --SOP SOPMC00039,SOPMC00040 -m "正常"
    
    Lims_report_uploader upload --input P101SC18072239-01-B1-3.zip --stage_code P101SC18072239-01-F002 --report_type Q --sample_num 4 --total_data 2 --SOP SOPMC00039,SOPMC00040 --remark "正常"

```







