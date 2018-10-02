---
title: HOW TO：建立安全性權杖服務
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 98e82101-4cff-4bb8-a220-f7abed3556e5
author: BrucePerlerMS
ms.openlocfilehash: dd2c4f32978107a82ce940e0ef984c70f461b2c3
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48046730"
---
# <a name="how-to-create-a-security-token-service"></a><span data-ttu-id="551e5-102">HOW TO：建立安全性權杖服務</span><span class="sxs-lookup"><span data-stu-id="551e5-102">How to: Create a Security Token Service</span></span>
<span data-ttu-id="551e5-103">安全性權杖服務實作於 WS-Trust 規格定義的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="551e5-103">A security token service implements the protocol defined in the WS-Trust specification.</span></span> <span data-ttu-id="551e5-104">此通訊協定定義用來核發、更新、取消及驗證安全性權杖的訊息格式以及訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="551e5-104">This protocol defines message formats and message exchange patterns for issuing, renewing, canceling, and validating security tokens.</span></span> <span data-ttu-id="551e5-105">指定的安全性權杖服務提供一個或一個以上的這些功能。</span><span class="sxs-lookup"><span data-stu-id="551e5-105">A given security token service provides one or more of these capabilities.</span></span> <span data-ttu-id="551e5-106">此主題檢視最常見的狀況：實作權杖核發。</span><span class="sxs-lookup"><span data-stu-id="551e5-106">This topic looks at the most common scenario: implementing token issuance.</span></span>  
  
## <a name="issuing-tokens"></a><span data-ttu-id="551e5-107">核發權杖</span><span class="sxs-lookup"><span data-stu-id="551e5-107">Issuing Tokens</span></span>  
 <span data-ttu-id="551e5-108">WS-Trust 根據 `RequestSecurityToken` XML Schema 定義語言 (XSD) 結構描述項目以及執行權杖核發的 `RequestSecurityTokenResponse` XSD 結構描述項目，定義訊息的格式。</span><span class="sxs-lookup"><span data-stu-id="551e5-108">WS-Trust defines message formats, based on the `RequestSecurityToken` XML Schema definition language (XSD) schema element, and `RequestSecurityTokenResponse` XSD schema element for performing token issuance.</span></span> <span data-ttu-id="551e5-109">除此之外，它還定義關聯的動作統一資源識別源 (URI)。</span><span class="sxs-lookup"><span data-stu-id="551e5-109">In addition, it defines the associated Action Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="551e5-110">URI 相關聯的動作`RequestSecurityToken`訊息是 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue 。</span><span class="sxs-lookup"><span data-stu-id="551e5-110">The action URI associated with the `RequestSecurityToken` message is http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue.</span></span> <span data-ttu-id="551e5-111">URI 相關聯的動作`RequestSecurityTokenResponse`訊息是 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue 。</span><span class="sxs-lookup"><span data-stu-id="551e5-111">The action URI associated with the `RequestSecurityTokenResponse` message is   http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue.</span></span>  
  
### <a name="request-message-structure"></a><span data-ttu-id="551e5-112">要求訊息結構</span><span class="sxs-lookup"><span data-stu-id="551e5-112">Request Message Structure</span></span>  
 <span data-ttu-id="551e5-113">發出要求訊息結構通常包括下列項目：</span><span class="sxs-lookup"><span data-stu-id="551e5-113">The issue request message structure typically consists of the following items:</span></span>  
  
-   <span data-ttu-id="551e5-114">要求輸入 URI 值為 http://schemas.xmlsoap.org/ws/2005/02/trust/Issue 。</span><span class="sxs-lookup"><span data-stu-id="551e5-114">A request type URI with a value of    http://schemas.xmlsoap.org/ws/2005/02/trust/Issue.</span></span>  
  
-   <span data-ttu-id="551e5-115">語彙基元型別 URI。</span><span class="sxs-lookup"><span data-stu-id="551e5-115">A token type URI.</span></span> <span data-ttu-id="551e5-116">此 URI 的值是安全性判斷提示標記語言 (SAML) 1.1 權杖 http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1 。</span><span class="sxs-lookup"><span data-stu-id="551e5-116">For Security Assertions Markup Language (SAML) 1.1 tokens, the value of this URI is http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1.</span></span>  
  
-   <span data-ttu-id="551e5-117">此金鑰大小值表示關聯於核發之權杖的金鑰位元數。</span><span class="sxs-lookup"><span data-stu-id="551e5-117">A key size value that indicates the number of bits in the key to be associated with the issued token.</span></span>  
  
