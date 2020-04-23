---
title: 風險降低：X509CertificateClaimSet.FindClaims 方法
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
ms.openlocfilehash: 0b306960c4f11bb6f54aecaeb13297e7725e16a8
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102641"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="2c16e-102">風險降低：X509CertificateClaimSet.FindClaims 方法</span><span class="sxs-lookup"><span data-stu-id="2c16e-102">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>

<span data-ttu-id="2c16e-103">從以 .NET Framework 4.6.1 為目標<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType>的應用開始,`claimType`該方法將嘗試 將參數與其 SAN 欄位中的所有 DNS 條目匹配。</span><span class="sxs-lookup"><span data-stu-id="2c16e-103">Starting with apps that target .NET Framework 4.6.1, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="2c16e-104">影響</span><span class="sxs-lookup"><span data-stu-id="2c16e-104">Impact</span></span>  
 <span data-ttu-id="2c16e-105">這項變更只會影響以 .NET Framework 4.6.1 和更新版本為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="2c16e-105">This change only affects apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>  
  
 <span data-ttu-id="2c16e-106">若是以舊版 .NET Framework 為目標的應用程式，則 <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> 方法僅會嘗試使 `claimType` 引數符合最後一個 DNS 項目。</span><span class="sxs-lookup"><span data-stu-id="2c16e-106">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="2c16e-107">降低</span><span class="sxs-lookup"><span data-stu-id="2c16e-107">Mitigation</span></span>  
 <span data-ttu-id="2c16e-108">如果此變更不可取,則以 .NET Framework 4.6.1 開頭的 .NET Framework 版本為目標的應用可以通過將以下設定設定添加到應用設定檔的[\<執行時>](../configure-apps/file-schema/runtime/runtime-element.md)部分來選擇宣告:</span><span class="sxs-lookup"><span data-stu-id="2c16e-108">If this change is undesirable, apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1 can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />
</runtime>  
```  
  
 <span data-ttu-id="2c16e-109">此外,針對 .NET Framework 的早期版本並在 .NET Framework 4.6.1 和更高版本下運行的應用可以通過將以下配置設置添加到應用配置檔的[\<執行時>](../configure-apps/file-schema/runtime/runtime-element.md)部分來選擇加入此行為:</span><span class="sxs-lookup"><span data-stu-id="2c16e-109">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2c16e-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c16e-110">See also</span></span>

- [<span data-ttu-id="2c16e-111">應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="2c16e-111">Application compatibility</span></span>](application-compatibility.md)
