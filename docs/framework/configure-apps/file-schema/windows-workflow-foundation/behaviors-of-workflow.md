---
title: 工作流程的 <behaviors>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: b7c5cf93a82ac88c25f9c478ad52cf41eb6f6d65
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129203"
---
# <a name="behaviors-of-workflow"></a><span data-ttu-id="ad5ec-102">\<行為 > 的工作流程</span><span class="sxs-lookup"><span data-stu-id="ad5ec-102">\<behaviors> of workflow</span></span>
<span data-ttu-id="ad5ec-103">這個元素包含**serviceBehaviors**集合。</span><span class="sxs-lookup"><span data-stu-id="ad5ec-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="ad5ec-104">集合中的每個項目都會定義工作流程服務使用的行為項目。</span><span class="sxs-lookup"><span data-stu-id="ad5ec-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="ad5ec-105">每個行為項目由其唯一**名稱**屬性。</span><span class="sxs-lookup"><span data-stu-id="ad5ec-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
 <span data-ttu-id="ad5ec-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ad5ec-106">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad5ec-107">語法</span><span class="sxs-lookup"><span data-stu-id="ad5ec-107">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad5ec-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ad5ec-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ad5ec-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ad5ec-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad5ec-110">屬性</span><span class="sxs-lookup"><span data-stu-id="ad5ec-110">Attributes</span></span>  
 <span data-ttu-id="ad5ec-111">None</span><span class="sxs-lookup"><span data-stu-id="ad5ec-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ad5ec-112">子元素</span><span class="sxs-lookup"><span data-stu-id="ad5ec-112">Child Elements</span></span>  
  
|<span data-ttu-id="ad5ec-113">項目</span><span class="sxs-lookup"><span data-stu-id="ad5ec-113">Element</span></span>|<span data-ttu-id="ad5ec-114">描述</span><span class="sxs-lookup"><span data-stu-id="ad5ec-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ad5ec-115">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="ad5ec-115">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|<span data-ttu-id="ad5ec-116">這個組態區段表示為特定工作流程服務定義的所有行為。</span><span class="sxs-lookup"><span data-stu-id="ad5ec-116">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ad5ec-117">父項目</span><span class="sxs-lookup"><span data-stu-id="ad5ec-117">Parent Elements</span></span>  
  
|<span data-ttu-id="ad5ec-118">項目</span><span class="sxs-lookup"><span data-stu-id="ad5ec-118">Element</span></span>|<span data-ttu-id="ad5ec-119">描述</span><span class="sxs-lookup"><span data-stu-id="ad5ec-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ad5ec-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ad5ec-120">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="ad5ec-121">所有工作流程組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="ad5ec-121">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ad5ec-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad5ec-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="ad5ec-123">使用行為來設定與擴充執行階段</span><span class="sxs-lookup"><span data-stu-id="ad5ec-123">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
