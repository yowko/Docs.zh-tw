---
title: HOW TO：變更 X.509 憑證私密金鑰的密碼編譯提供者
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptographic provider [WCF], changing
- cryptographic provider [WCF]
ms.assetid: b4254406-272e-4774-bd61-27e39bbb6c12
ms.openlocfilehash: 9d7216b3aed89dc88737cc346386d6b03929fe60
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61997019"
---
# <a name="how-to-change-the-cryptographic-provider-for-an-x509-certificates-private-key"></a><span data-ttu-id="d1ab3-102">HOW TO：變更 X.509 憑證私密金鑰的密碼編譯提供者</span><span class="sxs-lookup"><span data-stu-id="d1ab3-102">How to: Change the Cryptographic Provider for an X.509 Certificate's Private Key</span></span>
<span data-ttu-id="d1ab3-103">本主題說明如何變更用來提供 X.509 憑證之私密金鑰的密碼編譯提供者，以及如何整合 Windows Communication Foundation (WCF) 安全性架構提供者。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-103">This topic shows how to change the cryptographic provider used to provide an X.509 certificate's private key and how to integrate the provider into the Windows Communication Foundation (WCF) security framework.</span></span> <span data-ttu-id="d1ab3-104">如需使用憑證的詳細資訊，請參閱[Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-104">For more information about using certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
 <span data-ttu-id="d1ab3-105">WCF 安全性架構可用來引進新的安全性權杖類型，如中所述[How to:建立自訂權杖](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-105">The WCF security framework provides a way to introduce new security token types as described in [How to: Create a Custom Token](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).</span></span> <span data-ttu-id="d1ab3-106">也可以使用自訂權杖來取代現有由系統提供的權杖型別。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-106">It is also possible to use a custom token to replace existing system-provided token types.</span></span>  
  
 <span data-ttu-id="d1ab3-107">在本主題中，系統提供的 X.509 安全性權杖會由自訂 X.509 權杖取代，為憑證私密金鑰提供不同的實作。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-107">In this topic, the system-provided X.509 security token is replaced by a custom X.509 token that provides a different implementation for the certificate private key.</span></span> <span data-ttu-id="d1ab3-108">在實際的私密金鑰是由與預設 Windows 密碼編譯提供者不同的密碼編譯提供者所提供的案例中，這十分有用。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-108">This is useful in scenarios where the actual private key is provided by a different cryptographic provider than the default Windows cryptographic provider.</span></span> <span data-ttu-id="d1ab3-109">替代密碼編譯提供者的其中一個範例是硬體安全性模組，它執行所有私密金鑰相關密碼編譯作業，且不會將私密金鑰儲存在記憶體中，因而增強系統的安全性。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-109">One example of an alternative cryptographic provider is a hardware security module that performs all private key related cryptographic operations, and does not store the private keys in memory, thus improving security of the system.</span></span>  
  
 <span data-ttu-id="d1ab3-110">下列範例僅供示範之用。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-110">The following example is for demonstration purposes only.</span></span> <span data-ttu-id="d1ab3-111">它不會取代預設的 Windows 密碼編譯提供者，但會顯示可以整合此類提供者之處。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-111">It does not replace the default Windows cryptographic provider, but it shows where such a provider could be integrated.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="d1ab3-112">程序</span><span class="sxs-lookup"><span data-stu-id="d1ab3-112">Procedures</span></span>  
 <span data-ttu-id="d1ab3-113">每個具有相關安全性金鑰的安全性權杖都必須實作 <xref:System.IdentityModel.Tokens.SecurityToken.SecurityKeys%2A> 屬性，它會從安全性權杖執行個體傳回金鑰的集合。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-113">Every security token that has an associated security key or keys must implement the <xref:System.IdentityModel.Tokens.SecurityToken.SecurityKeys%2A> property, which returns a collection of keys from the security token instance.</span></span> <span data-ttu-id="d1ab3-114">如果權杖是 X.509 安全性權杖，集合就會包含 <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey> 類別的單一執行個體，表示與憑證有關聯的公開和私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-114">If the token is an X.509 security token, the collection contains a single instance of the <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey> class that represents both public and private keys associated with the certificate.</span></span> <span data-ttu-id="d1ab3-115">如果要取代用於提供憑證金鑰的預設密碼編譯提供者，請建立這個類別的新實作。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-115">To replace the default cryptographic provider used to provide the certificate's keys, create a new implementation of this class.</span></span>  
  
#### <a name="to-create-a-custom-x509-asymmetric-key"></a><span data-ttu-id="d1ab3-116">建立自訂 X.509 非對稱金鑰</span><span class="sxs-lookup"><span data-stu-id="d1ab3-116">To create a custom X.509 asymmetric key</span></span>  
  
1. <span data-ttu-id="d1ab3-117">定義衍生自 <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey> 類別的新類別。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-117">Define a new class derived from the <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey> class.</span></span>  
  
2. <span data-ttu-id="d1ab3-118">覆寫 <xref:System.IdentityModel.Tokens.SecurityKey.KeySize%2A> 唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-118">Override the <xref:System.IdentityModel.Tokens.SecurityKey.KeySize%2A> read-only property.</span></span> <span data-ttu-id="d1ab3-119">這個屬性會傳回憑證之公開/私密金鑰組的實際金鑰大小。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-119">This property returns the actual key size of the certificate's public/private key pair.</span></span>  
  
3. <span data-ttu-id="d1ab3-120">覆寫 <xref:System.IdentityModel.Tokens.SecurityKey.DecryptKey%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-120">Override the <xref:System.IdentityModel.Tokens.SecurityKey.DecryptKey%2A> method.</span></span> <span data-ttu-id="d1ab3-121">WCF 的安全性架構，來解密對稱金鑰憑證的私密金鑰被呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-121">This method is called by the WCF security framework to decrypt a symmetric key with the certificate's private key.</span></span> <span data-ttu-id="d1ab3-122">(金鑰之前是使用憑證的公開金鑰來加密)。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-122">(The key was previously encrypted with the certificate's public key.)</span></span>  
  
