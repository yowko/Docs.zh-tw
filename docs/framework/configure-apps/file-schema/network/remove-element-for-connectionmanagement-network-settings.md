---
title: "connectionManagement 的 &lt;remove&gt; 項目 (網路設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/remove"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#remove"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<connectionManagement>, remove 項目"
  - "<remove> 項目, connectionManagement"
  - "connectionManagement, remove 項目"
  - "remove 項目, connectionManagement"
ms.assetid: 94b81775-5a22-4975-8c47-8620c40c3f35
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# connectionManagement 的 &lt;remove&gt; 項目 (網路設定)
移除連結管理清單中的 IP 位址或 DNS 名稱。  
  
## 語法  
  
```  
  
      <remove   
   name = "server name or IP address"   
/>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|**屬性**|**描述**|  
|------------|------------|  
|`address`|IP 位址或 DNS 名稱。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|**項目**|**描述**|  
|------------|------------|  
|[connectionManagement](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|指定與網路主機的連接之最大數目。|  
  
## 備註  
 `remove` 項目會移除所指定伺服器的連線管理清單項目。  
  
 `address` 屬性的值必須是有效的 IP 位址或主機名稱。  
  
## 組態檔  
 這個項目可以用於應用程式組態檔或電腦組態檔 \(Machine.config\)。  
  
## 範例  
 下列程式碼範例會移除伺服器 www.adventure\-works.com 的任何連接管理清單項目，然後設定應用程式使用四個至 server www.contoso.com 的連接，以及兩個至其他所有伺服器的連接。  
  
```  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <remove address = "http://www.adventure-works.com"/>  
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