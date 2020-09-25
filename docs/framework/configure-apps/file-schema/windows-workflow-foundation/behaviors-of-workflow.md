---
title: 工作流程的 <behaviors>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 21974f77526f55a47c014a285efd3bbac6fc1f7b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189600"
---
# <a name="behaviors-of-workflow"></a><span data-ttu-id="f23c9-102">工作流程的 \<behaviors></span><span class="sxs-lookup"><span data-stu-id="f23c9-102">\<behaviors> of workflow</span></span>

<span data-ttu-id="f23c9-103">這個元素包含 **>servicebehaviors>** 集合。</span><span class="sxs-lookup"><span data-stu-id="f23c9-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="f23c9-104">集合中的每個項目都會定義工作流程服務使用的行為項目。</span><span class="sxs-lookup"><span data-stu-id="f23c9-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="f23c9-105">每個行為元素都是由其唯一 **名稱** 屬性來識別。</span><span class="sxs-lookup"><span data-stu-id="f23c9-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**  
  
## <a name="syntax"></a><span data-ttu-id="f23c9-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f23c9-106">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f23c9-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f23c9-107">Attributes and Elements</span></span>  

 <span data-ttu-id="f23c9-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f23c9-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f23c9-109">屬性</span><span class="sxs-lookup"><span data-stu-id="f23c9-109">Attributes</span></span>  

 <span data-ttu-id="f23c9-110">無</span><span class="sxs-lookup"><span data-stu-id="f23c9-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f23c9-111">子元素</span><span class="sxs-lookup"><span data-stu-id="f23c9-111">Child Elements</span></span>  
  
|<span data-ttu-id="f23c9-112">項目</span><span class="sxs-lookup"><span data-stu-id="f23c9-112">Element</span></span>|<span data-ttu-id="f23c9-113">描述</span><span class="sxs-lookup"><span data-stu-id="f23c9-113">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors-of-workflow.md)|<span data-ttu-id="f23c9-114">這個組態區段表示為特定工作流程服務定義的所有行為。</span><span class="sxs-lookup"><span data-stu-id="f23c9-114">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f23c9-115">父項目</span><span class="sxs-lookup"><span data-stu-id="f23c9-115">Parent Elements</span></span>  
  
|<span data-ttu-id="f23c9-116">項目</span><span class="sxs-lookup"><span data-stu-id="f23c9-116">Element</span></span>|<span data-ttu-id="f23c9-117">描述</span><span class="sxs-lookup"><span data-stu-id="f23c9-117">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](../wcf/system-servicemodel.md)|<span data-ttu-id="f23c9-118">所有工作流程組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="f23c9-118">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f23c9-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f23c9-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="f23c9-120">使用行為來設定與擴充執行階段</span><span class="sxs-lookup"><span data-stu-id="f23c9-120">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
