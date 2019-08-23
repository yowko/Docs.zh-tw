---
title: SAML 權杖與宣告
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
- issued tokens
- SAML token
ms.assetid: 930b6e34-9eab-4e95-826c-4e06659bb977
ms.openlocfilehash: 7037daf299d7c750ab398c21c1d7ccb541620701
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943069"
---
# <a name="saml-tokens-and-claims"></a><span data-ttu-id="6482e-102">SAML 權杖與宣告</span><span class="sxs-lookup"><span data-stu-id="6482e-102">SAML Tokens and Claims</span></span>
<span data-ttu-id="6482e-103">安全性判斷提示標記語言 (SAML)*權杖*是宣告的 XML 標記法。</span><span class="sxs-lookup"><span data-stu-id="6482e-103">Security Assertions Markup Language (SAML) *tokens* are XML representations of claims.</span></span> <span data-ttu-id="6482e-104">根據預設, 在同盟安全性案例中使用的 SAML 權杖 Windows Communication Foundation (WCF) 會*發行權杖*。</span><span class="sxs-lookup"><span data-stu-id="6482e-104">By default, SAML tokens Windows Communication Foundation (WCF) uses in federated security scenarios are *issued tokens*.</span></span>  
  
 <span data-ttu-id="6482e-105">SAML 權杖包含一實體對另一實體所做出之宣告集合的陳述式。</span><span class="sxs-lookup"><span data-stu-id="6482e-105">SAML tokens carry statements that are sets of claims made by one entity about another entity.</span></span> <span data-ttu-id="6482e-106">例如，在聯合安全性案例中，陳述式是由系統中關於使用者的安全性權杖服務所表示。</span><span class="sxs-lookup"><span data-stu-id="6482e-106">For example, in federated security scenarios, the statements are made by a security token service about a user in the system.</span></span> <span data-ttu-id="6482e-107">安全性權杖服務會簽署 SAML 權杖，以表示權杖中所含陳述式的真實性。</span><span class="sxs-lookup"><span data-stu-id="6482e-107">The security token service signs the SAML token to indicate the veracity of the statements contained in the token.</span></span> <span data-ttu-id="6482e-108">除此之外，SAML 權杖會與 SAML 權杖使用者證實知悉的密碼編譯金鑰內容產生關聯。</span><span class="sxs-lookup"><span data-stu-id="6482e-108">In addition, the SAML token is associated with cryptographic key material that the user of the SAML token proves knowledge of.</span></span> <span data-ttu-id="6482e-109">這項證明能滿足信賴憑證者，證實該 SAML 權杖確實簽發至該使用者。</span><span class="sxs-lookup"><span data-stu-id="6482e-109">This proof satisfies the relying party that the SAML token was, in fact, issued to that user.</span></span> <span data-ttu-id="6482e-110">例如，在典型的案例中：</span><span class="sxs-lookup"><span data-stu-id="6482e-110">For example, in a typical scenario:</span></span>  
  
1. <span data-ttu-id="6482e-111">用戶端向安全性權杖服務要求 SAML 權杖，藉由使用 Windows 認證，驗證至該安全性權杖服務。</span><span class="sxs-lookup"><span data-stu-id="6482e-111">A client requests a SAML token from a security token service, authenticating to that security token service by using Windows credentials.</span></span>  
  
2. <span data-ttu-id="6482e-112">安全性權杖服務簽發 SAML 權杖至用戶端。</span><span class="sxs-lookup"><span data-stu-id="6482e-112">The security token service issues a SAML token to the client.</span></span> <span data-ttu-id="6482e-113">SAML 權杖是以與安全性權杖服務相關的憑證進行簽署，並且包含針對目標服務加密的證明金鑰。</span><span class="sxs-lookup"><span data-stu-id="6482e-113">The SAML token is signed with a certificate associated with the security token service and contains a proof key encrypted for the target service.</span></span>  
  
3. <span data-ttu-id="6482e-114">用戶端也會收到*證明金鑰*的複本。</span><span class="sxs-lookup"><span data-stu-id="6482e-114">The client also receives a copy of the *proof key*.</span></span> <span data-ttu-id="6482e-115">然後, 用戶端會向應用程式服務 (*信賴*憑證者) 出示 SAML 權杖, 並使用該證明金鑰來簽署訊息。</span><span class="sxs-lookup"><span data-stu-id="6482e-115">The client then presents the SAML token to the application service (the *relying party*) and signs the message with that proof key.</span></span>  
  
4. <span data-ttu-id="6482e-116">SAML 權杖上的簽章會告訴信賴憑證者，這是由安全性權杖服務所簽發的權杖。</span><span class="sxs-lookup"><span data-stu-id="6482e-116">The signature over the SAML token tells the relying party that the security token service issued the token.</span></span> <span data-ttu-id="6482e-117">使用證明金鑰所建立的訊息簽章會告訴信賴憑證者，該權杖曾簽發至用戶端。</span><span class="sxs-lookup"><span data-stu-id="6482e-117">The message signature created with the proof key tells the relying party that the token was issued to the client.</span></span>  
  
