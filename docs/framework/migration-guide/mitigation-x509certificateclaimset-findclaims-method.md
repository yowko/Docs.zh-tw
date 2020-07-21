---
title: 風險降低：X509CertificateClaimSet.FindClaims 方法
description: 瞭解以 .NET Framework 4.6.1 為目標之應用程式的 X509CertificateClaimSet. FindClaims 方法已變更。
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
ms.openlocfilehash: 304d8fb5adc27b33f2410faaaf8662e0ff9be66d
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475316"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="45ec4-103">風險降低：X509CertificateClaimSet.FindClaims 方法</span><span class="sxs-lookup"><span data-stu-id="45ec4-103">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>

<span data-ttu-id="45ec4-104">從以 .NET Framework 4.6.1 為目標的應用程式開始， <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> 方法會嘗試將 `claimType` 引數與 SAN 欄位中的所有 DNS 專案進行比對。</span><span class="sxs-lookup"><span data-stu-id="45ec4-104">Starting with apps that target .NET Framework 4.6.1, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="45ec4-105">影響</span><span class="sxs-lookup"><span data-stu-id="45ec4-105">Impact</span></span>  
 <span data-ttu-id="45ec4-106">這項變更只會影響以 .NET Framework 4.6.1 和更新版本為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="45ec4-106">This change only affects apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>  
  
 <span data-ttu-id="45ec4-107">若是以舊版 .NET Framework 為目標的應用程式，則 <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> 方法僅會嘗試使 `claimType` 引數符合最後一個 DNS 項目。</span><span class="sxs-lookup"><span data-stu-id="45ec4-107">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="45ec4-108">降低</span><span class="sxs-lookup"><span data-stu-id="45ec4-108">Mitigation</span></span>  
 <span data-ttu-id="45ec4-109">如果不需要這項變更，以 .NET Framework 4.6.1 開頭之 .NET Framework 版本的應用程式可以藉由在 [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) 應用程式佈建檔的區段中新增下列設定，來退出宣告：</span><span class="sxs-lookup"><span data-stu-id="45ec4-109">If this change is undesirable, apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1 can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />
</runtime>  
```  
  
 <span data-ttu-id="45ec4-110">此外，以舊版 .NET Framework 為目標但在 .NET Framework 4.6.1 和更新版本下執行的應用程式，可以藉由在 [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) 應用程式佈建檔的區段中新增下列設定，來加入宣告此行為：</span><span class="sxs-lookup"><span data-stu-id="45ec4-110">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="45ec4-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45ec4-111">See also</span></span>

- [<span data-ttu-id="45ec4-112">應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="45ec4-112">Application compatibility</span></span>](application-compatibility.md)
