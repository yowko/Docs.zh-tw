---
title: '&lt;serviceAuthenticationManager&gt;'
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: 3b58214a1fd7a50fb1a9ab3dfee0a14870f8a476
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltserviceauthenticationmanagergt"></a><span data-ttu-id="cbec3-102">&lt;serviceAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="cbec3-102">&lt;serviceAuthenticationManager&gt;</span></span>
<span data-ttu-id="cbec3-103">提供工作流程組態項目，這個項目會在服務層級建立傳輸、訊息或建立者的有效性。</span><span class="sxs-lookup"><span data-stu-id="cbec3-103">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator..</span></span>  
  
<span data-ttu-id="cbec3-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cbec3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cbec3-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="cbec3-105">\<behaviors></span></span>  
<span data-ttu-id="cbec3-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="cbec3-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="cbec3-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="cbec3-107">\<behavior></span></span>  
<span data-ttu-id="cbec3-108">\<serviceAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="cbec3-108">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbec3-109">語法</span><span class="sxs-lookup"><span data-stu-id="cbec3-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cbec3-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cbec3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cbec3-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="cbec3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cbec3-112">屬性</span><span class="sxs-lookup"><span data-stu-id="cbec3-112">Attributes</span></span>  
  
|<span data-ttu-id="cbec3-113">屬性</span><span class="sxs-lookup"><span data-stu-id="cbec3-113">Attribute</span></span>|<span data-ttu-id="cbec3-114">描述</span><span class="sxs-lookup"><span data-stu-id="cbec3-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cbec3-115">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="cbec3-115">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="cbec3-116">字串，指定目前行為的驗證原則類型。</span><span class="sxs-lookup"><span data-stu-id="cbec3-116">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cbec3-117">子項目</span><span class="sxs-lookup"><span data-stu-id="cbec3-117">Child Elements</span></span>  
 <span data-ttu-id="cbec3-118">無。</span><span class="sxs-lookup"><span data-stu-id="cbec3-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cbec3-119">父項目</span><span class="sxs-lookup"><span data-stu-id="cbec3-119">Parent Elements</span></span>  
  
|<span data-ttu-id="cbec3-120">項目</span><span class="sxs-lookup"><span data-stu-id="cbec3-120">Element</span></span>|<span data-ttu-id="cbec3-121">描述</span><span class="sxs-lookup"><span data-stu-id="cbec3-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cbec3-122">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="cbec3-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="cbec3-123">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="cbec3-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cbec3-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbec3-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
