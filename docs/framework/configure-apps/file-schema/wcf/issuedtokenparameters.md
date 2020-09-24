---
title: <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: c90024a0629f39d160967ca00434e48f682d8933
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157313"
---
# \<issuedTokenParameters>

<span data-ttu-id="b1ab3-101">指定在聯合安全性案例中發行之安全性權杖的參數。</span><span class="sxs-lookup"><span data-stu-id="b1ab3-101">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedTokenParameters>**  
  
## <a name="syntax"></a><span data-ttu-id="b1ab3-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="b1ab3-102">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="b1ab3-103">類型</span><span class="sxs-lookup"><span data-stu-id="b1ab3-103">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1ab3-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b1ab3-104">Attributes and Elements</span></span>  

 <span data-ttu-id="b1ab3-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b1ab3-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1ab3-106">屬性</span><span class="sxs-lookup"><span data-stu-id="b1ab3-106">Attributes</span></span>  
  
|<span data-ttu-id="b1ab3-107">屬性</span><span class="sxs-lookup"><span data-stu-id="b1ab3-107">Attribute</span></span>|<span data-ttu-id="b1ab3-108">描述</span><span class="sxs-lookup"><span data-stu-id="b1ab3-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b1ab3-109">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="b1ab3-109">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="b1ab3-110">指定繫結必須支援的安全性規格版本 (WS-Security、WS-Trust、WS-Secure Conversation 和 WS-Security Policy)。</span><span class="sxs-lookup"><span data-stu-id="b1ab3-110">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="b1ab3-111">這個值的型別為 <xref:System.ServiceModel.MessageSecurityVersion>。</span><span class="sxs-lookup"><span data-stu-id="b1ab3-111">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="b1ab3-112">inclusionMode</span><span class="sxs-lookup"><span data-stu-id="b1ab3-112">inclusionMode</span></span>|<span data-ttu-id="b1ab3-113">指定權杖內含需求。</span><span class="sxs-lookup"><span data-stu-id="b1ab3-113">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="b1ab3-114">此屬性的型別為 <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>。</span><span class="sxs-lookup"><span data-stu-id="b1ab3-114">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="b1ab3-115">keySize</span><span class="sxs-lookup"><span data-stu-id="b1ab3-115">keySize</span></span>|<span data-ttu-id="b1ab3-116">指定權杖金鑰大小的整數。</span><span class="sxs-lookup"><span data-stu-id="b1ab3-116">An integer that specifies the token key size.</span></span> <span data-ttu-id="b1ab3-117">預設值為 256。</span><span class="sxs-lookup"><span data-stu-id="b1ab3-117">The default value is 256.</span></span>|  
|<span data-ttu-id="b1ab3-118">keyType</span><span class="sxs-lookup"><span data-stu-id="b1ab3-118">keyType</span></span>|<span data-ttu-id="b1ab3-119">指定金鑰型別之 <xref:System.IdentityModel.Tokens.SecurityKeyType> 的有效值。</span><span class="sxs-lookup"><span data-stu-id="b1ab3-119">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="b1ab3-120">預設值為 `SymmetricKey`。</span><span class="sxs-lookup"><span data-stu-id="b1ab3-120">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="b1ab3-121">tokenType</span><span class="sxs-lookup"><span data-stu-id="b1ab3-121">tokenType</span></span>|<span data-ttu-id="b1ab3-122">指定權杖型別的字串。</span><span class="sxs-lookup"><span data-stu-id="b1ab3-122">A string that specifies the token type.</span></span> <span data-ttu-id="b1ab3-123">預設值為「http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML」。</span><span class="sxs-lookup"><span data-stu-id="b1ab3-123">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1ab3-124">子元素</span><span class="sxs-lookup"><span data-stu-id="b1ab3-124">Child Elements</span></span>  
  
|<span data-ttu-id="b1ab3-125">項目</span><span class="sxs-lookup"><span data-stu-id="b1ab3-125">Element</span></span>|<span data-ttu-id="b1ab3-126">描述</span><span class="sxs-lookup"><span data-stu-id="b1ab3-126">Description</span></span>|  
|-------------|-----------------|  
|[\<additionalRequestParameters>](additionalrequestparameters-element.md)|<span data-ttu-id="b1ab3-127">指定額外要求參數的組態項目集合。</span><span class="sxs-lookup"><span data-stu-id="b1ab3-127">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="b1ab3-128">指定必要宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="b1ab3-128">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="b1ab3-129">在聯合案例中，服務會聲明對傳入認證的需求。</span><span class="sxs-lookup"><span data-stu-id="b1ab3-129">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="b1ab3-130">例如，傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="b1ab3-130">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="b1ab3-131">這個集合中的每一個項目都會指定要顯示在聯合認證中的必要和選擇性宣告型別。</span><span class="sxs-lookup"><span data-stu-id="b1ab3-131">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[\<issuer>](issuer-of-issuedtokenparameters.md)|<span data-ttu-id="b1ab3-132">指定發行目前權杖之端點的組態項目。</span><span class="sxs-lookup"><span data-stu-id="b1ab3-132">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[\<issuerMetadata>](issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="b1ab3-133">指定權杖簽發者中繼資料之端點位址的組態項目。</span><span class="sxs-lookup"><span data-stu-id="b1ab3-133">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b1ab3-134">父項目</span><span class="sxs-lookup"><span data-stu-id="b1ab3-134">Parent Elements</span></span>  
  
|<span data-ttu-id="b1ab3-135">項目</span><span class="sxs-lookup"><span data-stu-id="b1ab3-135">Element</span></span>|<span data-ttu-id="b1ab3-136">描述</span><span class="sxs-lookup"><span data-stu-id="b1ab3-136">Description</span></span>|  
|-------------|-----------------|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|<span data-ttu-id="b1ab3-137">指定用於啟始安全對話服務的預設值。</span><span class="sxs-lookup"><span data-stu-id="b1ab3-137">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[\<security>](security-of-custombinding.md)|<span data-ttu-id="b1ab3-138">指定自訂繫結的安全性選項。</span><span class="sxs-lookup"><span data-stu-id="b1ab3-138">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b1ab3-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1ab3-139">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="b1ab3-140">繫結</span><span class="sxs-lookup"><span data-stu-id="b1ab3-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b1ab3-141">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="b1ab3-141">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b1ab3-142">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="b1ab3-142">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="b1ab3-143">作法：使用 SecurityBindingElement 建立自訂繫結</span><span class="sxs-lookup"><span data-stu-id="b1ab3-143">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="b1ab3-144">自訂繫結安全性</span><span class="sxs-lookup"><span data-stu-id="b1ab3-144">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
- [<span data-ttu-id="b1ab3-145">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="b1ab3-145">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="b1ab3-146">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="b1ab3-146">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="b1ab3-147">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="b1ab3-147">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="b1ab3-148">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="b1ab3-148">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