-   <span data-ttu-id="551e5-118">金鑰型別 URI。</span><span class="sxs-lookup"><span data-stu-id="551e5-118">A key type URI.</span></span> <span data-ttu-id="551e5-119">對稱金鑰，這個 URI 的值是 http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey 。</span><span class="sxs-lookup"><span data-stu-id="551e5-119">For symmetric keys, the value of this URI is http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey.</span></span>  
  
 <span data-ttu-id="551e5-120">此外，也許存在一些其他項目：</span><span class="sxs-lookup"><span data-stu-id="551e5-120">In addition, a couple of other items might be present:</span></span>  
  
-   <span data-ttu-id="551e5-121">用戶端提供的金錀資料。</span><span class="sxs-lookup"><span data-stu-id="551e5-121">Key material provided by the client.</span></span>  
  
-   <span data-ttu-id="551e5-122">表示將使用已發行權杖之目標服務的範圍資訊。</span><span class="sxs-lookup"><span data-stu-id="551e5-122">Scope information that indicates the target service that the issued token will be used with.</span></span>  
  
 <span data-ttu-id="551e5-123">安全性權杖服務在建構發出回應 (Issue Response) 訊息時，使用發出要求訊息內的資訊。</span><span class="sxs-lookup"><span data-stu-id="551e5-123">The security token service uses the information in the issue request message when it constructs the Issue Response message.</span></span>  
  
## <a name="response-message-structure"></a><span data-ttu-id="551e5-124">回應訊息結構</span><span class="sxs-lookup"><span data-stu-id="551e5-124">Response Message Structure</span></span>  
 <span data-ttu-id="551e5-125">發出回應訊息結構通常包括下列項目：</span><span class="sxs-lookup"><span data-stu-id="551e5-125">The issue response message structure typically consists of the following items;</span></span>  
  
-   <span data-ttu-id="551e5-126">例如，核發的安全性權杖為 SAML 1.1 判斷提示。</span><span class="sxs-lookup"><span data-stu-id="551e5-126">The issued security token, for example, a SAML 1.1 assertion.</span></span>  
  
-   <span data-ttu-id="551e5-127">與安全性權杖相關聯的證明權杖。</span><span class="sxs-lookup"><span data-stu-id="551e5-127">A proof token associated with the security token.</span></span> <span data-ttu-id="551e5-128">就對稱金鑰而言，這經常是金鑰資料的加密格式。</span><span class="sxs-lookup"><span data-stu-id="551e5-128">For symmetric keys, this is often an encrypted form of the key material.</span></span>  
  
-   <span data-ttu-id="551e5-129">核發的安全性權杖的參照。</span><span class="sxs-lookup"><span data-stu-id="551e5-129">References to the issued security token.</span></span> <span data-ttu-id="551e5-130">一般而言，安全性權杖服務會於已核發權杖出現於用戶端發出的後續訊息時，傳回可使用的參照，以及另一個當後續訊息無權杖時可使用的參照。</span><span class="sxs-lookup"><span data-stu-id="551e5-130">Typically, the security token service returns a reference that can be used when the issued token appears in a subsequent message sent by the client and another that can be used when the token is not present in subsequent messages.</span></span>  
  
 <span data-ttu-id="551e5-131">此外，也許存在一些其他項目：</span><span class="sxs-lookup"><span data-stu-id="551e5-131">In addition, a couple of other items might be present:</span></span>  
  
-   <span data-ttu-id="551e5-132">安全性權杖服務提供的金錀資料。</span><span class="sxs-lookup"><span data-stu-id="551e5-132">Key material provided by the security token service.</span></span>  
  
-   <span data-ttu-id="551e5-133">要計算共用金鑰所需的演算法。</span><span class="sxs-lookup"><span data-stu-id="551e5-133">The algorithm needed to compute the shared key.</span></span>  
  
-   <span data-ttu-id="551e5-134">核發權杖的存留期資訊。</span><span class="sxs-lookup"><span data-stu-id="551e5-134">Lifetime information for the issued token.</span></span>  
  
## <a name="processing-request-messages"></a><span data-ttu-id="551e5-135">處理要求訊息</span><span class="sxs-lookup"><span data-stu-id="551e5-135">Processing Request Messages</span></span>  
 <span data-ttu-id="551e5-136">安全性權杖服務檢查各個要求訊息以處理核發要求，並且確保能核發滿足要求的權杖。</span><span class="sxs-lookup"><span data-stu-id="551e5-136">The security token service processes the issue request by examining the various pieces of the request message and ensuring that it can issue a token that satisfies the request.</span></span> <span data-ttu-id="551e5-137">在建構要核發的權杖前，安全性權杖服務必須決定下列項目：</span><span class="sxs-lookup"><span data-stu-id="551e5-137">The security token service must determine the following before it constructs the token to be issued:</span></span>  
  
