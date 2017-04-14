---
title: "&lt;NetFx40_LegacySecurityPolicy&gt; 項目 | Microsoft Docs"
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
  - "<NetFx40_LegacySecurityPolicy> 項目"
  - "NetFx40_LegacySecurityPolicy 項目"
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
caps.latest.revision: 21
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 21
---
# &lt;NetFx40_LegacySecurityPolicy&gt; 項目
指定執行階段是否會使用舊有的程式碼存取安全性 \(CAS\) 原則。  
  
## 語法  
  
```  
<NetFx40_LegacySecurityPolicy  
   enabled="true|false"/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|說明|  
|--------|--------|  
|`enabled`|必要屬性。<br /><br /> 指定執行階段是否會使用舊有的 CAS 原則。|  
  
## 啟用屬性  
  
|值|說明|  
|-------|--------|  
|`false`|執行階段不使用舊版 CAS 原則。  這是預設值。|  
|`true`|執行階段使用舊版 CAS 原則。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含與執行階段初始化選項有關的資訊。|  
  
## 備註  
 在 .NET Framework 3.5 \(含\) 以前版本中，CAS 原則永遠有效。  在 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 中，就必須自行啟用 CAS 原則。  
  
 CAS 原則是版本特定的。  存在於舊版 .NET Framework 中的自訂 CAS 原則，都必須在 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 中重新指定。  
  
 將 `<NetFx40_LegacySecurityPolicy>` 項目套用至 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 組件不會影響[安全性透明程式碼](../../../../../docs/framework/misc/security-transparent-code.md)，透明度規則依然會適用。  
  
> [!IMPORTANT]
>  套用 `<NetFx40_LegacySecurityPolicy>` 項目，可能會對由 [原生映像產生器 \(Ngen.exe\)](../../../../../docs/framework/tools/ngen-exe-native-image-generator.md) 建立，卻未安裝在 [全域組件快取](../../../../../docs/framework/app-domains/gac.md)中的原生映像組件，造成重大的效能負面影響。  效能降低的情形，是因為執行階段無法在套用屬性時將組件載入為原生映像，導致它們被載入為 Just\-In\-Time 組件。  
  
> [!NOTE]
>  如果您在 Visual Studio 專案的專案設定中，指定早於 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 的目標 .NET Framework 版本，就會啟用 CAS 原則，其中包括您對該版本指定的任何自訂 CAS 原則。  不過，您將無法使用新的 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 型別和成員。  您也可以在[應用程式組態檔](../../../../../docs/framework/configure-apps/index.md)的啟始設定結構描述中，使用 [\<supportedRuntime\> 項目](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)藉以指定舊版 .NET Framework。  
  
> [!NOTE]
>  組態檔語法要區分大小寫。  您應該使用＜語法＞和＜範例＞小節中提供的語法。  
  
## 組態檔  
 這個項目只能在應用程式組態檔中使用。  
  
## 範例  
 下列範例將示範如何為應用程式啟用舊有的 CAS 原則。  
  
```  
<configuration>  
   <runtime>  
      <NetFx40_LegacySecurityPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## 請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)