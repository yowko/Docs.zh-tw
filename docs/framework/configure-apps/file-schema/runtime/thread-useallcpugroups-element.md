---
title: "&lt;Thread_UseAllCpuGroups&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 187e391acf3b80a5ae2dfe795c4a3b397af815ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltthreaduseallcpugroupsgt-element"></a><span data-ttu-id="c5c3d-102">&lt;Thread_UseAllCpuGroups&gt;項目</span><span class="sxs-lookup"><span data-stu-id="c5c3d-102">&lt;Thread_UseAllCpuGroups&gt; Element</span></span>
<span data-ttu-id="c5c3d-103">指定執行階段是否會將 Managed 執行緒分散到所有 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="c5c3d-103">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>  
  
 <span data-ttu-id="c5c3d-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="c5c3d-104">\<configuration></span></span>  
<span data-ttu-id="c5c3d-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="c5c3d-105">\<runtime></span></span>  
<span data-ttu-id="c5c3d-106">< Thread_UseAllCpuGroups ></span><span class="sxs-lookup"><span data-stu-id="c5c3d-106"><Thread_UseAllCpuGroups></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5c3d-107">語法</span><span class="sxs-lookup"><span data-stu-id="c5c3d-107">Syntax</span></span>  
  
```xml
<Thread_UseAllCpuGroups    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5c3d-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c5c3d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c5c3d-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c5c3d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5c3d-110">屬性</span><span class="sxs-lookup"><span data-stu-id="c5c3d-110">Attributes</span></span>  
  
|<span data-ttu-id="c5c3d-111">屬性</span><span class="sxs-lookup"><span data-stu-id="c5c3d-111">Attribute</span></span>|<span data-ttu-id="c5c3d-112">描述</span><span class="sxs-lookup"><span data-stu-id="c5c3d-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="c5c3d-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="c5c3d-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="c5c3d-114">指定執行階段是否會將 Managed 執行緒分散到所有 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="c5c3d-114">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="c5c3d-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="c5c3d-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="c5c3d-116">值</span><span class="sxs-lookup"><span data-stu-id="c5c3d-116">Value</span></span>|<span data-ttu-id="c5c3d-117">說明</span><span class="sxs-lookup"><span data-stu-id="c5c3d-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="c5c3d-118">執行階段不將多個 CPU 群組受管理的執行緒。</span><span class="sxs-lookup"><span data-stu-id="c5c3d-118">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="c5c3d-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="c5c3d-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="c5c3d-120">執行階段受管理將執行緒分配給多個 CPU 群組，如果電腦中有多個 CPU 群組和[ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)項目啟用。</span><span class="sxs-lookup"><span data-stu-id="c5c3d-120">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5c3d-121">子元素</span><span class="sxs-lookup"><span data-stu-id="c5c3d-121">Child Elements</span></span>  
 <span data-ttu-id="c5c3d-122">無。</span><span class="sxs-lookup"><span data-stu-id="c5c3d-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c5c3d-123">父項目</span><span class="sxs-lookup"><span data-stu-id="c5c3d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c5c3d-124">項目</span><span class="sxs-lookup"><span data-stu-id="c5c3d-124">Element</span></span>|<span data-ttu-id="c5c3d-125">描述</span><span class="sxs-lookup"><span data-stu-id="c5c3d-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c5c3d-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="c5c3d-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c5c3d-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="c5c3d-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5c3d-128">備註</span><span class="sxs-lookup"><span data-stu-id="c5c3d-128">Remarks</span></span>  
 <span data-ttu-id="c5c3d-129">當電腦有多個 CPU 群組時，則啟用這個項目會導致執行階段散發 managed 的執行緒的所有 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="c5c3d-129">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="c5c3d-130">若要使用這項功能，您也必須啟用[ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)元素，其會延伸到所有的 CPU 群組記憶體回收並考量所有核心建立和平衡堆積時。</span><span class="sxs-lookup"><span data-stu-id="c5c3d-130">To use this feature, you must also enable the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="c5c3d-131">啟用[ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)項目時，必須啟用[ \<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)項目。</span><span class="sxs-lookup"><span data-stu-id="c5c3d-131">Enabling the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element requires enabling the [\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element.</span></span> <span data-ttu-id="c5c3d-132">如果這些項目未啟用，啟用`<Thread_UseAllCpuGroups>`項目沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="c5c3d-132">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5c3d-133">範例</span><span class="sxs-lookup"><span data-stu-id="c5c3d-133">Example</span></span>  
 <span data-ttu-id="c5c3d-134">下列範例會示範如何啟用支援多個 CPU 的群組。</span><span class="sxs-lookup"><span data-stu-id="c5c3d-134">The following example shows how to enable support for multiple CPU groups.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Thread_UseAllCpuGroups enabled="true"/>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c5c3d-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5c3d-135">See Also</span></span>  
 [<span data-ttu-id="c5c3d-136">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="c5c3d-136">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="c5c3d-137">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="c5c3d-137">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="c5c3d-138">\<GCCpuGroup > 項目</span><span class="sxs-lookup"><span data-stu-id="c5c3d-138">\<GCCpuGroup> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)
