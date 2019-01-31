---
title: <claimTypeRequirements> 的 <message>
ms.date: 03/30/2017
ms.assetid: f95c5ecd-abb6-4b77-a6d7-a38727f4a142
ms.openlocfilehash: 9cf77f6c026df5f78cc8ae6e6783e91f1c86e282
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55256599"
---
# <a name="claimtyperequirements-for-message"></a><span data-ttu-id="09444-102">\<claimTypeRequirements > 針對\<訊息 ></span><span class="sxs-lookup"><span data-stu-id="09444-102">\<claimTypeRequirements> for \<message></span></span>
<span data-ttu-id="09444-103">指定必要宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="09444-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="09444-104">服務會使用這個集合，指定發行的權杖中的必要與選用的宣告，而用戶端會使用此權杖存取服務。</span><span class="sxs-lookup"><span data-stu-id="09444-104">The collection is used by the service to specify any required and optional claims which must be in the issued token the client uses to access the service.</span></span> <span data-ttu-id="09444-105">如果啟用 WSDL 發行，但 WCF 不要求發行的權杖中含有指定的宣告型別，則服務會在中繼資料公開需要的宣告型別。</span><span class="sxs-lookup"><span data-stu-id="09444-105">The service exposes the required claim types in metadata if WSDL publishing is enabled but WCF does not require the issued token contain the specified claim types.</span></span> <span data-ttu-id="09444-106">如果服務希望強制需要的宣告型別要出現，應使用授權原則。</span><span class="sxs-lookup"><span data-stu-id="09444-106">Services wishing to enforce required claim types are present should do using authorization policy.</span></span>  
  
 <span data-ttu-id="09444-107">在聯合用戶端上，此集合包含必要與選用宣告的清單，用戶端要求發行的權杖時，此清單會傳送給安全性權杖服務。</span><span class="sxs-lookup"><span data-stu-id="09444-107">On federated clients, this collection contains the list of required and optional claims which is sent to the security token service in the client’s request for an issued token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09444-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09444-108">See also</span></span>
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
