---
title: <remove> 項目的 <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 84f4208d3f4581cf7e8c4455bf3f5d78f7e13b9f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399990"
---
# <a name="remove-of-claimtyperequirements-element"></a><span data-ttu-id="c5952-102">\<remove> 項目的 \<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="c5952-102">\<remove> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="c5952-103">指定聯合認證中要移除的宣告型別。</span><span class="sxs-lookup"><span data-stu-id="c5952-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="c5952-104">語法</span><span class="sxs-lookup"><span data-stu-id="c5952-104">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <remove claimType="URI" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5952-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c5952-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c5952-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c5952-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5952-107">屬性</span><span class="sxs-lookup"><span data-stu-id="c5952-107">Attributes</span></span>  
  
|<span data-ttu-id="c5952-108">屬性</span><span class="sxs-lookup"><span data-stu-id="c5952-108">Attribute</span></span>|<span data-ttu-id="c5952-109">描述</span><span class="sxs-lookup"><span data-stu-id="c5952-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c5952-110">claimType</span><span class="sxs-lookup"><span data-stu-id="c5952-110">claimType</span></span>|<span data-ttu-id="c5952-111">定義要移除之宣告型別的 URI。</span><span class="sxs-lookup"><span data-stu-id="c5952-111">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5952-112">子元素</span><span class="sxs-lookup"><span data-stu-id="c5952-112">Child Elements</span></span>  
 <span data-ttu-id="c5952-113">無。</span><span class="sxs-lookup"><span data-stu-id="c5952-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c5952-114">父項目</span><span class="sxs-lookup"><span data-stu-id="c5952-114">Parent Elements</span></span>  
  
|<span data-ttu-id="c5952-115">元素</span><span class="sxs-lookup"><span data-stu-id="c5952-115">Element</span></span>|<span data-ttu-id="c5952-116">描述</span><span class="sxs-lookup"><span data-stu-id="c5952-116">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|<span data-ttu-id="c5952-117">指定必要宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="c5952-117">Specifies a collection of required claim types.</span></span> <span data-ttu-id="c5952-118">每個項目的型別為 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="c5952-118">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="c5952-119">在聯合案例中，服務會聲明對傳入認證的需求。</span><span class="sxs-lookup"><span data-stu-id="c5952-119">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="c5952-120">例如，傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="c5952-120">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="c5952-121">這個集合中的每一個項目都會指定要顯示在聯合認證中的必要和選擇性宣告型別。</span><span class="sxs-lookup"><span data-stu-id="c5952-121">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c5952-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5952-122">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
