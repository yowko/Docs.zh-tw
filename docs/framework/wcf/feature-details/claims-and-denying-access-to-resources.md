---
title: "宣告與拒絕資源的存取"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: claims [WCF], denying access to resources
ms.assetid: 145ebb41-680e-4256-b14c-1efb4af1e982
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2b94c8b77cd659438ec26129137dd9b8cab056b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="claims-and-denying-access-to-resources"></a><span data-ttu-id="2c0c9-102">宣告與拒絕資源的存取</span><span class="sxs-lookup"><span data-stu-id="2c0c9-102">Claims and Denying Access to Resources</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="2c0c9-103"> 支援宣告架構的授權機制。</span><span class="sxs-lookup"><span data-stu-id="2c0c9-103"> supports a claims-based authorization mechanism.</span></span> <span data-ttu-id="2c0c9-104">就像根據宣告的存在而允許存取資源，系統也經常會根據宣告的存在而拒絕存取資源。</span><span class="sxs-lookup"><span data-stu-id="2c0c9-104">As well as allowing access to resources based on the presence of claims, systems often deny access to resources based on the presence of claims.</span></span> <span data-ttu-id="2c0c9-105">這類系統應該在尋找會導致允許存取的宣告之前，先檢查 <xref:System.IdentityModel.Policy.AuthorizationContext> 是否有會導致拒絕存取的宣告。</span><span class="sxs-lookup"><span data-stu-id="2c0c9-105">Such systems should examine the <xref:System.IdentityModel.Policy.AuthorizationContext> for claims that result in access being denied before looking for claims that result in access being allowed.</span></span>  
  
 <span data-ttu-id="2c0c9-106">例如，系統可能只會在任何人擁有類型為 `Age`、權限為 <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> 且資源值為 `Under 21` 的宣告，而此身分識別又同時擁有類型為 `Name`、權限為 <xref:System.IdentityModel.Claims.Rights.Identity%2A> 且資源值為 `Mallory` 的宣告時，才拒絕該人員對資源的存取。</span><span class="sxs-lookup"><span data-stu-id="2c0c9-106">For example, a system might deny access to a resource to anyone who has a claim with a type of `Age`, a right of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>, and a resource value of `Under 21` only when that identity also has a claim of type `Name`, a right of <xref:System.IdentityModel.Claims.Rights.Identity%2A>, and a resource value of `Mallory`.</span></span> <span data-ttu-id="2c0c9-107">換句話說，此系統會拒絕低於 21 歲的任何人的存取，而在名稱為 Mallory 時授與存取。</span><span class="sxs-lookup"><span data-stu-id="2c0c9-107">Put another way, the system denies access to anyone who is under 21 years old and grants access when the name is Mallory.</span></span> <span data-ttu-id="2c0c9-108">為了正確地實作這項語意，這時先尋找 `Age` 宣告並判斷年齡是否低於 21 歲是非常重要的步驟。</span><span class="sxs-lookup"><span data-stu-id="2c0c9-108">To correctly implement this semantic, it is important to look for the `Age` claim first and determine whether the age is under 21 years old.</span></span> <span data-ttu-id="2c0c9-109">否則，如果 Mallory 低於 21 歲，這時可能就只會根據 `Name` 宣告基礎來授與資源的存取。</span><span class="sxs-lookup"><span data-stu-id="2c0c9-109">Otherwise, if Mallory is under 21, then the resource may be granted access solely on the basis of the `Name` claim.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c0c9-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c0c9-110">See Also</span></span>  
 [<span data-ttu-id="2c0c9-111">管理宣告和授權與身分識別模型</span><span class="sxs-lookup"><span data-stu-id="2c0c9-111">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [<span data-ttu-id="2c0c9-112">宣告與權杖</span><span class="sxs-lookup"><span data-stu-id="2c0c9-112">Claims and Tokens</span></span>](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)
