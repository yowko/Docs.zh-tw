---
title: 工作流程的 <behaviors>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 05a15cdf5c043eb5d94b36028324310d2b7a8413
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398882"
---
# <a name="behaviors-of-workflow"></a><span data-ttu-id="1deed-102">工作流程的 \<behaviors></span><span class="sxs-lookup"><span data-stu-id="1deed-102">\<behaviors> of workflow</span></span>
<span data-ttu-id="1deed-103">此元素包含**serviceBehaviors**集合。</span><span class="sxs-lookup"><span data-stu-id="1deed-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="1deed-104">集合中的每個項目都會定義工作流程服務使用的行為項目。</span><span class="sxs-lookup"><span data-stu-id="1deed-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="1deed-105">每個行為元素都是由其唯一的**名稱**屬性來識別。</span><span class="sxs-lookup"><span data-stu-id="1deed-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**  
  
## <a name="syntax"></a><span data-ttu-id="1deed-106">語法</span><span class="sxs-lookup"><span data-stu-id="1deed-106">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1deed-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1deed-107">Attributes and Elements</span></span>  
 <span data-ttu-id="1deed-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1deed-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1deed-109">屬性</span><span class="sxs-lookup"><span data-stu-id="1deed-109">Attributes</span></span>  
 <span data-ttu-id="1deed-110">無</span><span class="sxs-lookup"><span data-stu-id="1deed-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1deed-111">子元素</span><span class="sxs-lookup"><span data-stu-id="1deed-111">Child Elements</span></span>  
  
|<span data-ttu-id="1deed-112">元素</span><span class="sxs-lookup"><span data-stu-id="1deed-112">Element</span></span>|<span data-ttu-id="1deed-113">描述</span><span class="sxs-lookup"><span data-stu-id="1deed-113">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors-of-workflow.md)|<span data-ttu-id="1deed-114">這個組態區段表示為特定工作流程服務定義的所有行為。</span><span class="sxs-lookup"><span data-stu-id="1deed-114">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1deed-115">父項目</span><span class="sxs-lookup"><span data-stu-id="1deed-115">Parent Elements</span></span>  
  
|<span data-ttu-id="1deed-116">元素</span><span class="sxs-lookup"><span data-stu-id="1deed-116">Element</span></span>|<span data-ttu-id="1deed-117">描述</span><span class="sxs-lookup"><span data-stu-id="1deed-117">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](../wcf/system-servicemodel.md)|<span data-ttu-id="1deed-118">所有工作流程組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="1deed-118">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1deed-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1deed-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="1deed-120">使用行為來設定與擴充執行階段</span><span class="sxs-lookup"><span data-stu-id="1deed-120">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
