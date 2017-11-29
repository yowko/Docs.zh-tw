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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 40278c0a3d99dd5c37df1d642b8a2e13e9f62633
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltbehaviorsgt-of-workflow"></a><span data-ttu-id="23bdd-102">工作流程的 &lt;behaviors&gt;</span><span class="sxs-lookup"><span data-stu-id="23bdd-102">&lt;behaviors&gt; of workflow</span></span>
<span data-ttu-id="23bdd-103">這個項目包含**serviceBehaviors**集合。</span><span class="sxs-lookup"><span data-stu-id="23bdd-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="23bdd-104">集合中的每個項目都會定義工作流程服務使用的行為項目。</span><span class="sxs-lookup"><span data-stu-id="23bdd-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="23bdd-105">每個行為項目由其唯一**名稱**屬性。</span><span class="sxs-lookup"><span data-stu-id="23bdd-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
 <span data-ttu-id="23bdd-106">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="23bdd-106">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23bdd-107">語法</span><span class="sxs-lookup"><span data-stu-id="23bdd-107">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23bdd-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="23bdd-108">Attributes and Elements</span></span>  
 <span data-ttu-id="23bdd-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="23bdd-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23bdd-110">屬性</span><span class="sxs-lookup"><span data-stu-id="23bdd-110">Attributes</span></span>  
 <span data-ttu-id="23bdd-111">無</span><span class="sxs-lookup"><span data-stu-id="23bdd-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="23bdd-112">子元素</span><span class="sxs-lookup"><span data-stu-id="23bdd-112">Child Elements</span></span>  
  
|<span data-ttu-id="23bdd-113">項目</span><span class="sxs-lookup"><span data-stu-id="23bdd-113">Element</span></span>|<span data-ttu-id="23bdd-114">說明</span><span class="sxs-lookup"><span data-stu-id="23bdd-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23bdd-115">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="23bdd-115">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|<span data-ttu-id="23bdd-116">這個組態區段表示為特定工作流程服務定義的所有行為。</span><span class="sxs-lookup"><span data-stu-id="23bdd-116">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="23bdd-117">父項目</span><span class="sxs-lookup"><span data-stu-id="23bdd-117">Parent Elements</span></span>  
  
|<span data-ttu-id="23bdd-118">項目</span><span class="sxs-lookup"><span data-stu-id="23bdd-118">Element</span></span>|<span data-ttu-id="23bdd-119">說明</span><span class="sxs-lookup"><span data-stu-id="23bdd-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23bdd-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="23bdd-120">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="23bdd-121">所有工作流程組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="23bdd-121">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="23bdd-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23bdd-122">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BehaviorsSection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>  
 [<span data-ttu-id="23bdd-123">設定與擴充執行階段行為</span><span class="sxs-lookup"><span data-stu-id="23bdd-123">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
