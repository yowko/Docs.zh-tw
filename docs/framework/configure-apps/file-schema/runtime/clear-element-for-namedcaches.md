---
title: "&lt;namedCaches&gt; 的 &lt;clear&gt; 項目 | Microsoft Docs"
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
  - "<namedCaches> 的 <clear> 項目"
  - "<namedCaches> 的 clear 項目"
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# &lt;namedCaches&gt; 的 &lt;clear&gt; 項目
清除記憶體快取之 `namedCaches` 集合內的所有 `namedCache` 項目。  
  
## 語法  
  
```  
<namedCaches>  
    <clear name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## 類型  
 `Type`  
  
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
 `clear` 項目會清除記憶體快取之具名快取集合中的所有 `namedCache` 項目。  使用 `add` 項目加入新的具名快取項目，以確定在集合中沒有其他具名快取之前，您可以先使用 `clear` 項目。  
  
## 請參閱  
 [\<namedCaches\> 項目 \(快取設定\)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)