4. <span data-ttu-id="d1ab3-123">覆寫 <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetAsymmetricAlgorithm%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-123">Override the <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetAsymmetricAlgorithm%2A> method.</span></span> <span data-ttu-id="d1ab3-124">若要取得的執行個體的 WCF 安全性架構會呼叫這個方法<xref:System.Security.Cryptography.AsymmetricAlgorithm>傳遞給方法的類別，表示的參數而定憑證的私用或公用金鑰的密碼編譯提供者。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-124">This method is called by the WCF security framework to obtain an instance of the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class that represents the cryptographic provider for either the certificate's private or public key, depending on the parameters passed to the method.</span></span>  
  
5. <span data-ttu-id="d1ab3-125">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-125">Optional.</span></span> <span data-ttu-id="d1ab3-126">覆寫 <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetHashAlgorithmForSignature%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-126">Override the <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetHashAlgorithmForSignature%2A> method.</span></span> <span data-ttu-id="d1ab3-127">如果需要 <xref:System.Security.Cryptography.HashAlgorithm> 類別的不同實作，請覆寫這個方法。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-127">Override this method if a different implementation of the <xref:System.Security.Cryptography.HashAlgorithm> class is required.</span></span>  
  
6. <span data-ttu-id="d1ab3-128">覆寫 <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetSignatureFormatter%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-128">Override the <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetSignatureFormatter%2A> method.</span></span> <span data-ttu-id="d1ab3-129">這個方法會傳回與憑證私密金鑰有關聯之 <xref:System.Security.Cryptography.AsymmetricSignatureFormatter> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-129">This method returns an instance of the <xref:System.Security.Cryptography.AsymmetricSignatureFormatter> class that is associated with the certificate's private key.</span></span>  
  
