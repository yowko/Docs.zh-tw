---
title: '&lt;workflowControlEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 443d23a3b0f73d2fd0a08112d51f745d1e1874fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltworkflowcontrolendpointgt"></a><span data-ttu-id="73095-102">&lt;workflowControlEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="73095-102">&lt;workflowControlEndpoint&gt;</span></span>
<span data-ttu-id="73095-103">這個組態項目會定義一個標準端點，用於控制工作流程執行個體的執行 (建立、執行、終止等)。</span><span class="sxs-lookup"><span data-stu-id="73095-103">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="73095-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="73095-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="73095-105">\<Kind ></span><span class="sxs-lookup"><span data-stu-id="73095-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73095-106">語法</span><span class="sxs-lookup"><span data-stu-id="73095-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73095-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="73095-107">Attributes and Elements</span></span>  
 <span data-ttu-id="73095-108">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="73095-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73095-109">屬性</span><span class="sxs-lookup"><span data-stu-id="73095-109">Attributes</span></span>  
  
|<span data-ttu-id="73095-110">屬性</span><span class="sxs-lookup"><span data-stu-id="73095-110">Attribute</span></span>|<span data-ttu-id="73095-111">描述</span><span class="sxs-lookup"><span data-stu-id="73095-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="73095-112">name</span><span class="sxs-lookup"><span data-stu-id="73095-112">name</span></span>|<span data-ttu-id="73095-113">字串，這個字串會指定標準端點之組態的名稱。</span><span class="sxs-lookup"><span data-stu-id="73095-113">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="73095-114">這個名稱用於服務端點的 `endpointConfiguration` 屬性中，可將標準端點連結至其組態。</span><span class="sxs-lookup"><span data-stu-id="73095-114">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73095-115">子元素</span><span class="sxs-lookup"><span data-stu-id="73095-115">Child Elements</span></span>  
 <span data-ttu-id="73095-116">無。</span><span class="sxs-lookup"><span data-stu-id="73095-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="73095-117">父項目</span><span class="sxs-lookup"><span data-stu-id="73095-117">Parent Elements</span></span>  
  
|<span data-ttu-id="73095-118">項目</span><span class="sxs-lookup"><span data-stu-id="73095-118">Element</span></span>|<span data-ttu-id="73095-119">描述</span><span class="sxs-lookup"><span data-stu-id="73095-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73095-120">\<Kind ></span><span class="sxs-lookup"><span data-stu-id="73095-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="73095-121">標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。</span><span class="sxs-lookup"><span data-stu-id="73095-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="73095-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="73095-122">See Also</span></span>  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
