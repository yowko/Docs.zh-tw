---
title: "&lt;GCCpuGroup&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dcead28d7bf66e0626a0108015add4f22c5fa476
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="ltgccpugroupgt-element"></a><span data-ttu-id="a2a2d-102">&lt;GCCpuGroup&gt;項目</span><span class="sxs-lookup"><span data-stu-id="a2a2d-102">&lt;GCCpuGroup&gt; Element</span></span>
<span data-ttu-id="a2a2d-103">指定記憶體回收是否支援多個 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="a2a2d-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>  
  
 <span data-ttu-id="a2a2d-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="a2a2d-104">\<configuration></span></span>  
<span data-ttu-id="a2a2d-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="a2a2d-105">\<runtime></span></span>  
<span data-ttu-id="a2a2d-106">\<GCCpuGroup></span><span class="sxs-lookup"><span data-stu-id="a2a2d-106">\<GCCpuGroup></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2a2d-107">語法</span><span class="sxs-lookup"><span data-stu-id="a2a2d-107">Syntax</span></span>  
  
```xml  
<GCCpuGroup    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a2a2d-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a2a2d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a2a2d-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a2a2d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a2a2d-110">屬性</span><span class="sxs-lookup"><span data-stu-id="a2a2d-110">Attributes</span></span>  
  
|<span data-ttu-id="a2a2d-111">屬性</span><span class="sxs-lookup"><span data-stu-id="a2a2d-111">Attribute</span></span>|<span data-ttu-id="a2a2d-112">描述</span><span class="sxs-lookup"><span data-stu-id="a2a2d-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="a2a2d-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="a2a2d-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="a2a2d-114">指定記憶體回收是否支援多個 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="a2a2d-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="a2a2d-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="a2a2d-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="a2a2d-116">值</span><span class="sxs-lookup"><span data-stu-id="a2a2d-116">Value</span></span>|<span data-ttu-id="a2a2d-117">描述</span><span class="sxs-lookup"><span data-stu-id="a2a2d-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="a2a2d-118">記憶體回收集合不支援多個 CPU 的群組。</span><span class="sxs-lookup"><span data-stu-id="a2a2d-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="a2a2d-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="a2a2d-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="a2a2d-120">記憶體回收支援多個 CPU 群組，如果已啟用伺服器記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="a2a2d-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a2a2d-121">子元素</span><span class="sxs-lookup"><span data-stu-id="a2a2d-121">Child Elements</span></span>  
 <span data-ttu-id="a2a2d-122">無。</span><span class="sxs-lookup"><span data-stu-id="a2a2d-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a2a2d-123">父項目</span><span class="sxs-lookup"><span data-stu-id="a2a2d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="a2a2d-124">項目</span><span class="sxs-lookup"><span data-stu-id="a2a2d-124">Element</span></span>|<span data-ttu-id="a2a2d-125">描述</span><span class="sxs-lookup"><span data-stu-id="a2a2d-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a2a2d-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="a2a2d-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a2a2d-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="a2a2d-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2a2d-128">備註</span><span class="sxs-lookup"><span data-stu-id="a2a2d-128">Remarks</span></span>  
 <span data-ttu-id="a2a2d-129">當電腦有多個 CPU 群組，且已啟用伺服器記憶體回收 (請參閱[ \<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)項目)，啟用這個項目延伸的所有 CPU 群組記憶體回收和採用到的所有核心若要建立並平衡堆積的帳戶。</span><span class="sxs-lookup"><span data-stu-id="a2a2d-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a2a2d-130">這個項目只適用於記憶體回收執行緒。</span><span class="sxs-lookup"><span data-stu-id="a2a2d-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="a2a2d-131">若要讓 runtime 能夠將使用者執行緒分散到所有的 CPU 群組，您必須同時啟用[< Thread_UseAllCpuGroups >](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)項目。</span><span class="sxs-lookup"><span data-stu-id="a2a2d-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2a2d-132">範例</span><span class="sxs-lookup"><span data-stu-id="a2a2d-132">Example</span></span>  
 <span data-ttu-id="a2a2d-133">下列範例會示範如何啟用多個 CPU 群組記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="a2a2d-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a2a2d-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="a2a2d-134">See Also</span></span>  
 [<span data-ttu-id="a2a2d-135">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="a2a2d-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="a2a2d-136">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="a2a2d-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="a2a2d-137">如何： 停用並行記憶體回收</span><span class="sxs-lookup"><span data-stu-id="a2a2d-137">How to: Disable Concurrent Garbage Collection</span></span>](http://msdn.microsoft.com/library/ba2c6c67-5778-497c-9fac-5f793b5500c7)  
 [<span data-ttu-id="a2a2d-138">工作站和伺服器記憶體回收</span><span class="sxs-lookup"><span data-stu-id="a2a2d-138">Workstation and server garbage collection</span></span>](../../../../../docs/standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
