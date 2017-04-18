---
title: "connectionManagement 的 &lt;clear&gt; 項目 (網路設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/clear"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#clear"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<clear> 項目, connectionManagement"
  - "<connectionManagement>, clear 項目"
  - "clear 項目, connectionManagement"
  - "connectionManagement, clear 項目"
ms.assetid: fb259282-84c4-4dc4-a226-78d904a6edc3
caps.latest.revision: 13
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# connectionManagement 的 &lt;clear&gt; 項目 (網路設定)
清除連結管理清單。  
  
## 語法  
  
```  
  
<clear/>  
  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
 無。  
  
### 父項目  
  
|**項目**|**描述**|  
|------------|------------|  
|[connectionManagement](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|指定與網路主機的連接之最大數目。|  
  
## 備註  
 `clear` 項目 \(Element\) 會清除連結管理清單中的所有項目 \(Entry\)。  
  
## 組態檔  
 這個項目可以用於應用程式組態檔或電腦組態檔 \(Machine.config\)。  
  
## 範例  
 下列程式碼範例會清除連結管理清單，然後加入 www.contoso.com 伺服器和其他所有網路主機的新連結管理項目。  
  
```  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <clear/>  
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