---
title: <add> 項目的 <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: 9c56cccd7a6f72a701e4b8652afecc2361e6218a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400680"
---
# <a name="add-of-claimtyperequirements-element"></a><span data-ttu-id="3eabf-102">\<新增 claimTypeRequirements > \<元素的 ></span><span class="sxs-lookup"><span data-stu-id="3eabf-102">\<add> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="3eabf-103">指定必須在聯合認證中出現的必要及選擇性宣告型別。</span><span class="sxs-lookup"><span data-stu-id="3eabf-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="3eabf-104">例如，服務說明傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="3eabf-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
<span data-ttu-id="3eabf-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3eabf-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3eabf-106">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="3eabf-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="3eabf-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="3eabf-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="3eabf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="3eabf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="3eabf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="3eabf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="3eabf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<安全性 >** ](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="3eabf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="3eabf-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<訊息 >** ](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="3eabf-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="3eabf-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<claimTypeRequirements >** ](claimtyperequirements-for-message.md)</span><span class="sxs-lookup"><span data-stu-id="3eabf-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)</span></span>\
<span data-ttu-id="3eabf-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<新增 >**</span><span class="sxs-lookup"><span data-stu-id="3eabf-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="3eabf-114">語法</span><span class="sxs-lookup"><span data-stu-id="3eabf-114">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3eabf-115">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3eabf-115">Attributes and Elements</span></span>  
 <span data-ttu-id="3eabf-116">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3eabf-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3eabf-117">屬性</span><span class="sxs-lookup"><span data-stu-id="3eabf-117">Attributes</span></span>  
  
|<span data-ttu-id="3eabf-118">屬性</span><span class="sxs-lookup"><span data-stu-id="3eabf-118">Attribute</span></span>|<span data-ttu-id="3eabf-119">描述</span><span class="sxs-lookup"><span data-stu-id="3eabf-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3eabf-120">claimType</span><span class="sxs-lookup"><span data-stu-id="3eabf-120">claimType</span></span>|<span data-ttu-id="3eabf-121">定義宣告型別的 URI。</span><span class="sxs-lookup"><span data-stu-id="3eabf-121">A URI that defines the type of a claim.</span></span> <span data-ttu-id="3eabf-122">例如，要在網站上購物，使用者必須提供具有足夠信用額度的有效信用卡。</span><span class="sxs-lookup"><span data-stu-id="3eabf-122">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="3eabf-123">宣告型別是信用卡的 URI。</span><span class="sxs-lookup"><span data-stu-id="3eabf-123">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="3eabf-124">isOptional</span><span class="sxs-lookup"><span data-stu-id="3eabf-124">isOptional</span></span>|<span data-ttu-id="3eabf-125">布林值，指定此宣告是否為選擇性宣告。</span><span class="sxs-lookup"><span data-stu-id="3eabf-125">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="3eabf-126">若此為必要宣告，請將此屬性設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="3eabf-126">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="3eabf-127">若服務要求某些資訊，但並非必要，便可使用此屬性。</span><span class="sxs-lookup"><span data-stu-id="3eabf-127">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="3eabf-128">例如，若您要求使用者輸入姓氏、名字和地址，但決定電話號碼為選擇性。</span><span class="sxs-lookup"><span data-stu-id="3eabf-128">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3eabf-129">子元素</span><span class="sxs-lookup"><span data-stu-id="3eabf-129">Child Elements</span></span>  
 <span data-ttu-id="3eabf-130">無。</span><span class="sxs-lookup"><span data-stu-id="3eabf-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3eabf-131">父項目</span><span class="sxs-lookup"><span data-stu-id="3eabf-131">Parent Elements</span></span>  
  
|<span data-ttu-id="3eabf-132">項目</span><span class="sxs-lookup"><span data-stu-id="3eabf-132">Element</span></span>|<span data-ttu-id="3eabf-133">描述</span><span class="sxs-lookup"><span data-stu-id="3eabf-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3eabf-134">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="3eabf-134">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="3eabf-135">指定必要宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="3eabf-135">Specifies a collection of required claim types.</span></span> <span data-ttu-id="3eabf-136">每個項目的型別為 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="3eabf-136">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="3eabf-137">在聯合案例中，服務會聲明對傳入認證的需求。</span><span class="sxs-lookup"><span data-stu-id="3eabf-137">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="3eabf-138">例如，傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="3eabf-138">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="3eabf-139">這個集合中的每一個項目都會指定要顯示在聯合認證中的必要和選擇性宣告型別。</span><span class="sxs-lookup"><span data-stu-id="3eabf-139">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3eabf-140">備註</span><span class="sxs-lookup"><span data-stu-id="3eabf-140">Remarks</span></span>  
 <span data-ttu-id="3eabf-141">在聯合案例中，服務會聲明對傳入認證的需求。</span><span class="sxs-lookup"><span data-stu-id="3eabf-141">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="3eabf-142">例如，傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="3eabf-142">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="3eabf-143">這項需求會顯示在安全性原則中。</span><span class="sxs-lookup"><span data-stu-id="3eabf-143">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="3eabf-144">當用戶端從聯合服務 (例如 CardSpace) 要求認證，它會將需求放入權杖要求 (RequestSecurityToken)，那麼聯合服務便可發出認證，滿足相應的需求。</span><span class="sxs-lookup"><span data-stu-id="3eabf-144">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3eabf-145">範例</span><span class="sxs-lookup"><span data-stu-id="3eabf-145">Example</span></span>  
 <span data-ttu-id="3eabf-146">下列組態會將兩項宣告型別需求新增至安全性繫結程序。</span><span class="sxs-lookup"><span data-stu-id="3eabf-146">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3eabf-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3eabf-147">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
