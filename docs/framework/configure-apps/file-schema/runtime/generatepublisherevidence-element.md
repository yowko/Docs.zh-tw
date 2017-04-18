---
title: "&lt;generatePublisherEvidence&gt; 項目 | Microsoft Docs"
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
  - "<generatePublisherEvidence> 項目"
  - "generatePublisherEvidence 項目"
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
caps.latest.revision: 21
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 21
---
# &lt;generatePublisherEvidence&gt; 項目
指定執行階段是否建立程式碼存取安全性 \(CAS\) 的 <xref:System.Security.Policy.Publisher> 辨識項。  
  
## 語法  
  
```  
<generatePublisherEvidence    
   enabled="true|false"/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|說明|  
|--------|--------|  
|`enabled`|必要屬性。<br /><br /> 指定執行階段是否建立 <xref:System.Security.Policy.Publisher> 辨識項。|  
  
## 啟用屬性  
  
|值|說明|  
|-------|--------|  
|`false`|不會建立 <xref:System.Security.Policy.Publisher> 辨識項。|  
|`true`|建立 <xref:System.Security.Policy.Publisher> 辨識項。  這是預設值。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含與執行階段初始化選項有關的資訊。|  
  
## 備註  
  
> [!NOTE]
>  在 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] \(含\) 以後版本中，此項目對組件載入時間沒有影響。  如需詳細資訊，請參閱 [安全性變更](../../../../../docs/framework/security/security-changes.md)中的＜安全性原則簡化＞一節。  
  
 Common Language Runtime \(CLR\) 會嘗試在載入時間 \(Load Time\) 驗證 Authenticode 簽章，以建立組件的 <xref:System.Security.Policy.Publisher> 辨識項。  不過，大多數應用程式預設都不需要 <xref:System.Security.Policy.Publisher> 辨識項。  標準 CAS 原則並不依賴 <xref:System.Security.Policy.PublisherMembershipCondition>。  除非您的應用程式在使用自訂 CAS 原則的電腦上執行，或者要在部分信任環境下滿足 <xref:System.Security.Permissions.PublisherIdentityPermission> 的要求，否則請避免因驗證發行者簽章而造成啟動時不必要的負荷 \(在完全信任的環境中，識別使用權限的要求一定會成功\)。  
  
> [!NOTE]
>  建議服務可以使用 `<generatePublisherEvidence>` 項目來改善啟動效能。使用這個項目也有助於避免延遲，延遲可能會導致逾時以及服務啟動取消。  
  
## 組態檔  
 這個項目只能在應用程式組態檔中使用。  
  
## 範例  
 下列範例顯示如何使用 `<generatePublisherEvidence>` 項目為某個應用程式停用 CAS 發行者原則檢查。  
  
```  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## 請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)