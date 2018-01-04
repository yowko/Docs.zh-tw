---
title: "SAML 權杖與宣告"
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
- WCF, federation
- federation
- issued tokens
- SAML token
ms.assetid: 930b6e34-9eab-4e95-826c-4e06659bb977
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a2b35ba4da503663a2bb92597ed193c408e7c99b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="saml-tokens-and-claims"></a><span data-ttu-id="4cb38-102">SAML 權杖與宣告</span><span class="sxs-lookup"><span data-stu-id="4cb38-102">SAML Tokens and Claims</span></span>
<span data-ttu-id="4cb38-103">安全性判斷提示標記語言 (SAML)*語彙基元*宣告的 XML 表示。</span><span class="sxs-lookup"><span data-stu-id="4cb38-103">Security Assertions Markup Language (SAML) *tokens* are XML representations of claims.</span></span> <span data-ttu-id="4cb38-104">根據預設，SAML 權杖[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]聯合的安全性案例中的用法是*發行的權杖*。</span><span class="sxs-lookup"><span data-stu-id="4cb38-104">By default, SAML tokens [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uses in federated security scenarios are *issued tokens*.</span></span>  
  
 <span data-ttu-id="4cb38-105">SAML 權杖包含一實體對另一實體所做出之宣告集合的陳述式。</span><span class="sxs-lookup"><span data-stu-id="4cb38-105">SAML tokens carry statements that are sets of claims made by one entity about another entity.</span></span> <span data-ttu-id="4cb38-106">例如，在聯合安全性案例中，陳述式是由系統中關於使用者的安全性權杖服務所表示。</span><span class="sxs-lookup"><span data-stu-id="4cb38-106">For example, in federated security scenarios, the statements are made by a security token service about a user in the system.</span></span> <span data-ttu-id="4cb38-107">安全性權杖服務會簽署 SAML 權杖，以表示權杖中所含陳述式的真實性。</span><span class="sxs-lookup"><span data-stu-id="4cb38-107">The security token service signs the SAML token to indicate the veracity of the statements contained in the token.</span></span> <span data-ttu-id="4cb38-108">除此之外，SAML 權杖會與 SAML 權杖使用者證實知悉的密碼編譯金鑰內容產生關聯。</span><span class="sxs-lookup"><span data-stu-id="4cb38-108">In addition, the SAML token is associated with cryptographic key material that the user of the SAML token proves knowledge of.</span></span> <span data-ttu-id="4cb38-109">這項證明能滿足信賴憑證者，證實該 SAML 權杖確實簽發至該使用者。</span><span class="sxs-lookup"><span data-stu-id="4cb38-109">This proof satisfies the relying party that the SAML token was, in fact, issued to that user.</span></span> <span data-ttu-id="4cb38-110">例如，在典型的案例中：</span><span class="sxs-lookup"><span data-stu-id="4cb38-110">For example, in a typical scenario:</span></span>  
  
1.  <span data-ttu-id="4cb38-111">用戶端向安全性權杖服務要求 SAML 權杖，藉由使用 Windows 認證，驗證至該安全性權杖服務。</span><span class="sxs-lookup"><span data-stu-id="4cb38-111">A client requests a SAML token from a security token service, authenticating to that security token service by using Windows credentials.</span></span>  
  
2.  <span data-ttu-id="4cb38-112">安全性權杖服務簽發 SAML 權杖至用戶端。</span><span class="sxs-lookup"><span data-stu-id="4cb38-112">The security token service issues a SAML token to the client.</span></span> <span data-ttu-id="4cb38-113">SAML 權杖是以與安全性權杖服務相關的憑證進行簽署，並且包含針對目標服務加密的證明金鑰。</span><span class="sxs-lookup"><span data-stu-id="4cb38-113">The SAML token is signed with a certificate associated with the security token service and contains a proof key encrypted for the target service.</span></span>  
  
3.  <span data-ttu-id="4cb38-114">用戶端也會收到一份*證明金鑰*。</span><span class="sxs-lookup"><span data-stu-id="4cb38-114">The client also receives a copy of the *proof key*.</span></span> <span data-ttu-id="4cb38-115">用戶端，然後呈現為應用程式服務的 SAML 權杖 (*信賴憑證者的合作對象*)，並以該證明金鑰簽署訊息。</span><span class="sxs-lookup"><span data-stu-id="4cb38-115">The client then presents the SAML token to the application service (the *relying party*) and signs the message with that proof key.</span></span>  
  
4.  <span data-ttu-id="4cb38-116">SAML 權杖上的簽章會告訴信賴憑證者，這是由安全性權杖服務所簽發的權杖。</span><span class="sxs-lookup"><span data-stu-id="4cb38-116">The signature over the SAML token tells the relying party that the security token service issued the token.</span></span> <span data-ttu-id="4cb38-117">使用證明金鑰所建立的訊息簽章會告訴信賴憑證者，該權杖曾簽發至用戶端。</span><span class="sxs-lookup"><span data-stu-id="4cb38-117">The message signature created with the proof key tells the relying party that the token was issued to the client.</span></span>  
  
## <a name="from-claims-to-samlattributes"></a><span data-ttu-id="4cb38-118">從宣告到 SamlAttributes</span><span class="sxs-lookup"><span data-stu-id="4cb38-118">From Claims to SamlAttributes</span></span>  
 <span data-ttu-id="4cb38-119">在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<xref:System.IdentityModel.Tokens.SamlAttribute>中，SAML 權杖中的陳述式會以 <xref:System.IdentityModel.Claims.Claim> 物件做為模型，可從 <xref:System.IdentityModel.Claims.Claim> 物件直接填入，前提是 <xref:System.IdentityModel.Claims.Claim.Right%2A> 物件擁有 <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A><xref:System.IdentityModel.Claims.Claim.Resource%2A>的 <xref:System.String> 屬性，且  屬性為 型別。</span><span class="sxs-lookup"><span data-stu-id="4cb38-119">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], statements in SAML tokens are modeled as <xref:System.IdentityModel.Tokens.SamlAttribute> objects, which can be populated directly from <xref:System.IdentityModel.Claims.Claim> objects, provided the <xref:System.IdentityModel.Claims.Claim> object has a <xref:System.IdentityModel.Claims.Claim.Right%2A> property of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> and the <xref:System.IdentityModel.Claims.Claim.Resource%2A> property is of type <xref:System.String>.</span></span> <span data-ttu-id="4cb38-120">例如: </span><span class="sxs-lookup"><span data-stu-id="4cb38-120">For example:</span></span>  
  
 [!code-csharp[c_CreateSTS#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#8)]
 [!code-vb[c_CreateSTS#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#8)]  
  
> [!NOTE]
>  <span data-ttu-id="4cb38-121">當 SAML 權杖在訊息中序列化，不論是當這些權杖是安全性權杖服務所核發，或是當這些權杖由用戶端視為驗證的一部分提供至服務，訊息大小配額上限必須大到足以容納 SAML 權杖及其他訊息部分。</span><span class="sxs-lookup"><span data-stu-id="4cb38-121">When SAML tokens are serialized in messages, either when they are issued by a security token service or when they are presented by clients to services as part of authentication, the maximum message size quota must be sufficiently large to accommodate the SAML token and the other message parts.</span></span> <span data-ttu-id="4cb38-122">正常情況下，預設訊息大小配額應足夠。</span><span class="sxs-lookup"><span data-stu-id="4cb38-122">In normal cases, the default message size quotas are sufficient.</span></span> <span data-ttu-id="4cb38-123">然而，若 SAML 權杖因為包含數百個宣告而變很大時，您可能需要增加配額以容納序列化的權杖。</span><span class="sxs-lookup"><span data-stu-id="4cb38-123">However, in cases where a SAML token is large because it contains hundreds of claims, you may need to increase the quotas to accommodate the serialized token.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="4cb38-124">[資料的安全性考量](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)。</span><span class="sxs-lookup"><span data-stu-id="4cb38-124"> [Security Considerations for Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span></span>  
  
## <a name="from-samlattributes-to-claims"></a><span data-ttu-id="4cb38-125">從 SamlAttributes 到宣告</span><span class="sxs-lookup"><span data-stu-id="4cb38-125">From SamlAttributes to Claims</span></span>  
 <span data-ttu-id="4cb38-126">當 SAML 權杖在訊息內接收時，SAML 權杖內的各種陳述式會轉變成 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> 物件，置於 <xref:System.IdentityModel.Policy.AuthorizationContext>之內。</span><span class="sxs-lookup"><span data-stu-id="4cb38-126">When SAML tokens are received in messages, the various statements in the SAML token are turned into <xref:System.IdentityModel.Policy.IAuthorizationPolicy> objects that are placed into the <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span> <span data-ttu-id="4cb38-127">來自每個 SAML 陳述式的宣告均由 <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> 的 <xref:System.IdentityModel.Policy.AuthorizationContext> 屬性傳回，並且可進行檢查以決定是否驗證並授權使用者。</span><span class="sxs-lookup"><span data-stu-id="4cb38-127">The claims from each SAML statement are returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> and can be examined to determine whether to authenticate and authorize the user.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cb38-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="4cb38-128">See Also</span></span>  
 <xref:System.IdentityModel.Policy.AuthorizationContext>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 <xref:System.IdentityModel.Claims.ClaimSet>  
 [<span data-ttu-id="4cb38-129">同盟</span><span class="sxs-lookup"><span data-stu-id="4cb38-129">Federation</span></span>](../../../../docs/framework/wcf/feature-details/federation.md)  
 [<span data-ttu-id="4cb38-130">如何：建立同盟用戶端</span><span class="sxs-lookup"><span data-stu-id="4cb38-130">How to: Create a Federated Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="4cb38-131">如何：設定同盟服務的認證</span><span class="sxs-lookup"><span data-stu-id="4cb38-131">How to: Configure Credentials on a Federation Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [<span data-ttu-id="4cb38-132">使用身分識別模型來管理宣告與授權</span><span class="sxs-lookup"><span data-stu-id="4cb38-132">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [<span data-ttu-id="4cb38-133">宣告與權杖</span><span class="sxs-lookup"><span data-stu-id="4cb38-133">Claims and Tokens</span></span>](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)  
 [<span data-ttu-id="4cb38-134">宣告建立與資源值</span><span class="sxs-lookup"><span data-stu-id="4cb38-134">Claim Creation and Resource Values</span></span>](../../../../docs/framework/wcf/feature-details/claim-creation-and-resource-values.md)  
 [<span data-ttu-id="4cb38-135">如何：建立自訂宣告</span><span class="sxs-lookup"><span data-stu-id="4cb38-135">How to: Create a Custom Claim</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
