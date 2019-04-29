---
title: HOW TO：建立自訂安全性權杖提供者
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], providing credentials
ms.assetid: db8cb478-aa43-478b-bf97-c6489ad7c7fd
ms.openlocfilehash: 1677d44faf6901eb1eda93a9374636b7caa558a0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61767191"
---
# <a name="how-to-create-a-custom-security-token-provider"></a><span data-ttu-id="e560a-102">HOW TO：建立自訂安全性權杖提供者</span><span class="sxs-lookup"><span data-stu-id="e560a-102">How to: Create a Custom Security Token Provider</span></span>
<span data-ttu-id="e560a-103">這個主題會說明如何以自訂安全性權杖提供者建立新的權杖型別，以及如何整合提供者和自訂安全性權杖管理員。</span><span class="sxs-lookup"><span data-stu-id="e560a-103">This topic shows how to create new token types with a custom security token provider and how to integrate the provider with a custom security token manager.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e560a-104">如果在 <xref:System.IdentityModel.Tokens> 命名空間中，所找到的系統提供之權杖不符合您的需求，請建立自訂權杖提供者。</span><span class="sxs-lookup"><span data-stu-id="e560a-104">Create a custom token provider if the system-provided tokens found in the <xref:System.IdentityModel.Tokens> namespace do not match your requirements.</span></span>  
  
 <span data-ttu-id="e560a-105">安全性權杖提供者會根據用戶端或服務認證中的資訊，建立安全性權杖表示。</span><span class="sxs-lookup"><span data-stu-id="e560a-105">The security token provider creates a security token representation based on information in the client or service credentials.</span></span> <span data-ttu-id="e560a-106">若要使用 Windows Communication Foundation (WCF) 安全性的自訂安全性權杖提供者，您必須建立自訂認證和安全性權杖管理員實作。</span><span class="sxs-lookup"><span data-stu-id="e560a-106">To use the custom security token provider in Windows Communication Foundation (WCF) security, you must create custom credentials and security token manager implementations.</span></span>  
  
 <span data-ttu-id="e560a-107">如需自訂認證和安全性權杖管理員的詳細資訊，請參閱[逐步解說：建立自訂用戶端和服務認證](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)。</span><span class="sxs-lookup"><span data-stu-id="e560a-107">For more information about custom credentials and security token manager see the [Walkthrough: Creating Custom Client and Service Credentials](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).</span></span>  
  
### <a name="to-create-a-custom-security-token-provider"></a><span data-ttu-id="e560a-108">建立自訂安全性權杖提供者</span><span class="sxs-lookup"><span data-stu-id="e560a-108">To create a custom security token provider</span></span>  
  
1. <span data-ttu-id="e560a-109">定義衍生自 <xref:System.IdentityModel.Selectors.SecurityTokenProvider> 類別的新類別。</span><span class="sxs-lookup"><span data-stu-id="e560a-109">Define a new class derived from the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class.</span></span>  
  
