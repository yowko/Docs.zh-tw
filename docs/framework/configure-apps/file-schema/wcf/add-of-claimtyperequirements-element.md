---
title: <add> 項目的 <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: f6948052c62684faa734b592f5bdfc2e7827a07a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153096"
---
# <a name="add-of-claimtyperequirements-element"></a><span data-ttu-id="b5abb-102">\<添加\<>索賠類型需求>元素</span><span class="sxs-lookup"><span data-stu-id="b5abb-102">\<add> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="b5abb-103">指定必須在聯合認證中出現的必要及選擇性宣告型別。</span><span class="sxs-lookup"><span data-stu-id="b5abb-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="b5abb-104">例如，服務說明傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="b5abb-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
<span data-ttu-id="b5abb-105">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b5abb-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b5abb-106">&nbsp;&nbsp;[**\<系統.服務模式>**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b5abb-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b5abb-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<綁定>**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="b5abb-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="b5abb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws 聯邦HTTP綁定>**](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="b5abb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="b5abb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<綁定>**</span><span class="sxs-lookup"><span data-stu-id="b5abb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="b5abb-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<安全>**](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="b5abb-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="b5abb-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<消息>**](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="b5abb-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="b5abb-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<索賠類型要求>**](claimtyperequirements-for-message.md)</span><span class="sxs-lookup"><span data-stu-id="b5abb-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)</span></span>\
<span data-ttu-id="b5abb-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<添加>**</span><span class="sxs-lookup"><span data-stu-id="b5abb-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="b5abb-114">語法</span><span class="sxs-lookup"><span data-stu-id="b5abb-114">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5abb-115">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b5abb-115">Attributes and Elements</span></span>  
 <span data-ttu-id="b5abb-116">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b5abb-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5abb-117">屬性</span><span class="sxs-lookup"><span data-stu-id="b5abb-117">Attributes</span></span>  
  
|<span data-ttu-id="b5abb-118">屬性</span><span class="sxs-lookup"><span data-stu-id="b5abb-118">Attribute</span></span>|<span data-ttu-id="b5abb-119">描述</span><span class="sxs-lookup"><span data-stu-id="b5abb-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b5abb-120">claimType</span><span class="sxs-lookup"><span data-stu-id="b5abb-120">claimType</span></span>|<span data-ttu-id="b5abb-121">定義宣告型別的 URI。</span><span class="sxs-lookup"><span data-stu-id="b5abb-121">A URI that defines the type of a claim.</span></span> <span data-ttu-id="b5abb-122">例如，要在網站上購物，使用者必須提供具有足夠信用額度的有效信用卡。</span><span class="sxs-lookup"><span data-stu-id="b5abb-122">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="b5abb-123">宣告型別是信用卡的 URI。</span><span class="sxs-lookup"><span data-stu-id="b5abb-123">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="b5abb-124">isOptional</span><span class="sxs-lookup"><span data-stu-id="b5abb-124">isOptional</span></span>|<span data-ttu-id="b5abb-125">布林值，指定此宣告是否為選擇性宣告。</span><span class="sxs-lookup"><span data-stu-id="b5abb-125">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="b5abb-126">若此為必要宣告，請將此屬性設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="b5abb-126">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="b5abb-127">若服務要求某些資訊，但並非必要，便可使用此屬性。</span><span class="sxs-lookup"><span data-stu-id="b5abb-127">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="b5abb-128">例如，如果要求使用者輸入其名字、姓氏和位址，但確定該電話號碼是可選的。</span><span class="sxs-lookup"><span data-stu-id="b5abb-128">For example, if you require the user to enter their first name, last name, and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b5abb-129">子元素</span><span class="sxs-lookup"><span data-stu-id="b5abb-129">Child Elements</span></span>  
 <span data-ttu-id="b5abb-130">無。</span><span class="sxs-lookup"><span data-stu-id="b5abb-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b5abb-131">父項目</span><span class="sxs-lookup"><span data-stu-id="b5abb-131">Parent Elements</span></span>  
  
|<span data-ttu-id="b5abb-132">元素</span><span class="sxs-lookup"><span data-stu-id="b5abb-132">Element</span></span>|<span data-ttu-id="b5abb-133">描述</span><span class="sxs-lookup"><span data-stu-id="b5abb-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b5abb-134">\<索賠類型要求></span><span class="sxs-lookup"><span data-stu-id="b5abb-134">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="b5abb-135">指定必要宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="b5abb-135">Specifies a collection of required claim types.</span></span> <span data-ttu-id="b5abb-136">每個項目的型別為 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="b5abb-136">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="b5abb-137">在聯合案例中，服務會聲明對傳入認證的需求。</span><span class="sxs-lookup"><span data-stu-id="b5abb-137">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="b5abb-138">例如，傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="b5abb-138">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="b5abb-139">這個集合中的每一個項目都會指定要顯示在聯合認證中的必要和選擇性宣告型別。</span><span class="sxs-lookup"><span data-stu-id="b5abb-139">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5abb-140">備註</span><span class="sxs-lookup"><span data-stu-id="b5abb-140">Remarks</span></span>  
 <span data-ttu-id="b5abb-141">在聯合案例中，服務會聲明對傳入認證的需求。</span><span class="sxs-lookup"><span data-stu-id="b5abb-141">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="b5abb-142">例如，傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="b5abb-142">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="b5abb-143">這項需求會顯示在安全性原則中。</span><span class="sxs-lookup"><span data-stu-id="b5abb-143">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="b5abb-144">當用戶端從聯合服務 (例如 CardSpace) 要求認證，它會將需求放入權杖要求 (RequestSecurityToken)，那麼聯合服務便可發出認證，滿足相應的需求。</span><span class="sxs-lookup"><span data-stu-id="b5abb-144">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5abb-145">範例</span><span class="sxs-lookup"><span data-stu-id="b5abb-145">Example</span></span>  
 <span data-ttu-id="b5abb-146">下列組態會將兩項宣告型別需求新增至安全性繫結程序。</span><span class="sxs-lookup"><span data-stu-id="b5abb-146">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b5abb-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5abb-147">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
