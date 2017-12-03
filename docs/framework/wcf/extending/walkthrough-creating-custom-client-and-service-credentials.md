---
title: "逐步解說：建立自訂用戶端與服務認證"
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
ms.assetid: 2b5ba5c3-0c6c-48e9-9e46-54acaec443ba
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aeea572bea367406b8391339748a76c8bd168a61
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="walkthrough-creating-custom-client-and-service-credentials"></a><span data-ttu-id="38ce1-102">逐步解說：建立自訂用戶端與服務認證</span><span class="sxs-lookup"><span data-stu-id="38ce1-102">Walkthrough: Creating Custom Client and Service Credentials</span></span>
<span data-ttu-id="38ce1-103">此主題顯示如何實作自訂用戶端和服務認證，以及如何使用來自應用程式碼的自訂認證。</span><span class="sxs-lookup"><span data-stu-id="38ce1-103">This topic shows how to implement custom client and service credentials and how to use custom credentials from application code.</span></span>  
  
## <a name="credentials-extensibility-classes"></a><span data-ttu-id="38ce1-104">認證擴充性類別</span><span class="sxs-lookup"><span data-stu-id="38ce1-104">Credentials Extensibility Classes</span></span>  
 <span data-ttu-id="38ce1-105"><xref:System.ServiceModel.Description.ClientCredentials> 和 <xref:System.ServiceModel.Description.ServiceCredentials> 類別是 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 安全性擴充性的主要進入點。</span><span class="sxs-lookup"><span data-stu-id="38ce1-105">The <xref:System.ServiceModel.Description.ClientCredentials> and <xref:System.ServiceModel.Description.ServiceCredentials> classes are the main entry points to the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] security extensibility.</span></span> <span data-ttu-id="38ce1-106">這些認證類別提供能夠讓應用程式碼設定認證資訊，以及將認證類型轉換為安全性權杖的 API </span><span class="sxs-lookup"><span data-stu-id="38ce1-106">These credentials classes provide the APIs that enable application code to set credentials information and to convert credential types into security tokens.</span></span> <span data-ttu-id="38ce1-107">(*安全性語彙基元*是用來傳送 SOAP 訊息內的認證資訊的形式。)這些認證類別的責任可以分為兩部分：</span><span class="sxs-lookup"><span data-stu-id="38ce1-107">(*Security tokens* are the form used to transmit credential information inside SOAP messages.) The responsibilities of these credentials classes can be divided into two areas:</span></span>  
  
-   <span data-ttu-id="38ce1-108">提供 API 讓應用程式設定認證資訊。</span><span class="sxs-lookup"><span data-stu-id="38ce1-108">Provide the APIs for applications to set credentials information.</span></span>  
  
-   <span data-ttu-id="38ce1-109">執行當做 <xref:System.IdentityModel.Selectors.SecurityTokenManager> 實作的處理站。</span><span class="sxs-lookup"><span data-stu-id="38ce1-109">Perform as a factory for <xref:System.IdentityModel.Selectors.SecurityTokenManager> implementations.</span></span>  
  
 <span data-ttu-id="38ce1-110"><xref:System.ServiceModel.Description.ClientCredentials> 和 <xref:System.ServiceModel.Description.ServiceCredentials> 類別都繼承自定義傳回 <xref:System.ServiceModel.Security.SecurityCredentialsManager> 之合約的抽象 <xref:System.IdentityModel.Selectors.SecurityTokenManager> 類別。</span><span class="sxs-lookup"><span data-stu-id="38ce1-110">Both the <xref:System.ServiceModel.Description.ClientCredentials> and the <xref:System.ServiceModel.Description.ServiceCredentials> classes inherit from the abstract <xref:System.ServiceModel.Security.SecurityCredentialsManager> class that defines the contract for returning the <xref:System.IdentityModel.Selectors.SecurityTokenManager>.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="38ce1-111">認證類別，以及它們納入如何[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]安全性架構，請參閱[安全性架構](http://msdn.microsoft.com/en-us/16593476-d36a-408d-808c-ae6fd483e28f)。</span><span class="sxs-lookup"><span data-stu-id="38ce1-111"> the credentials classes and how they fit into the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security architecture, see [Security Architecture](http://msdn.microsoft.com/en-us/16593476-d36a-408d-808c-ae6fd483e28f).</span></span>  
  
 <span data-ttu-id="38ce1-112">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中提供的預設實作會支援系統提供的認證類型，並且建立能夠處理那些認證類型的安全性權杖管理員。</span><span class="sxs-lookup"><span data-stu-id="38ce1-112">The default implementations provided in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] support the system-provided credential types and create a security token manager that is capable of handling those credentials types.</span></span>  
  