2. <span data-ttu-id="e560a-110">實作 <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> 方法。</span><span class="sxs-lookup"><span data-stu-id="e560a-110">Implement the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> method.</span></span> <span data-ttu-id="e560a-111">這個方法會負責建立和傳回安全性權杖的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e560a-111">The method is responsible for creating and returning an instance of the security token.</span></span> <span data-ttu-id="e560a-112">下列範例會建立名稱為 `MySecurityTokenProvider` 的類別，並覆寫 <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> 方法以傳回 <xref:System.IdentityModel.Tokens.X509SecurityToken> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e560a-112">The following example creates a class named `MySecurityTokenProvider`, and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> method to return an instance of the <xref:System.IdentityModel.Tokens.X509SecurityToken> class.</span></span> <span data-ttu-id="e560a-113">類別建構函式需要 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e560a-113">The class constructor requires an instance of the <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> class.</span></span>  
  
     [!code-csharp[c_CustomTokenProvider#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#1)]
     [!code-vb[c_CustomTokenProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#1)]  
  
### <a name="to-integrate-a-custom-security-token-provider-with-a-custom-security-token-manager"></a><span data-ttu-id="e560a-114">整合自訂安全性權杖提供者和自訂安全性權杖管理員</span><span class="sxs-lookup"><span data-stu-id="e560a-114">To integrate a custom security token provider with a custom security token manager</span></span>  
  
1. <span data-ttu-id="e560a-115">定義衍生自 <xref:System.IdentityModel.Selectors.SecurityTokenManager> 類別的新類別。</span><span class="sxs-lookup"><span data-stu-id="e560a-115">Define a new class derived from the <xref:System.IdentityModel.Selectors.SecurityTokenManager> class.</span></span> <span data-ttu-id="e560a-116">(以下範例衍生自 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> 類別，而這個類別則衍生自 <xref:System.IdentityModel.Selectors.SecurityTokenManager> 類別)。</span><span class="sxs-lookup"><span data-stu-id="e560a-116">(The example below derives from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class, which derives from the <xref:System.IdentityModel.Selectors.SecurityTokenManager> class.)</span></span>  
  
2. <span data-ttu-id="e560a-117">如果尚未覆寫 <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> 方法，請覆寫之。</span><span class="sxs-lookup"><span data-stu-id="e560a-117">Override the <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> method if is not already overridden.</span></span>  
  
     <span data-ttu-id="e560a-118"><xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29>方法會負責傳回的執行個體<xref:System.IdentityModel.Selectors.SecurityTokenProvider>適用於類別<xref:System.IdentityModel.Selectors.SecurityTokenRequirement>參數傳遞給方法的 WCF 安全性架構。</span><span class="sxs-lookup"><span data-stu-id="e560a-118">The <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> method is responsible for returning an instance of the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class appropriate to the <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parameter passed to the method by the WCF security framework.</span></span> <span data-ttu-id="e560a-119">使用適當的安全性權杖參數呼叫方法時，請修改方法以傳回自訂安全性權杖提供者實作 (在之前的程序中建立此實作)。</span><span class="sxs-lookup"><span data-stu-id="e560a-119">Modify the method to return the custom security token provider implementation (created in the previous procedure) when the method is called with an appropriate security token parameter.</span></span> <span data-ttu-id="e560a-120">如需有關安全性權杖管理員的詳細資訊，請參閱[逐步解說：建立自訂用戶端和服務認證](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)。</span><span class="sxs-lookup"><span data-stu-id="e560a-120">For more information about the security token manager, see the [Walkthrough: Creating Custom Client and Service Credentials](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).</span></span>  
  
3. <span data-ttu-id="e560a-121">將自訂邏輯新增至方法，讓方法可以根據 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> 參數傳回自訂安全性權杖提供者。</span><span class="sxs-lookup"><span data-stu-id="e560a-121">Add custom logic to the method to enable it to return your custom security token provider based on the <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parameter.</span></span> <span data-ttu-id="e560a-122">下列範例會在符合權杖需求時，傳回自訂安全性權杖提供者。</span><span class="sxs-lookup"><span data-stu-id="e560a-122">The following sample returns the custom security token provider if the token requirements are met.</span></span> <span data-ttu-id="e560a-123">這些需求包括 X.509 安全性權杖和訊息方向 (當權杖用於訊息輸出時)。</span><span class="sxs-lookup"><span data-stu-id="e560a-123">The requirements include an X.509 security token and the message direction (that the token is used for message output).</span></span> <span data-ttu-id="e560a-124">在其他情況下，程式碼會呼叫基底類別，以針對其他安全性權杖需求維護系統提供的行為。</span><span class="sxs-lookup"><span data-stu-id="e560a-124">For all other cases, the code calls the base class to maintain the system-provided behavior for other security token requirements.</span></span>  
  
 [!code-csharp[c_CustomTokenProvider#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#2)]
 [!code-vb[c_CustomTokenProvider#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="e560a-125">範例</span><span class="sxs-lookup"><span data-stu-id="e560a-125">Example</span></span>  
 <span data-ttu-id="e560a-126">下列範例會顯示完整 <xref:System.IdentityModel.Selectors.SecurityTokenProvider> 實作以及相對應的 <xref:System.IdentityModel.Selectors.SecurityTokenManager> 實作。</span><span class="sxs-lookup"><span data-stu-id="e560a-126">The following shows a complete <xref:System.IdentityModel.Selectors.SecurityTokenProvider> implementation along with a corresponding <xref:System.IdentityModel.Selectors.SecurityTokenManager> implementation.</span></span>  
  
 [!code-csharp[c_CustomTokenProvider#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#0)]
 [!code-vb[c_CustomTokenProvider#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="e560a-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e560a-127">See also</span></span>

- <xref:System.IdentityModel.Selectors.SecurityTokenProvider>
- <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>
- <xref:System.IdentityModel.Selectors.SecurityTokenManager>
- <xref:System.IdentityModel.Tokens.X509SecurityToken>
- [<span data-ttu-id="e560a-128">逐步解說：建立自訂用戶端和服務認證</span><span class="sxs-lookup"><span data-stu-id="e560a-128">Walkthrough: Creating Custom Client and Service Credentials</span></span>](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)
- [<span data-ttu-id="e560a-129">如何：建立自訂安全性權杖驗證器</span><span class="sxs-lookup"><span data-stu-id="e560a-129">How to: Create a Custom Security Token Authenticator</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)
