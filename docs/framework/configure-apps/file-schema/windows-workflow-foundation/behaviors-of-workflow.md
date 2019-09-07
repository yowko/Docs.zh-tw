---
title: 工作流程的 <behaviors>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 05a15cdf5c043eb5d94b36028324310d2b7a8413
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398882"
---
# <a name="behaviors-of-workflow"></a><span data-ttu-id="0ec78-102">\<工作流程 > 的行為</span><span class="sxs-lookup"><span data-stu-id="0ec78-102">\<behaviors> of workflow</span></span>
<span data-ttu-id="0ec78-103">此元素包含**serviceBehaviors**集合。</span><span class="sxs-lookup"><span data-stu-id="0ec78-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="0ec78-104">集合中的每個項目都會定義工作流程服務使用的行為項目。</span><span class="sxs-lookup"><span data-stu-id="0ec78-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="0ec78-105">每個行為元素都是由其唯一的**名稱**屬性來識別。</span><span class="sxs-lookup"><span data-stu-id="0ec78-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
<span data-ttu-id="0ec78-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0ec78-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0ec78-107">&nbsp;&nbsp;[ **\<筆記本電腦.System.servicemodel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="0ec78-107">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="0ec78-108">&nbsp;&nbsp;&nbsp;&nbsp; **\<行為 >**</span><span class="sxs-lookup"><span data-stu-id="0ec78-108">&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ec78-109">語法</span><span class="sxs-lookup"><span data-stu-id="0ec78-109">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0ec78-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0ec78-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0ec78-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0ec78-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0ec78-112">屬性</span><span class="sxs-lookup"><span data-stu-id="0ec78-112">Attributes</span></span>  
 <span data-ttu-id="0ec78-113">None</span><span class="sxs-lookup"><span data-stu-id="0ec78-113">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0ec78-114">子元素</span><span class="sxs-lookup"><span data-stu-id="0ec78-114">Child Elements</span></span>  
  
|<span data-ttu-id="0ec78-115">項目</span><span class="sxs-lookup"><span data-stu-id="0ec78-115">Element</span></span>|<span data-ttu-id="0ec78-116">描述</span><span class="sxs-lookup"><span data-stu-id="0ec78-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0ec78-117">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="0ec78-117">\<serviceBehaviors></span></span>](servicebehaviors-of-workflow.md)|<span data-ttu-id="0ec78-118">這個組態區段表示為特定工作流程服務定義的所有行為。</span><span class="sxs-lookup"><span data-stu-id="0ec78-118">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0ec78-119">父項目</span><span class="sxs-lookup"><span data-stu-id="0ec78-119">Parent Elements</span></span>  
  
|<span data-ttu-id="0ec78-120">項目</span><span class="sxs-lookup"><span data-stu-id="0ec78-120">Element</span></span>|<span data-ttu-id="0ec78-121">說明</span><span class="sxs-lookup"><span data-stu-id="0ec78-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0ec78-122">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0ec78-122">\<system.serviceModel></span></span>](../wcf/system-servicemodel.md)|<span data-ttu-id="0ec78-123">所有工作流程組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="0ec78-123">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0ec78-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ec78-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="0ec78-125">使用行為來設定與擴充執行階段</span><span class="sxs-lookup"><span data-stu-id="0ec78-125">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
