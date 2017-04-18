---
title: "&lt;legacyCorruptedStateExceptionsPolicy&gt; 項目 | Microsoft Docs"
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
  - "<legacyCorruptedStateExceptionsPolicy> 項目"
  - "legacyCorruptedStateExceptionsPolicy 項目"
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# &lt;legacyCorruptedStateExceptionsPolicy&gt; 項目
指定 Common Language Runtime 是否允許 Managed 程式碼攔截存取違規及其他毀損狀態例外狀況。  
  
## 語法  
  
```  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`enabled`|必要屬性。<br /><br /> 指定應用程式要攔截毀損狀態例外狀況失敗，例如存取違規。|  
  
## 啟用屬性  
  
|值|描述|  
|-------|--------|  
|`false`|應用程式不會攔截毀損狀態例外狀況失敗，例如存取違規。  這是預設值。|  
|`true`|應用程式會攔截毀損狀態例外狀況失敗，例如存取違規。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## 備註  
 在 .NET Framework 3.5 \(含\) 以前版本中，Common Language Runtime 允許 Managed 程式碼攔截毀損處理序狀態引發的例外狀況。  存取違規即是這種例外狀況類型的範例。  
  
 從 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 開始，Managed 程式碼不再於 `catch` 區塊中攔截這些例外狀況類型。  但是，您可以覆寫這項變更，並透過兩種方式保留對毀損狀態例外狀況的處理機制：  
  
-   將 `<legacyCorruptedStateExceptionsPolicy>` 項目的 `enabled` 屬性設定為 `true`。  這個組態設定會在整個處理序中套用，並影響所有方法。  
  
 \-或\-  
  
-   將 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=fullName> 屬性套用至包含例外狀況 `catch` 區塊的方法。  
  
 這個組態項目只能在 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] \(含\) 以後版本中使用。  
  
## 範例  
 在下列範例中，會示範如何指定應用程式應還原成 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 之前的行為，並攔截所有毀損狀態例外狀況失敗。  
  
```  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>   
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)