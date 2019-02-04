---
title: <GCCpuGroup> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7998275ae1e80a87354dd5b3a8b0a1aa73b3b987
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674772"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="59ff2-102">\<GCCpuGroup > 項目</span><span class="sxs-lookup"><span data-stu-id="59ff2-102">\<GCCpuGroup> Element</span></span>
<span data-ttu-id="59ff2-103">指定記憶體回收是否支援多個 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="59ff2-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>  
  
 <span data-ttu-id="59ff2-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="59ff2-104">\<configuration></span></span>  
<span data-ttu-id="59ff2-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="59ff2-105">\<runtime></span></span>  
<span data-ttu-id="59ff2-106">\<GCCpuGroup></span><span class="sxs-lookup"><span data-stu-id="59ff2-106">\<GCCpuGroup></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59ff2-107">語法</span><span class="sxs-lookup"><span data-stu-id="59ff2-107">Syntax</span></span>  
  
```xml  
<GCCpuGroup    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59ff2-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="59ff2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="59ff2-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="59ff2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59ff2-110">屬性</span><span class="sxs-lookup"><span data-stu-id="59ff2-110">Attributes</span></span>  
  
|<span data-ttu-id="59ff2-111">屬性</span><span class="sxs-lookup"><span data-stu-id="59ff2-111">Attribute</span></span>|<span data-ttu-id="59ff2-112">描述</span><span class="sxs-lookup"><span data-stu-id="59ff2-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="59ff2-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="59ff2-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="59ff2-114">指定記憶體回收是否支援多個 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="59ff2-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="59ff2-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="59ff2-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="59ff2-116">值</span><span class="sxs-lookup"><span data-stu-id="59ff2-116">Value</span></span>|<span data-ttu-id="59ff2-117">描述</span><span class="sxs-lookup"><span data-stu-id="59ff2-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="59ff2-118">記憶體回收不支援多個 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="59ff2-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="59ff2-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="59ff2-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="59ff2-120">記憶體回收會支援多個 CPU 群組，如果已啟用伺服器記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="59ff2-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59ff2-121">子元素</span><span class="sxs-lookup"><span data-stu-id="59ff2-121">Child Elements</span></span>  
 <span data-ttu-id="59ff2-122">無。</span><span class="sxs-lookup"><span data-stu-id="59ff2-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="59ff2-123">父項目</span><span class="sxs-lookup"><span data-stu-id="59ff2-123">Parent Elements</span></span>  
  
|<span data-ttu-id="59ff2-124">項目</span><span class="sxs-lookup"><span data-stu-id="59ff2-124">Element</span></span>|<span data-ttu-id="59ff2-125">描述</span><span class="sxs-lookup"><span data-stu-id="59ff2-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="59ff2-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="59ff2-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="59ff2-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="59ff2-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59ff2-128">備註</span><span class="sxs-lookup"><span data-stu-id="59ff2-128">Remarks</span></span>  
 <span data-ttu-id="59ff2-129">當電腦具有多個 CPU 群組，而且啟用伺服器記憶體回收之後 (請參閱[ \<Gcserver> >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)項目)，啟用這個項目延伸到所有 CPU 群組的記憶體回收和採用到的所有核心帳戶建立和平衡堆積時。</span><span class="sxs-lookup"><span data-stu-id="59ff2-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59ff2-130">這個項目僅適用於記憶體回收執行緒。</span><span class="sxs-lookup"><span data-stu-id="59ff2-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="59ff2-131">若要啟用使用者執行緒分散到所有 CPU 群組的執行階段，您也必須啟用[< Thread_UseAllCpuGroups >](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)項目。</span><span class="sxs-lookup"><span data-stu-id="59ff2-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59ff2-132">範例</span><span class="sxs-lookup"><span data-stu-id="59ff2-132">Example</span></span>  
 <span data-ttu-id="59ff2-133">下列範例示範如何啟用多個 CPU 群組記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="59ff2-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="59ff2-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59ff2-134">See also</span></span>
- [<span data-ttu-id="59ff2-135">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="59ff2-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="59ff2-136">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="59ff2-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="59ff2-137">若要停用並行記憶體回收</span><span class="sxs-lookup"><span data-stu-id="59ff2-137">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="59ff2-138">工作站和伺服器記憶體回收</span><span class="sxs-lookup"><span data-stu-id="59ff2-138">Workstation and server garbage collection</span></span>](../../../../../docs/standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
