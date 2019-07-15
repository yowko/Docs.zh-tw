---
ms.openlocfilehash: 1ece2bb2d5e4ce93f201536d03aabeff5eb0012e
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804354"
---
### <a name="x509certificateclaimsetfindclaims-considers-all-claimtypes"></a><span data-ttu-id="e7d2f-101">X509CertificateClaimSet.FindClaims 會考慮所有 claimTypes</span><span class="sxs-lookup"><span data-stu-id="e7d2f-101">X509CertificateClaimSet.FindClaims Considers All claimTypes</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e7d2f-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e7d2f-102">Details</span></span>|<span data-ttu-id="e7d2f-103">在目標為 .NET Framework 4.6.1 的應用程式中，如果 X509 宣告集是初始化自 SAN 欄位中含有多個 DNS 項目的憑證，<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> 方法會嘗試使用所有 DNS 項目來比對 claimType 引數。若是以舊版 .NET Framework 為目標的應用程式，則 <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> 方法僅會嘗試使 claimType 引數符合最後一個 DNS 項目。</span><span class="sxs-lookup"><span data-stu-id="e7d2f-103">In apps that target the .NET Framework 4.6.1, if an X509 claim set is initialized from a certificate that has multiple DNS entries in its SAN field, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> method attempts to match the claimType argument with all the DNS entries.For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> method attempts to match the claimType argument only with the last DNS entry.</span></span>|
|<span data-ttu-id="e7d2f-104">建議</span><span class="sxs-lookup"><span data-stu-id="e7d2f-104">Suggestion</span></span>|<span data-ttu-id="e7d2f-105">這項變更只會影響以 .NET Framework 4.6.1 為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e7d2f-105">This change only affects applications targeting the .NET Framework 4.6.1.</span></span> <span data-ttu-id="e7d2f-106">您可以使用 [DisableMultipleDNSEntries](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation) 相容性參數來停用這項變更 (如果以 4.6.1 以前版本為目標則可啟用)。</span><span class="sxs-lookup"><span data-stu-id="e7d2f-106">This change may be disabled (or enabled if targetting pre-4.6.1) with the [DisableMultipleDNSEntries](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation) compatibility switch.</span></span>|
|<span data-ttu-id="e7d2f-107">範圍</span><span class="sxs-lookup"><span data-stu-id="e7d2f-107">Scope</span></span>|<span data-ttu-id="e7d2f-108">次要</span><span class="sxs-lookup"><span data-stu-id="e7d2f-108">Minor</span></span>|
|<span data-ttu-id="e7d2f-109">版本</span><span class="sxs-lookup"><span data-stu-id="e7d2f-109">Version</span></span>|<span data-ttu-id="e7d2f-110">4.6.1</span><span class="sxs-lookup"><span data-stu-id="e7d2f-110">4.6.1</span></span>|
|<span data-ttu-id="e7d2f-111">類型</span><span class="sxs-lookup"><span data-stu-id="e7d2f-111">Type</span></span>|<span data-ttu-id="e7d2f-112">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="e7d2f-112">Retargeting</span></span>|
|<span data-ttu-id="e7d2f-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="e7d2f-113">Affected APIs</span></span>|<ul><li><xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=nameWithType></li></ul>|

