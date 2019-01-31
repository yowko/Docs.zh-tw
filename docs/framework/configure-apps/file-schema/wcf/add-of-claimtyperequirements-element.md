---
title: <add> 項目的 <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: 6971837ef2e68de54179daaf225394b9de769987
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55275583"
---
# <a name="add-of-claimtyperequirements-element"></a><span data-ttu-id="e7839-102">\<新增 > 的\<claimTypeRequirements > 項目</span><span class="sxs-lookup"><span data-stu-id="e7839-102">\<add> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="e7839-103">指定必須在聯合認證中出現的必要及選擇性宣告型別。</span><span class="sxs-lookup"><span data-stu-id="e7839-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="e7839-104">例如，服務說明傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="e7839-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
 <span data-ttu-id="e7839-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e7839-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="e7839-106">\<bindings></span><span class="sxs-lookup"><span data-stu-id="e7839-106">\<bindings></span></span>  
<span data-ttu-id="e7839-107">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="e7839-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="e7839-108">\<binding></span><span class="sxs-lookup"><span data-stu-id="e7839-108">\<binding></span></span>  
<span data-ttu-id="e7839-109">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="e7839-109">\<security></span></span>  
<span data-ttu-id="e7839-110">\<message></span><span class="sxs-lookup"><span data-stu-id="e7839-110">\<message></span></span>  
<span data-ttu-id="e7839-111">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="e7839-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7839-112">語法</span><span class="sxs-lookup"><span data-stu-id="e7839-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7839-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e7839-113">Attributes and Elements</span></span>  
 <span data-ttu-id="e7839-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e7839-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7839-115">屬性</span><span class="sxs-lookup"><span data-stu-id="e7839-115">Attributes</span></span>  
  
|<span data-ttu-id="e7839-116">屬性</span><span class="sxs-lookup"><span data-stu-id="e7839-116">Attribute</span></span>|<span data-ttu-id="e7839-117">描述</span><span class="sxs-lookup"><span data-stu-id="e7839-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e7839-118">claimType</span><span class="sxs-lookup"><span data-stu-id="e7839-118">claimType</span></span>|<span data-ttu-id="e7839-119">定義宣告型別的 URI。</span><span class="sxs-lookup"><span data-stu-id="e7839-119">A URI that defines the type of a claim.</span></span> <span data-ttu-id="e7839-120">例如，要在網站上購物，使用者必須提供具有足夠信用額度的有效信用卡。</span><span class="sxs-lookup"><span data-stu-id="e7839-120">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="e7839-121">宣告型別是信用卡的 URI。</span><span class="sxs-lookup"><span data-stu-id="e7839-121">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="e7839-122">isOptional</span><span class="sxs-lookup"><span data-stu-id="e7839-122">isOptional</span></span>|<span data-ttu-id="e7839-123">布林值，指定此宣告是否為選擇性宣告。</span><span class="sxs-lookup"><span data-stu-id="e7839-123">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="e7839-124">若此為必要宣告，請將此屬性設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="e7839-124">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="e7839-125">若服務要求某些資訊，但並非必要，便可使用此屬性。</span><span class="sxs-lookup"><span data-stu-id="e7839-125">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="e7839-126">例如，若您要求使用者輸入姓氏、名字和地址，但決定電話號碼為選擇性。</span><span class="sxs-lookup"><span data-stu-id="e7839-126">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e7839-127">子元素</span><span class="sxs-lookup"><span data-stu-id="e7839-127">Child Elements</span></span>  
 <span data-ttu-id="e7839-128">無。</span><span class="sxs-lookup"><span data-stu-id="e7839-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e7839-129">父項目</span><span class="sxs-lookup"><span data-stu-id="e7839-129">Parent Elements</span></span>  
  
|<span data-ttu-id="e7839-130">項目</span><span class="sxs-lookup"><span data-stu-id="e7839-130">Element</span></span>|<span data-ttu-id="e7839-131">描述</span><span class="sxs-lookup"><span data-stu-id="e7839-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e7839-132">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="e7839-132">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="e7839-133">指定必要宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="e7839-133">Specifies a collection of required claim types.</span></span> <span data-ttu-id="e7839-134">每個項目的型別為 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="e7839-134">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="e7839-135">在聯合案例中，服務會聲明對傳入認證的需求。</span><span class="sxs-lookup"><span data-stu-id="e7839-135">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="e7839-136">例如，傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="e7839-136">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="e7839-137">這個集合中的每一個項目都會指定要顯示在聯合認證中的必要和選擇性宣告型別。</span><span class="sxs-lookup"><span data-stu-id="e7839-137">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7839-138">備註</span><span class="sxs-lookup"><span data-stu-id="e7839-138">Remarks</span></span>  
 <span data-ttu-id="e7839-139">在聯合案例中，服務會聲明對傳入認證的需求。</span><span class="sxs-lookup"><span data-stu-id="e7839-139">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="e7839-140">例如，傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="e7839-140">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="e7839-141">這項需求會顯示在安全性原則中。</span><span class="sxs-lookup"><span data-stu-id="e7839-141">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="e7839-142">當用戶端從聯合服務 (例如 CardSpace) 要求認證，它會將需求放入權杖要求 (RequestSecurityToken)，那麼聯合服務便可發出認證，滿足相應的需求。</span><span class="sxs-lookup"><span data-stu-id="e7839-142">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7839-143">範例</span><span class="sxs-lookup"><span data-stu-id="e7839-143">Example</span></span>  
 <span data-ttu-id="e7839-144">下列組態會將兩項宣告型別需求新增至安全性繫結程序。</span><span class="sxs-lookup"><span data-stu-id="e7839-144">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e7839-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7839-145">See also</span></span>
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
