---
title: "&lt;connectionManagement&gt; 項目 (網路設定) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<connectionManagement> 項目"
  - "connectionManagement 項目"
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# &lt;connectionManagement&gt; 項目 (網路設定)
指定與網路主機的連接之最大數目。  
  
## 語法  
  
```  
  
      <connectionManagement>   
</connectionManagement>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|**元素**|**說明**|  
|------------|------------|  
|[加入](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-connectionmanagement-network-settings.md)|將 IP 位址或 DNS 名稱加入至連結管理清單。|  
|[clear](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-connectionmanagement-network-settings.md)|清除連結管理清單。|  
|[remove](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-connectionmanagement-network-settings.md)|移除連結管理清單中的 IP 位址或 DNS 名稱。|  
  
### 父項目  
  
|**元素**|**說明**|  
|------------|------------|  
|[system.net](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|包含指定 .NET Framework 如何連接至網路的設定。|  
  
## 備註  
 `connectionManagement` 項目會定義連至伺服器或伺服器群組的最大連接數目。  
  
## 組態檔  
 這個項目可以用於應用程式組態檔或電腦組態檔 \(Machine.config\)。  
  
## 範例  
 下列程式碼範例會設定應用程式使用四個至 www.contoso.com 伺服器的連接，以及至其他所有伺服器的兩個連接。  
  
```  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.Net.ServicePoint>   
 <xref:System.Net.ServicePointManager>   
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)