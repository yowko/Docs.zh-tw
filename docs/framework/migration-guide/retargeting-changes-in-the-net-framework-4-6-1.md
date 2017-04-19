---
title: ".NET Framework 4.6.1 中的重定目標變更 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retargeting changes, .NET Framework
- retargeting changes, .NET Framework 4.6.1
- application compatibility
ms.assetid: 411ad548-30fa-43da-8716-10eccfc839e6
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 0adc4a6cae566b6a15c5fa492620abb74b47335b
ms.lasthandoff: 04/18/2017

---
# <a name="retargeting-changes-in-the-net-framework-461"></a>.NET Framework 4.6.1 中的重定目標變更
在某些罕見的情況下，重定目標變更可能會影響以 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 為目標來重新編譯的應用程式。 除非另有指定，否則這些變更不會影響以舊版 .NET Framework 為目標但在[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]下執行的二進位檔。  
  
 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 包含下列區域的重定目標變更：  
  
-   [核心](#Core)  
  
-   [程式碼合約](#Contracts)  
  
-   [Windows Communication Foundation](#WCF)  
  
-   [Windows Forms](#WinForms)  
  
<a name="Core"></a>   
## <a name="core"></a>核心  
  
|功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|<xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=fullName>|針對以 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 和更新版本為目標的應用程式，在由 <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=fullName> 方法的多載所建立之 <xref:System.IO.Compression.ZipArchiveEntry> 物件的 <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A> 屬性中，路徑分隔符號字元已從反斜線 ("\\") 變更為正斜線 ("/")。|這項變更使得 .NET 實作遵守 [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) (.ZIP 檔案格式規格) 的 4.4.17.1 小節，並允許在非 Windows 系統上解壓縮 ZIP 封存。<br /><br /> 不過，以 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 和更新版本為目標的應用程式可以選擇不使用這種行為。 如需詳細資訊，請參閱[風險降低：ZipArchiveEntry.FullName 路徑分隔符號](../../../docs/framework/migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md)。|Edge|  
  
<a name="Contracts"></a>   
## <a name="code-contracts"></a>程式碼合約  
  
|功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|<xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=fullName> 和 <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=fullName>，以及 <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> 的呼叫|針對以 .NET Framework 4.6.1 為目標的應用程式，重寫器會發出編譯器警告 CC1036：「偵測到對方法 'System.String.IsNullOrWhiteSpace(System.String)' 的呼叫，但在方法中沒有 [Pure]...」|這是編譯器警告，不是編譯器錯誤。<br /><br /> [GitHub 問題 #339](https://github.com/Microsoft/CodeContracts/issues/339) 中已解決這種行為。 若要移除這個警告，您可以從 [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md) 下載並編譯程式碼合約工具原始程式碼的更新版本。 您可以在頁面底部找到下載資訊。|次要|  
  
<a name="WCF"></a>   
## <a name="windows-communication-foundation"></a>Windows Communication Foundation  
  
|功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=fullName><br /><br /> (<xref:System.IdentityModel.Claims> 命名空間)|在以 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 為目標的應用程式中，如果 X509 宣告集是初始化自 SAN 欄位中含有多個 DNS 項目的憑證，<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A> 方法會嘗試將 `claimType` 引數與所有 DNS 項目進行比對。<br /><br /> 若是以舊版 .NET Framework 為目標的應用程式，<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A> 方法只會嘗試將 `claimType` 引數與最後一個 DNS 項目進行比對。|這項變更會影響所有目標為 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 的應用程式。 目標為舊版 .NET Framework 的應用程式不會受到影響。<br /><br /> 不過，以 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 為目標的應用程式可以選擇不使用這種行為。 此外，以舊版 .NET Framework 為目標但在 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 下執行的應用程式，可以選擇使用這種行為。 如需詳細資訊，請參閱[風險降低：X509CertificateClaimSet.FindClaims 方法](../../../docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md)。|次要|  
  
<a name="WinForms"></a>   
## <a name="windows-forms"></a>Windows Form  
  
|功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|<xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName> 方法 (<xref:System.Windows.Forms> 命名空間)|在以 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 為目標的 Windows Forms 應用程式中，自訂 <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=fullName> 實作可以在呼叫 <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName> 方法時安全地篩選訊息，但前提是 <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=fullName> 實作必須：<br /><br /> <ul><li>則會執行下列其中一項或兩項：<br /><br /> <ul><li>呼叫 <xref:System.Windows.Forms.Application.AddMessageFilter%2A> 方法來新增訊息篩選器。</li><li>呼叫 <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> 方法來移除訊息篩選器。 方法。</li></ul></li><li>**而且**藉由呼叫 <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=fullName> 方法來提取訊息。</li></ul><br /> 在以舊版 .NET Framework 為目標的 Windows Forms 應用程式中，這類實作在某些情況下會在呼叫 <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName> 方法時，擲回 <xref:System.IndexOutOfRangeException> 例外狀況|這項變更會影響所有目標為 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 的應用程式。 目標為舊版 .NET Framework 的應用程式不會受到影響。<br /><br /> 不過，以 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 為目標的應用程式可以選擇不使用這種行為。 此外，以舊版 .NET Framework 為目標但在 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 下執行的應用程式，可以選擇使用這種行為。 如需詳細資訊，請參閱[風險降低：自訂 IMessageFilter.PreFilterMessage 實作](../../../docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md)。|Edge|  
  
## <a name="see-also"></a>另請參閱  
 [4.6.1 中的應用程式相容性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)
