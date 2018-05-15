---
title: '&lt;r&gt;'
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: 550b3412b193b996b8de800856d6833369fc4bc7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltissuedtokenparametersgt"></a><span data-ttu-id="5f524-102">&lt;r&gt;</span><span class="sxs-lookup"><span data-stu-id="5f524-102">&lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="5f524-103">指定在聯合安全性案例中發行之安全性權杖的參數。</span><span class="sxs-lookup"><span data-stu-id="5f524-103">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
 <span data-ttu-id="5f524-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5f524-104">\<system.serviceModel></span></span>  
<span data-ttu-id="5f524-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="5f524-105">\<bindings></span></span>  
<span data-ttu-id="5f524-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="5f524-106">\<customBinding></span></span>  
<span data-ttu-id="5f524-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="5f524-107">\<binding></span></span>  
<span data-ttu-id="5f524-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="5f524-108">\<security></span></span>  
<span data-ttu-id="5f524-109">\<></span><span class="sxs-lookup"><span data-stu-id="5f524-109">\<issuedTokenParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f524-110">語法</span><span class="sxs-lookup"><span data-stu-id="5f524-110">Syntax</span></span>  
  
```xml  
<issuedTokenParameters   
      DefaultMessageSecurityVersion="System.ServiceModel.MessageSecurityVersion"  
      inclusionMode="AlwaysToInitiator/AlwaysToRecipient/Never/Once"  
      keySize="Integer"  
   keyType="AsymmetricKey/BearerKey/SymmetricKey"  
      tokenType="String" >  
   <additionalRequestParameters />  
      <claimTypeRequirements>  
            <add claimType="URI"  
           isOptional="Boolean" />  
      </claimTypeRequirements>  
      <issuer address="String"   
                      binding=" " />  
      <issuerMetadata address="String" />   
</issuedTokenParameters>  
```  
  
## <a name="type"></a><span data-ttu-id="5f524-111">類型</span><span class="sxs-lookup"><span data-stu-id="5f524-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f524-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5f524-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5f524-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5f524-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f524-114">屬性</span><span class="sxs-lookup"><span data-stu-id="5f524-114">Attributes</span></span>  
  
|<span data-ttu-id="5f524-115">屬性</span><span class="sxs-lookup"><span data-stu-id="5f524-115">Attribute</span></span>|<span data-ttu-id="5f524-116">描述</span><span class="sxs-lookup"><span data-stu-id="5f524-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5f524-117">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="5f524-117">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="5f524-118">指定繫結必須支援的安全性規格版本 (WS-Security、WS-Trust、WS-Secure Conversation 和 WS-Security Policy)。</span><span class="sxs-lookup"><span data-stu-id="5f524-118">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="5f524-119">這個值的型別為 <xref:System.ServiceModel.MessageSecurityVersion>。</span><span class="sxs-lookup"><span data-stu-id="5f524-119">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="5f524-120">inclusionMode</span><span class="sxs-lookup"><span data-stu-id="5f524-120">inclusionMode</span></span>|<span data-ttu-id="5f524-121">指定權杖內含需求。</span><span class="sxs-lookup"><span data-stu-id="5f524-121">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="5f524-122">此屬性的型別為 <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>。</span><span class="sxs-lookup"><span data-stu-id="5f524-122">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="5f524-123">keySize</span><span class="sxs-lookup"><span data-stu-id="5f524-123">keySize</span></span>|<span data-ttu-id="5f524-124">指定權杖金鑰大小的整數。</span><span class="sxs-lookup"><span data-stu-id="5f524-124">An integer that specifies the token key size.</span></span> <span data-ttu-id="5f524-125">預設值為 256。</span><span class="sxs-lookup"><span data-stu-id="5f524-125">The default value is 256.</span></span>|  
|<span data-ttu-id="5f524-126">keyType</span><span class="sxs-lookup"><span data-stu-id="5f524-126">keyType</span></span>|<span data-ttu-id="5f524-127">指定金鑰型別之 <xref:System.IdentityModel.Tokens.SecurityKeyType> 的有效值。</span><span class="sxs-lookup"><span data-stu-id="5f524-127">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="5f524-128">預設為 `SymmetricKey`。</span><span class="sxs-lookup"><span data-stu-id="5f524-128">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="5f524-129">tokenType</span><span class="sxs-lookup"><span data-stu-id="5f524-129">tokenType</span></span>|<span data-ttu-id="5f524-130">指定權杖型別的字串。</span><span class="sxs-lookup"><span data-stu-id="5f524-130">A string that specifies the token type.</span></span> <span data-ttu-id="5f524-131">預設值為「http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML」。</span><span class="sxs-lookup"><span data-stu-id="5f524-131">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5f524-132">子項目</span><span class="sxs-lookup"><span data-stu-id="5f524-132">Child Elements</span></span>  
  
