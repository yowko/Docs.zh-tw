---
title: <workflowControlEndpoint>
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: 670c1573fe4378a18c19d0a58fe58241745725bd
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854791"
---
# <a name="workflowcontrolendpoint"></a><span data-ttu-id="5eb3b-101">\<workflowControlEndpoint></span><span class="sxs-lookup"><span data-stu-id="5eb3b-101">\<workflowControlEndpoint></span></span>
<span data-ttu-id="5eb3b-102">這個組態項目會定義一個標準端點，用於控制工作流程執行個體的執行 (建立、執行、終止等)。</span><span class="sxs-lookup"><span data-stu-id="5eb3b-102">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="5eb3b-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5eb3b-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5eb3b-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5eb3b-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5eb3b-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="5eb3b-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="5eb3b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowControlEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="5eb3b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowControlEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5eb3b-107">語法</span><span class="sxs-lookup"><span data-stu-id="5eb3b-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5eb3b-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5eb3b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5eb3b-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5eb3b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5eb3b-110">屬性</span><span class="sxs-lookup"><span data-stu-id="5eb3b-110">Attributes</span></span>  
  
|<span data-ttu-id="5eb3b-111">屬性</span><span class="sxs-lookup"><span data-stu-id="5eb3b-111">Attribute</span></span>|<span data-ttu-id="5eb3b-112">說明</span><span class="sxs-lookup"><span data-stu-id="5eb3b-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5eb3b-113">NAME</span><span class="sxs-lookup"><span data-stu-id="5eb3b-113">name</span></span>|<span data-ttu-id="5eb3b-114">字串，這個字串會指定標準端點之組態的名稱。</span><span class="sxs-lookup"><span data-stu-id="5eb3b-114">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="5eb3b-115">這個名稱用於服務端點的 `endpointConfiguration` 屬性中，可將標準端點連結至其組態。</span><span class="sxs-lookup"><span data-stu-id="5eb3b-115">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5eb3b-116">子元素</span><span class="sxs-lookup"><span data-stu-id="5eb3b-116">Child Elements</span></span>  
 <span data-ttu-id="5eb3b-117">無。</span><span class="sxs-lookup"><span data-stu-id="5eb3b-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5eb3b-118">父項目</span><span class="sxs-lookup"><span data-stu-id="5eb3b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="5eb3b-119">項目</span><span class="sxs-lookup"><span data-stu-id="5eb3b-119">Element</span></span>|<span data-ttu-id="5eb3b-120">說明</span><span class="sxs-lookup"><span data-stu-id="5eb3b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5eb3b-121">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="5eb3b-121">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="5eb3b-122">標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。</span><span class="sxs-lookup"><span data-stu-id="5eb3b-122">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5eb3b-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5eb3b-123">See also</span></span>

- <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
