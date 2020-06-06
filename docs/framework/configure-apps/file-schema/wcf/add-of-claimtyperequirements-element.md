---
title: <add> 項目的 <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: f6948052c62684faa734b592f5bdfc2e7827a07a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153096"
---
# <a name="add-of-claimtyperequirements-element"></a><span data-ttu-id="5f5cb-102">\<add> 項目的 \<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="5f5cb-102">\<add> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="5f5cb-103">指定必須在聯合認證中出現的必要及選擇性宣告型別。</span><span class="sxs-lookup"><span data-stu-id="5f5cb-103">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="5f5cb-104">例如，服務說明傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="5f5cb-104">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**
  
## <a name="syntax"></a><span data-ttu-id="5f5cb-105">語法</span><span class="sxs-lookup"><span data-stu-id="5f5cb-105">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f5cb-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5f5cb-106">Attributes and Elements</span></span>  
 <span data-ttu-id="5f5cb-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5f5cb-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f5cb-108">屬性</span><span class="sxs-lookup"><span data-stu-id="5f5cb-108">Attributes</span></span>  
  
|<span data-ttu-id="5f5cb-109">屬性</span><span class="sxs-lookup"><span data-stu-id="5f5cb-109">Attribute</span></span>|<span data-ttu-id="5f5cb-110">描述</span><span class="sxs-lookup"><span data-stu-id="5f5cb-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5f5cb-111">claimType</span><span class="sxs-lookup"><span data-stu-id="5f5cb-111">claimType</span></span>|<span data-ttu-id="5f5cb-112">定義宣告型別的 URI。</span><span class="sxs-lookup"><span data-stu-id="5f5cb-112">A URI that defines the type of a claim.</span></span> <span data-ttu-id="5f5cb-113">例如，要在網站上購物，使用者必須提供具有足夠信用額度的有效信用卡。</span><span class="sxs-lookup"><span data-stu-id="5f5cb-113">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="5f5cb-114">宣告型別是信用卡的 URI。</span><span class="sxs-lookup"><span data-stu-id="5f5cb-114">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="5f5cb-115">isOptional</span><span class="sxs-lookup"><span data-stu-id="5f5cb-115">isOptional</span></span>|<span data-ttu-id="5f5cb-116">布林值，指定此宣告是否為選擇性宣告。</span><span class="sxs-lookup"><span data-stu-id="5f5cb-116">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="5f5cb-117">若此為必要宣告，請將此屬性設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="5f5cb-117">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="5f5cb-118">若服務要求某些資訊，但並非必要，便可使用此屬性。</span><span class="sxs-lookup"><span data-stu-id="5f5cb-118">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="5f5cb-119">例如，如果您要求使用者輸入名字、姓氏和位址，但決定電話號碼是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="5f5cb-119">For example, if you require the user to enter their first name, last name, and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5f5cb-120">子元素</span><span class="sxs-lookup"><span data-stu-id="5f5cb-120">Child Elements</span></span>  
 <span data-ttu-id="5f5cb-121">無。</span><span class="sxs-lookup"><span data-stu-id="5f5cb-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5f5cb-122">父項目</span><span class="sxs-lookup"><span data-stu-id="5f5cb-122">Parent Elements</span></span>  
  
|<span data-ttu-id="5f5cb-123">元素</span><span class="sxs-lookup"><span data-stu-id="5f5cb-123">Element</span></span>|<span data-ttu-id="5f5cb-124">描述</span><span class="sxs-lookup"><span data-stu-id="5f5cb-124">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|<span data-ttu-id="5f5cb-125">指定必要宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="5f5cb-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="5f5cb-126">每個項目的型別為 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="5f5cb-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="5f5cb-127">在聯合案例中，服務會聲明對傳入認證的需求。</span><span class="sxs-lookup"><span data-stu-id="5f5cb-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="5f5cb-128">例如，傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="5f5cb-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="5f5cb-129">這個集合中的每一個項目都會指定要顯示在聯合認證中的必要和選擇性宣告型別。</span><span class="sxs-lookup"><span data-stu-id="5f5cb-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f5cb-130">備註</span><span class="sxs-lookup"><span data-stu-id="5f5cb-130">Remarks</span></span>  
 <span data-ttu-id="5f5cb-131">在聯合案例中，服務會聲明對傳入認證的需求。</span><span class="sxs-lookup"><span data-stu-id="5f5cb-131">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="5f5cb-132">例如，傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="5f5cb-132">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="5f5cb-133">這項需求會顯示在安全性原則中。</span><span class="sxs-lookup"><span data-stu-id="5f5cb-133">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="5f5cb-134">當用戶端從聯合服務 (例如 CardSpace) 要求認證，它會將需求放入權杖要求 (RequestSecurityToken)，那麼聯合服務便可發出認證，滿足相應的需求。</span><span class="sxs-lookup"><span data-stu-id="5f5cb-134">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f5cb-135">範例</span><span class="sxs-lookup"><span data-stu-id="5f5cb-135">Example</span></span>  
 <span data-ttu-id="5f5cb-136">下列組態會將兩項宣告型別需求新增至安全性繫結程序。</span><span class="sxs-lookup"><span data-stu-id="5f5cb-136">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5f5cb-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f5cb-137">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
