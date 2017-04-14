---
title: "&lt;Thread_UseAllCpuGroups&gt; 項目 | Microsoft Docs"
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
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# &lt;Thread_UseAllCpuGroups&gt; 項目
指定執行階段是否在所有 CPU 群組分配 Managed 執行緒。  
  
## 語法  
  
```vb  
<Thread_UseAllCpuGroups    
   enabled="true|false"/>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`enabled`|必要屬性。<br /><br /> 指定執行階段是否在所有 CPU 群組分配 Managed 執行緒。|  
  
## 啟用屬性  
  
|值|描述|  
|-------|--------|  
|`false`|執行階段不會跨多個 CPU 群組分配 Managed 執行緒。  這是預設值。|  
|`true`|如果電腦上有多個 CPU 群組，而且已啟用 [\<GCCpuGroup\>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) 項目，執行階段會將 Managed 執行緒分散到多個 CPU 群組。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|描述|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## 備註  
 當電腦上有多個 CPU 群組時，啟用這個項目會造成執行階段將 Managed 執行緒分散到所有的 CPU 群組。  若要使用此功能，您也必須啟用 [\<GCCpuGroup\>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) 項目，以將記憶體回收擴及所有 CPU 群組，並在建立和平衡堆積時考慮所有核心。  啟用 [\<GCCpuGroup\>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) 項目需要啟用 [\<gcServer\>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) 項目。  這些項目未啟用，啟用 `<Thread_UseAllCpuGroups>` 項目沒有作用。  
  
## 範例  
 下列範例說明如何啟用多個 CPU 群組的支援。  
  
```  
<configuration>  
   <runtime>  
      <Thread_UseAllCpuGroups enabled="true"/>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## 請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [\<GCCpuGroup\> 項目](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)