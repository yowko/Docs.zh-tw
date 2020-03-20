---
title: <add> 的 <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: 6ba935f7f6dae0e4d9e6581f53a50c684efcbed3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153083"
---
# <a name="add-of-claimtyperequirements"></a><span data-ttu-id="976d4-102">\<添加\<索賠類型需求>></span><span class="sxs-lookup"><span data-stu-id="976d4-102">\<add> of \<claimTypeRequirements></span></span>
<span data-ttu-id="976d4-103">指定必須在聯合認證中出現的必要及選擇性宣告型別。</span><span class="sxs-lookup"><span data-stu-id="976d4-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="976d4-104">例如，服務說明傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="976d4-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
<span data-ttu-id="976d4-105">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="976d4-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="976d4-106">&nbsp;&nbsp;[**\<系統.服務模式>**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="976d4-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="976d4-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<綁定>**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="976d4-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="976d4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<自訂綁定>**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="976d4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="976d4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<綁定>**</span><span class="sxs-lookup"><span data-stu-id="976d4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="976d4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<安全>**](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="976d4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="976d4-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<已發出權杖參數>**](issuedtokenparameters.md)</span><span class="sxs-lookup"><span data-stu-id="976d4-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)</span></span>\
<span data-ttu-id="976d4-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<索賠類型要求>**](claimtyperequirements-element.md)</span><span class="sxs-lookup"><span data-stu-id="976d4-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-element.md)</span></span>\
<span data-ttu-id="976d4-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<添加>**</span><span class="sxs-lookup"><span data-stu-id="976d4-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="976d4-114">語法</span><span class="sxs-lookup"><span data-stu-id="976d4-114">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="976d4-115">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="976d4-115">Attributes and Elements</span></span>  
 <span data-ttu-id="976d4-116">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="976d4-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="976d4-117">屬性</span><span class="sxs-lookup"><span data-stu-id="976d4-117">Attributes</span></span>  
  
|<span data-ttu-id="976d4-118">屬性</span><span class="sxs-lookup"><span data-stu-id="976d4-118">Attribute</span></span>|<span data-ttu-id="976d4-119">描述</span><span class="sxs-lookup"><span data-stu-id="976d4-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="976d4-120">claimType</span><span class="sxs-lookup"><span data-stu-id="976d4-120">claimType</span></span>|<span data-ttu-id="976d4-121">定義宣告型別的 URI。</span><span class="sxs-lookup"><span data-stu-id="976d4-121">A URI that defines the type of a claim.</span></span> <span data-ttu-id="976d4-122">例如，要在網站上購物，使用者必須提供具有足夠信用額度的有效信用卡。</span><span class="sxs-lookup"><span data-stu-id="976d4-122">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="976d4-123">宣告型別是信用卡的 URI。</span><span class="sxs-lookup"><span data-stu-id="976d4-123">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="976d4-124">isOptional</span><span class="sxs-lookup"><span data-stu-id="976d4-124">isOptional</span></span>|<span data-ttu-id="976d4-125">布林值，指定此宣告是否為選擇性宣告。</span><span class="sxs-lookup"><span data-stu-id="976d4-125">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="976d4-126">若此為必要宣告，請將此屬性設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="976d4-126">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="976d4-127">若服務要求某些資訊，但並非必要，便可使用此屬性。</span><span class="sxs-lookup"><span data-stu-id="976d4-127">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="976d4-128">例如，如果要求使用者輸入其名字、姓氏和位址，但確定該電話號碼是可選的。</span><span class="sxs-lookup"><span data-stu-id="976d4-128">For example, if you require the user to enter their first name, last name, and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="976d4-129">子元素</span><span class="sxs-lookup"><span data-stu-id="976d4-129">Child Elements</span></span>  
 <span data-ttu-id="976d4-130">無。</span><span class="sxs-lookup"><span data-stu-id="976d4-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="976d4-131">父項目</span><span class="sxs-lookup"><span data-stu-id="976d4-131">Parent Elements</span></span>  
  
|<span data-ttu-id="976d4-132">元素</span><span class="sxs-lookup"><span data-stu-id="976d4-132">Element</span></span>|<span data-ttu-id="976d4-133">描述</span><span class="sxs-lookup"><span data-stu-id="976d4-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="976d4-134">\<索賠類型要求></span><span class="sxs-lookup"><span data-stu-id="976d4-134">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="976d4-135">指定必要宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="976d4-135">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="976d4-136">在聯合案例中，服務會聲明對傳入認證的需求。</span><span class="sxs-lookup"><span data-stu-id="976d4-136">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="976d4-137">例如，傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="976d4-137">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="976d4-138">這個集合中的每一個項目都會指定要顯示在聯合認證中的必要和選擇性宣告型別。</span><span class="sxs-lookup"><span data-stu-id="976d4-138">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="976d4-139">備註</span><span class="sxs-lookup"><span data-stu-id="976d4-139">Remarks</span></span>  
 <span data-ttu-id="976d4-140">在聯合案例中，服務會聲明對傳入認證的需求。</span><span class="sxs-lookup"><span data-stu-id="976d4-140">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="976d4-141">例如，傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="976d4-141">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="976d4-142">這項需求會顯示在安全性原則中。</span><span class="sxs-lookup"><span data-stu-id="976d4-142">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="976d4-143">當用戶端從聯合服務 (例如 CardSpace) 要求認證，它會將需求放入權杖要求 (RequestSecurityToken)，那麼聯合服務便可發出認證，滿足相應的需求。</span><span class="sxs-lookup"><span data-stu-id="976d4-143">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="976d4-144">範例</span><span class="sxs-lookup"><span data-stu-id="976d4-144">Example</span></span>  
 <span data-ttu-id="976d4-145">下列組態會將兩項宣告型別需求新增至安全性繫結程序。</span><span class="sxs-lookup"><span data-stu-id="976d4-145">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="myFederatedBinding">
      <security mode="Message">
        <message issuedTokenType="urn:oasis:names:tc:SAML:1.0:assertion">
          <claimTypeRequirements>
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/EmailAddress" />
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/UserName"
                 optional="true" />
          </claimTypeRequirements>
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>
```  
  
## <a name="see-also"></a><span data-ttu-id="976d4-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="976d4-146">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="976d4-147">\<索賠類型要求></span><span class="sxs-lookup"><span data-stu-id="976d4-147">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)
- [<span data-ttu-id="976d4-148">綁定</span><span class="sxs-lookup"><span data-stu-id="976d4-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="976d4-149">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="976d4-149">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="976d4-150">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="976d4-150">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="976d4-151">\<自訂綁定></span><span class="sxs-lookup"><span data-stu-id="976d4-151">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="976d4-152">HOW TO：使用 SecurityBindingElement 建立自訂繫結</span><span class="sxs-lookup"><span data-stu-id="976d4-152">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="976d4-153">自訂繫結安全性</span><span class="sxs-lookup"><span data-stu-id="976d4-153">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
