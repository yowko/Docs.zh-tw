---
title: "&lt;tokenReplayDetection&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
caps.latest.revision: 6
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 5
---
# &lt;tokenReplayDetection&gt;
啟用語彙基元重新執行偵測，並指定語彙基元的到期時間。  
  
## 語法  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## 類型  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|enabled|值，指出是否已啟用語彙基元重新執行偵測。 「 真正 」 語彙基元，以便重新執行偵測。|  
|expirationPeriod|A <xref:System.TimeSpan> ，指定最大項目會被視為過期，並從快取中移除之前的時間量。  如需有關如何指定<xref:System.TimeSpan>的值，請參閱[Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_TimespanValues)。|  
  
### 子項目  
 None  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|指定服務層級識別設定。|  
|[\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|提供設定一系列安全性語彙基元的處理常式。|  
  
## 備註  
 A `<tokenReplayDetection>`項目，請指定在服務層級下`<identityConfiguration>`項目或安全性語彙基元的處理常式集合下的層級上`<securityTokenHandlerConfiguration>`項目。  在 \[語彙基元的處理常式集合的設定會覆寫所指定的服務。  
  
 指定的型別語彙基元的重新顯示快取的[\<tokenReplayCache\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)項目。