## <a name="reasons-to-customize"></a><span data-ttu-id="38ce1-113">自訂原因</span><span class="sxs-lookup"><span data-stu-id="38ce1-113">Reasons to Customize</span></span>  
 <span data-ttu-id="38ce1-114">有幾項自訂用戶端或服務認證類別的原因。</span><span class="sxs-lookup"><span data-stu-id="38ce1-114">There are multiple reasons for customizing either client or service credential classes.</span></span> <span data-ttu-id="38ce1-115">首要需求莫過於變更 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 涉及處理系統提供之認證類型的預設安全性行為，特別是基於下列原因：</span><span class="sxs-lookup"><span data-stu-id="38ce1-115">Foremost is the requirement to change the default [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security behavior with regard to handling system-provided credential types, especially for the following reasons:</span></span>  
  
-   <span data-ttu-id="38ce1-116">使用其他擴充點無法進行若干變更。</span><span class="sxs-lookup"><span data-stu-id="38ce1-116">Changes that are not possible using other extensibility points.</span></span>  
  
-   <span data-ttu-id="38ce1-117">為了加入新的認證類型。</span><span class="sxs-lookup"><span data-stu-id="38ce1-117">Adding new credential types.</span></span>  
  
-   <span data-ttu-id="38ce1-118">為了加入新的自訂安全性權杖類型。</span><span class="sxs-lookup"><span data-stu-id="38ce1-118">Adding new custom security token types.</span></span>  
  
 <span data-ttu-id="38ce1-119">此主題描述如何實作自訂用戶端和服務認證，以及如何在應用程式碼使用它們。</span><span class="sxs-lookup"><span data-stu-id="38ce1-119">This topic describes how to implement custom client and service credentials and how to use them from application code.</span></span>  
  
## <a name="first-in-a-series"></a><span data-ttu-id="38ce1-120">第一步</span><span class="sxs-lookup"><span data-stu-id="38ce1-120">First in a Series</span></span>  
 <span data-ttu-id="38ce1-121">建立自訂認證類別只是第一步，因為自訂認證的原因是要變更關於認證佈建、安全性權杖序列化或驗證的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 行為。</span><span class="sxs-lookup"><span data-stu-id="38ce1-121">Creating a custom credentials class is only the first step, because the reason for customizing credentials is to change [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] behavior regarding credentials provisioning, security token serialization, or authentication.</span></span> <span data-ttu-id="38ce1-122">本章節中的其他主題描述如何建立自訂序列化程式和驗證器。</span><span class="sxs-lookup"><span data-stu-id="38ce1-122">Other topics in this section describe how to create custom serializers and authenticators.</span></span> <span data-ttu-id="38ce1-123">就這一點而言，建立自訂認證類別是所有步驟的第一個主題。</span><span class="sxs-lookup"><span data-stu-id="38ce1-123">In this regard, creating custom credential class is the first topic in the series.</span></span> <span data-ttu-id="38ce1-124">只有在建立自訂認證後才能完成後續動作 (建立自訂序列化程式和驗證器)。</span><span class="sxs-lookup"><span data-stu-id="38ce1-124">Subsequent actions (creating custom serializers and authenticators) can be done only after creating custom credentials.</span></span> <span data-ttu-id="38ce1-125">建構在此主題上的其他主題包含：</span><span class="sxs-lookup"><span data-stu-id="38ce1-125">Additional topics that build upon this topic include:</span></span>  
  
-   [<span data-ttu-id="38ce1-126">如何： 建立自訂安全性權杖提供者</span><span class="sxs-lookup"><span data-stu-id="38ce1-126">How to: Create a Custom Security Token Provider</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
  
-   [<span data-ttu-id="38ce1-127">如何： 建立自訂安全性權杖驗證器</span><span class="sxs-lookup"><span data-stu-id="38ce1-127">How to: Create a Custom Security Token Authenticator</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
  
-   <span data-ttu-id="38ce1-128">[如何： 建立自訂權杖](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)。</span><span class="sxs-lookup"><span data-stu-id="38ce1-128">[How to: Create a Custom Token](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="38ce1-129">程序</span><span class="sxs-lookup"><span data-stu-id="38ce1-129">Procedures</span></span>  
  
#### <a name="to-implement-custom-client-credentials"></a><span data-ttu-id="38ce1-130">實作自訂用戶端認證</span><span class="sxs-lookup"><span data-stu-id="38ce1-130">To implement custom client credentials</span></span>  
  
1.  <span data-ttu-id="38ce1-131">定義衍生自 <xref:System.ServiceModel.Description.ClientCredentials> 類別的新類別。</span><span class="sxs-lookup"><span data-stu-id="38ce1-131">Define a new class derived from the <xref:System.ServiceModel.Description.ClientCredentials> class.</span></span>  
  
2.  <span data-ttu-id="38ce1-132">選擇項。</span><span class="sxs-lookup"><span data-stu-id="38ce1-132">Optional.</span></span> <span data-ttu-id="38ce1-133">為新的認證類型加入新方法或屬性。</span><span class="sxs-lookup"><span data-stu-id="38ce1-133">Add new methods or properties for new credential types.</span></span> <span data-ttu-id="38ce1-134">如果您不需要新增新的認證類型，請略過這個步驟。</span><span class="sxs-lookup"><span data-stu-id="38ce1-134">If you do not add new credential types, skip this step.</span></span> <span data-ttu-id="38ce1-135">下列範例即是加入 `CreditCardNumber` 屬性。</span><span class="sxs-lookup"><span data-stu-id="38ce1-135">The following example adds a `CreditCardNumber` property.</span></span>  
  
3.  <span data-ttu-id="38ce1-136">覆寫 <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="38ce1-136">Override the <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> method.</span></span> <span data-ttu-id="38ce1-137">當使用自訂用戶端認證時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 安全性基礎結構會自動呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="38ce1-137">This method is automatically called by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security infrastructure when the custom client credential is used.</span></span> <span data-ttu-id="38ce1-138">這個方法是負責建立和傳回 <xref:System.IdentityModel.Selectors.SecurityTokenManager> 類別實作的執行個體。</span><span class="sxs-lookup"><span data-stu-id="38ce1-138">This method is responsible for creating and returning an instance of an implementation of the <xref:System.IdentityModel.Selectors.SecurityTokenManager> class.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="38ce1-139">請注意，覆寫 <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> 方法以建立自訂安全性權杖管理員是很重要的。</span><span class="sxs-lookup"><span data-stu-id="38ce1-139">It is important to note that the <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> method is overridden to create a custom security token manager.</span></span> <span data-ttu-id="38ce1-140">衍生自 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> 的安全性權杖管理員，必須傳回衍生自 <xref:System.IdentityModel.Selectors.SecurityTokenProvider> 的自訂安全性權杖提供者，以建立實際的安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="38ce1-140">The security token manager, derived from <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>, must return a custom security token provider, derived from <xref:System.IdentityModel.Selectors.SecurityTokenProvider>, to create the actual security token.</span></span> <span data-ttu-id="38ce1-141">若未依照這個模式建立安全性權杖，應用程式在快取 <xref:System.ServiceModel.ChannelFactory> 物件時 (此乃 WCF 用戶端 Proxy 的預設行為) 可能會運作不正常，以致難免遭受提高權限攻擊。</span><span class="sxs-lookup"><span data-stu-id="38ce1-141">If you do not follow this pattern for creating security tokens, your application may function incorrectly when <xref:System.ServiceModel.ChannelFactory> objects are cached (which is the default behavior for WCF client proxies), potentially resulting in an elevation of privilege attack.</span></span> <span data-ttu-id="38ce1-142">自訂認證物件是快取為 <xref:System.ServiceModel.ChannelFactory> 的一部分。</span><span class="sxs-lookup"><span data-stu-id="38ce1-142">The custom credential object is cached as part of the <xref:System.ServiceModel.ChannelFactory>.</span></span> <span data-ttu-id="38ce1-143">不過，自訂 <xref:System.IdentityModel.Selectors.SecurityTokenManager> 則為每次叫用時所建立，因而只要將權仗建立邏輯置於 <xref:System.IdentityModel.Selectors.SecurityTokenManager> 中，便能減緩安全性威脅。</span><span class="sxs-lookup"><span data-stu-id="38ce1-143">However, the custom <xref:System.IdentityModel.Selectors.SecurityTokenManager> is created on every invocation, which mitigates the security threat as long as the token creation logic is placed in the <xref:System.IdentityModel.Selectors.SecurityTokenManager>.</span></span>  
  
4.  <span data-ttu-id="38ce1-144">覆寫 <xref:System.ServiceModel.Description.ClientCredentials.CloneCore%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="38ce1-144">Override the <xref:System.ServiceModel.Description.ClientCredentials.CloneCore%2A> method.</span></span>  
  
     [!code-csharp[c_CustomCredentials#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#1)]
     [!code-vb[c_CustomCredentials#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#1)]  
  
#### <a name="to-implement-a-custom-client-security-token-manager"></a><span data-ttu-id="38ce1-145">實作自訂用戶端安全性權杖管理員</span><span class="sxs-lookup"><span data-stu-id="38ce1-145">To implement a custom client security token manager</span></span>  
  
1.  <span data-ttu-id="38ce1-146">定義衍生自 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> 的新類別。</span><span class="sxs-lookup"><span data-stu-id="38ce1-146">Define a new class derived from <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>.</span></span>  
  
2.  <span data-ttu-id="38ce1-147">選擇項。</span><span class="sxs-lookup"><span data-stu-id="38ce1-147">Optional.</span></span> <span data-ttu-id="38ce1-148">如果必須建立自訂 <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> 實作，請覆寫 <xref:System.IdentityModel.Selectors.SecurityTokenProvider> 方法。</span><span class="sxs-lookup"><span data-stu-id="38ce1-148">Override the <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> method if a custom <xref:System.IdentityModel.Selectors.SecurityTokenProvider> implementation must be created.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="38ce1-149">自訂安全性權杖提供者，請參閱[How to： 建立自訂安全性權杖提供者](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="38ce1-149"> custom security token providers, see [How to: Create a Custom Security Token Provider](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).</span></span>  
  
3.  <span data-ttu-id="38ce1-150">選擇項。</span><span class="sxs-lookup"><span data-stu-id="38ce1-150">Optional.</span></span> <span data-ttu-id="38ce1-151">如果必須建立自訂 <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%28System.IdentityModel.Selectors.SecurityTokenRequirement%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%40%29> 實作，請覆寫 <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> 方法。</span><span class="sxs-lookup"><span data-stu-id="38ce1-151">Override the <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%28System.IdentityModel.Selectors.SecurityTokenRequirement%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%40%29> method if a custom <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> implementation must be created.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="38ce1-152">自訂安全性權杖驗證器，請參閱[How to： 建立自訂安全性權杖驗證器](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)。</span><span class="sxs-lookup"><span data-stu-id="38ce1-152"> custom security token authenticators, see [How to: Create a Custom Security Token Authenticator](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md).</span></span>  
  
4.  <span data-ttu-id="38ce1-153">選擇項。</span><span class="sxs-lookup"><span data-stu-id="38ce1-153">Optional.</span></span> <span data-ttu-id="38ce1-154">如果必須建立自訂 <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%2A>，請覆寫 <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> 方法。</span><span class="sxs-lookup"><span data-stu-id="38ce1-154">Override the <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%2A> method if a custom <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> must be created.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="38ce1-155">自訂安全性權杖與自訂安全性權杖序列化程式，請參閱[How to： 建立自訂權杖](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)。</span><span class="sxs-lookup"><span data-stu-id="38ce1-155"> custom security tokens and custom security token serializers, see [How to: Create a Custom Token](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).</span></span>  
  
     [!code-csharp[c_CustomCredentials#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#2)]
     [!code-vb[c_CustomCredentials#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#2)]  
  
#### <a name="to-use-a-custom-client-credentials-from-application-code"></a><span data-ttu-id="38ce1-156">使用來自應用程式碼的自訂用戶端認證</span><span class="sxs-lookup"><span data-stu-id="38ce1-156">To use a custom client credentials from application code</span></span>  
  
1.  <span data-ttu-id="38ce1-157">建立所產生之用戶端的執行個體以代表服務介面，或建立 <xref:System.ServiceModel.ChannelFactory> 的執行個體指向想要通訊的服務。</span><span class="sxs-lookup"><span data-stu-id="38ce1-157">Either create an instance of the generated client that represents the service interface, or create an instance of the <xref:System.ServiceModel.ChannelFactory> pointing to a service you want to communicate with.</span></span>  
  
2.  <span data-ttu-id="38ce1-158">從 <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> 集合中移除系統提供的用戶端認證行為，您可以透過 <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> 屬性存取這個集合。</span><span class="sxs-lookup"><span data-stu-id="38ce1-158">Remove the system-provided client credentials behavior from the <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> collection, which can be accessed through the <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> property.</span></span>  
  
3.  <span data-ttu-id="38ce1-159">建立自訂用戶端認證類別的新執行個體，並將其新增至 <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> 集合中，您可以透過 <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> 屬性存取這個集合。</span><span class="sxs-lookup"><span data-stu-id="38ce1-159">Create a new instance of a custom client credentials class and add it to the <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> collection, which can be accessed through the <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> property.</span></span>  
  
     [!code-csharp[c_CustomCredentials#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#3)]
     [!code-vb[c_CustomCredentials#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#3)]  
  
 <span data-ttu-id="38ce1-160">前面的程序示範如何從應用程式程式碼使用用戶端認證。</span><span class="sxs-lookup"><span data-stu-id="38ce1-160">The previous procedure shows how to use client credentials from application code.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="38ce1-161"> 認證也可以使用應用程式組態檔進行設定。</span><span class="sxs-lookup"><span data-stu-id="38ce1-161"> credentials can also be configured using the application configuration file.</span></span> <span data-ttu-id="38ce1-162">在硬式編碼方面通常偏好使用應用程式組態，因為能夠在不修改原始程式碼、重新編譯和重新部署的情況下修改應用程式參數。</span><span class="sxs-lookup"><span data-stu-id="38ce1-162">Using application configuration is often preferable to hard-coding because it enables modification of application parameters without having to modify the source, recompiling, and redeployment.</span></span>  
  
 <span data-ttu-id="38ce1-163">下一個程序描述如何提供自訂認證組態的支援。</span><span class="sxs-lookup"><span data-stu-id="38ce1-163">The next procedure describes how to provide support for configuration of custom credentials.</span></span>  
  
#### <a name="creating-a-configuration-handler-for-custom-client-credentials"></a><span data-ttu-id="38ce1-164">建立自訂用戶端認證的組態處理常式</span><span class="sxs-lookup"><span data-stu-id="38ce1-164">Creating a configuration handler for custom client credentials</span></span>  
  
1.  <span data-ttu-id="38ce1-165">定義衍生自 <xref:System.ServiceModel.Configuration.ClientCredentialsElement> 的新類別。</span><span class="sxs-lookup"><span data-stu-id="38ce1-165">Define a new class derived from <xref:System.ServiceModel.Configuration.ClientCredentialsElement>.</span></span>  
  
2.  <span data-ttu-id="38ce1-166">選擇項。</span><span class="sxs-lookup"><span data-stu-id="38ce1-166">Optional.</span></span> <span data-ttu-id="38ce1-167">針對想要透過應用程式組態公開的所有其他組態參數新增屬性。</span><span class="sxs-lookup"><span data-stu-id="38ce1-167">Add properties for all additional configuration parameters that you want to expose through application configuration.</span></span> <span data-ttu-id="38ce1-168">下列範例會新增一個名為 `CreditCardNumber` 的屬性。</span><span class="sxs-lookup"><span data-stu-id="38ce1-168">The example below adds one property named `CreditCardNumber`.</span></span>  
  
3.  <span data-ttu-id="38ce1-169">覆寫 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.BehaviorType%2A> 屬性以傳回使用組態項目建立之自訂用戶端認證類別的型別。</span><span class="sxs-lookup"><span data-stu-id="38ce1-169">Override the <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.BehaviorType%2A> property to return the type of the custom client credentials class created with the configuration element.</span></span>  
  
4.  <span data-ttu-id="38ce1-170">覆寫 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.CreateBehavior%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="38ce1-170">Override the <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.CreateBehavior%2A> method.</span></span> <span data-ttu-id="38ce1-171">這個方法會根據從組態檔載入的設定，負責建立和傳回自訂認證類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="38ce1-171">The method is responsible for creating and returning an instance of the custom credential class based on the settings loaded from the configuration file.</span></span> <span data-ttu-id="38ce1-172">請呼叫這個方法的基底 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ApplyConfiguration%28System.ServiceModel.Description.ClientCredentials%29> 方法，擷取已載入自訂用戶端認證執行個體之系統提供的認證設定。</span><span class="sxs-lookup"><span data-stu-id="38ce1-172">Call the base <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ApplyConfiguration%28System.ServiceModel.Description.ClientCredentials%29> method from this method to retrieve the system-provided credentials settings loaded into your custom client credentials instance.</span></span>  
  
5.  <span data-ttu-id="38ce1-173">選擇項。</span><span class="sxs-lookup"><span data-stu-id="38ce1-173">Optional.</span></span> <span data-ttu-id="38ce1-174">如果您在步驟 2 新增其他屬性，就需要覆寫 <xref:System.Configuration.ConfigurationElement.Properties%2A> 屬性以登錄組態架構的其他組態設定，才能加以辨認。</span><span class="sxs-lookup"><span data-stu-id="38ce1-174">If you added additional properties in step 2, you need to override the <xref:System.Configuration.ConfigurationElement.Properties%2A> property in order to register your additional configuration settings for the configuration framework to recognize them.</span></span> <span data-ttu-id="38ce1-175">結合屬性與基底類別屬性，以便透過這個自訂用戶端認證組態項目設定系統提供的設定。</span><span class="sxs-lookup"><span data-stu-id="38ce1-175">Combine your properties with the base class properties to allow the system-provided settings to be configured through this custom client credentials configuration element.</span></span>  
  
     [!code-csharp[c_CustomCredentials#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#7)]
     [!code-vb[c_CustomCredentials#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#7)]  
  
 <span data-ttu-id="38ce1-176">在擁有組態處理常式類別後，就能夠整合至 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 組態架構。</span><span class="sxs-lookup"><span data-stu-id="38ce1-176">Once you have the configuration handler class, it can be integrated into the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] configuration framework.</span></span> <span data-ttu-id="38ce1-177">就能夠在用戶端端點行為項目中使用自訂用戶端認證，如同下一個程序中所示。</span><span class="sxs-lookup"><span data-stu-id="38ce1-177">That enables the custom client credentials to be used in the client endpoint behavior elements, as shown in the next procedure.</span></span>  
  
#### <a name="to-register-and-use-a-custom-client-credentials-configuration-handler-in-the-application-configuration"></a><span data-ttu-id="38ce1-178">在應用程式組態中登錄和使用自訂用戶端認證組態處理常式</span><span class="sxs-lookup"><span data-stu-id="38ce1-178">To register and use a custom client credentials configuration handler in the application configuration</span></span>  
  
1.  <span data-ttu-id="38ce1-179">新增 <`extensions`> 元素與 <`behaviorExtensions`> 組態檔項目。</span><span class="sxs-lookup"><span data-stu-id="38ce1-179">Add an <`extensions`> element and a <`behaviorExtensions`> element to the configuration file.</span></span>  
  
2.  <span data-ttu-id="38ce1-180">新增 <`add`> 項目 <`behaviorExtensions`> 項目並設定`name`屬性設為適當值。</span><span class="sxs-lookup"><span data-stu-id="38ce1-180">Add an <`add`> element to the <`behaviorExtensions`> element and set the `name` attribute to an appropriate value.</span></span>  
  
3.  <span data-ttu-id="38ce1-181">將 `type` 屬性設定為完整型別名稱。</span><span class="sxs-lookup"><span data-stu-id="38ce1-181">Set the `type` attribute to the fully-qualified type name.</span></span> <span data-ttu-id="38ce1-182">同時包含組件名稱和其他組件屬性。</span><span class="sxs-lookup"><span data-stu-id="38ce1-182">Also include the assembly name and other assembly attributes.</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <extensions>  
        <behaviorExtensions>  
          <add name="myClientCredentials" type="Microsoft.ServiceModel.Samples.MyClientCredentialsConfigHandler, CustomCredentials, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
      </extensions>  
    <system.serviceModel>  
    ```  
  
4.  <span data-ttu-id="38ce1-183">註冊您的組態處理常式之後, 的自訂認證項目也可以使用相同的組態檔，而不是系統提供 <`clientCredentials`> 項目。</span><span class="sxs-lookup"><span data-stu-id="38ce1-183">After registering your configuration handler, the custom credentials element can be used inside the same configuration file instead of the system-provided <`clientCredentials`> element.</span></span> <span data-ttu-id="38ce1-184">您可以同時使用系統提供的屬性，以及新增至組態處理常式實作的任何新屬性。</span><span class="sxs-lookup"><span data-stu-id="38ce1-184">You can use both the system-provided properties and any new properties that you have added to your configuration handler implementation.</span></span> <span data-ttu-id="38ce1-185">下列程式碼範例會使用 `creditCardNumber` 屬性 (Attribute) 設定自訂屬性 (Property) 的值。</span><span class="sxs-lookup"><span data-stu-id="38ce1-185">The following example sets the value of a custom property using the `creditCardNumber` attribute.</span></span>  
  
    ```xml  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="myClientCredentialsBehavior">  
          <myClientCredentials creditCardNumber="123-123-123"/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    ```  
  
#### <a name="to-implement-custom-service-credentials"></a><span data-ttu-id="38ce1-186">實作自訂服務認證</span><span class="sxs-lookup"><span data-stu-id="38ce1-186">To implement custom service credentials</span></span>  
  
1.  <span data-ttu-id="38ce1-187">定義衍生自 <xref:System.ServiceModel.Description.ServiceCredentials> 的新類別。</span><span class="sxs-lookup"><span data-stu-id="38ce1-187">Define a new class derived from <xref:System.ServiceModel.Description.ServiceCredentials>.</span></span>  
  
2.  <span data-ttu-id="38ce1-188">選擇項。</span><span class="sxs-lookup"><span data-stu-id="38ce1-188">Optional.</span></span> <span data-ttu-id="38ce1-189">新增新的屬性以提供已新增之新認證值的 API。</span><span class="sxs-lookup"><span data-stu-id="38ce1-189">Add new properties to provide APIs for new credential values that are being added.</span></span> <span data-ttu-id="38ce1-190">如果您不需要新增新的認證值，請略過這個步驟。</span><span class="sxs-lookup"><span data-stu-id="38ce1-190">If you do not add new credential values, skip this step.</span></span> <span data-ttu-id="38ce1-191">下列程式碼範例會新增 `AdditionalCertificate` 屬性。</span><span class="sxs-lookup"><span data-stu-id="38ce1-191">The following example adds an `AdditionalCertificate` property.</span></span>  
  
3.  <span data-ttu-id="38ce1-192">覆寫 <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="38ce1-192">Override the <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> method.</span></span> <span data-ttu-id="38ce1-193">當使用自訂用戶端認證時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 基礎結構會自動呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="38ce1-193">This method is automatically called by the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastructure when the custom client credential is used.</span></span> <span data-ttu-id="38ce1-194">這個方法是負責建立和傳回 <xref:System.IdentityModel.Selectors.SecurityTokenManager> 類別實作的執行個體 (在下一個程序中會描述)。</span><span class="sxs-lookup"><span data-stu-id="38ce1-194">The method is responsible for creating and returning an instance of an implementation of the <xref:System.IdentityModel.Selectors.SecurityTokenManager> class (described in the next procedure).</span></span>  
  
4.  <span data-ttu-id="38ce1-195">選擇項。</span><span class="sxs-lookup"><span data-stu-id="38ce1-195">Optional.</span></span> <span data-ttu-id="38ce1-196">覆寫 <xref:System.ServiceModel.Description.ServiceCredentials.CloneCore%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="38ce1-196">Override the <xref:System.ServiceModel.Description.ServiceCredentials.CloneCore%2A> method.</span></span> <span data-ttu-id="38ce1-197">只有在將新屬性或內部欄位新增至自訂用戶端認證實作時才會需要這麼做。</span><span class="sxs-lookup"><span data-stu-id="38ce1-197">This is required only if adding new properties or internal fields to the custom client credentials implementation.</span></span>  
  
     [!code-csharp[c_CustomCredentials#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#4)]
     [!code-vb[c_CustomCredentials#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#4)]  
  
#### <a name="to-implement-a-custom-service-security-token-manager"></a><span data-ttu-id="38ce1-198">實作自訂服務安全性權杖管理員</span><span class="sxs-lookup"><span data-stu-id="38ce1-198">To implement a custom service security token manager</span></span>  
  
1.  <span data-ttu-id="38ce1-199">定義衍生自 <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> 類別的新類別。</span><span class="sxs-lookup"><span data-stu-id="38ce1-199">Define a new class derived from the <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> class.</span></span>  
  
2.  <span data-ttu-id="38ce1-200">選擇項。</span><span class="sxs-lookup"><span data-stu-id="38ce1-200">Optional.</span></span> <span data-ttu-id="38ce1-201">如果必須建立自訂 <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%2A> 實作，請覆寫 <xref:System.IdentityModel.Selectors.SecurityTokenProvider> 方法。</span><span class="sxs-lookup"><span data-stu-id="38ce1-201">Override the <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%2A> method if a custom <xref:System.IdentityModel.Selectors.SecurityTokenProvider> implementation must be created.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="38ce1-202">自訂安全性權杖提供者，請參閱[How to： 建立自訂安全性權杖提供者](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="38ce1-202"> custom security token providers, see [How to: Create a Custom Security Token Provider](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).</span></span>  
  
3.  <span data-ttu-id="38ce1-203">選擇項。</span><span class="sxs-lookup"><span data-stu-id="38ce1-203">Optional.</span></span> <span data-ttu-id="38ce1-204">如果必須建立自訂 <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> 實作，請覆寫 <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> 方法。</span><span class="sxs-lookup"><span data-stu-id="38ce1-204">Override the <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> method if a custom <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> implementation must be created.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="38ce1-205">自訂安全性權杖驗證器，請參閱[How to： 建立自訂安全性權杖驗證器](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)主題。</span><span class="sxs-lookup"><span data-stu-id="38ce1-205"> custom security token authenticators, see [How to: Create a Custom Security Token Authenticator](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md) topic.</span></span>  
  
4.  <span data-ttu-id="38ce1-206">選擇項。</span><span class="sxs-lookup"><span data-stu-id="38ce1-206">Optional.</span></span> <span data-ttu-id="38ce1-207">如果必須建立自訂 <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%28System.IdentityModel.Selectors.SecurityTokenVersion%29>，請覆寫 <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> 方法。</span><span class="sxs-lookup"><span data-stu-id="38ce1-207">Override the <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%28System.IdentityModel.Selectors.SecurityTokenVersion%29> method if a custom <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> must be created.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="38ce1-208">自訂安全性權杖與自訂安全性權杖序列化程式，請參閱[How to： 建立自訂權杖](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)。</span><span class="sxs-lookup"><span data-stu-id="38ce1-208"> custom security tokens and custom security token serializers, see [How to: Create a Custom Token](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).</span></span>  
  
     [!code-csharp[c_CustomCredentials#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#5)]
     [!code-vb[c_CustomCredentials#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#5)]  
  
#### <a name="to-use-custom-service-credentials-from-application-code"></a><span data-ttu-id="38ce1-209">使用來自應用程式碼的自訂服務認證</span><span class="sxs-lookup"><span data-stu-id="38ce1-209">To use custom service credentials from application code</span></span>  
  
1.  <span data-ttu-id="38ce1-210">建立 <xref:System.ServiceModel.ServiceHost> 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="38ce1-210">Create an instance of the <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
2.  <span data-ttu-id="38ce1-211">從 <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> 集合移除系統提供的服務認證行為。</span><span class="sxs-lookup"><span data-stu-id="38ce1-211">Remove the system-provided service credentials behavior from the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection.</span></span>  
  
3.  <span data-ttu-id="38ce1-212">建立自訂服務認證類別的新執行個體，並將其新增至 <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> 集合。</span><span class="sxs-lookup"><span data-stu-id="38ce1-212">Create a new instance of the custom service credentials class and add it to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection.</span></span>  
  
     [!code-csharp[c_CustomCredentials#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#6)]
     [!code-vb[c_CustomCredentials#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#6)]  
  
 <span data-ttu-id="38ce1-213">使用上列程序「`To create a configuration handler for custom client credentials`」和「`To register and use a custom client credentials configuration handler in the application configuration`」中描述的步驟加入對組態的支援。唯一的差別是使用 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement> 類別而不是 <xref:System.ServiceModel.Configuration.ClientCredentialsElement> 類別，當做組態處理常式的基底類別。</span><span class="sxs-lookup"><span data-stu-id="38ce1-213">Add support for configuration using the steps described previously in the procedures "`To create a configuration handler for custom client credentials`" and "`To register and use a custom client credentials configuration handler in the application configuration`." The only difference is to use the <xref:System.ServiceModel.Configuration.ServiceCredentialsElement> class instead of the <xref:System.ServiceModel.Configuration.ClientCredentialsElement> class as a base class for the configuration handler.</span></span> <span data-ttu-id="38ce1-214">然後可以在使用系統提供 `<serviceCredentials>` 項目的地方使用自訂服務認證項目。</span><span class="sxs-lookup"><span data-stu-id="38ce1-214">The custom service credential element can then be used wherever the system-provided `<serviceCredentials>` element is used.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38ce1-215">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38ce1-215">See Also</span></span>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
 <xref:System.ServiceModel.Security.SecurityCredentialsManager>  
 <xref:System.IdentityModel.Selectors.SecurityTokenManager>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>  
 [<span data-ttu-id="38ce1-216">如何： 建立自訂安全性權杖提供者</span><span class="sxs-lookup"><span data-stu-id="38ce1-216">How to: Create a Custom Security Token Provider</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 [<span data-ttu-id="38ce1-217">如何： 建立自訂安全性權杖驗證器</span><span class="sxs-lookup"><span data-stu-id="38ce1-217">How to: Create a Custom Security Token Authenticator</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 [<span data-ttu-id="38ce1-218">如何： 建立自訂權杖</span><span class="sxs-lookup"><span data-stu-id="38ce1-218">How to: Create a Custom Token</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)
