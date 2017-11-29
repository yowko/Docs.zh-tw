---
title: "在 ClaimSet 中尋找宣告"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], finding in a claimset
- claims [WCF]
ms.assetid: a76ce107-aeb3-47d0-bfa9-134c53664e20
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cc6a4d98529357aa58f55be2fc33d6b7a95a8999
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="finding-claims-in-a-claimset"></a><span data-ttu-id="8c2a6-102">在 ClaimSet 中尋找宣告</span><span class="sxs-lookup"><span data-stu-id="8c2a6-102">Finding Claims in a ClaimSet</span></span>
<span data-ttu-id="8c2a6-103">檢查 <xref:System.IdentityModel.Claims.ClaimSet> 內容以尋找特定類型的宣告，是在使用宣告架構授權時的常見工作。</span><span class="sxs-lookup"><span data-stu-id="8c2a6-103">Examining the content of a <xref:System.IdentityModel.Claims.ClaimSet> for particular types of claims is a common task when using claim-based authorization.</span></span> <span data-ttu-id="8c2a6-104">若要檢查 <xref:System.IdentityModel.Claims.ClaimSet> 是否存在特定的宣告，請使用 <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="8c2a6-104">To examine a <xref:System.IdentityModel.Claims.ClaimSet> for the presence of particular claims, use the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> method.</span></span> <span data-ttu-id="8c2a6-105">這個方法比直接在 <xref:System.IdentityModel.Claims.ClaimSet> 上逐一查看提供更高的效能。</span><span class="sxs-lookup"><span data-stu-id="8c2a6-105">This method provides better performance than iterating directly over the <xref:System.IdentityModel.Claims.ClaimSet>.</span></span> <span data-ttu-id="8c2a6-106">下列範例會示範這種使用方式。</span><span class="sxs-lookup"><span data-stu-id="8c2a6-106">The following example demonstrates this usage.</span></span> <span data-ttu-id="8c2a6-107">請注意，`claimType` 和 `claimRight` 參數可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="8c2a6-107">Note that the `claimType` and `claimRight` parameters can be `null`.</span></span> <span data-ttu-id="8c2a6-108">在此情況下，這些參數將比對所有的宣告類型和宣告權限。</span><span class="sxs-lookup"><span data-stu-id="8c2a6-108">In that case, the parameters will match all claim types and claim rights.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c2a6-109">範例</span><span class="sxs-lookup"><span data-stu-id="8c2a6-109">Example</span></span>  
 [!code-csharp[c_FindClaimsPerf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_findclaimsperf/cs/c_findclaimsperf.cs#2)]
 [!code-vb[c_FindClaimsPerf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_findclaimsperf/vb/c_findclaimsperf.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="8c2a6-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c2a6-110">See Also</span></span>  
 [<span data-ttu-id="8c2a6-111">管理宣告和授權與身分識別模型</span><span class="sxs-lookup"><span data-stu-id="8c2a6-111">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
