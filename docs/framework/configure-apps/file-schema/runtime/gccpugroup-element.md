---
title: "&lt;GCCpuGroup&gt; 項目 | Microsoft Docs"
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
  - "<GCCpuGroup> 項目"
  - "GCCpuGroup 項目"
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# &lt;GCCpuGroup&gt; 項目
指定記憶體回收是否支援多個 CPU 群組。  
  
## 語法  
  
```  
<GCCpuGroup    
   enabled="true|false"/>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`enabled`|必要屬性。<br /><br /> 指定記憶體回收是否支援多個 CPU 群組。|  
  
## 啟用屬性  
  
|值|描述|  
|-------|--------|  
|`false`|記憶體回收不支援多個 CPU 群組。  這是預設值。|  
|`true`|如果伺服器記憶體回收已啟用，記憶體回收支援多個 CPU 群組。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|描述|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## 備註  
 當電腦上有多個 CPU 群組且伺服器記憶體回收已啟動 \(請參閱 [\<gcServer\>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) 元素\)，當建立和平衡堆積時啟用跨所有 CPU 的這個項目延伸記憶體回收群組並考慮所有核心。  
  
> [!NOTE]
>  這個項目僅適用於記憶體回收執行緒。  若要使執行階段發出所有 CPU 群組的使用者執行緒，您也必須啟用 [\<Thread\_UseAllCpuGroups\>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) 項目。  
  
## 範例  
 下列範例說明如何啟用多個 CPU 群組的記憶體回收。  
  
```  
<configuration>  
   <runtime>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## 請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [How to: Disable Concurrent Garbage Collection](http://msdn.microsoft.com/zh-tw/ba2c6c67-5778-497c-9fac-5f793b5500c7)   
 [工作站和伺服器記憶體回收](../../../../../docs/standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)