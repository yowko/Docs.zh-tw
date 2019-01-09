---
title: '&lt;serviceAuthenticationManager&gt;'
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: 3456ffa952372b014d579b5c420f7c44222fdad5
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145350"
---
# <a name="ltserviceauthenticationmanagergt"></a><span data-ttu-id="e13f6-102">&lt;serviceAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="e13f6-102">&lt;serviceAuthenticationManager&gt;</span></span>
<span data-ttu-id="e13f6-103">提供工作流程組態項目，這個項目會在服務層級建立傳輸、訊息或建立者的有效性。</span><span class="sxs-lookup"><span data-stu-id="e13f6-103">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
<span data-ttu-id="e13f6-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e13f6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e13f6-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="e13f6-105">\<behaviors></span></span>  
<span data-ttu-id="e13f6-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="e13f6-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="e13f6-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="e13f6-107">\<behavior></span></span>  
<span data-ttu-id="e13f6-108">\<serviceAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="e13f6-108">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e13f6-109">語法</span><span class="sxs-lookup"><span data-stu-id="e13f6-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e13f6-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e13f6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e13f6-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e13f6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e13f6-112">屬性</span><span class="sxs-lookup"><span data-stu-id="e13f6-112">Attributes</span></span>  
  
|<span data-ttu-id="e13f6-113">屬性</span><span class="sxs-lookup"><span data-stu-id="e13f6-113">Attribute</span></span>|<span data-ttu-id="e13f6-114">描述</span><span class="sxs-lookup"><span data-stu-id="e13f6-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e13f6-115">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="e13f6-115">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="e13f6-116">字串，指定目前行為的驗證原則類型。</span><span class="sxs-lookup"><span data-stu-id="e13f6-116">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e13f6-117">子元素</span><span class="sxs-lookup"><span data-stu-id="e13f6-117">Child Elements</span></span>  
 <span data-ttu-id="e13f6-118">無。</span><span class="sxs-lookup"><span data-stu-id="e13f6-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e13f6-119">父項目</span><span class="sxs-lookup"><span data-stu-id="e13f6-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e13f6-120">項目</span><span class="sxs-lookup"><span data-stu-id="e13f6-120">Element</span></span>|<span data-ttu-id="e13f6-121">描述</span><span class="sxs-lookup"><span data-stu-id="e13f6-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e13f6-122">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="e13f6-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="e13f6-123">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="e13f6-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e13f6-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e13f6-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
