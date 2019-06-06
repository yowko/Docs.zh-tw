---
title: 風險降低：X509CertificateClaimSet.FindClaims 方法
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7fb1eb0c502584caac11ca3dde6e7e646b29cfe
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251085"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="0ffdd-102">風險降低：X509CertificateClaimSet.FindClaims 方法</span><span class="sxs-lookup"><span data-stu-id="0ffdd-102">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>
<span data-ttu-id="0ffdd-103">從以 .NET Framework 4.6.1 為目標的應用程式開始，<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> 方法會嘗試使 `claimType` 引數符合其 SAN 欄位中的所有 DNS 項目。</span><span class="sxs-lookup"><span data-stu-id="0ffdd-103">Starting with apps that target the .NET Framework 4.6.1,  the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="0ffdd-104">影響</span><span class="sxs-lookup"><span data-stu-id="0ffdd-104">Impact</span></span>  
 <span data-ttu-id="0ffdd-105">這項變更只會影響以 .NET Framework 4.6.1 和更新版本為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0ffdd-105">This change only affects apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>  
  
 <span data-ttu-id="0ffdd-106">若是以舊版 .NET Framework 為目標的應用程式，則 <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> 方法僅會嘗試使 `claimType` 引數符合最後一個 DNS 項目。</span><span class="sxs-lookup"><span data-stu-id="0ffdd-106">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="0ffdd-107">緩和</span><span class="sxs-lookup"><span data-stu-id="0ffdd-107">Mitigation</span></span>  
 <span data-ttu-id="0ffdd-108">如果這不是您要的變更，以 .NET Framework 4.6.1 和更新版本為目標的應用程式，可以藉由將下列組態設定新增至應用程式組態檔的[\<執行階段>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段，來選擇退出這項行為：</span><span class="sxs-lookup"><span data-stu-id="0ffdd-108">If this change is undesirable, apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1 can opt out of it by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
```  
  
 <span data-ttu-id="0ffdd-109">此外，以舊版 .NET Framework 為目標，但在 .NET Framework 4.6.1 和更新版本下執行的應用程式，可以藉由將下列組態設定新增至應用程式組態檔的[\<執行階段>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段，來選擇加入這項行為：</span><span class="sxs-lookup"><span data-stu-id="0ffdd-109">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0ffdd-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ffdd-110">See also</span></span>

- [<span data-ttu-id="0ffdd-111">重定目標變更</span><span class="sxs-lookup"><span data-stu-id="0ffdd-111">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
