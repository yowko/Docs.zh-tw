---
title: <clear> 項目的 <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: 01f101f7d0dd5da6a834a4ffb2c7e09df0e23cd8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400532"
---
# <a name="clear-of-claimtyperequirements-element"></a><span data-ttu-id="3eb1b-102">\<clear> 項目的 \<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="3eb1b-102">\<clear> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="3eb1b-103">指定移除聯合認證中的所有宣告型別。</span><span class="sxs-lookup"><span data-stu-id="3eb1b-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="3eb1b-104">這個動作可確保集合啟動時是空的。</span><span class="sxs-lookup"><span data-stu-id="3eb1b-104">This ensures that the collection starts empty.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**  
  
## <a name="syntax"></a><span data-ttu-id="3eb1b-105">語法</span><span class="sxs-lookup"><span data-stu-id="3eb1b-105">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <clear />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3eb1b-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3eb1b-106">Attributes and Elements</span></span>  
 <span data-ttu-id="3eb1b-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3eb1b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3eb1b-108">屬性</span><span class="sxs-lookup"><span data-stu-id="3eb1b-108">Attributes</span></span>  
 <span data-ttu-id="3eb1b-109">無。</span><span class="sxs-lookup"><span data-stu-id="3eb1b-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3eb1b-110">子元素</span><span class="sxs-lookup"><span data-stu-id="3eb1b-110">Child Elements</span></span>  
 <span data-ttu-id="3eb1b-111">無。</span><span class="sxs-lookup"><span data-stu-id="3eb1b-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3eb1b-112">父項目</span><span class="sxs-lookup"><span data-stu-id="3eb1b-112">Parent Elements</span></span>  
  
|<span data-ttu-id="3eb1b-113">元素</span><span class="sxs-lookup"><span data-stu-id="3eb1b-113">Element</span></span>|<span data-ttu-id="3eb1b-114">描述</span><span class="sxs-lookup"><span data-stu-id="3eb1b-114">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|<span data-ttu-id="3eb1b-115">指定必要宣告型別的集合。</span><span class="sxs-lookup"><span data-stu-id="3eb1b-115">Specifies a collection of required claim types.</span></span> <span data-ttu-id="3eb1b-116">每個項目的型別為 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="3eb1b-116">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="3eb1b-117">在聯合案例中，服務會聲明對傳入認證的需求。</span><span class="sxs-lookup"><span data-stu-id="3eb1b-117">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="3eb1b-118">例如，傳入認證必須處理特定的一組宣告型別。</span><span class="sxs-lookup"><span data-stu-id="3eb1b-118">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="3eb1b-119">這個集合中的每一個項目都會指定要顯示在聯合認證中的必要和選擇性宣告型別。</span><span class="sxs-lookup"><span data-stu-id="3eb1b-119">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3eb1b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3eb1b-120">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
