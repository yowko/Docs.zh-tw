---
title: "&lt;UseSmallInternalThreadStacks&gt; 項目 | Microsoft Docs"
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
  - "<UseSmallInternalThreadStacks> 項目"
  - "UseSmallInternalThreadStacks 項目"
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# &lt;UseSmallInternalThreadStacks&gt; 項目
建立在內部使用的特定執行緒時，透過指定明確的堆疊大小，而不讓那些執行緒使用預設的堆疊大小，要求 Common Language Runtime \(CLR\) 降低記憶體的使用量。  
  
## 語法  
  
```  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|enabled|必要屬性。<br /><br /> 指定是否要求 CLR 在建立內部使用的特定執行緒時使用明確的堆疊大小，而非預設的堆疊大小。  明確的堆疊大小會小於 1 MB 的預設堆疊大小。|  
  
## 啟用屬性  
  
|值|描述|  
|-------|--------|  
|true|要求明確的堆疊大小。|  
|false|使用預設堆疊大小。  這是 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 的預設值。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## 備註  
 這個組態項目用來要求在處理序中減少使用虛擬記憶體，因為如果接受該要求，CLR 用於其內部執行緒的明確執行緒大小會小於預設大小。  
  
> [!IMPORTANT]
>  這個組態項目是對 CLR 的要求，而不是對絕對需求的要求。  在 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 中，只有 x 86 架構接受這個要求。  未來的 CLR 可能會完全忽略這個項目，或者會以選取之內部執行緒一定會使用的明確堆疊大小取代。  
  
 如果 CLR 接受要求，指定此組態項目會犧牲較小虛擬記憶體用法的可靠性，因為較小的堆疊大小比較容易造成堆疊溢位。  
  
## 範例  
 下列範例示範如何要求 CLR 針對內部使用的特定執行緒使用明確堆疊大小  
  
```  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## 請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)