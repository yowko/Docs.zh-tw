---
title: <workflowControlEndpoint>
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: a9c16d1036a8177120cd152d4ac211ad084d588e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150380"
---
# <a name="workflowcontrolendpoint"></a><span data-ttu-id="ad79c-101">\<workflowControlEndpoint></span><span class="sxs-lookup"><span data-stu-id="ad79c-101">\<workflowControlEndpoint></span></span>
<span data-ttu-id="ad79c-102">這個組態項目會定義一個標準端點，用於控制工作流程執行個體的執行 (建立、執行、終止等)。</span><span class="sxs-lookup"><span data-stu-id="ad79c-102">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="ad79c-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ad79c-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="ad79c-104">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="ad79c-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad79c-105">語法</span><span class="sxs-lookup"><span data-stu-id="ad79c-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad79c-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ad79c-106">Attributes and Elements</span></span>  
 <span data-ttu-id="ad79c-107">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ad79c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad79c-108">屬性</span><span class="sxs-lookup"><span data-stu-id="ad79c-108">Attributes</span></span>  
  
|<span data-ttu-id="ad79c-109">屬性</span><span class="sxs-lookup"><span data-stu-id="ad79c-109">Attribute</span></span>|<span data-ttu-id="ad79c-110">描述</span><span class="sxs-lookup"><span data-stu-id="ad79c-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ad79c-111">名稱</span><span class="sxs-lookup"><span data-stu-id="ad79c-111">name</span></span>|<span data-ttu-id="ad79c-112">字串，這個字串會指定標準端點之組態的名稱。</span><span class="sxs-lookup"><span data-stu-id="ad79c-112">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="ad79c-113">這個名稱用於服務端點的 `endpointConfiguration` 屬性中，可將標準端點連結至其組態。</span><span class="sxs-lookup"><span data-stu-id="ad79c-113">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ad79c-114">子元素</span><span class="sxs-lookup"><span data-stu-id="ad79c-114">Child Elements</span></span>  
 <span data-ttu-id="ad79c-115">無。</span><span class="sxs-lookup"><span data-stu-id="ad79c-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ad79c-116">父項目</span><span class="sxs-lookup"><span data-stu-id="ad79c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="ad79c-117">項目</span><span class="sxs-lookup"><span data-stu-id="ad79c-117">Element</span></span>|<span data-ttu-id="ad79c-118">描述</span><span class="sxs-lookup"><span data-stu-id="ad79c-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ad79c-119">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="ad79c-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="ad79c-120">標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。</span><span class="sxs-lookup"><span data-stu-id="ad79c-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ad79c-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad79c-121">See also</span></span>

- <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
