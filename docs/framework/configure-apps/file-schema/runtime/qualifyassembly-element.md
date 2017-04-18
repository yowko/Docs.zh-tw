---
title: "&lt;qualifyAssembly&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<qualifyAssembly> 項目"
  - "容器標記, <qualifyAssembly> 項目"
  - "qualifyAssembly 項目"
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# &lt;qualifyAssembly&gt; 項目
指定組件的完整名稱，使用部分名稱時，應以動態方式載入這個名稱。  
  
## 語法  
  
```  
  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|說明|  
|--------|--------|  
|`partialName`|必要屬性。<br /><br /> 指定出現在程式碼中的組件部分名稱。|  
|`fullName`|必要屬性。<br /><br /> 指定出現在全域組件快取中的組件完整名稱。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|`assemblyBinding`|包含有關組件版本重新導向和組件位置的資訊。|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## 備註  
 使用部分組件名稱來呼叫 <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> 方法，Common Language Runtime 只在應用程式基底目錄中尋找組件。  使用應用程式組態檔中的 **\<qualifyAssembly\>** 項目來提供完整的組件資訊 \(名稱、版本、公開金鑰語彙基元和文化特性\)，並使 Common Language Runtime 在全域組件快取中搜尋組件。  
  
 **fullName** 屬性必須包含組件識別 \(Identity\) 的四個欄位：名稱、版本、公開金鑰語彙基元和文化特性 \(Culture\)。  **partialName** 屬性必須部分參考組件。  您至少必須指定組件的文字名稱 \(最常見的情況\)，但是您也可以包含版本、公開金鑰語彙基元或文化特性 \(或是這四個欄位的任意組合，但是並非全部四個欄位\)。  **partialName** 必須符合在呼叫中指定的名稱。  例如，您不可以在組態檔中將 `"math"` 指定為 **partialName**  屬性，然後在程式碼中呼叫 `Assembly.Load("math, Version=3.3.3.3")`。  
  
## 範例  
 下列範例以邏輯方式將呼叫 `Assembly.Load("math")`  變成 `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`。  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <qualifyAssembly partialName="math"   
                         fullName=  
"math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## 請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [執行階段如何找出組件](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)   
 [NIB: Partial Assembly References](http://msdn.microsoft.com/zh-tw/ec90f07a-398c-4306-9401-0fc5ff9cb59f)