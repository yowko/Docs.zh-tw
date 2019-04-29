---
title: <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: 6bdf56e3d2084dec8d44e1c4d3f0c1e50b711b92
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758233"
---
# <a name="issuedtokenparameters"></a><span data-ttu-id="5f3c2-101">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="5f3c2-101">\<issuedTokenParameters></span></span>
<span data-ttu-id="5f3c2-102">指定在聯合安全性案例中發行之安全性權杖的參數。</span><span class="sxs-lookup"><span data-stu-id="5f3c2-102">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
 <span data-ttu-id="5f3c2-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5f3c2-103">\<system.serviceModel></span></span>  
<span data-ttu-id="5f3c2-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="5f3c2-104">\<bindings></span></span>  
<span data-ttu-id="5f3c2-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="5f3c2-105">\<customBinding></span></span>  
<span data-ttu-id="5f3c2-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="5f3c2-106">\<binding></span></span>  
<span data-ttu-id="5f3c2-107">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="5f3c2-107">\<security></span></span>  
<span data-ttu-id="5f3c2-108">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="5f3c2-108">\<issuedTokenParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f3c2-109">語法</span><span class="sxs-lookup"><span data-stu-id="5f3c2-109">Syntax</span></span>  
  
```xml  
<issuedTokenParameters defaultMessageSecurityVersion="System.ServiceModel.MessageSecurityVersion"
                       inclusionMode="AlwaysToInitiator/AlwaysToRecipient/Never/Once"
                       keySize="Integer"
                       keyType="AsymmetricKey/BearerKey/SymmetricKey"
                       tokenType="String">
  <additionalRequestParameters />
  <claimTypeRequirements>
    <add claimType="URI"
         isOptional="Boolean" />
  </claimTypeRequirements>
  <issuer address="String"
          binding="" />
  <issuerMetadata address="String" />
</issuedTokenParameters>
```  
  
## <a name="type"></a><span data-ttu-id="5f3c2-110">類型</span><span class="sxs-lookup"><span data-stu-id="5f3c2-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f3c2-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5f3c2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5f3c2-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5f3c2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f3c2-113">屬性</span><span class="sxs-lookup"><span data-stu-id="5f3c2-113">Attributes</span></span>  
  
|<span data-ttu-id="5f3c2-114">屬性</span><span class="sxs-lookup"><span data-stu-id="5f3c2-114">Attribute</span></span>|<span data-ttu-id="5f3c2-115">描述</span><span class="sxs-lookup"><span data-stu-id="5f3c2-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5f3c2-116">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="5f3c2-116">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="5f3c2-117">指定繫結必須支援的安全性規格版本 (WS-Security、WS-Trust、WS-Secure Conversation 和 WS-Security Policy)。</span><span class="sxs-lookup"><span data-stu-id="5f3c2-117">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="5f3c2-118">這個值的型別為 <xref:System.ServiceModel.MessageSecurityVersion>。</span><span class="sxs-lookup"><span data-stu-id="5f3c2-118">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="5f3c2-119">inclusionMode</span><span class="sxs-lookup"><span data-stu-id="5f3c2-119">inclusionMode</span></span>|<span data-ttu-id="5f3c2-120">指定權杖內含需求。</span><span class="sxs-lookup"><span data-stu-id="5f3c2-120">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="5f3c2-121">此屬性的型別為 <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>。</span><span class="sxs-lookup"><span data-stu-id="5f3c2-121">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="5f3c2-122">keySize</span><span class="sxs-lookup"><span data-stu-id="5f3c2-122">keySize</span></span>|<span data-ttu-id="5f3c2-123">指定權杖金鑰大小的整數。</span><span class="sxs-lookup"><span data-stu-id="5f3c2-123">An integer that specifies the token key size.</span></span> <span data-ttu-id="5f3c2-124">預設值為 256。</span><span class="sxs-lookup"><span data-stu-id="5f3c2-124">The default value is 256.</span></span>|  
|<span data-ttu-id="5f3c2-125">keyType</span><span class="sxs-lookup"><span data-stu-id="5f3c2-125">keyType</span></span>|<span data-ttu-id="5f3c2-126">指定金鑰型別之 <xref:System.IdentityModel.Tokens.SecurityKeyType> 的有效值。</span><span class="sxs-lookup"><span data-stu-id="5f3c2-126">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="5f3c2-127">預設為 `SymmetricKey`。</span><span class="sxs-lookup"><span data-stu-id="5f3c2-127">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="5f3c2-128">tokenType</span><span class="sxs-lookup"><span data-stu-id="5f3c2-128">tokenType</span></span>|<span data-ttu-id="5f3c2-129">指定權杖型別的字串。</span><span class="sxs-lookup"><span data-stu-id="5f3c2-129">A string that specifies the token type.</span></span> <span data-ttu-id="5f3c2-130">預設值為「 http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML」。</span><span class="sxs-lookup"><span data-stu-id="5f3c2-130">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5f3c2-131">子元素</span><span class="sxs-lookup"><span data-stu-id="5f3c2-131">Child Elements</span></span>  
  
