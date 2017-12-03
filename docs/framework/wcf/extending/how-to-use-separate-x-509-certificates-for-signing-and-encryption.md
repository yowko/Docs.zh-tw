---
title: "HOW TO：使用個別 X.509 憑證簽署與加密"
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
- WCF, extensibility
- ClientCredentials class
- ClientCredentialsSecurityTokenManager class
ms.assetid: 0b06ce4e-7835-4d82-8baf-d525c71a0e49
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 312a4b854cb527e63d6866247d4147720ce0710c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-separate-x509-certificates-for-signing-and-encryption"></a><span data-ttu-id="5c824-102">HOW TO：使用個別 X.509 憑證簽署與加密</span><span class="sxs-lookup"><span data-stu-id="5c824-102">How to: Use Separate X.509 Certificates for Signing and Encryption</span></span>
<span data-ttu-id="5c824-103">本主題顯示如何設定 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]，以在用戶端和服務上的訊息簽章和加密中使用各種憑證。</span><span class="sxs-lookup"><span data-stu-id="5c824-103">This topic shows how to configure [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to use different certificates for message signing and encryption on both the client and service.</span></span>  
  
 <span data-ttu-id="5c824-104">若要使用個別的憑證來進行簽章和加密，此時必須建立自訂的用戶端或服務憑證 (或兩者皆建立)，這是因為 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 並未提供可以設定多個用戶端或服務憑證的 API。</span><span class="sxs-lookup"><span data-stu-id="5c824-104">To enable separate certificates to be used for signing and encryption, a custom client or service credentials (or both) must be created because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not provide an API to set multiple client or service certificates.</span></span> <span data-ttu-id="5c824-105">此外，必須提供安全性權杖管理員才能運用多份憑證的資訊，以及建立可用於特定金鑰使用方式和訊息方向的適當安全性權杖提供者。</span><span class="sxs-lookup"><span data-stu-id="5c824-105">Additionally, a security token manager must be provided to leverage the multiple certificates' information and to create an appropriate security token provider for specified key usage and message direction.</span></span>  
  
 <span data-ttu-id="5c824-106">下方圖表會顯示所使用的主要類別、它們繼承的來源類別 (以上指標示)，以及特定方向和屬性所傳回的類別。</span><span class="sxs-lookup"><span data-stu-id="5c824-106">The following diagram shows the main classes used, the classes they inherit from (shown by an upward-pointing arrow), and the return types of certain methods and properties.</span></span>  
  
-   <span data-ttu-id="5c824-107">`MyClientCredentials` 為 <xref:System.ServiceModel.Description.ClientCredentials> 的自訂實作。</span><span class="sxs-lookup"><span data-stu-id="5c824-107">`MyClientCredentials` is a custom implementation of <xref:System.ServiceModel.Description.ClientCredentials>.</span></span>  
  
    -   <span data-ttu-id="5c824-108">它在圖表中所顯示的屬性都會傳回 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="5c824-108">Its properties shown in the diagram all return instances of <xref:System.Security.Cryptography.X509Certificates.X509Certificate2>.</span></span>  
  
    -   <span data-ttu-id="5c824-109">它的方法 <xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> 會傳回 `MyClientCredentialsSecurityTokenManager` 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="5c824-109">Its method <xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> returns an instance of `MyClientCredentialsSecurityTokenManager`.</span></span>  
  
-   <span data-ttu-id="5c824-110">`MyClientCredentialsSecurityTokenManager` 為 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> 的自訂實作。</span><span class="sxs-lookup"><span data-stu-id="5c824-110">`MyClientCredentialsSecurityTokenManager` is a custom implementation of <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>.</span></span>  
  
    -   <span data-ttu-id="5c824-111">它的方法 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> 會傳回 <xref:System.IdentityModel.Selectors.X509SecurityTokenProvider> 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="5c824-111">Its method <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> returns an instance of <xref:System.IdentityModel.Selectors.X509SecurityTokenProvider>.</span></span>  
  
 <span data-ttu-id="5c824-112">![顯示如何使用用戶端認證的圖表](../../../../docs/framework/wcf/extending/media/e4971edd-a59f-4571-b36f-7e6b2f0d610f.gif "e4971edd-a59f-4571-b36f-7e6b2f0d610f")</span><span class="sxs-lookup"><span data-stu-id="5c824-112">![Chart showing how client credentials are used](../../../../docs/framework/wcf/extending/media/e4971edd-a59f-4571-b36f-7e6b2f0d610f.gif "e4971edd-a59f-4571-b36f-7e6b2f0d610f")</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="5c824-113">自訂認證，請參閱[逐步解說： 建立自訂用戶端和服務認證](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)。</span><span class="sxs-lookup"><span data-stu-id="5c824-113"> custom credentials, see [Walkthrough: Creating Custom Client and Service Credentials](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).</span></span>  
  
 <span data-ttu-id="5c824-114">此外，您必須建立自訂身分識別驗證器，並將驗證器以自訂繫結連結到一個安全性繫結項目。</span><span class="sxs-lookup"><span data-stu-id="5c824-114">In addition, you must create a custom identity verifier, and link it to a security binding element in a custom binding.</span></span> <span data-ttu-id="5c824-115">同時，不要使用預設認證，而必須使用自訂認證。</span><span class="sxs-lookup"><span data-stu-id="5c824-115">You must also use the custom credentials instead of the default credentials.</span></span>  
  
 <span data-ttu-id="5c824-116">以下的圖表會顯示自訂繫結中使用的類別，以及自訂身分識別驗證器所連結的方法。</span><span class="sxs-lookup"><span data-stu-id="5c824-116">The following diagram shows the classes involved in the custom binding, and how the custom identity verifier is linked.</span></span> <span data-ttu-id="5c824-117">其中包含幾個繫結項目，全部都是繼承自 <xref:System.ServiceModel.Channels.BindingElement>。</span><span class="sxs-lookup"><span data-stu-id="5c824-117">There are several binding elements involved, all of which inherit from <xref:System.ServiceModel.Channels.BindingElement>.</span></span> <span data-ttu-id="5c824-118"><xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> 有 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings><xref:System.ServiceModel.Security.IdentityVerifier>屬性，會傳回 `MyIdentityVerifier`(便是自訂 的來源)的執行個體。</span><span class="sxs-lookup"><span data-stu-id="5c824-118">The <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> has the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> property, which returns an instance of <xref:System.ServiceModel.Security.IdentityVerifier>, from which `MyIdentityVerifier` is customized.</span></span>  
  
 <span data-ttu-id="5c824-119">![顯示自訂繫結項目的圖表](../../../../docs/framework/wcf/extending/media/dddea4a2-0bb4-4921-9bf4-20d4d82c3da5.gif "dddea4a2-0bb4-4921-9bf4-20d4d82c3da5")</span><span class="sxs-lookup"><span data-stu-id="5c824-119">![Chart showing a custom binding element](../../../../docs/framework/wcf/extending/media/dddea4a2-0bb4-4921-9bf4-20d4d82c3da5.gif "dddea4a2-0bb4-4921-9bf4-20d4d82c3da5")</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="5c824-120">建立自訂身分識別驗證器，請參閱 < How to: [How to： 建立自訂的用戶端身分識別驗證器](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)。</span><span class="sxs-lookup"><span data-stu-id="5c824-120"> creating a custom identity verifier, see How to: [How to: Create a Custom Client Identity Verifier](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md).</span></span>  
  
### <a name="to-use-separate-certificates-for-signing-and-encryption"></a><span data-ttu-id="5c824-121">使用個別憑證簽署與加密</span><span class="sxs-lookup"><span data-stu-id="5c824-121">To use separate certificates for signing and encryption</span></span>  
  
1.  <span data-ttu-id="5c824-122">定義從 <xref:System.ServiceModel.Description.ClientCredentials> 類別繼承的新用戶端認證類別。</span><span class="sxs-lookup"><span data-stu-id="5c824-122">Define a new client credentials class that inherits from the <xref:System.ServiceModel.Description.ClientCredentials> class.</span></span> <span data-ttu-id="5c824-123">建立四個新屬性即可允許使用多個憑證規格：`ClientSigningCertificate`、`ClientEncryptingCertificate`、`ServiceSigningCertificate``ServiceEncryptingCertificate`及 。</span><span class="sxs-lookup"><span data-stu-id="5c824-123">Implement four new properties to allow multiple certificates specification: `ClientSigningCertificate`, `ClientEncryptingCertificate`, `ServiceSigningCertificate`, and `ServiceEncryptingCertificate`.</span></span> <span data-ttu-id="5c824-124">此外，覆寫 <xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> 方法，以傳回下一步所定義之自訂 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="5c824-124">Also override the <xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> method to return an instance of the customized <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class that is defined in the next step.</span></span>  
  
     [!code-csharp[c_FourCerts#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#1)]
     [!code-vb[c_FourCerts#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#1)]  
  
2.  <span data-ttu-id="5c824-125">定義從 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> 類別繼承的新用戶端安全性權杖管理員。</span><span class="sxs-lookup"><span data-stu-id="5c824-125">Define a new client security token manager that inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class.</span></span> <span data-ttu-id="5c824-126">覆寫 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> 方法，即可建立適當的安全性權杖提供者。</span><span class="sxs-lookup"><span data-stu-id="5c824-126">Override the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> method to create an appropriate security token provider.</span></span> <span data-ttu-id="5c824-127">`requirement` 參數 (<xref:System.IdentityModel.Selectors.SecurityTokenRequirement>) 可提供訊息方向和金鑰使用方式。</span><span class="sxs-lookup"><span data-stu-id="5c824-127">The `requirement` parameter (a <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>) provides the message direction and key usage.</span></span>  
  
     [!code-csharp[c_FourCerts#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#2)]
     [!code-vb[c_FourCerts#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#2)]  
  
3.  <span data-ttu-id="5c824-128">定義從 <xref:System.ServiceModel.Description.ServiceCredentials> 類別繼承的新服務認證類別。</span><span class="sxs-lookup"><span data-stu-id="5c824-128">Define a new service credentials class that inherits from the <xref:System.ServiceModel.Description.ServiceCredentials> class.</span></span> <span data-ttu-id="5c824-129">建立四個新屬性即可允許使用多個憑證規格：`ClientSigningCertificate`、`ClientEncryptingCertificate`、`ServiceSigningCertificate``ServiceEncryptingCertificate`及 。</span><span class="sxs-lookup"><span data-stu-id="5c824-129">Implement four new properties to allow multiple certificates specification: `ClientSigningCertificate`, `ClientEncryptingCertificate`, `ServiceSigningCertificate`, and `ServiceEncryptingCertificate`.</span></span> <span data-ttu-id="5c824-130">此外，覆寫 <xref:System.ServiceModel.Description.ServiceCredentials.CreateSecurityTokenManager%2A> 方法，以傳回下一步所定義之自訂 <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="5c824-130">Also override the <xref:System.ServiceModel.Description.ServiceCredentials.CreateSecurityTokenManager%2A> method to return an instance of the customized <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> class that is defined in the next step.</span></span>  
  
     [!code-csharp[c_FourCerts#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#3)]
     [!code-vb[c_FourCerts#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#3)]  
  
4.  <span data-ttu-id="5c824-131">定義從 <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> 類別繼承的新服務安全性權杖管理員。</span><span class="sxs-lookup"><span data-stu-id="5c824-131">Define a new service security token manager that inherits from the <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> class.</span></span> <span data-ttu-id="5c824-132">覆寫 <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> 方法，即可建立已指定傳入訊息方向和金鑰使用方式的適當安全性權杖提供者。</span><span class="sxs-lookup"><span data-stu-id="5c824-132">Override the <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> method to create an appropriate security token provider given the passed-in message direction and key usage.</span></span>  
  
     [!code-csharp[c_FourCerts#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#4)]
     [!code-vb[c_FourCerts#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#4)]  
  
### <a name="to-use-multiple-certificates-on-the-client"></a><span data-ttu-id="5c824-133">使用用戶端上的多個憑證</span><span class="sxs-lookup"><span data-stu-id="5c824-133">To use multiple certificates on the client</span></span>  
  
1.  <span data-ttu-id="5c824-134">建立自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="5c824-134">Create a custom binding.</span></span> <span data-ttu-id="5c824-135">安全性繫結項目必須在雙工模式下運作，才能在要求和回應時提供不同的安全性權杖提供者。</span><span class="sxs-lookup"><span data-stu-id="5c824-135">The security binding element must operate in duplex mode to allow different security token providers to be present for requests and responses.</span></span> <span data-ttu-id="5c824-136">執行這項作業的一種方法是使用具雙工能力的傳輸或使用 <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="5c824-136">One way to do this is to use a duplex-capable transport or to use the <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> as shown in the following code.</span></span> <span data-ttu-id="5c824-137">將下一步所定義的自訂 <xref:System.ServiceModel.Security.IdentityVerifier> 連結到安全性繫結項目。</span><span class="sxs-lookup"><span data-stu-id="5c824-137">Link the customized <xref:System.ServiceModel.Security.IdentityVerifier> which is defined in the next step to the security binding element.</span></span> <span data-ttu-id="5c824-138">以先前建立的自訂用戶端認證取代預設的用戶端認證。</span><span class="sxs-lookup"><span data-stu-id="5c824-138">Replace the default client credentials with the customized client credentials previously created.</span></span>  
  
     [!code-csharp[c_FourCerts#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#5)]
     [!code-vb[c_FourCerts#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#5)]  
  
2.  <span data-ttu-id="5c824-139">定義一個自訂的 <xref:System.ServiceModel.Security.IdentityVerifier>。</span><span class="sxs-lookup"><span data-stu-id="5c824-139">Define a custom <xref:System.ServiceModel.Security.IdentityVerifier>.</span></span> <span data-ttu-id="5c824-140">服務會擁有多個識別，因為此時會使用不同的憑證來加密要求及簽署回應。</span><span class="sxs-lookup"><span data-stu-id="5c824-140">The service has multiple identities because different certificates are used to encrypt the request and to sign the response.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5c824-141">在下列範例中所提供的自訂識別驗證器，並不會示範執行任何的端點識別檢查。</span><span class="sxs-lookup"><span data-stu-id="5c824-141">In the following sample, the provided custom identity verifier does not perform any endpoint identity checking for demonstration purposes.</span></span> <span data-ttu-id="5c824-142">但是在實際執行程式碼 (Production Code) 中不建議這樣做。</span><span class="sxs-lookup"><span data-stu-id="5c824-142">This is not recommended practice for production code.</span></span>  
  
     [!code-csharp[c_FourCerts#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#6)]
     [!code-vb[c_FourCerts#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#6)]  
  
### <a name="to-use-multiple-certificates-on-the-service"></a><span data-ttu-id="5c824-143">使用服務上的多個憑證</span><span class="sxs-lookup"><span data-stu-id="5c824-143">To use multiple certificates on the service</span></span>  
  
1.  <span data-ttu-id="5c824-144">建立自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="5c824-144">Create a custom binding.</span></span> <span data-ttu-id="5c824-145">安全性繫結項目必須在雙工模式下運作，才能在要求和回應時提供不同的安全性權杖提供者。</span><span class="sxs-lookup"><span data-stu-id="5c824-145">The security binding element must operate in a duplex mode to allow different security token providers to be present for requests and responses.</span></span> <span data-ttu-id="5c824-146">在用戶端上，使用具雙工能力的傳輸或使用 <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="5c824-146">As with the client, use a duplex-capable transport or use <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> as shown in the following code.</span></span> <span data-ttu-id="5c824-147">以先前建立的自訂服務認證取代預設的服務認證。</span><span class="sxs-lookup"><span data-stu-id="5c824-147">Replace the default service credentials with the customized service credentials previously created.</span></span>  
  
     [!code-csharp[c_FourCerts#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#7)]
     [!code-vb[c_FourCerts#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="5c824-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c824-148">See Also</span></span>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>  
 <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager>  
 <xref:System.ServiceModel.Security.IdentityVerifier>  
 [<span data-ttu-id="5c824-149">逐步解說： 建立自訂用戶端和服務認證</span><span class="sxs-lookup"><span data-stu-id="5c824-149">Walkthrough: Creating Custom Client and Service Credentials</span></span>](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)
