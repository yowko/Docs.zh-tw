---
title: 逐步解說：建立自訂用戶端與服務認證
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b5ba5c3-0c6c-48e9-9e46-54acaec443ba
ms.openlocfilehash: d49df909521b3b5e5cf509c1367821856e91e30b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795479"
---
# <a name="walkthrough-creating-custom-client-and-service-credentials"></a><span data-ttu-id="dee76-102">逐步解說：建立自訂用戶端與服務認證</span><span class="sxs-lookup"><span data-stu-id="dee76-102">Walkthrough: Creating Custom Client and Service Credentials</span></span>

<span data-ttu-id="dee76-103">此主題顯示如何實作自訂用戶端和服務認證，以及如何使用來自應用程式碼的自訂認證。</span><span class="sxs-lookup"><span data-stu-id="dee76-103">This topic shows how to implement custom client and service credentials and how to use custom credentials from application code.</span></span>

## <a name="credentials-extensibility-classes"></a><span data-ttu-id="dee76-104">認證擴充性類別</span><span class="sxs-lookup"><span data-stu-id="dee76-104">Credentials Extensibility Classes</span></span>

<span data-ttu-id="dee76-105"><xref:System.ServiceModel.Description.ClientCredentials> 和<xref:System.ServiceModel.Description.ServiceCredentials>類別是 Windows Communication Foundation （WCF）安全性擴充性的主要進入點。</span><span class="sxs-lookup"><span data-stu-id="dee76-105">The <xref:System.ServiceModel.Description.ClientCredentials> and <xref:System.ServiceModel.Description.ServiceCredentials> classes are the main entry points to the Windows Communication Foundation (WCF) security extensibility.</span></span> <span data-ttu-id="dee76-106">這些認證類別提供能夠讓應用程式碼設定認證資訊，以及將認證類型轉換為安全性權杖的 API</span><span class="sxs-lookup"><span data-stu-id="dee76-106">These credentials classes provide the APIs that enable application code to set credentials information and to convert credential types into security tokens.</span></span> <span data-ttu-id="dee76-107">（*安全性權杖*是用來在 SOAP 訊息內傳輸認證資訊的格式）。這些認證類別的責任可以分為兩部分：</span><span class="sxs-lookup"><span data-stu-id="dee76-107">(*Security tokens* are the form used to transmit credential information inside SOAP messages.) The responsibilities of these credentials classes can be divided into two areas:</span></span>

- <span data-ttu-id="dee76-108">提供 API 讓應用程式設定認證資訊。</span><span class="sxs-lookup"><span data-stu-id="dee76-108">Provide the APIs for applications to set credentials information.</span></span>

- <span data-ttu-id="dee76-109">執行當做 <xref:System.IdentityModel.Selectors.SecurityTokenManager> 實作的處理站。</span><span class="sxs-lookup"><span data-stu-id="dee76-109">Perform as a factory for <xref:System.IdentityModel.Selectors.SecurityTokenManager> implementations.</span></span>

<span data-ttu-id="dee76-110">WCF 中提供的預設實現支援系統提供的認證類型，並建立能夠處理這些認證類型的安全性權杖管理員。</span><span class="sxs-lookup"><span data-stu-id="dee76-110">The default implementations provided in WCF support the system-provided credential types and create a security token manager that is capable of handling those credentials types.</span></span>

## <a name="reasons-to-customize"></a><span data-ttu-id="dee76-111">自訂原因</span><span class="sxs-lookup"><span data-stu-id="dee76-111">Reasons to Customize</span></span>

<span data-ttu-id="dee76-112">有幾項自訂用戶端或服務認證類別的原因。</span><span class="sxs-lookup"><span data-stu-id="dee76-112">There are multiple reasons for customizing either client or service credential classes.</span></span> <span data-ttu-id="dee76-113">最重要的是，變更處理系統提供之認證類型的預設 WCF 安全性行為的需求，特別是基於下列原因：</span><span class="sxs-lookup"><span data-stu-id="dee76-113">Foremost is the requirement to change the default WCF security behavior with regard to handling system-provided credential types, especially for the following reasons:</span></span>

- <span data-ttu-id="dee76-114">使用其他擴充點無法進行若干變更。</span><span class="sxs-lookup"><span data-stu-id="dee76-114">Changes that are not possible using other extensibility points.</span></span>

- <span data-ttu-id="dee76-115">為了加入新的認證類型。</span><span class="sxs-lookup"><span data-stu-id="dee76-115">Adding new credential types.</span></span>

