---
title: "&lt;gcAllowVeryLargeObjects&gt; 項目 | Microsoft Docs"
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
  - "<gcAllowVeryLargeObjects> 項目"
  - "gcAllowVeryLargeObjects 項目"
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# &lt;gcAllowVeryLargeObjects&gt; 項目
在 64 位元平台上，啟用大小超過 2 GB 的陣列。  
  
## 語法  
  
```  
<gcAllowVeryLargeObjects    
   enabled="true|false" />  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`enabled`|必要屬性。<br /><br /> 設定在 64 位元平台上是否啟用超過2 GB 的陣列。|  
  
## 啟用屬性  
  
|值|描述|  
|-------|--------|  
|`false`|未啟用總額超過 2 GB 的陣列。  這是預設值。|  
|`true`|在 64 位元平台上啟用總額超過 2 GB 的陣列。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|描述|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含與執行階段初始化選項有關的資訊。|  
  
## 備註  
 在您的應用程式組態檔中使用這個元素會啟用超過 2 GB 的陣列，但不會變更其他物件大小或陣列大小的限制：  
  
-   陣列中數值最大的元素為<xref:System.UInt32.MaxValue?displayProperty=fullName>。  
  
-   位元組陣列和單一位元組結構的陣列在單一維度中的最大的索引值是 2,147,483,591 \(0x7FFFFFC7\)，其他型別陣列則為 2,146,435,071 \(0X7FEFFFFF\)。  
  
-   字串和其他非陣列物件的大小上限不變。  
  
> [!CAUTION]
>  在啟用這個功能之前，請確定您的應用程式沒有假設所有陣列大小小於 2 GB 的不安全程式碼。  例如，程式碼中若假設用來作為緩衝區的陣列不會大於 2 GB ，則緩衝區可能因滿溢而超出陣列範圍，如此即為不安全的程式碼。  
  
## 範例  
 下列範例將示範如何為應用程式啟用舊有的此功能。  
  
```  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## 請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)