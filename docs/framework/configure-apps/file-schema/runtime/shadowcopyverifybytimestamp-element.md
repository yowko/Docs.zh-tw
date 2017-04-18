---
title: "&lt;shadowCopyVerifyByTimestamp&gt; 項目 | Microsoft Docs"
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
  - "<shadowCopyTimeStampVerification> 項目"
  - "shadowCopyTimeStampVerification 項目"
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# &lt;shadowCopyVerifyByTimestamp&gt; 項目
指定陰影複製是否使用在 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 中引入的預設啟動行為，或者會還原到舊版 .NET Framework 的啟動行為。  
  
## 語法  
  
```  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|說明|  
|--------|--------|  
|enabled|必要屬性。<br /><br /> 指定使用陰影複製的應用程式定義域是否會在啟動時比對組件時間戳記，在陰影複製組件之前判斷該組建是否已更新。|  
  
## 啟用屬性  
  
|值|說明|  
|-------|--------|  
|true|啟動時只複製自上次複製到陰影複製目錄中以來已經更新的組件。  這是 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 的預設值。|  
|false|會還原成舊版 .NET Framework 的啟動行為，也就是在啟動時複製所有檔案。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## 備註  
 自 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 起，只有在組件的時間戳記指出自從這些組件最近複製到陰影複製目錄之後已發生變更時，才會陰影複製組件。  這可改善許多使用陰影複製的應用程式的啟動時間，如[陰影複製組件](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md)所述。  具有高比例與高頻率組件更新的應用程式，可能無法受益於這種行為變化。  在這種情況下，您可以使用此項目還原舊版 .NET Framework 行為。  
  
## 範例  
 下列範例示範如何停用 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 中陰影複製的預設啟動行為，並還原到舊版 .NET Framework 的啟動行為。  
  
```  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## 請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [陰影複製組件](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md)