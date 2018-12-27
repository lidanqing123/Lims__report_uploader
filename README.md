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

   1. 首先,需要通过’init’命令初始化配置自己的lims账号和密码,此后,使用不需要再重新配置.
   2. 使用’upload’命令来上传结题报告;
   3. 如果不清楚SOP编号,可通过’search’命令查询可选SOP

```
$ /PUBLIC/software/MICRO/Anaconda/anaconda3/bin/python /TJPROJ1/MICRO/lidanqing/lims_report_upload/Lims_report_uploader -h
usage: Lims_report_uploader.py [-h] [-V] {init,search,upload} ...

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
            Lims_report_uploader.py init -h
            Lims_report_uploader.py search -h
            Lims_report_uploader.py upload -h

```


### 初始化lims账号信息


### SOP编号查询


### 报告上传

