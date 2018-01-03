---
title: "工作流程的 &lt;behaviors&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83c1bf4beb244b72d2fe3d82d749ff6ae6723baf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltbehaviorsgt-of-workflow"></a><span data-ttu-id="9371f-102">工作流程的 &lt;behaviors&gt;</span><span class="sxs-lookup"><span data-stu-id="9371f-102">&lt;behaviors&gt; of workflow</span></span>
<span data-ttu-id="9371f-103">這個項目包含**serviceBehaviors**集合。</span><span class="sxs-lookup"><span data-stu-id="9371f-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="9371f-104">集合中的每個項目都會定義工作流程服務使用的行為項目。</span><span class="sxs-lookup"><span data-stu-id="9371f-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="9371f-105">每個行為項目由其唯一**名稱**屬性。</span><span class="sxs-lookup"><span data-stu-id="9371f-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
 <span data-ttu-id="9371f-106">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="9371f-106">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9371f-107">語法</span><span class="sxs-lookup"><span data-stu-id="9371f-107">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9371f-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9371f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9371f-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="9371f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9371f-110">屬性</span><span class="sxs-lookup"><span data-stu-id="9371f-110">Attributes</span></span>  
 <span data-ttu-id="9371f-111">無</span><span class="sxs-lookup"><span data-stu-id="9371f-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9371f-112">子元素</span><span class="sxs-lookup"><span data-stu-id="9371f-112">Child Elements</span></span>  
  
|<span data-ttu-id="9371f-113">項目</span><span class="sxs-lookup"><span data-stu-id="9371f-113">Element</span></span>|<span data-ttu-id="9371f-114">描述</span><span class="sxs-lookup"><span data-stu-id="9371f-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9371f-115">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="9371f-115">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|<span data-ttu-id="9371f-116">這個組態區段表示為特定工作流程服務定義的所有行為。</span><span class="sxs-lookup"><span data-stu-id="9371f-116">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9371f-117">父項目</span><span class="sxs-lookup"><span data-stu-id="9371f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="9371f-118">項目</span><span class="sxs-lookup"><span data-stu-id="9371f-118">Element</span></span>|<span data-ttu-id="9371f-119">描述</span><span class="sxs-lookup"><span data-stu-id="9371f-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9371f-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9371f-120">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="9371f-121">所有工作流程組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="9371f-121">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9371f-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="9371f-122">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BehaviorsSection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>  
 [<span data-ttu-id="9371f-123">使用行為來設定與擴充執行階段</span><span class="sxs-lookup"><span data-stu-id="9371f-123">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
