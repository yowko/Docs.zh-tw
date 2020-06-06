---
title: <bufferReceive>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: be5173ea43c6f7fca7180a311885a26c889b12db
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398840"
---
# \<bufferReceive>
<span data-ttu-id="02bda-101">讓服務可以使用緩衝接收處理的服務行為，該處理可讓工作流程服務處理失序的訊息。</span><span class="sxs-lookup"><span data-stu-id="02bda-101">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bufferReceive>**  
  
## <a name="syntax"></a><span data-ttu-id="02bda-102">語法</span><span class="sxs-lookup"><span data-stu-id="02bda-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02bda-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="02bda-103">Attributes and Elements</span></span>  
 <span data-ttu-id="02bda-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="02bda-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02bda-105">屬性</span><span class="sxs-lookup"><span data-stu-id="02bda-105">Attributes</span></span>  
  
|<span data-ttu-id="02bda-106">屬性</span><span class="sxs-lookup"><span data-stu-id="02bda-106">Attribute</span></span>|<span data-ttu-id="02bda-107">描述</span><span class="sxs-lookup"><span data-stu-id="02bda-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="02bda-108">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="02bda-108">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="02bda-109">整數，可指定每個通道允許的暫止訊息數目上限。</span><span class="sxs-lookup"><span data-stu-id="02bda-109">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="02bda-110">預設值為 512。</span><span class="sxs-lookup"><span data-stu-id="02bda-110">The default value is 512.</span></span> <span data-ttu-id="02bda-111">這個屬性會限制工作流程服務所能接收的失序訊息數目。</span><span class="sxs-lookup"><span data-stu-id="02bda-111">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="02bda-112">子元素</span><span class="sxs-lookup"><span data-stu-id="02bda-112">Child Elements</span></span>  
 <span data-ttu-id="02bda-113">無。</span><span class="sxs-lookup"><span data-stu-id="02bda-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="02bda-114">父項目</span><span class="sxs-lookup"><span data-stu-id="02bda-114">Parent Elements</span></span>  
  
|<span data-ttu-id="02bda-115">元素</span><span class="sxs-lookup"><span data-stu-id="02bda-115">Element</span></span>|<span data-ttu-id="02bda-116">描述</span><span class="sxs-lookup"><span data-stu-id="02bda-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02bda-117">\<behavior>的\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="02bda-117">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="02bda-118">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="02bda-118">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="02bda-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02bda-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.BufferedReceiveServiceBehavior>
- <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
