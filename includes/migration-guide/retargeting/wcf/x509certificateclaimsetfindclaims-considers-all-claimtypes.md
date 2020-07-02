---
ms.openlocfilehash: abef47c64a7cfd99c5b50bf2100401a2d5fcc5c3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614356"
---
### <a name="x509certificateclaimsetfindclaims-considers-all-claimtypes"></a><span data-ttu-id="6b859-101">X509CertificateClaimSet.FindClaims 會考慮所有 claimTypes</span><span class="sxs-lookup"><span data-stu-id="6b859-101">X509CertificateClaimSet.FindClaims Considers All claimTypes</span></span>

#### <a name="details"></a><span data-ttu-id="6b859-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6b859-102">Details</span></span>

<span data-ttu-id="6b859-103">在目標為 .NET Framework 4.6.1 的應用程式中，如果 X509 宣告集是初始化自 SAN 欄位中含有多個 DNS 項目的憑證，<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> 方法會嘗試使用所有 DNS 項目來比對 claimType 引數。若是以舊版 .NET Framework 為目標的應用程式，則 <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> 方法僅會嘗試使 claimType 引數符合最後一個 DNS 項目。</span><span class="sxs-lookup"><span data-stu-id="6b859-103">In apps that target the .NET Framework 4.6.1, if an X509 claim set is initialized from a certificate that has multiple DNS entries in its SAN field, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> method attempts to match the claimType argument with all the DNS entries.For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> method attempts to match the claimType argument only with the last DNS entry.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6b859-104">建議</span><span class="sxs-lookup"><span data-stu-id="6b859-104">Suggestion</span></span>

<span data-ttu-id="6b859-105">這項變更只會影響以 .NET Framework 4.6.1 為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6b859-105">This change only affects applications targeting the .NET Framework 4.6.1.</span></span> <span data-ttu-id="6b859-106">您可以使用 [DisableMultipleDNSEntries](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation) 相容性參數來停用這項變更 (如果以 4.6.1 以前版本為目標則可啟用)。</span><span class="sxs-lookup"><span data-stu-id="6b859-106">This change may be disabled (or enabled if targeting pre-4.6.1) with the [DisableMultipleDNSEntries](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation) compatibility switch.</span></span>

| <span data-ttu-id="6b859-107">名稱</span><span class="sxs-lookup"><span data-stu-id="6b859-107">Name</span></span>    | <span data-ttu-id="6b859-108">值</span><span class="sxs-lookup"><span data-stu-id="6b859-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6b859-109">影響範圍</span><span class="sxs-lookup"><span data-stu-id="6b859-109">Scope</span></span>   | <span data-ttu-id="6b859-110">Minor</span><span class="sxs-lookup"><span data-stu-id="6b859-110">Minor</span></span>       |
| <span data-ttu-id="6b859-111">版本</span><span class="sxs-lookup"><span data-stu-id="6b859-111">Version</span></span> | <span data-ttu-id="6b859-112">4.6.1</span><span class="sxs-lookup"><span data-stu-id="6b859-112">4.6.1</span></span>       |
| <span data-ttu-id="6b859-113">類型</span><span class="sxs-lookup"><span data-stu-id="6b859-113">Type</span></span>    | <span data-ttu-id="6b859-114">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="6b859-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="6b859-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="6b859-115">Affected APIs</span></span>

- <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=nameWithType>