-   <span data-ttu-id="551e5-138">所謂要求其實是核發權杖的要求。</span><span class="sxs-lookup"><span data-stu-id="551e5-138">The request really is a request for a token to be issued.</span></span>  
  
-   <span data-ttu-id="551e5-139">安全性權杖服務支援要求的權杖類型。</span><span class="sxs-lookup"><span data-stu-id="551e5-139">The security token service supports the requested token type.</span></span>  
  
-   <span data-ttu-id="551e5-140">要求者獲得授權提出要求。</span><span class="sxs-lookup"><span data-stu-id="551e5-140">The requester is authorized to make the request.</span></span>  
  
-   <span data-ttu-id="551e5-141">安全性權杖服務可滿足要求者對金鑰資料的期望。</span><span class="sxs-lookup"><span data-stu-id="551e5-141">The security token service can meet the requester's expectations with respect to key material.</span></span>  
  
 <span data-ttu-id="551e5-142">建構權杖的兩個重要部分為決定要使用什麼金鑰簽署權杖，以及共用金鑰要用什麼金鑰加密。</span><span class="sxs-lookup"><span data-stu-id="551e5-142">Two vital parts of constructing a token are determining what key to sign the token with and what key to encrypt the shared key with.</span></span> <span data-ttu-id="551e5-143">權杖需要簽署，這樣當用戶端對目標服務提出權杖時，該服務才能判斷此權杖是否為自己信賴之安全性權杖服務所核發的權杖。</span><span class="sxs-lookup"><span data-stu-id="551e5-143">The token needs to be signed so that when the client presents the token to the target service, that service can determine that the token was issued by a security token service that it trusts.</span></span> <span data-ttu-id="551e5-144">金鑰資料需要以目標服務能解密金鑰資料的方式進行加密。</span><span class="sxs-lookup"><span data-stu-id="551e5-144">The key material needs to be encrypted in such a way that the target service can decrypt that key material.</span></span>  
  
 <span data-ttu-id="551e5-145">簽署 SAML 判斷提示包括建立 <xref:System.IdentityModel.Tokens.SigningCredentials> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="551e5-145">Signing a SAML assertion involves creating a <xref:System.IdentityModel.Tokens.SigningCredentials> instance.</span></span> <span data-ttu-id="551e5-146">此類別的建構函式接受下列項目：</span><span class="sxs-lookup"><span data-stu-id="551e5-146">The constructor for this class takes the following:</span></span>  
  
-   <span data-ttu-id="551e5-147"><xref:System.IdentityModel.Tokens.SecurityKey> 用於金鑰簽署 SAML 判斷提示。</span><span class="sxs-lookup"><span data-stu-id="551e5-147">A <xref:System.IdentityModel.Tokens.SecurityKey> for the key to use to sign the SAML assertion.</span></span>  
  
-   <span data-ttu-id="551e5-148">識別要使用之簽署演算法的字串。</span><span class="sxs-lookup"><span data-stu-id="551e5-148">A string identifying the signature algorithm to use.</span></span>  
  
-   <span data-ttu-id="551e5-149">識別要使用之摘要演算法的字串。</span><span class="sxs-lookup"><span data-stu-id="551e5-149">A string identifying the digest algorithm to use.</span></span>  
  