7. <span data-ttu-id="d1ab3-130">覆寫 <xref:System.IdentityModel.Tokens.SecurityKey.IsSupportedAlgorithm%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-130">Override the <xref:System.IdentityModel.Tokens.SecurityKey.IsSupportedAlgorithm%2A> method.</span></span> <span data-ttu-id="d1ab3-131">這個方法是用於指出安全性金鑰實作是否支援特定的密碼編譯演算法。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-131">This method is used to indicate whether a particular cryptographic algorithm is supported by the security key implementation.</span></span>  
  
     [!code-csharp[c_CustomX509Token#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#1)]
     [!code-vb[c_CustomX509Token#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#1)]  
  
 <span data-ttu-id="d1ab3-132">下列程序顯示如何整合自訂 X.509 非對稱安全性金鑰實作與 WCF 安全性架構之前程序中建立，以便取代系統提供的 X.509 安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-132">The following procedure shows how to integrate the custom X.509 asymmetric security key implementation created in the preceding procedure with the WCF security framework in order to replace the system-provided X.509 security token.</span></span>  
  
#### <a name="to-replace-the-system-provided-x509-security-token-with-a-custom-x509-asymmetric-security-key-token"></a><span data-ttu-id="d1ab3-133">使用自訂的 X.509 非對稱安全性金鑰權杖來取代系統提供的 X.509 安全性權杖</span><span class="sxs-lookup"><span data-stu-id="d1ab3-133">To replace the system-provided X.509 security token with a custom X.509 asymmetric security key token</span></span>  
  
1. <span data-ttu-id="d1ab3-134">請建立自訂 X.509 安全性權杖，它會傳回自訂 X.509 非對稱安全性金鑰而非系統提供的安全性金鑰，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-134">Create a custom X.509 security token that returns the custom X.509 asymmetric security key instead of the system-provided security key, as shown in the following example.</span></span> <span data-ttu-id="d1ab3-135">如需有關自訂安全性權杖的詳細資訊，請參閱[How to:建立自訂權杖](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-135">For more information about custom security tokens, see [How to: Create a Custom Token](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).</span></span>  
  
     [!code-csharp[c_CustomX509Token#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#2)]
     [!code-vb[c_CustomX509Token#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#2)]  
  
2. <span data-ttu-id="d1ab3-136">請建立會傳回自訂 X.509 安全性權杖的自訂安全性權杖提供者，如範例所示。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-136">Create a custom security token provider that returns a custom X.509 security token, as shown in the example.</span></span> <span data-ttu-id="d1ab3-137">如需有關自訂安全性權杖提供者的詳細資訊，請參閱[How to:建立自訂安全性權杖提供者](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-137">For more information about custom security token providers, see [How to: Create a Custom Security Token Provider](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).</span></span>  
  
     [!code-csharp[c_CustomX509Token#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#3)]
     [!code-vb[c_CustomX509Token#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#3)]  
  
3. <span data-ttu-id="d1ab3-138">如果自訂安全性金鑰需要用在啟動器端，請建立自訂用戶端安全性權杖管理員和自訂用戶端認證類別，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-138">If the custom security key needs to be used on the initiator side, create a custom client security token manager and custom client credentials classes, as shown in the following example.</span></span> <span data-ttu-id="d1ab3-139">如需有關自訂用戶端認證和用戶端安全性權杖管理員的詳細資訊，請參閱[逐步解說：建立自訂用戶端和服務認證](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-139">For more information about custom client credentials and client security token managers, see [Walkthrough: Creating Custom Client and Service Credentials](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).</span></span>  
  
     [!code-csharp[c_CustomX509Token#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#4)]
     [!code-vb[c_CustomX509Token#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#4)]  
  
     [!code-csharp[c_CustomX509Token#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#6)]
     [!code-vb[c_CustomX509Token#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#6)]  
  
4. <span data-ttu-id="d1ab3-140">如果自訂安全性金鑰需要用在收件者端，請建立自訂服務安全性權杖管理員和自訂服務認證，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-140">If the custom security key needs to be used on the recipient side, create a custom service security token manager and custom service credentials, as shown in the following example.</span></span> <span data-ttu-id="d1ab3-141">如需有關自訂服務認證和服務安全性權杖管理員的詳細資訊，請參閱[逐步解說：建立自訂用戶端和服務認證](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)。</span><span class="sxs-lookup"><span data-stu-id="d1ab3-141">For more information about custom service credentials and service security token managers, see [Walkthrough: Creating Custom Client and Service Credentials](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).</span></span>  
  
     [!code-csharp[c_CustomX509Token#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#5)]
     [!code-vb[c_CustomX509Token#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#5)]  
  
     [!code-csharp[c_CustomX509Token#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#7)]
     [!code-vb[c_CustomX509Token#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="d1ab3-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1ab3-142">See also</span></span>

- <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey>
- <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey>
- <xref:System.IdentityModel.Tokens.SecurityKey>
- <xref:System.Security.Cryptography.AsymmetricAlgorithm>
- <xref:System.Security.Cryptography.HashAlgorithm>
- <xref:System.Security.Cryptography.AsymmetricSignatureFormatter>
- [<span data-ttu-id="d1ab3-143">逐步解說：建立自訂用戶端和服務認證</span><span class="sxs-lookup"><span data-stu-id="d1ab3-143">Walkthrough: Creating Custom Client and Service Credentials</span></span>](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)
- [<span data-ttu-id="d1ab3-144">如何：建立自訂安全性權杖驗證器</span><span class="sxs-lookup"><span data-stu-id="d1ab3-144">How to: Create a Custom Security Token Authenticator</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)
- [<span data-ttu-id="d1ab3-145">如何：建立自訂安全性權杖提供者</span><span class="sxs-lookup"><span data-stu-id="d1ab3-145">How to: Create a Custom Security Token Provider</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)
- [<span data-ttu-id="d1ab3-146">如何：建立自訂權杖</span><span class="sxs-lookup"><span data-stu-id="d1ab3-146">How to: Create a Custom Token</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)
