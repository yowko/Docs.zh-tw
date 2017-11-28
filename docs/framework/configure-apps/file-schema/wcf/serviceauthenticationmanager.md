---
title: '&lt;serviceAuthenticationManager&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2385b96460e0a3d53efb62054fb7da334ddd2d49
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltserviceauthenticationmanagergt"></a><span data-ttu-id="14635-102">&lt;serviceAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="14635-102">&lt;serviceAuthenticationManager&gt;</span></span>
<span data-ttu-id="14635-103">提供工作流程組態項目，這個項目會在服務層級建立傳輸、訊息或建立者的有效性。</span><span class="sxs-lookup"><span data-stu-id="14635-103">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator..</span></span>  
  
<span data-ttu-id="14635-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="14635-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="14635-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="14635-105">\<behaviors></span></span>  
<span data-ttu-id="14635-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="14635-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="14635-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="14635-107">\<behavior></span></span>  
<span data-ttu-id="14635-108">\<serviceAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="14635-108">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14635-109">語法</span><span class="sxs-lookup"><span data-stu-id="14635-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14635-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="14635-110">Attributes and Elements</span></span>  
 <span data-ttu-id="14635-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="14635-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14635-112">屬性</span><span class="sxs-lookup"><span data-stu-id="14635-112">Attributes</span></span>  
  
|<span data-ttu-id="14635-113">屬性</span><span class="sxs-lookup"><span data-stu-id="14635-113">Attribute</span></span>|<span data-ttu-id="14635-114">描述</span><span class="sxs-lookup"><span data-stu-id="14635-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="14635-115">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="14635-115">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="14635-116">字串，指定目前行為的驗證原則類型。</span><span class="sxs-lookup"><span data-stu-id="14635-116">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="14635-117">子元素</span><span class="sxs-lookup"><span data-stu-id="14635-117">Child Elements</span></span>  
 <span data-ttu-id="14635-118">無。</span><span class="sxs-lookup"><span data-stu-id="14635-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="14635-119">父項目</span><span class="sxs-lookup"><span data-stu-id="14635-119">Parent Elements</span></span>  
  
|<span data-ttu-id="14635-120">項目</span><span class="sxs-lookup"><span data-stu-id="14635-120">Element</span></span>|<span data-ttu-id="14635-121">說明</span><span class="sxs-lookup"><span data-stu-id="14635-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14635-122">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="14635-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="14635-123">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="14635-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="14635-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14635-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