- <span data-ttu-id="dee76-116">為了加入新的自訂安全性權杖類型。</span><span class="sxs-lookup"><span data-stu-id="dee76-116">Adding new custom security token types.</span></span>

<span data-ttu-id="dee76-117">此主題描述如何實作自訂用戶端和服務認證，以及如何在應用程式碼使用它們。</span><span class="sxs-lookup"><span data-stu-id="dee76-117">This topic describes how to implement custom client and service credentials and how to use them from application code.</span></span>

## <a name="first-in-a-series"></a><span data-ttu-id="dee76-118">第一步</span><span class="sxs-lookup"><span data-stu-id="dee76-118">First in a Series</span></span>

<span data-ttu-id="dee76-119">建立自訂認證類別只是第一個步驟，因為自訂認證的原因是要變更關於認證布建、安全性權杖序列化或驗證的 WCF 行為。</span><span class="sxs-lookup"><span data-stu-id="dee76-119">Creating a custom credentials class is only the first step, because the reason for customizing credentials is to change WCF behavior regarding credentials provisioning, security token serialization, or authentication.</span></span> <span data-ttu-id="dee76-120">本章節中的其他主題描述如何建立自訂序列化程式和驗證器。</span><span class="sxs-lookup"><span data-stu-id="dee76-120">Other topics in this section describe how to create custom serializers and authenticators.</span></span> <span data-ttu-id="dee76-121">就這一點而言，建立自訂認證類別是所有步驟的第一個主題。</span><span class="sxs-lookup"><span data-stu-id="dee76-121">In this regard, creating custom credential class is the first topic in the series.</span></span> <span data-ttu-id="dee76-122">只有在建立自訂認證後才能完成後續動作 (建立自訂序列化程式和驗證器)。</span><span class="sxs-lookup"><span data-stu-id="dee76-122">Subsequent actions (creating custom serializers and authenticators) can be done only after creating custom credentials.</span></span> <span data-ttu-id="dee76-123">建構在此主題上的其他主題包含：</span><span class="sxs-lookup"><span data-stu-id="dee76-123">Additional topics that build upon this topic include:</span></span>

- [<span data-ttu-id="dee76-124">如何：建立自訂安全性權杖提供者</span><span class="sxs-lookup"><span data-stu-id="dee76-124">How to: Create a Custom Security Token Provider</span></span>](how-to-create-a-custom-security-token-provider.md)

- [<span data-ttu-id="dee76-125">如何：建立自訂安全性權杖驗證器</span><span class="sxs-lookup"><span data-stu-id="dee76-125">How to: Create a Custom Security Token Authenticator</span></span>](how-to-create-a-custom-security-token-authenticator.md)

- <span data-ttu-id="dee76-126">[如何：建立自訂權杖](how-to-create-a-custom-token.md)。</span><span class="sxs-lookup"><span data-stu-id="dee76-126">[How to: Create a Custom Token](how-to-create-a-custom-token.md).</span></span>

## <a name="procedures"></a><span data-ttu-id="dee76-127">程序</span><span class="sxs-lookup"><span data-stu-id="dee76-127">Procedures</span></span>

#### <a name="to-implement-custom-client-credentials"></a><span data-ttu-id="dee76-128">實作自訂用戶端認證</span><span class="sxs-lookup"><span data-stu-id="dee76-128">To implement custom client credentials</span></span>

1. <span data-ttu-id="dee76-129">定義衍生自 <xref:System.ServiceModel.Description.ClientCredentials> 類別的新類別。</span><span class="sxs-lookup"><span data-stu-id="dee76-129">Define a new class derived from the <xref:System.ServiceModel.Description.ClientCredentials> class.</span></span>

2. <span data-ttu-id="dee76-130">選擇性。</span><span class="sxs-lookup"><span data-stu-id="dee76-130">Optional.</span></span> <span data-ttu-id="dee76-131">為新的認證類型加入新方法或屬性。</span><span class="sxs-lookup"><span data-stu-id="dee76-131">Add new methods or properties for new credential types.</span></span> <span data-ttu-id="dee76-132">如果您不需要新增新的認證類型，請略過這個步驟。</span><span class="sxs-lookup"><span data-stu-id="dee76-132">If you do not add new credential types, skip this step.</span></span> <span data-ttu-id="dee76-133">下列範例即是加入 `CreditCardNumber` 屬性。</span><span class="sxs-lookup"><span data-stu-id="dee76-133">The following example adds a `CreditCardNumber` property.</span></span>