|<span data-ttu-id="5f524-133">項目</span><span class="sxs-lookup"><span data-stu-id="5f524-133">Element</span></span>|<span data-ttu-id="5f524-134">描述</span><span class="sxs-lookup"><span data-stu-id="5f524-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5f524-135">\<additionalRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="5f524-135">\<additionalRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/additionalrequestparameters-element.md)|<span data-ttu-id="5f524-136">指定額外要求參數的組態項目集合。</span><span class="sxs-lookup"><span data-stu-id="5f524-136">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[<span data-ttu-id="5f524-137">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="5f524-137">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="5f524-138">指定必要宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="5f524-138">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="5f524-139">在聯合案例中，服務會聲明對傳入認證的需求。</span><span class="sxs-lookup"><span data-stu-id="5f524-139">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="5f524-140">例如，傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="5f524-140">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="5f524-141">這個集合中的每一個項目都會指定要顯示在聯合認證中的必要和選擇性宣告型別。</span><span class="sxs-lookup"><span data-stu-id="5f524-141">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[<span data-ttu-id="5f524-142">\<issuer></span><span class="sxs-lookup"><span data-stu-id="5f524-142">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer-of-issuedtokenparameters.md)|<span data-ttu-id="5f524-143">指定發行目前權杖之端點的組態項目。</span><span class="sxs-lookup"><span data-stu-id="5f524-143">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[<span data-ttu-id="5f524-144">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="5f524-144">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="5f524-145">指定權杖簽發者中繼資料之端點位址的組態項目。</span><span class="sxs-lookup"><span data-stu-id="5f524-145">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5f524-146">父項目</span><span class="sxs-lookup"><span data-stu-id="5f524-146">Parent Elements</span></span>  
  
|<span data-ttu-id="5f524-147">項目</span><span class="sxs-lookup"><span data-stu-id="5f524-147">Element</span></span>|<span data-ttu-id="5f524-148">描述</span><span class="sxs-lookup"><span data-stu-id="5f524-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5f524-149">\<secureConversationBootstrap ></span><span class="sxs-lookup"><span data-stu-id="5f524-149">\<secureConversationBootstrap></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|<span data-ttu-id="5f524-150">指定用於啟始安全對話服務的預設值。</span><span class="sxs-lookup"><span data-stu-id="5f524-150">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[<span data-ttu-id="5f524-151">\<security></span><span class="sxs-lookup"><span data-stu-id="5f524-151">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="5f524-152">指定自訂繫結的安全性選項。</span><span class="sxs-lookup"><span data-stu-id="5f524-152">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5f524-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f524-153">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="5f524-154">繫結</span><span class="sxs-lookup"><span data-stu-id="5f524-154">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="5f524-155">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="5f524-155">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="5f524-156">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="5f524-156">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="5f524-157">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="5f524-157">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="5f524-158">如何：使用 SecurityBindingElement 建立自訂繫結</span><span class="sxs-lookup"><span data-stu-id="5f524-158">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="5f524-159">自訂繫結安全性</span><span class="sxs-lookup"><span data-stu-id="5f524-159">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)  
 [<span data-ttu-id="5f524-160">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="5f524-160">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="5f524-161">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="5f524-161">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="5f524-162">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="5f524-162">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="5f524-163">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="5f524-163">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