## <a name="from-claims-to-samlattributes"></a><span data-ttu-id="6482e-118">從宣告到 SamlAttributes</span><span class="sxs-lookup"><span data-stu-id="6482e-118">From Claims to SamlAttributes</span></span>  
 <span data-ttu-id="6482e-119">在 WCF 中, SAML 權杖中的語句會<xref:System.IdentityModel.Tokens.SamlAttribute>模型化為物件, <xref:System.IdentityModel.Claims.Claim.Right%2A> <xref:System.IdentityModel.Claims.Claim>如果物件具有的<xref:System.IdentityModel.Claims.Claim> <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>屬性為, 且<xref:System.IdentityModel.Claims.Claim.Resource%2A>屬性為, 則可以直接從物件填入輸入<xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="6482e-119">In WCF, statements in SAML tokens are modeled as <xref:System.IdentityModel.Tokens.SamlAttribute> objects, which can be populated directly from <xref:System.IdentityModel.Claims.Claim> objects, provided the <xref:System.IdentityModel.Claims.Claim> object has a <xref:System.IdentityModel.Claims.Claim.Right%2A> property of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> and the <xref:System.IdentityModel.Claims.Claim.Resource%2A> property is of type <xref:System.String>.</span></span> <span data-ttu-id="6482e-120">例如：</span><span class="sxs-lookup"><span data-stu-id="6482e-120">For example:</span></span>  
  
 [!code-csharp[c_CreateSTS#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#8)]
 [!code-vb[c_CreateSTS#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#8)]  
  
> [!NOTE]
> <span data-ttu-id="6482e-121">當 SAML 權杖在訊息中序列化，不論是當這些權杖是安全性權杖服務所核發，或是當這些權杖由用戶端視為驗證的一部分提供至服務，訊息大小配額上限必須大到足以容納 SAML 權杖及其他訊息部分。</span><span class="sxs-lookup"><span data-stu-id="6482e-121">When SAML tokens are serialized in messages, either when they are issued by a security token service or when they are presented by clients to services as part of authentication, the maximum message size quota must be sufficiently large to accommodate the SAML token and the other message parts.</span></span> <span data-ttu-id="6482e-122">正常情況下，預設訊息大小配額應足夠。</span><span class="sxs-lookup"><span data-stu-id="6482e-122">In normal cases, the default message size quotas are sufficient.</span></span> <span data-ttu-id="6482e-123">然而，若 SAML 權杖因為包含數百個宣告而變很大時，您可能需要增加配額以容納序列化的權杖。</span><span class="sxs-lookup"><span data-stu-id="6482e-123">However, in cases where a SAML token is large because it contains hundreds of claims, you may need to increase the quotas to accommodate the serialized token.</span></span> <span data-ttu-id="6482e-124">如需詳細資訊, 請參閱[資料的安全性考慮](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)。</span><span class="sxs-lookup"><span data-stu-id="6482e-124">For more information, see [Security Considerations for Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span></span>  
  
## <a name="from-samlattributes-to-claims"></a><span data-ttu-id="6482e-125">從 SamlAttributes 到宣告</span><span class="sxs-lookup"><span data-stu-id="6482e-125">From SamlAttributes to Claims</span></span>  
 <span data-ttu-id="6482e-126">當 SAML 權杖在訊息內接收時，SAML 權杖內的各種陳述式會轉變成 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> 物件，置於 <xref:System.IdentityModel.Policy.AuthorizationContext>之內。</span><span class="sxs-lookup"><span data-stu-id="6482e-126">When SAML tokens are received in messages, the various statements in the SAML token are turned into <xref:System.IdentityModel.Policy.IAuthorizationPolicy> objects that are placed into the <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span> <span data-ttu-id="6482e-127">來自每個 SAML 陳述式的宣告均由 <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> 的 <xref:System.IdentityModel.Policy.AuthorizationContext> 屬性傳回，並且可進行檢查以決定是否驗證並授權使用者。</span><span class="sxs-lookup"><span data-stu-id="6482e-127">The claims from each SAML statement are returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> and can be examined to determine whether to authenticate and authorize the user.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6482e-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6482e-128">See also</span></span>

- <xref:System.IdentityModel.Policy.AuthorizationContext>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- <xref:System.IdentityModel.Claims.ClaimSet>
- [<span data-ttu-id="6482e-129">同盟</span><span class="sxs-lookup"><span data-stu-id="6482e-129">Federation</span></span>](../../../../docs/framework/wcf/feature-details/federation.md)
- [<span data-ttu-id="6482e-130">如何：建立同盟用戶端</span><span class="sxs-lookup"><span data-stu-id="6482e-130">How to: Create a Federated Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="6482e-131">如何：在同盟服務上設定認證</span><span class="sxs-lookup"><span data-stu-id="6482e-131">How to: Configure Credentials on a Federation Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="6482e-132">使用身分識別模型來管理宣告與授權</span><span class="sxs-lookup"><span data-stu-id="6482e-132">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [<span data-ttu-id="6482e-133">宣告與權杖</span><span class="sxs-lookup"><span data-stu-id="6482e-133">Claims and Tokens</span></span>](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)
- [<span data-ttu-id="6482e-134">宣告建立與資源值</span><span class="sxs-lookup"><span data-stu-id="6482e-134">Claim Creation and Resource Values</span></span>](../../../../docs/framework/wcf/feature-details/claim-creation-and-resource-values.md)
- [<span data-ttu-id="6482e-135">如何：建立自訂宣告</span><span class="sxs-lookup"><span data-stu-id="6482e-135">How to: Create a Custom Claim</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
