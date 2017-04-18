---
title: "&lt;etwEnable&gt; 項目 | Microsoft Docs"
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
  - "<etwEnable> 項目"
  - "etwEnable 項目"
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# &lt;etwEnable&gt; 項目
指定是否針對 Common Language Runtime 事件啟用 Windows \(ETW\) 的事件追蹤。  
  
## 語法  
  
```  
<etwEnable enabled="true|false"/>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|enabled|必要屬性。<br /><br /> 指定是否應該啟用 ETW。|  
  
## 啟用屬性  
  
|值|描述|  
|-------|--------|  
|true|啟用 ETW。  這是 Windows Vista 及 Windows Server 2008 作業系統起的 Windows 版本的預設值。|  
|false|停用 ETW。  這是 Windows 舊版的預設值。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## 備註  
 從 Windows Vista 開始，預設會啟用 ETW。  使用這個項目停用應用程式的 ETW。  在舊版的 Windows 中，使用這個項目啟用應用程式的 ETW。  
  
> [!NOTE]
>  使用登錄設定即可在伺服器上全域停用 ETW。  請參閱 [控制 .NET Framework 記錄](../../../../../docs/framework/performance/controlling-logging.md)。  
  
## 範例  
 下列範例示範如何啟用應用程式的 ETW 追蹤。  
  
```  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## 請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [控制 .NET Framework 記錄](../../../../../docs/framework/performance/controlling-logging.md)