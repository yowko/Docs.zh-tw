---
title: <clear> 項目的 <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: 01f101f7d0dd5da6a834a4ffb2c7e09df0e23cd8
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400532"
---
# <a name="clear-of-claimtyperequirements-element"></a><span data-ttu-id="90aa9-102">\<清除\<claimTypeRequirements > 元素 ></span><span class="sxs-lookup"><span data-stu-id="90aa9-102">\<clear> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="90aa9-103">指定移除聯合認證中的所有宣告型別。</span><span class="sxs-lookup"><span data-stu-id="90aa9-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="90aa9-104">這個動作可確保集合啟動時是空的。</span><span class="sxs-lookup"><span data-stu-id="90aa9-104">This ensures that the collection starts empty.</span></span>  
  
<span data-ttu-id="90aa9-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="90aa9-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="90aa9-106">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="90aa9-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="90aa9-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="90aa9-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="90aa9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="90aa9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="90aa9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="90aa9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="90aa9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<安全性 >** ](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="90aa9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="90aa9-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<訊息 >** ](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="90aa9-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="90aa9-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<claimTypeRequirements >** ](claimtyperequirements-for-message.md)</span><span class="sxs-lookup"><span data-stu-id="90aa9-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)</span></span>\
<span data-ttu-id="90aa9-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<清除 >**</span><span class="sxs-lookup"><span data-stu-id="90aa9-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90aa9-114">語法</span><span class="sxs-lookup"><span data-stu-id="90aa9-114">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <clear />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90aa9-115">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="90aa9-115">Attributes and Elements</span></span>  
 <span data-ttu-id="90aa9-116">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="90aa9-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90aa9-117">屬性</span><span class="sxs-lookup"><span data-stu-id="90aa9-117">Attributes</span></span>  
 <span data-ttu-id="90aa9-118">無。</span><span class="sxs-lookup"><span data-stu-id="90aa9-118">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="90aa9-119">子元素</span><span class="sxs-lookup"><span data-stu-id="90aa9-119">Child Elements</span></span>  
 <span data-ttu-id="90aa9-120">無。</span><span class="sxs-lookup"><span data-stu-id="90aa9-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="90aa9-121">父項目</span><span class="sxs-lookup"><span data-stu-id="90aa9-121">Parent Elements</span></span>  
  
|<span data-ttu-id="90aa9-122">項目</span><span class="sxs-lookup"><span data-stu-id="90aa9-122">Element</span></span>|<span data-ttu-id="90aa9-123">描述</span><span class="sxs-lookup"><span data-stu-id="90aa9-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="90aa9-124">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="90aa9-124">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="90aa9-125">指定必要宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="90aa9-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="90aa9-126">每個項目的型別為 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="90aa9-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="90aa9-127">在聯合案例中，服務會聲明對傳入認證的需求。</span><span class="sxs-lookup"><span data-stu-id="90aa9-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="90aa9-128">例如，傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="90aa9-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="90aa9-129">這個集合中的每一個項目都會指定要顯示在聯合認證中的必要和選擇性宣告型別。</span><span class="sxs-lookup"><span data-stu-id="90aa9-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="90aa9-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90aa9-130">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