-   <span data-ttu-id="551e5-150">或者，<xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> 識別要用來簽署判斷提示的金鑰。</span><span class="sxs-lookup"><span data-stu-id="551e5-150">Optionally, a <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> that identifies the key to use to sign the assertion.</span></span>  
  
 [!code-csharp[c_CreateSTS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#1)]
 [!code-vb[c_CreateSTS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#1)]  
  
 <span data-ttu-id="551e5-151">加密共用金鑰包含將金鑰資料以金鑰加密，目標服務能使用此金鑰解密共用金鑰。</span><span class="sxs-lookup"><span data-stu-id="551e5-151">Encrypting the shared key involves taking the key material and encrypting it with a key that the target service can use to decrypt the shared key.</span></span> <span data-ttu-id="551e5-152">一般而言，會使用目標服務的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="551e5-152">Typically, the public key of the target service is used.</span></span>  
  
 [!code-csharp[c_CreateSTS#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#2)]
 [!code-vb[c_CreateSTS#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#2)]  
  
 <span data-ttu-id="551e5-153">除此之外，加密金鑰還需要 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>。</span><span class="sxs-lookup"><span data-stu-id="551e5-153">In addition, a <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> for the encrypted key is needed.</span></span>  
  
 [!code-csharp[c_CreateSTS#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#3)]
 [!code-vb[c_CreateSTS#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#3)]  
  
 <span data-ttu-id="551e5-154">然後使用 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> 建立 `SamlSubject` 做為 `SamlToken` 的一部分。</span><span class="sxs-lookup"><span data-stu-id="551e5-154">This <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> is then used to create a `SamlSubject` as part of the `SamlToken`.</span></span>  
  
 [!code-csharp[c_CreateSTS#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#4)]
 [!code-vb[c_CreateSTS#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#4)]  
  
 <span data-ttu-id="551e5-155">如需詳細資訊，請參閱 <<c0> [ 聯合範例](../../../../docs/framework/wcf/samples/federation-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="551e5-155">For more information, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
## <a name="creating-response-messages"></a><span data-ttu-id="551e5-156">建立回應訊息</span><span class="sxs-lookup"><span data-stu-id="551e5-156">Creating Response Messages</span></span>  
 <span data-ttu-id="551e5-157">一旦安全性權杖服務處理發出的要求，並且建構出要核發之權杖以及證明金鑰後，就需要建構回應訊息，至少包括要求的權杖、證明權杖以及核發的權杖參照。</span><span class="sxs-lookup"><span data-stu-id="551e5-157">Once the security token service processes the issue request and constructs the token to be issued along with the proof key, the response message needs to be constructed, including at least the requested token, the proof token, and the issued token references.</span></span> <span data-ttu-id="551e5-158">此核發的權杖一般而言是 <xref:System.IdentityModel.Tokens.SamlSecurityToken> 自 <xref:System.IdentityModel.Tokens.SamlAssertion>所建造，如以下範例所示。</span><span class="sxs-lookup"><span data-stu-id="551e5-158">The issued token is typically a <xref:System.IdentityModel.Tokens.SamlSecurityToken> created from the <xref:System.IdentityModel.Tokens.SamlAssertion>, as shown in the following example.</span></span>  
  
 [!code-csharp[c_CreateSTS#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#5)]
 [!code-vb[c_CreateSTS#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#5)]  
  
 <span data-ttu-id="551e5-159">當安全性權杖服務提供共用金鑰資料時，證明權杖就是由建立 <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken> 加以建構。</span><span class="sxs-lookup"><span data-stu-id="551e5-159">In the case where the security token service provides the shared key material, the proof token is constructed by creating a <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>.</span></span>  
  
 [!code-csharp[c_CreateSTS#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#6)]
 [!code-vb[c_CreateSTS#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#6)]  
  
 <span data-ttu-id="551e5-160">如需如何建構證明權杖，當用戶端和安全性權杖服務都提供共用金鑰的金鑰內容的詳細資訊，請參閱[聯合範例](../../../../docs/framework/wcf/samples/federation-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="551e5-160">For more information about how to construct the proof token when the client and the security token service both provide key material for the shared key, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
 <span data-ttu-id="551e5-161">核發的權杖參照以建立 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> 類別執行個體而建構。</span><span class="sxs-lookup"><span data-stu-id="551e5-161">The issued token references are constructed by creating instances of the <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> class.</span></span>  
  
 [!code-csharp[c_CreateSTS#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#7)]
 [!code-vb[c_CreateSTS#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#7)]  
  
 <span data-ttu-id="551e5-162">然後將這些不同的值序列化成回應訊息傳回用戶端。</span><span class="sxs-lookup"><span data-stu-id="551e5-162">These various values are then serialized into the response message returned to the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="551e5-163">範例</span><span class="sxs-lookup"><span data-stu-id="551e5-163">Example</span></span>  
 <span data-ttu-id="551e5-164">安全性權杖服務的完整程式碼，請參閱[聯合範例](../../../../docs/framework/wcf/samples/federation-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="551e5-164">For full code for a security token service, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="551e5-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="551e5-165">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SigningCredentials>  
 <xref:System.IdentityModel.Tokens.SecurityKey>  
 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
 <xref:System.IdentityModel.Tokens.SamlAssertion>  
 <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>  
 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause>  
 [<span data-ttu-id="551e5-166">同盟範例</span><span class="sxs-lookup"><span data-stu-id="551e5-166">Federation Sample</span></span>](../../../../docs/framework/wcf/samples/federation-sample.md)
