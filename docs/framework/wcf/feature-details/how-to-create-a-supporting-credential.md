---
title: HOW TO：建立支援的認證
ms.date: 03/30/2017
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
ms.openlocfilehash: 2f922f2df424b0ca2a468ae2f6cb8e8753e1d8a1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64635491"
---
# <a name="how-to-create-a-supporting-credential"></a><span data-ttu-id="97736-102">HOW TO：建立支援的認證</span><span class="sxs-lookup"><span data-stu-id="97736-102">How to: Create a Supporting Credential</span></span>
<span data-ttu-id="97736-103">您可能具有需要多個認證的自訂安全性配置。</span><span class="sxs-lookup"><span data-stu-id="97736-103">It is possible to have a custom security scheme that requires more than one credential.</span></span> <span data-ttu-id="97736-104">例如，服務對用戶端的要求可能不只是提供使用者名稱和密碼，可能也要提供可證明用戶端已超過 18 歲的認證。</span><span class="sxs-lookup"><span data-stu-id="97736-104">For example, a service may demand from the client not just a user name and password, but also a credential that proves the client is over the age of 18.</span></span> <span data-ttu-id="97736-105">第二個認證已*支援認證*。</span><span class="sxs-lookup"><span data-stu-id="97736-105">The second credential is a *supporting credential*.</span></span> <span data-ttu-id="97736-106">本主題說明如何在 Windows Communication Foundation (WCF) 用戶端實作這類認證。</span><span class="sxs-lookup"><span data-stu-id="97736-106">This topic explains how to implement such credentials in an Windows Communication Foundation (WCF) client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="97736-107">支援認證的規格為 WS-SecurityPolicy 規格的一部分。</span><span class="sxs-lookup"><span data-stu-id="97736-107">The specification for supporting credentials is part of the WS-SecurityPolicy specification.</span></span> <span data-ttu-id="97736-108">如需詳細資訊，請參閱 < [Web 服務安全性規格](https://go.microsoft.com/fwlink/?LinkId=88537)。</span><span class="sxs-lookup"><span data-stu-id="97736-108">For more information, see [Web Services Security Specifications](https://go.microsoft.com/fwlink/?LinkId=88537).</span></span>  
  
## <a name="supporting-tokens"></a><span data-ttu-id="97736-109">支援權杖</span><span class="sxs-lookup"><span data-stu-id="97736-109">Supporting Tokens</span></span>  
 <span data-ttu-id="97736-110">簡單地說，當使用訊息安全性時才*主要認證*一律用來保護訊息 （例如，X.509 憑證或 Kerberos 票證）。</span><span class="sxs-lookup"><span data-stu-id="97736-110">In brief, when you use message security, a *primary credential* is always used to secure the message (for example, an X.509 certificate or a Kerberos ticket).</span></span>  
  
 <span data-ttu-id="97736-111">如規格所定義，會使用安全性繫結*語彙基元*來保護訊息交換。</span><span class="sxs-lookup"><span data-stu-id="97736-111">As defined by the specification, a security binding uses *tokens* to secure the message exchange.</span></span> <span data-ttu-id="97736-112">A*語彙基元*是一種安全性認證。</span><span class="sxs-lookup"><span data-stu-id="97736-112">A *token* is a representation of a security credential.</span></span>  
  
 <span data-ttu-id="97736-113">安全性繫結會使用安全性繫結原則中識別的主要權杖來建立簽章。</span><span class="sxs-lookup"><span data-stu-id="97736-113">The security binding uses a primary token identified in the security binding policy to create a signature.</span></span> <span data-ttu-id="97736-114">此簽章指*訊息簽章*。</span><span class="sxs-lookup"><span data-stu-id="97736-114">This signature is referred to as the *message signature*.</span></span>  
  
 <span data-ttu-id="97736-115">您也可以指定其他權杖，以擴大與訊息簽章相關聯的權杖所提供的宣告。</span><span class="sxs-lookup"><span data-stu-id="97736-115">Additional tokens can be specified to augment the claims provided by the token associated with the message signature.</span></span>  
  
## <a name="endorsing-signing-and-encrypting"></a><span data-ttu-id="97736-116">簽署 (Endorsing)、簽署 (Signing) 和加密</span><span class="sxs-lookup"><span data-stu-id="97736-116">Endorsing, Signing, and Encrypting</span></span>  
 <span data-ttu-id="97736-117">支援的認證將會導致*支援權杖*訊息內進行傳輸。</span><span class="sxs-lookup"><span data-stu-id="97736-117">A supporting credential results in a *supporting token* transmitted inside the message.</span></span> <span data-ttu-id="97736-118">WS-SecurityPolicy 規格定義了四種可將支援權杖附加至訊息的方法，如下表所述。</span><span class="sxs-lookup"><span data-stu-id="97736-118">The WS-SecurityPolicy specification defines four ways to attach a supporting token to the message, as described in the following table.</span></span>  
  
|<span data-ttu-id="97736-119">用途</span><span class="sxs-lookup"><span data-stu-id="97736-119">Purpose</span></span>|<span data-ttu-id="97736-120">描述</span><span class="sxs-lookup"><span data-stu-id="97736-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="97736-121">簽署人</span><span class="sxs-lookup"><span data-stu-id="97736-121">Signed</span></span>|<span data-ttu-id="97736-122">支援權杖包含在安全性標頭中，而且是由訊息簽章進行簽署。</span><span class="sxs-lookup"><span data-stu-id="97736-122">The supporting token is included in the security header and is signed by the message signature.</span></span>|  
|<span data-ttu-id="97736-123">簽署</span><span class="sxs-lookup"><span data-stu-id="97736-123">Endorsing</span></span>|<span data-ttu-id="97736-124">*簽署 （endorsing） 權杖*簽署訊息簽章。</span><span class="sxs-lookup"><span data-stu-id="97736-124">An *endorsing token* signs the message signature.</span></span>|  
|<span data-ttu-id="97736-125">已簽署 (Signed) 和簽署 (Endorsing)</span><span class="sxs-lookup"><span data-stu-id="97736-125">Signed and Endorsing</span></span>|<span data-ttu-id="97736-126">已簽署的簽署權杖會簽署從訊息簽章產生的整個 `ds:Signature` 項目，而這些權杖本身就是由該訊息簽章所簽署；也就是說，這兩個權杖 (用於訊息簽章的權杖和已簽署的簽署權杖) 會彼此進行簽署。</span><span class="sxs-lookup"><span data-stu-id="97736-126">Signed, endorsing tokens sign the entire `ds:Signature` element produced from the message signature and are themselves signed by that message signature; that is, both tokens (the token used for the message signature and the signed endorsing token) sign each other.</span></span>|  
|<span data-ttu-id="97736-127">已簽署和加密</span><span class="sxs-lookup"><span data-stu-id="97736-127">Signed and Encrypting</span></span>|<span data-ttu-id="97736-128">已簽署的加密支援權杖是出現在 `wsse:SecurityHeader` 時，也會進行加密的已簽署支援權杖。</span><span class="sxs-lookup"><span data-stu-id="97736-128">Signed, encrypted supporting tokens are signed supporting tokens that are also encrypted when they appear in the `wsse:SecurityHeader`.</span></span>|  
  
## <a name="programming-supporting-credentials"></a><span data-ttu-id="97736-129">程式設計的支援認證</span><span class="sxs-lookup"><span data-stu-id="97736-129">Programming Supporting Credentials</span></span>  
 <span data-ttu-id="97736-130">若要建立會使用支援的權杖，您必須建立服務[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)。</span><span class="sxs-lookup"><span data-stu-id="97736-130">To create a service that uses supporting tokens you must create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span> <span data-ttu-id="97736-131">(如需詳細資訊，請參閱[How to:建立自訂繫結使用 SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)。)</span><span class="sxs-lookup"><span data-stu-id="97736-131">(For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)</span></span>  
  
 <span data-ttu-id="97736-132">建立自訂繫結的第一個步驟為建立安全性繫結項目，可以是下列三種類型的其中之一：</span><span class="sxs-lookup"><span data-stu-id="97736-132">The first step when creating a custom binding is to create a security binding element, which can be one of three types:</span></span>  
  
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="97736-133">繼承自 <xref:System.ServiceModel.Channels.SecurityBindingElement> 的所有類別，可包含四個相關的屬性：</span><span class="sxs-lookup"><span data-stu-id="97736-133">All classes inherit from the <xref:System.ServiceModel.Channels.SecurityBindingElement>, which includes four relevant properties:</span></span>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.EndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OperationSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalEndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalOperationSupportingTokenParameters%2A>  
  
#### <a name="scopes"></a><span data-ttu-id="97736-134">範圍</span><span class="sxs-lookup"><span data-stu-id="97736-134">Scopes</span></span>  
 <span data-ttu-id="97736-135">支援認證中有兩個範圍：</span><span class="sxs-lookup"><span data-stu-id="97736-135">Two scopes exist for supporting credentials:</span></span>  
  
- <span data-ttu-id="97736-136">*支援權杖的端點*支援所有作業的端點。</span><span class="sxs-lookup"><span data-stu-id="97736-136">*Endpoint supporting tokens* support all operations of an endpoint.</span></span> <span data-ttu-id="97736-137">這也就是支援權杖所表示的認證，可以在每次叫用端點作業時使用此認證。</span><span class="sxs-lookup"><span data-stu-id="97736-137">That is, the credential that the supporting token represents can be used whenever any endpoint operations are invoked.</span></span>  
  
- <span data-ttu-id="97736-138">*支援權杖的作業*支援只在特定端點的作業。</span><span class="sxs-lookup"><span data-stu-id="97736-138">*Operation supporting tokens* support only a specific endpoint operation.</span></span>  
  
 <span data-ttu-id="97736-139">如屬性名稱所指出，支援認證可以為必要項目或選用項目。</span><span class="sxs-lookup"><span data-stu-id="97736-139">As indicated by the property names, supporting credentials can be either required or optional.</span></span> <span data-ttu-id="97736-140">也就是說，如果在出現支援認證時使用該認證 (雖然不需要該認證)，在沒有出現該認證時驗證也不會失敗。</span><span class="sxs-lookup"><span data-stu-id="97736-140">That is, if the supporting credential is used if it is present, although it is not necessary, but the authentication will not fail if it is not present.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="97736-141">程序</span><span class="sxs-lookup"><span data-stu-id="97736-141">Procedures</span></span>  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a><span data-ttu-id="97736-142">建立包含支援認證的自訂繫結</span><span class="sxs-lookup"><span data-stu-id="97736-142">To create a custom binding that includes supporting credentials</span></span>  
  
1. <span data-ttu-id="97736-143">建立安全性繫結項目。</span><span class="sxs-lookup"><span data-stu-id="97736-143">Create a security binding element.</span></span> <span data-ttu-id="97736-144">底下的範例會使用 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 驗證模式建立 `UserNameForCertificate`。</span><span class="sxs-lookup"><span data-stu-id="97736-144">The example below creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> with the `UserNameForCertificate` authentication mode.</span></span> <span data-ttu-id="97736-145">請使用 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="97736-145">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> method.</span></span>  
  
2. <span data-ttu-id="97736-146">將支援參數新增至適當屬性 (`Endorsing`、`Signed`、`SignedEncrypted` 或 `SignedEndorsed`) 所傳回的類型集合。</span><span class="sxs-lookup"><span data-stu-id="97736-146">Add the supporting parameter to the collection of types returned by the appropriate property (`Endorsing`, `Signed`, `SignedEncrypted`, or `SignedEndorsed`).</span></span> <span data-ttu-id="97736-147"><xref:System.ServiceModel.Security.Tokens> 命名空間中的類型包含常用類型，例如 <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>。</span><span class="sxs-lookup"><span data-stu-id="97736-147">The types in the <xref:System.ServiceModel.Security.Tokens> namespace include commonly used types, such as the <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97736-148">範例</span><span class="sxs-lookup"><span data-stu-id="97736-148">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="97736-149">描述</span><span class="sxs-lookup"><span data-stu-id="97736-149">Description</span></span>  
 <span data-ttu-id="97736-150">下列範例會建立 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 的執行個體，並將 <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> 類別的執行個體新增至所傳回的簽署屬性集合。</span><span class="sxs-lookup"><span data-stu-id="97736-150">The following example creates an instance of the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and adds an instance of the <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> class to the collection the Endorsing property returned.</span></span>  
  
### <a name="code"></a><span data-ttu-id="97736-151">程式碼</span><span class="sxs-lookup"><span data-stu-id="97736-151">Code</span></span>  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="97736-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97736-152">See also</span></span>

- [<span data-ttu-id="97736-153">如何：建立自訂繫結使用 SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="97736-153">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
