---
title: ".NET Framework 4.6.1 中的重定目標變更 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 411ad548-30fa-43da-8716-10eccfc839e6
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 4
---
# .NET Framework 4.6.1 中的重定目標變更
在某些罕見的情況下，重定目標變更可能會影響以 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 為目標來重新編譯的應用程式。 除非另有指定，否則這些變更不會影響以舊版 .NET Framework 為目標但在[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]下執行的二進位檔。  
  
 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 包含下列區域的重定目標變更：  
  
-   [Windows Communication Foundation](#WCF)  
  
-   [Windows Form](#WinForms)  
  
<a name="WCF"></a>   
## Windows Communication Foundation  
  
|功能|變更|影響|範圍|  
|--------|--------|--------|--------|  
|<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=fullName><br /><br /> \(<xref:System.IdentityModel.Claims> 命名空間\)|在目標為 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 的應用程式中，如果 X509 宣告集是初始化自 SAN 欄位中含有多個 DNS 項目的憑證，<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A> 方法會嘗試使用所有 DNS 項目來比對 `claimType` 引數。<br /><br /> 若是以舊版 .NET Framework 為目標的應用程式，<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A> 方法僅會嘗試使用最後一個 DNS 項目來比對 `claimType` 引數。|這項變更會影響所有目標為 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 的應用程式。 目標為舊版 .NET Framework 的應用程式不會受到影響。<br /><br /> 不過，以 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 為目標的應用程式可以選擇不使用這種行為。 此外，以舊版 .NET Framework 為目標但在 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 下執行的應用程式，可以選擇使用這種行為。 如需詳細資訊，請參閱[緩和：X509CertificiateClaimSet.FindClaims 方法](../../../docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md)。|次要|  
  
<a name="WinForms"></a>   
## Windows Form  
  
|功能|變更|影響|範圍|  
|--------|--------|--------|--------|  
|<xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName> 方法 \(<xref:System.Windows.Forms> 命名空間\)|在以 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 為目標的 Windows Forms 應用程式中，自訂 <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=fullName> 實作可以在呼叫 <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName> 方法時安全地篩選訊息；若是 <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=fullName> 實作，<br /><br /> <ul><li>則會執行下列其中一項或兩項：<br /><br /> <ul><li>呼叫 <xref:System.Windows.Forms.Application.AddMessageFilter%2A> 方法來加入訊息篩選器。</li><li>呼叫 <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> 方法來移除訊息篩選器。 方法。</li></ul></li><li>**並且**呼叫 <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=fullName> 方法來激發訊息。</li></ul><br /> 針對在目標為舊版 .NET Framework 之 Windows Forms 應用程式中的這類實作，某些情況下會於呼叫 <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName> 方法時擲回 <xref:System.IndexOutOfRangeException> 例外狀況|這項變更會影響所有目標為 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 的應用程式。 目標為舊版 .NET Framework 的應用程式不會受到影響。<br /><br /> 不過，以 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 為目標的應用程式可以選擇不使用這種行為。 此外，以舊版 .NET Framework 為目標但在 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 下執行的應用程式，可以選擇使用這種行為。 如需詳細資訊，請參閱[緩和：自訂 IMessageFilter.PreFilterMessage 實作](../../../docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md)。|邊緣|  
  
## 請參閱  
 [4.6.1 的應用程式相容性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)