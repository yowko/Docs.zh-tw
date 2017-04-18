---
title: "&lt;bypassTrustedAppStrongNames&gt; 項目 | Microsoft Docs"
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
  - "<bypassTrustedAppStrongNames> 項目"
  - "bypassTrustedAppStrongNames 項目"
  - "強式名稱略過功能"
  - "強式名稱組件, 載入至受信任的應用程式定義域"
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
caps.latest.revision: 18
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 18
---
# &lt;bypassTrustedAppStrongNames&gt; 項目
指定載入至完全信任 <xref:System.AppDomain> 的完全信任組件是否要略過強式名稱驗證。  
  
## 語法  
  
```  
<bypassTrustedAppStrongNames    
   enabled="true|false"/>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`enabled`|必要屬性。<br /><br /> 指定是否啟用略過功能，不驗證完全信任組件的強式名稱。  如果啟用此功能，當載入組件時，不會驗證強式名稱是否正確。  預設值為 `true`。|  
  
## 啟用屬性  
  
|值|描述|  
|-------|--------|  
|`true`|當組件載入至完全信任 <xref:System.AppDomain> 時，不會驗證完全信任組件上的強式名稱簽章。  這是預設值。|  
|`false`|當組件載入至完全信任 <xref:System.AppDomain> 時，會驗證完全信任組件上的強式名稱簽章。  系統只會檢查強式名稱簽章是否正確，而不會將它與其他強式名稱比較是否相符。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## 備註  
 強式名稱略過功能可避免完全信任組件進行強式名稱簽章驗證的額外負擔。  
  
 略過功能適用於使用強式名稱簽署且具有下列特性的任何組件：  
  
-   完全信任且無 <xref:System.Security.Policy.StrongName> 辨識項 \(例如，有 `MyComputer` 區域辨識項\)。  
  
-   載入至完全信任的 <xref:System.AppDomain>。  
  
-   從該 <xref:System.AppDomain> 的 <xref:System.AppDomainSetup.ApplicationBase%2A> 屬性底下某個位置載入。  
  
-   未延遲簽署。  
  
> [!NOTE]
>  如果電腦上的所有應用程式藉由使用登錄機碼來關閉略過功能，則此組態檔設定沒有作用。  如需詳細資訊，請參閱 [如何：停用強式名稱略過功能](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)。  
  
## 範例  
 下列範例顯示如何指定在完全信任組件上驗證強式名稱簽章的行為。  
  
```  
<configuration>  
   <runtime>  
      <bypassTrustedAppStrongNames enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
## 請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [如何：停用強式名稱略過功能](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)