|<span data-ttu-id="5f3c2-132">項目</span><span class="sxs-lookup"><span data-stu-id="5f3c2-132">Element</span></span>|<span data-ttu-id="5f3c2-133">描述</span><span class="sxs-lookup"><span data-stu-id="5f3c2-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5f3c2-134">\<additionalRequestParameters></span><span class="sxs-lookup"><span data-stu-id="5f3c2-134">\<additionalRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/additionalrequestparameters-element.md)|<span data-ttu-id="5f3c2-135">指定額外要求參數的組態項目集合。</span><span class="sxs-lookup"><span data-stu-id="5f3c2-135">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[<span data-ttu-id="5f3c2-136">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="5f3c2-136">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="5f3c2-137">指定必要宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="5f3c2-137">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="5f3c2-138">在聯合案例中，服務會聲明對傳入認證的需求。</span><span class="sxs-lookup"><span data-stu-id="5f3c2-138">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="5f3c2-139">例如，傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="5f3c2-139">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="5f3c2-140">這個集合中的每一個項目都會指定要顯示在聯合認證中的必要和選擇性宣告型別。</span><span class="sxs-lookup"><span data-stu-id="5f3c2-140">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[<span data-ttu-id="5f3c2-141">\<issuer></span><span class="sxs-lookup"><span data-stu-id="5f3c2-141">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer-of-issuedtokenparameters.md)|<span data-ttu-id="5f3c2-142">指定發行目前權杖之端點的組態項目。</span><span class="sxs-lookup"><span data-stu-id="5f3c2-142">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[<span data-ttu-id="5f3c2-143">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="5f3c2-143">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="5f3c2-144">指定權杖簽發者中繼資料之端點位址的組態項目。</span><span class="sxs-lookup"><span data-stu-id="5f3c2-144">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5f3c2-145">父項目</span><span class="sxs-lookup"><span data-stu-id="5f3c2-145">Parent Elements</span></span>  
  
|<span data-ttu-id="5f3c2-146">項目</span><span class="sxs-lookup"><span data-stu-id="5f3c2-146">Element</span></span>|<span data-ttu-id="5f3c2-147">描述</span><span class="sxs-lookup"><span data-stu-id="5f3c2-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5f3c2-148">\<secureConversationBootstrap></span><span class="sxs-lookup"><span data-stu-id="5f3c2-148">\<secureConversationBootstrap></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|<span data-ttu-id="5f3c2-149">指定用於啟始安全對話服務的預設值。</span><span class="sxs-lookup"><span data-stu-id="5f3c2-149">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[<span data-ttu-id="5f3c2-150">\<security></span><span class="sxs-lookup"><span data-stu-id="5f3c2-150">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="5f3c2-151">指定自訂繫結的安全性選項。</span><span class="sxs-lookup"><span data-stu-id="5f3c2-151">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5f3c2-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f3c2-152">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="5f3c2-153">繫結</span><span class="sxs-lookup"><span data-stu-id="5f3c2-153">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="5f3c2-154">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="5f3c2-154">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="5f3c2-155">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="5f3c2-155">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="5f3c2-156">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="5f3c2-156">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="5f3c2-157">如何：建立自訂繫結使用 SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="5f3c2-157">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="5f3c2-158">自訂繫結安全性</span><span class="sxs-lookup"><span data-stu-id="5f3c2-158">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
- [<span data-ttu-id="5f3c2-159">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="5f3c2-159">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="5f3c2-160">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="5f3c2-160">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="5f3c2-161">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="5f3c2-161">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="5f3c2-162">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="5f3c2-162">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
