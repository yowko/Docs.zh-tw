---
title: "啟動設定結構描述 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "組態結構描述 [.NET Framework], 啟動設定"
  - "結構描述啟動設定"
  - "啟動設定結構描述"
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
caps.latest.revision: 10
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# 啟動設定結構描述
啟始設定指定應該執行應用程式的 Common Language Runtime 版本。  
  
|元素|說明|  
|--------|--------|  
|[\<requiredRuntime\>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|指定應用程式只支援 Common Language Runtime 1.0 版。  以 runtime 1.1 版建置的應用程式應該使用 **\<supportedRuntime\>** 項目。|  
|[\<supportedRuntime\>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|指定應用程式所支援的 Common Language Runtime 版本。|  
|[\<startup\>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)|包含 **\<requiredRuntime\>**項目和 **\<supportedRuntime\>** 項目。|  
  
## 請參閱  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [\<PaveOver\> Specifying Which Runtime Version to Use](http://msdn.microsoft.com/zh-tw/c376208d-980d-42b4-865b-fbe0d9cc97c2)