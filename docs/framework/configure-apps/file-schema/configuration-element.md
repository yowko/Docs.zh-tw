---
title: "&lt;configuration&gt; 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<configuration> 項目"
  - "configuration 項目"
  - "容器標記, <configuration> 項目"
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
caps.latest.revision: 15
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# &lt;configuration&gt; 項目
Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。  
  
 **\<設定\>**  
  
## 語法  
  
```  
  
      <configuration>   
   <!-- configuration settings -->   
</configuration>  
```  
  
## 子項目  
  
|元素|說明|  
|--------|--------|  
|[\<assemblyBinding\> 項目](../../../../docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)|指定位於組態層級的組件繫結原則。|  
|[啟始設定結構描述](../../../../docs/framework/configure-apps/file-schema/startup/index.md)|啟始設定結構描述中的所有項目。|  
|[執行階段設定結構描述](../../../../docs/framework/configure-apps/file-schema/runtime/index.md)|執行階段設定結構描述中的所有項目。|  
|[遠端設定結構描述](http://msdn.microsoft.com/zh-tw/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e)|遠端設定結構描述中的所有項目。|  
|[網路設定結構描述](../../../../docs/framework/configure-apps/file-schema/network/index.md)|網路設定結構描述中的所有項目。|  
|[密碼編譯設定結構描述](../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)|密碼編譯設定結構描述中的所有項目。|  
|[組態區段結構描述](../../../../docs/framework/configure-apps/file-schema/configuration-sections-schema.md)|組態區段設定結構描述中的所有項目。|  
|[追蹤和偵錯設定結構描述](../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)|追蹤和偵錯設定結構描述中的所有項目。|  
|[ASP.NET 設定結構描述](http://msdn.microsoft.com/zh-tw/116608f3-c03d-4413-9fc7-978703e18b0f)|ASP.NET 組態結構描述中的所有項目，包括設定 ASP.NET 網站和應用程式的項目。  用於 Web.config 檔案。|  
|[XML Web Service 設定結構描述](http://msdn.microsoft.com/zh-tw/f84d6d55-1add-4eb7-ae46-33df5833ea2e)|Web 服務設定結構描述中的所有項目。|  
|[Web 設定結構描述](../../../../docs/framework/configure-apps/file-schema/web/index.md)|Web 設定結構描述中的所有項目，包括用來設定 ASP.NET 如何配合主機應用程式 \(例如 IIS\) 運作的項目。  用於 aspnet.config 檔案。|  
  
## 備註  
 每個組態檔必須剛好有一個 **\<configuration\>** 項目。  
  
## 請參閱  
 [組態檔結構描述](../../../../docs/framework/configure-apps/file-schema/index.md)