---
title: 工作流程的 <behaviors>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 7dd3b0b20c9d7accd80a85b3693e67ffc9b729e5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945998"
---
# <a name="behaviors-of-workflow"></a><span data-ttu-id="1374e-102">\<工作流程 > 的行為</span><span class="sxs-lookup"><span data-stu-id="1374e-102">\<behaviors> of workflow</span></span>
<span data-ttu-id="1374e-103">此元素包含**serviceBehaviors**集合。</span><span class="sxs-lookup"><span data-stu-id="1374e-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="1374e-104">集合中的每個項目都會定義工作流程服務使用的行為項目。</span><span class="sxs-lookup"><span data-stu-id="1374e-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="1374e-105">每個行為元素都是由其唯一的**名稱**屬性來識別。</span><span class="sxs-lookup"><span data-stu-id="1374e-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
 <span data-ttu-id="1374e-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1374e-106">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1374e-107">語法</span><span class="sxs-lookup"><span data-stu-id="1374e-107">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1374e-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1374e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1374e-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1374e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1374e-110">屬性</span><span class="sxs-lookup"><span data-stu-id="1374e-110">Attributes</span></span>  
 <span data-ttu-id="1374e-111">無</span><span class="sxs-lookup"><span data-stu-id="1374e-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1374e-112">子元素</span><span class="sxs-lookup"><span data-stu-id="1374e-112">Child Elements</span></span>  
  
|<span data-ttu-id="1374e-113">項目</span><span class="sxs-lookup"><span data-stu-id="1374e-113">Element</span></span>|<span data-ttu-id="1374e-114">描述</span><span class="sxs-lookup"><span data-stu-id="1374e-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1374e-115">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="1374e-115">\<serviceBehaviors></span></span>](servicebehaviors-of-workflow.md)|<span data-ttu-id="1374e-116">這個組態區段表示為特定工作流程服務定義的所有行為。</span><span class="sxs-lookup"><span data-stu-id="1374e-116">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1374e-117">父項目</span><span class="sxs-lookup"><span data-stu-id="1374e-117">Parent Elements</span></span>  
  
|<span data-ttu-id="1374e-118">項目</span><span class="sxs-lookup"><span data-stu-id="1374e-118">Element</span></span>|<span data-ttu-id="1374e-119">描述</span><span class="sxs-lookup"><span data-stu-id="1374e-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1374e-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1374e-120">\<system.serviceModel></span></span>](../wcf/system-servicemodel.md)|<span data-ttu-id="1374e-121">所有工作流程組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="1374e-121">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1374e-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1374e-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="1374e-123">使用行為來設定與擴充執行階段</span><span class="sxs-lookup"><span data-stu-id="1374e-123">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
