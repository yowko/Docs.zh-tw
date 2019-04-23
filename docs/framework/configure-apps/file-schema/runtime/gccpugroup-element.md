---
title: <GCCpuGroup> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85cfe57f7a3b8cfecfae4c4ae00efaea464e6120
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59090338"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="7163e-102">\<GCCpuGroup > 項目</span><span class="sxs-lookup"><span data-stu-id="7163e-102">\<GCCpuGroup> Element</span></span>
<span data-ttu-id="7163e-103">指定記憶體回收是否支援多個 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="7163e-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>  
  
 <span data-ttu-id="7163e-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="7163e-104">\<configuration></span></span>  
<span data-ttu-id="7163e-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="7163e-105">\<runtime></span></span>  
<span data-ttu-id="7163e-106">\<GCCpuGroup></span><span class="sxs-lookup"><span data-stu-id="7163e-106">\<GCCpuGroup></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7163e-107">語法</span><span class="sxs-lookup"><span data-stu-id="7163e-107">Syntax</span></span>  
  
```xml  
<GCCpuGroup    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7163e-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7163e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7163e-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7163e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7163e-110">屬性</span><span class="sxs-lookup"><span data-stu-id="7163e-110">Attributes</span></span>  
  
|<span data-ttu-id="7163e-111">屬性</span><span class="sxs-lookup"><span data-stu-id="7163e-111">Attribute</span></span>|<span data-ttu-id="7163e-112">描述</span><span class="sxs-lookup"><span data-stu-id="7163e-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="7163e-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="7163e-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="7163e-114">指定記憶體回收是否支援多個 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="7163e-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="7163e-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="7163e-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="7163e-116">值</span><span class="sxs-lookup"><span data-stu-id="7163e-116">Value</span></span>|<span data-ttu-id="7163e-117">描述</span><span class="sxs-lookup"><span data-stu-id="7163e-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="7163e-118">記憶體回收不支援多個 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="7163e-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="7163e-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="7163e-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="7163e-120">記憶體回收會支援多個 CPU 群組，如果已啟用伺服器記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="7163e-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7163e-121">子元素</span><span class="sxs-lookup"><span data-stu-id="7163e-121">Child Elements</span></span>  
 <span data-ttu-id="7163e-122">無。</span><span class="sxs-lookup"><span data-stu-id="7163e-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7163e-123">父項目</span><span class="sxs-lookup"><span data-stu-id="7163e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7163e-124">項目</span><span class="sxs-lookup"><span data-stu-id="7163e-124">Element</span></span>|<span data-ttu-id="7163e-125">描述</span><span class="sxs-lookup"><span data-stu-id="7163e-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7163e-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="7163e-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="7163e-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="7163e-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7163e-128">備註</span><span class="sxs-lookup"><span data-stu-id="7163e-128">Remarks</span></span>  
 <span data-ttu-id="7163e-129">當電腦具有多個 CPU 群組，而且啟用伺服器記憶體回收之後 (請參閱[ \<Gcserver> >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)項目)，啟用這個項目延伸到所有 CPU 群組的記憶體回收和採用到的所有核心帳戶建立和平衡堆積時。</span><span class="sxs-lookup"><span data-stu-id="7163e-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7163e-130">這個項目僅適用於記憶體回收執行緒。</span><span class="sxs-lookup"><span data-stu-id="7163e-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="7163e-131">若要啟用使用者執行緒分散到所有 CPU 群組的執行階段，您也必須啟用[< Thread_UseAllCpuGroups >](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)項目。</span><span class="sxs-lookup"><span data-stu-id="7163e-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7163e-132">範例</span><span class="sxs-lookup"><span data-stu-id="7163e-132">Example</span></span>  
 <span data-ttu-id="7163e-133">下列範例示範如何啟用多個 CPU 群組記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="7163e-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7163e-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7163e-134">See also</span></span>

- [<span data-ttu-id="7163e-135">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="7163e-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="7163e-136">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="7163e-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="7163e-137">若要停用並行記憶體回收</span><span class="sxs-lookup"><span data-stu-id="7163e-137">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="7163e-138">工作站和伺服器記憶體回收</span><span class="sxs-lookup"><span data-stu-id="7163e-138">Workstation and server garbage collection</span></span>](../../../../../docs/standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