3. <span data-ttu-id="dee76-134">覆寫 <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="dee76-134">Override the <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> method.</span></span> <span data-ttu-id="dee76-135">當使用自訂用戶端認證時，WCF 安全性基礎結構會自動呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="dee76-135">This method is automatically called by WCF security infrastructure when the custom client credential is used.</span></span> <span data-ttu-id="dee76-136">這個方法是負責建立和傳回 <xref:System.IdentityModel.Selectors.SecurityTokenManager> 類別實作的執行個體。</span><span class="sxs-lookup"><span data-stu-id="dee76-136">This method is responsible for creating and returning an instance of an implementation of the <xref:System.IdentityModel.Selectors.SecurityTokenManager> class.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="dee76-137">請注意，覆寫 <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> 方法以建立自訂安全性權杖管理員是很重要的。</span><span class="sxs-lookup"><span data-stu-id="dee76-137">It is important to note that the <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> method is overridden to create a custom security token manager.</span></span> <span data-ttu-id="dee76-138">衍生自 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> 的安全性權杖管理員，必須傳回衍生自 <xref:System.IdentityModel.Selectors.SecurityTokenProvider> 的自訂安全性權杖提供者，以建立實際的安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="dee76-138">The security token manager, derived from <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>, must return a custom security token provider, derived from <xref:System.IdentityModel.Selectors.SecurityTokenProvider>, to create the actual security token.</span></span> <span data-ttu-id="dee76-139">若未依照這個模式建立安全性權杖，應用程式在快取 <xref:System.ServiceModel.ChannelFactory> 物件時 (此乃 WCF 用戶端 Proxy 的預設行為) 可能會運作不正常，以致難免遭受提高權限攻擊。</span><span class="sxs-lookup"><span data-stu-id="dee76-139">If you do not follow this pattern for creating security tokens, your application may function incorrectly when <xref:System.ServiceModel.ChannelFactory> objects are cached (which is the default behavior for WCF client proxies), potentially resulting in an elevation of privilege attack.</span></span> <span data-ttu-id="dee76-140">自訂認證物件是快取為 <xref:System.ServiceModel.ChannelFactory> 的一部分。</span><span class="sxs-lookup"><span data-stu-id="dee76-140">The custom credential object is cached as part of the <xref:System.ServiceModel.ChannelFactory>.</span></span> <span data-ttu-id="dee76-141">不過，自訂 <xref:System.IdentityModel.Selectors.SecurityTokenManager> 則為每次叫用時所建立，因而只要將權仗建立邏輯置於 <xref:System.IdentityModel.Selectors.SecurityTokenManager> 中，便能減緩安全性威脅。</span><span class="sxs-lookup"><span data-stu-id="dee76-141">However, the custom <xref:System.IdentityModel.Selectors.SecurityTokenManager> is created on every invocation, which mitigates the security threat as long as the token creation logic is placed in the <xref:System.IdentityModel.Selectors.SecurityTokenManager>.</span></span>

