---
title: '&lt;claimTypeRequirements&gt; 的 &lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: b4f9275fdc36ea3c7ba79c6609f039c3b1f4c3ed
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750592"
---
# <a name="ltaddgt-of-ltclaimtyperequirementsgt"></a><span data-ttu-id="b7f94-102">&lt;claimTypeRequirements&gt; 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="b7f94-102">&lt;add&gt; of &lt;claimTypeRequirements&gt;</span></span>
<span data-ttu-id="b7f94-103">指定必須在聯合認證中出現的必要及選擇性宣告型別。</span><span class="sxs-lookup"><span data-stu-id="b7f94-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="b7f94-104">例如，服務說明傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="b7f94-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
 <span data-ttu-id="b7f94-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b7f94-105">\<system.serviceModel></span></span>  
<span data-ttu-id="b7f94-106">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="b7f94-106">\<bindings></span></span>  
<span data-ttu-id="b7f94-107">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="b7f94-107">\<customBinding></span></span>  
<span data-ttu-id="b7f94-108">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="b7f94-108">\<binding></span></span>  
<span data-ttu-id="b7f94-109">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="b7f94-109">\<security></span></span>  
<span data-ttu-id="b7f94-110">\<></span><span class="sxs-lookup"><span data-stu-id="b7f94-110">\<issuedTokenParameters></span></span>  
<span data-ttu-id="b7f94-111">\<q ></span><span class="sxs-lookup"><span data-stu-id="b7f94-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7f94-112">語法</span><span class="sxs-lookup"><span data-stu-id="b7f94-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>  
      <add claimType="URI"  
           isOptional="Boolean" />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7f94-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b7f94-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b7f94-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="b7f94-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7f94-115">屬性</span><span class="sxs-lookup"><span data-stu-id="b7f94-115">Attributes</span></span>  
  
|<span data-ttu-id="b7f94-116">屬性</span><span class="sxs-lookup"><span data-stu-id="b7f94-116">Attribute</span></span>|<span data-ttu-id="b7f94-117">描述</span><span class="sxs-lookup"><span data-stu-id="b7f94-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b7f94-118">claimType</span><span class="sxs-lookup"><span data-stu-id="b7f94-118">claimType</span></span>|<span data-ttu-id="b7f94-119">定義宣告型別的 URI。</span><span class="sxs-lookup"><span data-stu-id="b7f94-119">A URI that defines the type of a claim.</span></span> <span data-ttu-id="b7f94-120">例如，要在網站上購物，使用者必須提供具有足夠信用額度的有效信用卡。</span><span class="sxs-lookup"><span data-stu-id="b7f94-120">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="b7f94-121">宣告型別是信用卡的 URI。</span><span class="sxs-lookup"><span data-stu-id="b7f94-121">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="b7f94-122">isOptional</span><span class="sxs-lookup"><span data-stu-id="b7f94-122">isOptional</span></span>|<span data-ttu-id="b7f94-123">布林值，指定此宣告是否為選擇性宣告。</span><span class="sxs-lookup"><span data-stu-id="b7f94-123">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="b7f94-124">若此為必要宣告，請將此屬性設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="b7f94-124">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="b7f94-125">若服務要求某些資訊，但並非必要，便可使用此屬性。</span><span class="sxs-lookup"><span data-stu-id="b7f94-125">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="b7f94-126">例如，若您要求使用者輸入姓氏、名字和地址，但決定電話號碼為選擇性。</span><span class="sxs-lookup"><span data-stu-id="b7f94-126">For example, if you require the user to enter his/her first name, last name and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b7f94-127">子項目</span><span class="sxs-lookup"><span data-stu-id="b7f94-127">Child Elements</span></span>  
 <span data-ttu-id="b7f94-128">無。</span><span class="sxs-lookup"><span data-stu-id="b7f94-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b7f94-129">父項目</span><span class="sxs-lookup"><span data-stu-id="b7f94-129">Parent Elements</span></span>  
  
|<span data-ttu-id="b7f94-130">項目</span><span class="sxs-lookup"><span data-stu-id="b7f94-130">Element</span></span>|<span data-ttu-id="b7f94-131">描述</span><span class="sxs-lookup"><span data-stu-id="b7f94-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7f94-132">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="b7f94-132">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="b7f94-133">指定必要宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="b7f94-133">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="b7f94-134">在聯合案例中，服務會聲明對傳入認證的需求。</span><span class="sxs-lookup"><span data-stu-id="b7f94-134">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="b7f94-135">例如，傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="b7f94-135">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="b7f94-136">這個集合中的每一個項目都會指定要顯示在聯合認證中的必要和選擇性宣告型別。</span><span class="sxs-lookup"><span data-stu-id="b7f94-136">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7f94-137">備註</span><span class="sxs-lookup"><span data-stu-id="b7f94-137">Remarks</span></span>  
 <span data-ttu-id="b7f94-138">在聯合案例中，服務會聲明對傳入認證的需求。</span><span class="sxs-lookup"><span data-stu-id="b7f94-138">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="b7f94-139">例如，傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="b7f94-139">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="b7f94-140">這項需求會顯示在安全性原則中。</span><span class="sxs-lookup"><span data-stu-id="b7f94-140">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="b7f94-141">當用戶端從聯合服務 (例如 CardSpace) 要求認證，它會將需求放入權杖要求 (RequestSecurityToken)，那麼聯合服務便可發出認證，滿足相應的需求。</span><span class="sxs-lookup"><span data-stu-id="b7f94-141">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7f94-142">範例</span><span class="sxs-lookup"><span data-stu-id="b7f94-142">Example</span></span>  
 <span data-ttu-id="b7f94-143">下列組態會將兩項宣告型別需求新增至安全性繫結程序。</span><span class="sxs-lookup"><span data-stu-id="b7f94-143">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
```xml  
<bindings>  
    <wsFederationHttpBinding>  
      <binding name="myFederatedBinding">  
        <security mode="Message">  
          <message issuedTokenType="urn:oasis:names:tc:SAML:1.0:assertion">  
            <claimTypeRequirements>  
              <add claimType=  
"http://schemas.microsoft.com/ws/2005/05/identity/claims/EmailAddress"/>  
              <add claimType=  
"http://schemas.microsoft.com/ws/2005/05/identity/claims/UserName"    
optional="true" />  
            </claims>  
          </message>  
        </security>  
      </binding>  
    </wsFederationHttpBinding>  
</bindings>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b7f94-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7f94-144">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="b7f94-145">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="b7f94-145">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)  
 [<span data-ttu-id="b7f94-146">繫結</span><span class="sxs-lookup"><span data-stu-id="b7f94-146">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="b7f94-147">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="b7f94-147">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="b7f94-148">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="b7f94-148">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="b7f94-149">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="b7f94-149">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="b7f94-150">如何：使用 SecurityBindingElement 建立自訂繫結</span><span class="sxs-lookup"><span data-stu-id="b7f94-150">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="b7f94-151">自訂繫結安全性</span><span class="sxs-lookup"><span data-stu-id="b7f94-151">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
