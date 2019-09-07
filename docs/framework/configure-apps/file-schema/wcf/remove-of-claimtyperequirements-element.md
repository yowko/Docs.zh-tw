---
title: <remove> 項目的 <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 84f4208d3f4581cf7e8c4455bf3f5d78f7e13b9f
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399990"
---
# <a name="remove-of-claimtyperequirements-element"></a><span data-ttu-id="91f62-102">\<移除 claimTypeRequirements > \<元素的 ></span><span class="sxs-lookup"><span data-stu-id="91f62-102">\<remove> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="91f62-103">指定聯合認證中要移除的宣告型別。</span><span class="sxs-lookup"><span data-stu-id="91f62-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
<span data-ttu-id="91f62-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="91f62-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="91f62-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="91f62-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="91f62-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="91f62-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="91f62-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="91f62-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="91f62-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="91f62-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="91f62-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<安全性 >** ](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="91f62-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="91f62-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<訊息 >** ](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="91f62-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="91f62-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<claimTypeRequirements >** ](claimtyperequirements-for-message.md)</span><span class="sxs-lookup"><span data-stu-id="91f62-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)</span></span>\
<span data-ttu-id="91f62-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<移除 >**</span><span class="sxs-lookup"><span data-stu-id="91f62-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91f62-113">語法</span><span class="sxs-lookup"><span data-stu-id="91f62-113">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <remove claimType="URI" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91f62-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="91f62-114">Attributes and Elements</span></span>  
 <span data-ttu-id="91f62-115">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="91f62-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91f62-116">屬性</span><span class="sxs-lookup"><span data-stu-id="91f62-116">Attributes</span></span>  
  
|<span data-ttu-id="91f62-117">屬性</span><span class="sxs-lookup"><span data-stu-id="91f62-117">Attribute</span></span>|<span data-ttu-id="91f62-118">描述</span><span class="sxs-lookup"><span data-stu-id="91f62-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="91f62-119">claimType</span><span class="sxs-lookup"><span data-stu-id="91f62-119">claimType</span></span>|<span data-ttu-id="91f62-120">定義要移除之宣告型別的 URI。</span><span class="sxs-lookup"><span data-stu-id="91f62-120">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="91f62-121">子元素</span><span class="sxs-lookup"><span data-stu-id="91f62-121">Child Elements</span></span>  
 <span data-ttu-id="91f62-122">無。</span><span class="sxs-lookup"><span data-stu-id="91f62-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="91f62-123">父項目</span><span class="sxs-lookup"><span data-stu-id="91f62-123">Parent Elements</span></span>  
  
|<span data-ttu-id="91f62-124">項目</span><span class="sxs-lookup"><span data-stu-id="91f62-124">Element</span></span>|<span data-ttu-id="91f62-125">描述</span><span class="sxs-lookup"><span data-stu-id="91f62-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="91f62-126">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="91f62-126">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="91f62-127">指定必要宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="91f62-127">Specifies a collection of required claim types.</span></span> <span data-ttu-id="91f62-128">每個項目的型別為 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="91f62-128">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="91f62-129">在聯合案例中，服務會聲明對傳入認證的需求。</span><span class="sxs-lookup"><span data-stu-id="91f62-129">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="91f62-130">例如，傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="91f62-130">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="91f62-131">這個集合中的每一個項目都會指定要顯示在聯合認證中的必要和選擇性宣告型別。</span><span class="sxs-lookup"><span data-stu-id="91f62-131">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="91f62-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91f62-132">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
