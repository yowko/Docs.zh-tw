---
title: <add> 的 <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: c68e83c9-39e8-4264-b1ce-b6a9eb5b98aa
ms.openlocfilehash: 00699a6fa5d0de7ac554db6ef8d0bbe511a85c0a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149214"
---
# <a name="add-of-claimtyperequirements"></a><span data-ttu-id="94a4e-102">\<add> 的 \<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="94a4e-102">\<add> of \<claimTypeRequirements></span></span>

<span data-ttu-id="94a4e-103">指定必須在聯合認證中出現的必要及選擇性宣告型別。</span><span class="sxs-lookup"><span data-stu-id="94a4e-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="94a4e-104">例如，服務說明傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="94a4e-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="94a4e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="94a4e-105">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94a4e-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="94a4e-106">Attributes and Elements</span></span>  

 <span data-ttu-id="94a4e-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="94a4e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94a4e-108">屬性</span><span class="sxs-lookup"><span data-stu-id="94a4e-108">Attributes</span></span>  
  
|<span data-ttu-id="94a4e-109">屬性</span><span class="sxs-lookup"><span data-stu-id="94a4e-109">Attribute</span></span>|<span data-ttu-id="94a4e-110">描述</span><span class="sxs-lookup"><span data-stu-id="94a4e-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="94a4e-111">claimType</span><span class="sxs-lookup"><span data-stu-id="94a4e-111">claimType</span></span>|<span data-ttu-id="94a4e-112">定義宣告型別的 URI。</span><span class="sxs-lookup"><span data-stu-id="94a4e-112">A URI that defines the type of a claim.</span></span> <span data-ttu-id="94a4e-113">例如，要在網站上購物，使用者必須提供具有足夠信用額度的有效信用卡。</span><span class="sxs-lookup"><span data-stu-id="94a4e-113">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="94a4e-114">宣告型別是信用卡的 URI。</span><span class="sxs-lookup"><span data-stu-id="94a4e-114">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="94a4e-115">isOptional</span><span class="sxs-lookup"><span data-stu-id="94a4e-115">isOptional</span></span>|<span data-ttu-id="94a4e-116">布林值，指定此宣告是否為選擇性宣告。</span><span class="sxs-lookup"><span data-stu-id="94a4e-116">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="94a4e-117">若此為必要宣告，請將此屬性設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="94a4e-117">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="94a4e-118">若服務要求某些資訊，但並非必要，便可使用此屬性。</span><span class="sxs-lookup"><span data-stu-id="94a4e-118">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="94a4e-119">例如，如果您要求使用者輸入他們的名字、姓氏和位址，但決定電話號碼是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="94a4e-119">For example, if you require the user to enter their first name, last name, and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="94a4e-120">子元素</span><span class="sxs-lookup"><span data-stu-id="94a4e-120">Child Elements</span></span>  

 <span data-ttu-id="94a4e-121">無。</span><span class="sxs-lookup"><span data-stu-id="94a4e-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="94a4e-122">父項目</span><span class="sxs-lookup"><span data-stu-id="94a4e-122">Parent Elements</span></span>  
  
|<span data-ttu-id="94a4e-123">項目</span><span class="sxs-lookup"><span data-stu-id="94a4e-123">Element</span></span>|<span data-ttu-id="94a4e-124">描述</span><span class="sxs-lookup"><span data-stu-id="94a4e-124">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="94a4e-125">指定必要宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="94a4e-125">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="94a4e-126">在聯合案例中，服務會聲明對傳入認證的需求。</span><span class="sxs-lookup"><span data-stu-id="94a4e-126">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="94a4e-127">例如，傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="94a4e-127">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="94a4e-128">這個集合中的每一個項目都會指定要顯示在聯合認證中的必要和選擇性宣告型別。</span><span class="sxs-lookup"><span data-stu-id="94a4e-128">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94a4e-129">備註</span><span class="sxs-lookup"><span data-stu-id="94a4e-129">Remarks</span></span>  

 <span data-ttu-id="94a4e-130">在聯合案例中，服務會聲明對傳入認證的需求。</span><span class="sxs-lookup"><span data-stu-id="94a4e-130">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="94a4e-131">例如，傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="94a4e-131">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="94a4e-132">這項需求會顯示在安全性原則中。</span><span class="sxs-lookup"><span data-stu-id="94a4e-132">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="94a4e-133">當用戶端從聯合服務 (例如 CardSpace) 要求認證，它會將需求放入權杖要求 (RequestSecurityToken)，那麼聯合服務便可發出認證，滿足相應的需求。</span><span class="sxs-lookup"><span data-stu-id="94a4e-133">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94a4e-134">範例</span><span class="sxs-lookup"><span data-stu-id="94a4e-134">Example</span></span>  

 <span data-ttu-id="94a4e-135">下列組態會將兩項宣告型別需求新增至安全性繫結程序。</span><span class="sxs-lookup"><span data-stu-id="94a4e-135">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="94a4e-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94a4e-136">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<claimTypeRequirements>](claimtyperequirements-element.md)
- [<span data-ttu-id="94a4e-137">繫結</span><span class="sxs-lookup"><span data-stu-id="94a4e-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="94a4e-138">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="94a4e-138">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="94a4e-139">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="94a4e-139">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="94a4e-140">作法：使用 SecurityBindingElement 建立自訂繫結</span><span class="sxs-lookup"><span data-stu-id="94a4e-140">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="94a4e-141">自訂繫結安全性</span><span class="sxs-lookup"><span data-stu-id="94a4e-141">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
