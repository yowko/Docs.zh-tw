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
ms.openlocfilehash: 81212d5b85ec516ae69c9c015c147cd011a9fd14
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495094"
---
# <a name="finding-claims-in-a-claimset"></a><span data-ttu-id="2d976-102">在 ClaimSet 中尋找宣告</span><span class="sxs-lookup"><span data-stu-id="2d976-102">Finding Claims in a ClaimSet</span></span>
<span data-ttu-id="2d976-103">檢查 <xref:System.IdentityModel.Claims.ClaimSet> 內容以尋找特定類型的宣告，是在使用宣告架構授權時的常見工作。</span><span class="sxs-lookup"><span data-stu-id="2d976-103">Examining the content of a <xref:System.IdentityModel.Claims.ClaimSet> for particular types of claims is a common task when using claim-based authorization.</span></span> <span data-ttu-id="2d976-104">若要檢查 <xref:System.IdentityModel.Claims.ClaimSet> 是否存在特定的宣告，請使用 <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="2d976-104">To examine a <xref:System.IdentityModel.Claims.ClaimSet> for the presence of particular claims, use the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> method.</span></span> <span data-ttu-id="2d976-105">這個方法比直接在 <xref:System.IdentityModel.Claims.ClaimSet> 上逐一查看提供更高的效能。</span><span class="sxs-lookup"><span data-stu-id="2d976-105">This method provides better performance than iterating directly over the <xref:System.IdentityModel.Claims.ClaimSet>.</span></span> <span data-ttu-id="2d976-106">下列範例會示範這種使用方式。</span><span class="sxs-lookup"><span data-stu-id="2d976-106">The following example demonstrates this usage.</span></span> <span data-ttu-id="2d976-107">請注意，`claimType` 和 `claimRight` 參數可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="2d976-107">Note that the `claimType` and `claimRight` parameters can be `null`.</span></span> <span data-ttu-id="2d976-108">在此情況下，這些參數將比對所有的宣告類型和宣告權限。</span><span class="sxs-lookup"><span data-stu-id="2d976-108">In that case, the parameters will match all claim types and claim rights.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d976-109">範例</span><span class="sxs-lookup"><span data-stu-id="2d976-109">Example</span></span>  
 [!code-csharp[c_FindClaimsPerf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_findclaimsperf/cs/c_findclaimsperf.cs#2)]
 [!code-vb[c_FindClaimsPerf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_findclaimsperf/vb/c_findclaimsperf.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="2d976-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d976-110">See also</span></span>
- [<span data-ttu-id="2d976-111">使用身分識別模型來管理宣告與授權</span><span class="sxs-lookup"><span data-stu-id="2d976-111">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