4. <span data-ttu-id="dee76-142">覆寫 <xref:System.ServiceModel.Description.ClientCredentials.CloneCore%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="dee76-142">Override the <xref:System.ServiceModel.Description.ClientCredentials.CloneCore%2A> method.</span></span>

    [!code-csharp[c_CustomCredentials#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#1)]
    [!code-vb[c_CustomCredentials#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#1)]

#### <a name="to-implement-a-custom-client-security-token-manager"></a><span data-ttu-id="dee76-143">實作自訂用戶端安全性權杖管理員</span><span class="sxs-lookup"><span data-stu-id="dee76-143">To implement a custom client security token manager</span></span>

1. <span data-ttu-id="dee76-144">定義衍生自 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> 的新類別。</span><span class="sxs-lookup"><span data-stu-id="dee76-144">Define a new class derived from <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>.</span></span>

2. <span data-ttu-id="dee76-145">選擇性。</span><span class="sxs-lookup"><span data-stu-id="dee76-145">Optional.</span></span> <span data-ttu-id="dee76-146">如果必須建立自訂 <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> 實作，請覆寫 <xref:System.IdentityModel.Selectors.SecurityTokenProvider> 方法。</span><span class="sxs-lookup"><span data-stu-id="dee76-146">Override the <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> method if a custom <xref:System.IdentityModel.Selectors.SecurityTokenProvider> implementation must be created.</span></span> <span data-ttu-id="dee76-147">如需有關自訂安全性權杖提供者的[詳細資訊，請參閱如何：建立自訂安全性權杖提供](how-to-create-a-custom-security-token-provider.md)者。</span><span class="sxs-lookup"><span data-stu-id="dee76-147">For more information about custom security token providers, see [How to: Create a Custom Security Token Provider](how-to-create-a-custom-security-token-provider.md).</span></span>

3. <span data-ttu-id="dee76-148">選擇性。</span><span class="sxs-lookup"><span data-stu-id="dee76-148">Optional.</span></span> <span data-ttu-id="dee76-149">如果必須建立自訂 <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%28System.IdentityModel.Selectors.SecurityTokenRequirement%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%40%29> 實作，請覆寫 <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> 方法。</span><span class="sxs-lookup"><span data-stu-id="dee76-149">Override the <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%28System.IdentityModel.Selectors.SecurityTokenRequirement%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%40%29> method if a custom <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> implementation must be created.</span></span> <span data-ttu-id="dee76-150">如需有關自訂安全性權杖驗證器的詳細[資訊，請參閱如何：建立自訂安全性權杖驗證](how-to-create-a-custom-security-token-authenticator.md)器。</span><span class="sxs-lookup"><span data-stu-id="dee76-150">For more information about custom security token authenticators, see [How to: Create a Custom Security Token Authenticator](how-to-create-a-custom-security-token-authenticator.md).</span></span>

4. <span data-ttu-id="dee76-151">選擇性。</span><span class="sxs-lookup"><span data-stu-id="dee76-151">Optional.</span></span> <span data-ttu-id="dee76-152">如果必須建立自訂 <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%2A>，請覆寫 <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> 方法。</span><span class="sxs-lookup"><span data-stu-id="dee76-152">Override the <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%2A> method if a custom <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> must be created.</span></span> <span data-ttu-id="dee76-153">如需有關自訂安全性權杖和自訂安全性權杖序列化程式[的詳細資訊，請參閱如何：建立自訂權杖](how-to-create-a-custom-token.md)。</span><span class="sxs-lookup"><span data-stu-id="dee76-153">For more information about custom security tokens and custom security token serializers, see [How to: Create a Custom Token](how-to-create-a-custom-token.md).</span></span>

    [!code-csharp[c_CustomCredentials#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#2)]
    [!code-vb[c_CustomCredentials#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#2)]

#### <a name="to-use-a-custom-client-credentials-from-application-code"></a><span data-ttu-id="dee76-154">使用來自應用程式碼的自訂用戶端認證</span><span class="sxs-lookup"><span data-stu-id="dee76-154">To use a custom client credentials from application code</span></span>

1. <span data-ttu-id="dee76-155">建立所產生之用戶端的執行個體以代表服務介面，或建立 <xref:System.ServiceModel.ChannelFactory> 的執行個體指向想要通訊的服務。</span><span class="sxs-lookup"><span data-stu-id="dee76-155">Either create an instance of the generated client that represents the service interface, or create an instance of the <xref:System.ServiceModel.ChannelFactory> pointing to a service you want to communicate with.</span></span>

2. <span data-ttu-id="dee76-156">從 <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> 集合中移除系統提供的用戶端認證行為，您可以透過 <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> 屬性存取這個集合。</span><span class="sxs-lookup"><span data-stu-id="dee76-156">Remove the system-provided client credentials behavior from the <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> collection, which can be accessed through the <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> property.</span></span>

3. <span data-ttu-id="dee76-157">建立自訂用戶端認證類別的新執行個體，並將其新增至 <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> 集合中，您可以透過 <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> 屬性存取這個集合。</span><span class="sxs-lookup"><span data-stu-id="dee76-157">Create a new instance of a custom client credentials class and add it to the <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> collection, which can be accessed through the <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> property.</span></span>

    [!code-csharp[c_CustomCredentials#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#3)]
    [!code-vb[c_CustomCredentials#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#3)]

<span data-ttu-id="dee76-158">前面的程序示範如何從應用程式程式碼使用用戶端認證。</span><span class="sxs-lookup"><span data-stu-id="dee76-158">The previous procedure shows how to use client credentials from application code.</span></span> <span data-ttu-id="dee76-159">WCF 認證也可以使用應用程式佈建檔來設定。</span><span class="sxs-lookup"><span data-stu-id="dee76-159">WCF credentials can also be configured using the application configuration file.</span></span> <span data-ttu-id="dee76-160">在硬式編碼方面通常偏好使用應用程式組態，因為能夠在不修改原始程式碼、重新編譯和重新部署的情況下修改應用程式參數。</span><span class="sxs-lookup"><span data-stu-id="dee76-160">Using application configuration is often preferable to hard-coding because it enables modification of application parameters without having to modify the source, recompiling, and redeployment.</span></span>

<span data-ttu-id="dee76-161">下一個程序描述如何提供自訂認證組態的支援。</span><span class="sxs-lookup"><span data-stu-id="dee76-161">The next procedure describes how to provide support for configuration of custom credentials.</span></span>

#### <a name="creating-a-configuration-handler-for-custom-client-credentials"></a><span data-ttu-id="dee76-162">建立自訂用戶端認證的組態處理常式</span><span class="sxs-lookup"><span data-stu-id="dee76-162">Creating a configuration handler for custom client credentials</span></span>

1. <span data-ttu-id="dee76-163">定義衍生自 <xref:System.ServiceModel.Configuration.ClientCredentialsElement> 的新類別。</span><span class="sxs-lookup"><span data-stu-id="dee76-163">Define a new class derived from <xref:System.ServiceModel.Configuration.ClientCredentialsElement>.</span></span>

2. <span data-ttu-id="dee76-164">選擇性。</span><span class="sxs-lookup"><span data-stu-id="dee76-164">Optional.</span></span> <span data-ttu-id="dee76-165">針對想要透過應用程式組態公開的所有其他組態參數新增屬性。</span><span class="sxs-lookup"><span data-stu-id="dee76-165">Add properties for all additional configuration parameters that you want to expose through application configuration.</span></span> <span data-ttu-id="dee76-166">下列範例會新增一個名為 `CreditCardNumber` 的屬性。</span><span class="sxs-lookup"><span data-stu-id="dee76-166">The example below adds one property named `CreditCardNumber`.</span></span>

3. <span data-ttu-id="dee76-167">覆寫 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.BehaviorType%2A> 屬性以傳回使用組態項目建立之自訂用戶端認證類別的型別。</span><span class="sxs-lookup"><span data-stu-id="dee76-167">Override the <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.BehaviorType%2A> property to return the type of the custom client credentials class created with the configuration element.</span></span>

4. <span data-ttu-id="dee76-168">覆寫 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.CreateBehavior%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="dee76-168">Override the <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.CreateBehavior%2A> method.</span></span> <span data-ttu-id="dee76-169">這個方法會根據從組態檔載入的設定，負責建立和傳回自訂認證類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="dee76-169">The method is responsible for creating and returning an instance of the custom credential class based on the settings loaded from the configuration file.</span></span> <span data-ttu-id="dee76-170">請呼叫這個方法的基底 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ApplyConfiguration%28System.ServiceModel.Description.ClientCredentials%29> 方法，擷取已載入自訂用戶端認證執行個體之系統提供的認證設定。</span><span class="sxs-lookup"><span data-stu-id="dee76-170">Call the base <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ApplyConfiguration%28System.ServiceModel.Description.ClientCredentials%29> method from this method to retrieve the system-provided credentials settings loaded into your custom client credentials instance.</span></span>

5. <span data-ttu-id="dee76-171">選擇性。</span><span class="sxs-lookup"><span data-stu-id="dee76-171">Optional.</span></span> <span data-ttu-id="dee76-172">如果您在步驟 2 新增其他屬性，就需要覆寫 <xref:System.Configuration.ConfigurationElement.Properties%2A> 屬性以登錄組態架構的其他組態設定，才能加以辨認。</span><span class="sxs-lookup"><span data-stu-id="dee76-172">If you added additional properties in step 2, you need to override the <xref:System.Configuration.ConfigurationElement.Properties%2A> property in order to register your additional configuration settings for the configuration framework to recognize them.</span></span> <span data-ttu-id="dee76-173">結合屬性與基底類別屬性，以便透過這個自訂用戶端認證組態項目設定系統提供的設定。</span><span class="sxs-lookup"><span data-stu-id="dee76-173">Combine your properties with the base class properties to allow the system-provided settings to be configured through this custom client credentials configuration element.</span></span>

    [!code-csharp[c_CustomCredentials#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#7)]
    [!code-vb[c_CustomCredentials#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#7)]

<span data-ttu-id="dee76-174">一旦有了設定處理常式類別，它就可以整合到 WCF 設定架構中。</span><span class="sxs-lookup"><span data-stu-id="dee76-174">Once you have the configuration handler class, it can be integrated into the WCF configuration framework.</span></span> <span data-ttu-id="dee76-175">就能夠在用戶端端點行為項目中使用自訂用戶端認證，如同下一個程序中所示。</span><span class="sxs-lookup"><span data-stu-id="dee76-175">That enables the custom client credentials to be used in the client endpoint behavior elements, as shown in the next procedure.</span></span>

#### <a name="to-register-and-use-a-custom-client-credentials-configuration-handler-in-the-application-configuration"></a><span data-ttu-id="dee76-176">在應用程式組態中登錄和使用自訂用戶端認證組態處理常式</span><span class="sxs-lookup"><span data-stu-id="dee76-176">To register and use a custom client credentials configuration handler in the application configuration</span></span>

1. <span data-ttu-id="dee76-177">將 <`extensions`> 元素和 <`behaviorExtensions`> 專案新增至設定檔。</span><span class="sxs-lookup"><span data-stu-id="dee76-177">Add an <`extensions`> element and a <`behaviorExtensions`> element to the configuration file.</span></span>

2. <span data-ttu-id="dee76-178">將 <`add`> 元素新增至 <`behaviorExtensions`的`name` > 專案，並將屬性設定為適當的值。</span><span class="sxs-lookup"><span data-stu-id="dee76-178">Add an <`add`> element to the <`behaviorExtensions`> element and set the `name` attribute to an appropriate value.</span></span>

3. <span data-ttu-id="dee76-179">將 `type` 屬性設定為完整型別名稱。</span><span class="sxs-lookup"><span data-stu-id="dee76-179">Set the `type` attribute to the fully-qualified type name.</span></span> <span data-ttu-id="dee76-180">同時包含組件名稱和其他組件屬性。</span><span class="sxs-lookup"><span data-stu-id="dee76-180">Also include the assembly name and other assembly attributes.</span></span>

    ```xml
    <system.serviceModel>
      <extensions>
        <behaviorExtensions>
          <add name="myClientCredentials" type="Microsoft.ServiceModel.Samples.MyClientCredentialsConfigHandler, CustomCredentials, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
        </behaviorExtensions>
      </extensions>
    <system.serviceModel>
    ```

4. <span data-ttu-id="dee76-181">在註冊您的設定處理常式之後，您可以在相同的設定檔中使用自訂認證元素，而不`clientCredentials`是系統提供的 < > 元素。</span><span class="sxs-lookup"><span data-stu-id="dee76-181">After registering your configuration handler, the custom credentials element can be used inside the same configuration file instead of the system-provided <`clientCredentials`> element.</span></span> <span data-ttu-id="dee76-182">您可以同時使用系統提供的屬性，以及新增至組態處理常式實作的任何新屬性。</span><span class="sxs-lookup"><span data-stu-id="dee76-182">You can use both the system-provided properties and any new properties that you have added to your configuration handler implementation.</span></span> <span data-ttu-id="dee76-183">下列程式碼範例會使用 `creditCardNumber` 屬性 (Attribute) 設定自訂屬性 (Property) 的值。</span><span class="sxs-lookup"><span data-stu-id="dee76-183">The following example sets the value of a custom property using the `creditCardNumber` attribute.</span></span>

    ```xml
    <behaviors>
      <endpointBehaviors>
        <behavior name="myClientCredentialsBehavior">
          <myClientCredentials creditCardNumber="123-123-123"/>
        </behavior>
      </endpointBehaviors>
    </behaviors>
    ```

#### <a name="to-implement-custom-service-credentials"></a><span data-ttu-id="dee76-184">實作自訂服務認證</span><span class="sxs-lookup"><span data-stu-id="dee76-184">To implement custom service credentials</span></span>

1. <span data-ttu-id="dee76-185">定義衍生自 <xref:System.ServiceModel.Description.ServiceCredentials> 的新類別。</span><span class="sxs-lookup"><span data-stu-id="dee76-185">Define a new class derived from <xref:System.ServiceModel.Description.ServiceCredentials>.</span></span>

2. <span data-ttu-id="dee76-186">選擇性。</span><span class="sxs-lookup"><span data-stu-id="dee76-186">Optional.</span></span> <span data-ttu-id="dee76-187">新增新的屬性以提供已新增之新認證值的 API。</span><span class="sxs-lookup"><span data-stu-id="dee76-187">Add new properties to provide APIs for new credential values that are being added.</span></span> <span data-ttu-id="dee76-188">如果您不需要新增新的認證值，請略過這個步驟。</span><span class="sxs-lookup"><span data-stu-id="dee76-188">If you do not add new credential values, skip this step.</span></span> <span data-ttu-id="dee76-189">下列程式碼範例會新增 `AdditionalCertificate` 屬性。</span><span class="sxs-lookup"><span data-stu-id="dee76-189">The following example adds an `AdditionalCertificate` property.</span></span>

3. <span data-ttu-id="dee76-190">覆寫 <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="dee76-190">Override the <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> method.</span></span> <span data-ttu-id="dee76-191">當使用自訂用戶端認證時，WCF 基礎結構會自動呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="dee76-191">This method is automatically called by the WCF infrastructure when the custom client credential is used.</span></span> <span data-ttu-id="dee76-192">這個方法是負責建立和傳回 <xref:System.IdentityModel.Selectors.SecurityTokenManager> 類別實作的執行個體 (在下一個程序中會描述)。</span><span class="sxs-lookup"><span data-stu-id="dee76-192">The method is responsible for creating and returning an instance of an implementation of the <xref:System.IdentityModel.Selectors.SecurityTokenManager> class (described in the next procedure).</span></span>

4. <span data-ttu-id="dee76-193">選擇性。</span><span class="sxs-lookup"><span data-stu-id="dee76-193">Optional.</span></span> <span data-ttu-id="dee76-194">覆寫 <xref:System.ServiceModel.Description.ServiceCredentials.CloneCore%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="dee76-194">Override the <xref:System.ServiceModel.Description.ServiceCredentials.CloneCore%2A> method.</span></span> <span data-ttu-id="dee76-195">只有在將新屬性或內部欄位新增至自訂用戶端認證實作時才會需要這麼做。</span><span class="sxs-lookup"><span data-stu-id="dee76-195">This is required only if adding new properties or internal fields to the custom client credentials implementation.</span></span>

    [!code-csharp[c_CustomCredentials#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#4)]
    [!code-vb[c_CustomCredentials#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#4)]

#### <a name="to-implement-a-custom-service-security-token-manager"></a><span data-ttu-id="dee76-196">實作自訂服務安全性權杖管理員</span><span class="sxs-lookup"><span data-stu-id="dee76-196">To implement a custom service security token manager</span></span>

1. <span data-ttu-id="dee76-197">定義衍生自 <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> 類別的新類別。</span><span class="sxs-lookup"><span data-stu-id="dee76-197">Define a new class derived from the <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> class.</span></span>

2. <span data-ttu-id="dee76-198">選擇性。</span><span class="sxs-lookup"><span data-stu-id="dee76-198">Optional.</span></span> <span data-ttu-id="dee76-199">如果必須建立自訂 <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%2A> 實作，請覆寫 <xref:System.IdentityModel.Selectors.SecurityTokenProvider> 方法。</span><span class="sxs-lookup"><span data-stu-id="dee76-199">Override the <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%2A> method if a custom <xref:System.IdentityModel.Selectors.SecurityTokenProvider> implementation must be created.</span></span> <span data-ttu-id="dee76-200">如需有關自訂安全性權杖提供者的[詳細資訊，請參閱如何：建立自訂安全性權杖提供](how-to-create-a-custom-security-token-provider.md)者。</span><span class="sxs-lookup"><span data-stu-id="dee76-200">For more information about custom security token providers, see [How to: Create a Custom Security Token Provider](how-to-create-a-custom-security-token-provider.md).</span></span>

3. <span data-ttu-id="dee76-201">選擇性。</span><span class="sxs-lookup"><span data-stu-id="dee76-201">Optional.</span></span> <span data-ttu-id="dee76-202">如果必須建立自訂 <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> 實作，請覆寫 <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> 方法。</span><span class="sxs-lookup"><span data-stu-id="dee76-202">Override the <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> method if a custom <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> implementation must be created.</span></span> <span data-ttu-id="dee76-203">如需有關自訂安全性權杖驗證器的詳細[資訊，請參閱如何：建立自訂安全性權杖驗證](how-to-create-a-custom-security-token-authenticator.md)器主題。</span><span class="sxs-lookup"><span data-stu-id="dee76-203">For more information about custom security token authenticators, see [How to: Create a Custom Security Token Authenticator](how-to-create-a-custom-security-token-authenticator.md) topic.</span></span>

4. <span data-ttu-id="dee76-204">選擇性。</span><span class="sxs-lookup"><span data-stu-id="dee76-204">Optional.</span></span> <span data-ttu-id="dee76-205">如果必須建立自訂 <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%28System.IdentityModel.Selectors.SecurityTokenVersion%29>，請覆寫 <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> 方法。</span><span class="sxs-lookup"><span data-stu-id="dee76-205">Override the <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%28System.IdentityModel.Selectors.SecurityTokenVersion%29> method if a custom <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> must be created.</span></span> <span data-ttu-id="dee76-206">如需有關自訂安全性權杖和自訂安全性權杖序列化程式[的詳細資訊，請參閱如何：建立自訂權杖](how-to-create-a-custom-token.md)。</span><span class="sxs-lookup"><span data-stu-id="dee76-206">For more information about custom security tokens and custom security token serializers, see [How to: Create a Custom Token](how-to-create-a-custom-token.md).</span></span>

    [!code-csharp[c_CustomCredentials#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#5)]
    [!code-vb[c_CustomCredentials#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#5)]

#### <a name="to-use-custom-service-credentials-from-application-code"></a><span data-ttu-id="dee76-207">使用來自應用程式碼的自訂服務認證</span><span class="sxs-lookup"><span data-stu-id="dee76-207">To use custom service credentials from application code</span></span>

1. <span data-ttu-id="dee76-208">建立 <xref:System.ServiceModel.ServiceHost>的執行個體。</span><span class="sxs-lookup"><span data-stu-id="dee76-208">Create an instance of the <xref:System.ServiceModel.ServiceHost>.</span></span>

2. <span data-ttu-id="dee76-209">從 <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> 集合移除系統提供的服務認證行為。</span><span class="sxs-lookup"><span data-stu-id="dee76-209">Remove the system-provided service credentials behavior from the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection.</span></span>

3. <span data-ttu-id="dee76-210">建立自訂服務認證類別的新執行個體，並將其新增至 <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> 集合。</span><span class="sxs-lookup"><span data-stu-id="dee76-210">Create a new instance of the custom service credentials class and add it to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection.</span></span>

    [!code-csharp[c_CustomCredentials#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#6)]
    [!code-vb[c_CustomCredentials#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#6)]

<span data-ttu-id="dee76-211">使用上列程序「`To create a configuration handler for custom client credentials`」和「`To register and use a custom client credentials configuration handler in the application configuration`」中描述的步驟加入對組態的支援。唯一的差別是使用 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement> 類別而不是 <xref:System.ServiceModel.Configuration.ClientCredentialsElement> 類別，當做組態處理常式的基底類別。</span><span class="sxs-lookup"><span data-stu-id="dee76-211">Add support for configuration using the steps described previously in the procedures "`To create a configuration handler for custom client credentials`" and "`To register and use a custom client credentials configuration handler in the application configuration`." The only difference is to use the <xref:System.ServiceModel.Configuration.ServiceCredentialsElement> class instead of the <xref:System.ServiceModel.Configuration.ClientCredentialsElement> class as a base class for the configuration handler.</span></span> <span data-ttu-id="dee76-212">然後可以在使用系統提供 `<serviceCredentials>` 項目的地方使用自訂服務認證項目。</span><span class="sxs-lookup"><span data-stu-id="dee76-212">The custom service credential element can then be used wherever the system-provided `<serviceCredentials>` element is used.</span></span>

## <a name="see-also"></a><span data-ttu-id="dee76-213">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dee76-213">See also</span></span>

- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.Security.SecurityCredentialsManager>
- <xref:System.IdentityModel.Selectors.SecurityTokenManager>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- [<span data-ttu-id="dee76-214">如何：建立自訂安全性權杖提供者</span><span class="sxs-lookup"><span data-stu-id="dee76-214">How to: Create a Custom Security Token Provider</span></span>](how-to-create-a-custom-security-token-provider.md)
- [<span data-ttu-id="dee76-215">如何：建立自訂安全性權杖驗證器</span><span class="sxs-lookup"><span data-stu-id="dee76-215">How to: Create a Custom Security Token Authenticator</span></span>](how-to-create-a-custom-security-token-authenticator.md)
- [<span data-ttu-id="dee76-216">如何：建立自訂權杖</span><span class="sxs-lookup"><span data-stu-id="dee76-216">How to: Create a Custom Token</span></span>](how-to-create-a-custom-token.md)
