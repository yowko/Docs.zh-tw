---
title: <workflowControlEndpoint>
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: 670c1573fe4378a18c19d0a58fe58241745725bd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854791"
---
# \<workflowControlEndpoint>
<span data-ttu-id="aab63-101">這個組態項目會定義一個標準端點，用於控制工作流程執行個體的執行 (建立、執行、終止等)。</span><span class="sxs-lookup"><span data-stu-id="aab63-101">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowControlEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="aab63-102">語法</span><span class="sxs-lookup"><span data-stu-id="aab63-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aab63-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="aab63-103">Attributes and Elements</span></span>  
 <span data-ttu-id="aab63-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="aab63-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aab63-105">屬性</span><span class="sxs-lookup"><span data-stu-id="aab63-105">Attributes</span></span>  
  
|<span data-ttu-id="aab63-106">屬性</span><span class="sxs-lookup"><span data-stu-id="aab63-106">Attribute</span></span>|<span data-ttu-id="aab63-107">描述</span><span class="sxs-lookup"><span data-stu-id="aab63-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aab63-108">NAME</span><span class="sxs-lookup"><span data-stu-id="aab63-108">name</span></span>|<span data-ttu-id="aab63-109">字串，這個字串會指定標準端點之組態的名稱。</span><span class="sxs-lookup"><span data-stu-id="aab63-109">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="aab63-110">這個名稱用於服務端點的 `endpointConfiguration` 屬性中，可將標準端點連結至其組態。</span><span class="sxs-lookup"><span data-stu-id="aab63-110">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aab63-111">子元素</span><span class="sxs-lookup"><span data-stu-id="aab63-111">Child Elements</span></span>  
 <span data-ttu-id="aab63-112">無。</span><span class="sxs-lookup"><span data-stu-id="aab63-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aab63-113">父項目</span><span class="sxs-lookup"><span data-stu-id="aab63-113">Parent Elements</span></span>  
  
|<span data-ttu-id="aab63-114">元素</span><span class="sxs-lookup"><span data-stu-id="aab63-114">Element</span></span>|<span data-ttu-id="aab63-115">描述</span><span class="sxs-lookup"><span data-stu-id="aab63-115">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="aab63-116">標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。</span><span class="sxs-lookup"><span data-stu-id="aab63-116">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aab63-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aab63-117">See also</span></span>

- <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
