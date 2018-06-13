---
title: 在 ClaimSet 中尋找宣告
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], finding in a claimset
- claims [WCF]
ms.assetid: a76ce107-aeb3-47d0-bfa9-134c53664e20
ms.openlocfilehash: 7ca22d701277e71e509e6b291eb59a0223a0250c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488594"
---
# <a name="finding-claims-in-a-claimset"></a><span data-ttu-id="68205-102">在 ClaimSet 中尋找宣告</span><span class="sxs-lookup"><span data-stu-id="68205-102">Finding Claims in a ClaimSet</span></span>
<span data-ttu-id="68205-103">檢查 <xref:System.IdentityModel.Claims.ClaimSet> 內容以尋找特定類型的宣告，是在使用宣告架構授權時的常見工作。</span><span class="sxs-lookup"><span data-stu-id="68205-103">Examining the content of a <xref:System.IdentityModel.Claims.ClaimSet> for particular types of claims is a common task when using claim-based authorization.</span></span> <span data-ttu-id="68205-104">若要檢查 <xref:System.IdentityModel.Claims.ClaimSet> 是否存在特定的宣告，請使用 <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="68205-104">To examine a <xref:System.IdentityModel.Claims.ClaimSet> for the presence of particular claims, use the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> method.</span></span> <span data-ttu-id="68205-105">這個方法比直接在 <xref:System.IdentityModel.Claims.ClaimSet> 上逐一查看提供更高的效能。</span><span class="sxs-lookup"><span data-stu-id="68205-105">This method provides better performance than iterating directly over the <xref:System.IdentityModel.Claims.ClaimSet>.</span></span> <span data-ttu-id="68205-106">下列範例會示範這種使用方式。</span><span class="sxs-lookup"><span data-stu-id="68205-106">The following example demonstrates this usage.</span></span> <span data-ttu-id="68205-107">請注意，`claimType` 和 `claimRight` 參數可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="68205-107">Note that the `claimType` and `claimRight` parameters can be `null`.</span></span> <span data-ttu-id="68205-108">在此情況下，這些參數將比對所有的宣告類型和宣告權限。</span><span class="sxs-lookup"><span data-stu-id="68205-108">In that case, the parameters will match all claim types and claim rights.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68205-109">範例</span><span class="sxs-lookup"><span data-stu-id="68205-109">Example</span></span>  
 [!code-csharp[c_FindClaimsPerf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_findclaimsperf/cs/c_findclaimsperf.cs#2)]
 [!code-vb[c_FindClaimsPerf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_findclaimsperf/vb/c_findclaimsperf.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="68205-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68205-110">See Also</span></span>  
 [<span data-ttu-id="68205-111">使用身分識別模型來管理宣告與授權</span><span class="sxs-lookup"><span data-stu-id="68205-111">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
