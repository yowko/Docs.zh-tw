---
title: "&lt;namedCaches&gt; 的 &lt;remove&gt; 項目 | Microsoft Docs"
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
  - "namedCaches 的 <remove> 項目"
  - "namedCaches 的 remove 項目"
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
caps.latest.revision: 10
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# &lt;namedCaches&gt; 的 &lt;remove&gt; 項目
從記憶體快取的 `namedCaches` 集合中移除具名快取項目。  
  
## 語法  
  
```  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## 類型  
 `None`  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
 `None`  
  
### 子項目  
 `None`  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<namedCaches\>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|包含具名 <xref:System.Runtime.Caching.MemoryCache> 執行個體之組態設定的集合。|  
  
## 備註  
 `remove` 項目會從記憶體快取的具名快取集合中移除 `namedCache` 項目。  
  
## 請參閱  
 [\<namedCaches\> 項目 \(快取設定\)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)