---
title: "&lt;developmentMode&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<developmentMode> 項目"
  - "容器標記, <developmentMode> 項目"
  - "developmentMode 項目"
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# &lt;developmentMode&gt; 項目
指定執行階段是否在 DEVPATH 環境變數所指定的目錄中搜尋組件。  
  
## 語法  
  
```  
<developmentMode developerInstallation="true | false"/>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|**developerInstallation**|指定執行階段是否在 DEVPATH 環境變數所指定的目錄中搜尋組件。|  
  
## developerInstallation 屬性  
  
|值|描述|  
|-------|--------|  
|**true**|在 DEVPATH 環境變數所指定的目錄中搜尋組件。|  
|**false**|不在 DEVPATH 環境變數所指定的目錄中搜尋組件。  這是預設值。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## 備註  
 這個設定只可以在程式開發階段使用。  Runtime 不會檢查在 DEVPATH 中所找到的強式名稱組件版本。  它只使用它所找到的第一個版本。  
  
## 範例  
 下列範例顯示如何使執行階段在 DEVPATH 環境變數所指定的目錄中搜尋組件。  
  
```  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## 請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [如何：使用 DEVPATH 找出組件](../../../../../docs/framework/configure-apps/how-to-locate-assemblies-by-using-devpath.md)