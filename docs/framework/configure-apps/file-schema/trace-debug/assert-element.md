---
title: "&lt;assert&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#assert"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<assert> 項目"
  - "assert 項目"
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# &lt;assert&gt; 項目
指定您呼叫 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> 方法時是否顯示訊息方塊，同時指定要寫入訊息的檔案名稱。  
  
## 語法  
  
```  
  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|說明|  
|--------|--------|  
|`assertuienabled`|選擇性屬性。<br /><br /> 指定 **Debug.Assert** 方法評估為 **false** 時是否要顯示訊息方塊。|  
|`logfilename`|選擇性屬性。<br /><br /> 指定如果 **Debug.Assert** 評估為 **false** 時，訊息要寫入的檔案名稱。|  
  
## assertuienabled 屬性  
  
|值|說明|  
|-------|--------|  
|`true`|顯示訊息方塊。  這是預設值。|  
|`false`|不顯示訊息方塊。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定收集、存放和傳送訊息的追蹤接聽程式，以及設定追蹤參數的層級。|  
  
## 備註  
 **\<assert\>** 項目中這兩種屬性都是選擇性項目。  可以不指定訊息要寫入的檔案，停用訊息方塊，或者指定訊息要寫入的檔案，讓訊息方塊保持啟用。  
  
## 範例  
 以下範例顯示呼叫 **Debug.Assert** 並將訊息寫入 `c:\log.txt` 時，如何停用顯示訊息方塊。  
  
```  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.Diagnostics.Debug>   
 [追蹤和偵錯設定結構描述](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)