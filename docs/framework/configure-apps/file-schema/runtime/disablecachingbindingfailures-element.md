---
title: "&lt;disableCachingBindingFailures&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCachingBindingFailures"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCachingBindingFailures"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<disableCachingBindingFailures> 項目"
  - "組件 [.NET Framework], 快取繫結失敗"
  - "快取組件繫結失敗"
  - "disableCachingBindingFailures 項目"
ms.assetid: bf598873-83b7-48de-8955-00b0504fbad0
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# &lt;disableCachingBindingFailures&gt; 項目
指定是否要停用繫結失敗的快取，失敗的原因是無法以探查找到組件。  
  
## 語法  
  
```  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|說明|  
|--------|--------|  
|enabled|必要屬性。<br /><br /> 指定是否要停用繫結失敗的快取，失敗的原因是無法以探查找到組件。|  
  
## 啟用屬性  
  
|值|說明|  
|-------|--------|  
|0|請勿停用繫結失敗的快取 \(因為探查找不到組件而發生\)。  這是從 .NET Framework 2.0 版開始的預設繫結行為。|  
|1|停用繫結失敗的快取，失敗的原因是探查找不到組件。  這個設定會還原成 .NET Framework 1.1 版的繫結行為。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## 備註  
 從 .NET Framework 2.0 版開始，載入組件的預設行為，都是會快取所有的繫結和載入失敗。  也就是說，如果嘗試載入組件失敗，則載入相同組件的後續要求會立即失敗，而不再嘗試找出該組件。  這個項目會停用因為在探查路徑中找不到組件而繫結失敗的預設行為。  這些失敗會擲回 <xref:System.IO.FileNotFoundException>。  
  
 某些繫結和載入失敗不會被這個項目影響，而且永遠都會快取。  找不到組件但無法載入，就會發生這些失敗。  它們會擲回 <xref:System.BadImageFormatException> or <xref:System.IO.FileLoadException>。  下列清單包含這類失敗的一些範例。  
  
-   如果您嘗試載入的檔案不是有效組件，載入該組件的後續嘗試都會失敗，即使以正確的組件取代錯誤的檔案也無濟於事。  
  
-   如果您嘗試載入的組件由檔案系統鎖定，載入該組件的後續嘗試都會失敗，即使組件由檔案系統釋放之後也是如此。  
  
-   如果您正嘗試載入之組件的一個或多個版本在探查路徑中，但您所要求的特定版本不在它們之中，載入該版本的後續嘗試將會失敗，即使正確的版本已移至探查路徑也無濟於事。  
  
## 範例  
 下列程式碼範例示範如何停用快取因探查找不到組件而發生的組件繫結失敗。  
  
```  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## 請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [執行階段如何找出組件](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)