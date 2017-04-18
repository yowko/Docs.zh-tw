---
title: "緩和：X509CertificiateClaimSet.FindClaims 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 3
---
# 緩和：X509CertificiateClaimSet.FindClaims 方法
從以 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 為目標的應用程式開始，<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=fullName> 方法會嘗試將 `claimType` 引數與其 SAN 欄位中的所有 DNS 項目進行比對。  
  
## 影響  
 這項變更只會影響以 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 為目標的應用程式。  
  
 若是以舊版 .NET Framework 為目標的應用程式，<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=fullName> 方法只會嘗試將 `claimType` 引數與最後一個 DNS 項目進行比對。  
  
## 緩和  
 如果這不是您要的變更，以 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 為目標的應用程式，可以藉由將下列組態設定加入應用程式組態檔的 [\<runtime\>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段，來選擇退出這項行為：  
  
```xml  
  
<runtime> <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" /> </runtime>  
  
```  
  
 此外，以舊版 .NET Framework 為目標，但在 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 下執行的應用程式，可以藉由將下列組態設定加入應用程式組態檔的 [\<runtime\>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段，來選擇加入這項行為：  
  
```xml  
  
<runtime> <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" /> </runtime>  
  
```  
  
## 請參閱  
 [重定目標變更](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)