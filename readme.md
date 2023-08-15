<h4>基于Nuclei扫描模板的POC仓库集成</h4>

```
   __ ___   ___   __          ____ 
  / // / | / / | / /__ ___ __/ / /_
 / _  /| |/ /| |/ / _ `/ // / / __/ 2023.HVV
/_//_/ |___/ |___/\_,_/\_,_/_/\__/  BY.HUFEI
                                   
```

<p align="center">
<a href="https://opensource.org/licenses/MIT"><img src="https://img.shields.io/badge/license-MIT-_red.svg"></a>
<a href="https://github.com/asaotomo/fofamap/issues"><img src="https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat"></a>
</p>

### 0x01. 项目说明
借2023HVV之机梳理【护网高利用率POC】并集成Nuclei仓库，针对单资产漏洞一键检测工具参次不齐问题。
具体参考：
- [PeiQi-WIKI-Book](https://github.com/PeiQi0/PeiQi-WIKI-Book)
- [Ibaiw-2023Hvv](https://github.com/ibaiw/2023Hvv)
- [OA - EXPTOOL 漏洞利用框架](https://github.com/LittleBear4/OA-EXPTOOL)


### 0x02. 免责声明
1. 本文仅用于技术交流，目的是向相关安全人员展示漏洞的存在和利用方式，以便更好地提高网络安全意识和技术水平。
2. 任何人不得利用本文中的技术手段进行非法攻击和侵犯他人的隐私和财产权利。一旦发生任何违法行为，责任自负。
3. 本文中提到的漏洞验证 poc 仅用于授权测试，任何未经授权的测试均属于非法行为。请在法律许可范围内使用此 poc。
4. 作者对使用此仓库导致的任何直接或间接损失不承担任何责任。使用此仓库的风险由使用者自行承担。

### 0x03. 索引相关
```
#### targets    # fofa导出的测试资产列表
#### domestic   # yaml列表
- 安恒明御运维审计风控系统 用户添加 2023HVV /service/?unix:/../../../../var/run/rpc/xmlrpc.sock
- 安恒明御安全网关 命令执行 2023HVV /webui/?g=aaa_portal_auth_local_submit&bkg_flag=0&suffix=

- 畅捷通T+ 命令执行 QVD-2023-13615 /tplus/ajaxpro/Ufida.T.CodeBehind._PriorityLevel,App_Code.ashx?method=GetStoreWarehouseByStore
- 畅捷通T+ 文件上传 CNVD-2022-60632 /tplus/SM/SetupAccount/Upload.aspx?preload=1

- 大华智慧园区 账户密码泄露 2023HVV /admin/user_getUserInfoByUserName.action
- 大华智慧园区 SQL注入 2023HVV /portal/services/carQuery/getFaceCapture/searchJson/
- 大华智慧园区 文件上传 2023HVV /publishing/publishing/material/file/video
- 大华智慧园区 文件上传 CVE-2023-3836 /emap/devicePoint_addImgIco?hasSubsystem=true

- 海康威视综合安防 命令执行 --- /bic/ssoService/v1/applyCT
- 海康威视综合安防 命令执行 --- /bic/ssoService/v1/keepAlive
- 海康威视综合安防 文件上传 2023HVV /center/api/files;.png
- 海康威视综合安防 文件上传 2023HVV /svm/api/external/report  # 待验证
- 海康威视综合安防 文件读取 2023HVV /artemis-portal/artemis/env
- 海康威视IVMS8700 文件上传 2023HVV /eps/api/resourceOperations/upload?token=
- 海康威视IVMS8700 文件上传 2023HVV /eps/resourceOperations/upload.action
- 海康威视IVMS8700 文件下载 2023HVV /eps/api/triggerSnapshot/download?token=

- 金蝶云星空 命令执行 2023 /Kingdee.BOS.ServiceFacade.ServicesStub.DevReportService.GetBusinessObjectData.common.kdsvc
- 金蝶云星空 文件读取 2023 /CommonFileServer/c%3A%2Fwindows%2Fwin.ini

- 绿盟SAS堡垒机 登录绕过 2023HVV /api/virtual/home/status?cat=
- 绿盟SAS堡垒机 命令执行 2023HVV /webconf/Exec/index?cmd=
- 绿盟SAS堡垒机 文件读取 2023HVV /webconf/GetFile/index?path=

- 网神SecGate3600 文件上传 2023HVV /?g=obj_app_upfile

- 深信服应用交付管理系统 命令执行 2023HVV /rep/login
- 深信服应用交付报表系统 文件读取 2023HVV /report/download.php?pdf=
- 深信服数据中心 XXE 2023HVV /src/sangforindex

- 泛微EOffice 文件上传 2023HVV /webservice/upload.php

- 用友NC 命令执行 2022 /servlet/~ic/bsh.servlet.BshServlet
- 用友NC 文件上传 2022 /aim/equipmap/accept.jsp
- 用友NC 文件读取 2022  /NCFindWeb?service=IPreAlertConfigService&filename=
- 用友NC-Cloud    命令执行 CNVD-C-2023-76801 /uapjs/jsinvoke/?action=invoke
- 用友移动系统管理 文件上传 2023HVV /maportal/appmanager/uploadApk.do?pk_obj=

信息泄露
- 2023HVV MilesightVPN      /../etc/passwd
- 2023HVV 企业微信          /cgi-bin/gateway/agentinfo
- 2023HVV 金盘微信管理平台   /admin/weichatcfg/getsysteminfo
命令执行
- 2023HVV 新开普前置服务管理平台  /service_transport/service.action
- 2023HVV 企望制造ERP系统        /mainFunctions/comboxstore.action
其他
- 2023HVV 广联达Linkworks SQL注入     /Webservice/IM/Config/ConfigService.asmx/GetIMDictionary
```
