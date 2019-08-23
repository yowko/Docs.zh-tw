---
title: <workflowControlEndpoint>
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: 2c9774217b835acdb9ebf7374b964d838497fc9f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915327"
---
# <a name="workflowcontrolendpoint"></a><span data-ttu-id="4e4a6-101">\<workflowControlEndpoint></span><span class="sxs-lookup"><span data-stu-id="4e4a6-101">\<workflowControlEndpoint></span></span>
<span data-ttu-id="4e4a6-102">這個組態項目會定義一個標準端點，用於控制工作流程執行個體的執行 (建立、執行、終止等)。</span><span class="sxs-lookup"><span data-stu-id="4e4a6-102">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="4e4a6-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4e4a6-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="4e4a6-104">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="4e4a6-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e4a6-105">語法</span><span class="sxs-lookup"><span data-stu-id="4e4a6-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4e4a6-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4e4a6-106">Attributes and Elements</span></span>  
 <span data-ttu-id="4e4a6-107">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="4e4a6-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4e4a6-108">屬性</span><span class="sxs-lookup"><span data-stu-id="4e4a6-108">Attributes</span></span>  
  
|<span data-ttu-id="4e4a6-109">屬性</span><span class="sxs-lookup"><span data-stu-id="4e4a6-109">Attribute</span></span>|<span data-ttu-id="4e4a6-110">說明</span><span class="sxs-lookup"><span data-stu-id="4e4a6-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4e4a6-111">NAME</span><span class="sxs-lookup"><span data-stu-id="4e4a6-111">name</span></span>|<span data-ttu-id="4e4a6-112">字串，這個字串會指定標準端點之組態的名稱。</span><span class="sxs-lookup"><span data-stu-id="4e4a6-112">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="4e4a6-113">這個名稱用於服務端點的 `endpointConfiguration` 屬性中，可將標準端點連結至其組態。</span><span class="sxs-lookup"><span data-stu-id="4e4a6-113">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4e4a6-114">子元素</span><span class="sxs-lookup"><span data-stu-id="4e4a6-114">Child Elements</span></span>  
 <span data-ttu-id="4e4a6-115">無。</span><span class="sxs-lookup"><span data-stu-id="4e4a6-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4e4a6-116">父項目</span><span class="sxs-lookup"><span data-stu-id="4e4a6-116">Parent Elements</span></span>  
  
|<span data-ttu-id="4e4a6-117">項目</span><span class="sxs-lookup"><span data-stu-id="4e4a6-117">Element</span></span>|<span data-ttu-id="4e4a6-118">說明</span><span class="sxs-lookup"><span data-stu-id="4e4a6-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4e4a6-119">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="4e4a6-119">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="4e4a6-120">標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。</span><span class="sxs-lookup"><span data-stu-id="4e4a6-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4e4a6-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e4a6-121">See also</span></span>

- <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
