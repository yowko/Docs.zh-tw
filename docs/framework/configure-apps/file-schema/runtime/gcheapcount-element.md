---
title: GCHeapCount 元素
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 3d6cac4185af182758cb82e6bfd9d96ed24869b4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283076"
---
# <a name="gcheapcount-element"></a><span data-ttu-id="481ff-102">\<GCHeapCount > 元素</span><span class="sxs-lookup"><span data-stu-id="481ff-102">\<GCHeapCount> element</span></span>

<span data-ttu-id="481ff-103">指定要用於伺服器垃圾收集的堆積/執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="481ff-103">Specifies the number of heaps/threads to use for server garbage collection.</span></span>

<span data-ttu-id="481ff-104">\<設定 > </span><span class="sxs-lookup"><span data-stu-id="481ff-104">\<configuration></span></span>\
<span data-ttu-id="481ff-105">&nbsp;&nbsp;\<執行時間 > </span><span class="sxs-lookup"><span data-stu-id="481ff-105">&nbsp;&nbsp;\<runtime></span></span>\
<span data-ttu-id="481ff-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapCount ></span><span class="sxs-lookup"><span data-stu-id="481ff-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapCount></span></span>

## <a name="syntax"></a><span data-ttu-id="481ff-107">語法</span><span class="sxs-lookup"><span data-stu-id="481ff-107">Syntax</span></span>

```xml
<GCHeapCount
   enabled="nn"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="481ff-108">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="481ff-108">Attributes and elements</span></span>

<span data-ttu-id="481ff-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="481ff-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="481ff-110">屬性</span><span class="sxs-lookup"><span data-stu-id="481ff-110">Attributes</span></span>

|<span data-ttu-id="481ff-111">屬性</span><span class="sxs-lookup"><span data-stu-id="481ff-111">Attribute</span></span>|<span data-ttu-id="481ff-112">描述</span><span class="sxs-lookup"><span data-stu-id="481ff-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="481ff-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="481ff-113">Required attribute.</span></span><br /><br /><span data-ttu-id="481ff-114">指定要用於伺服器垃圾收集的堆積數目。</span><span class="sxs-lookup"><span data-stu-id="481ff-114">Specifies the number of heaps to use for server garbage collection.</span></span> <span data-ttu-id="481ff-115">實際的堆積數目是您指定之堆積數目的最小值，以及您的進程允許使用的處理器數目。</span><span class="sxs-lookup"><span data-stu-id="481ff-115">The actual number of heaps is the minimum of the number of heaps you specify and the number of processors your process is allowed to use.</span></span> |

#### <a name="enabled-attribute"></a><span data-ttu-id="481ff-116">enabled 屬性</span><span class="sxs-lookup"><span data-stu-id="481ff-116">enabled attribute</span></span>

|<span data-ttu-id="481ff-117">值</span><span class="sxs-lookup"><span data-stu-id="481ff-117">Value</span></span>|<span data-ttu-id="481ff-118">描述</span><span class="sxs-lookup"><span data-stu-id="481ff-118">Description</span></span>|
|-----------|-----------------|
|`nn`|<span data-ttu-id="481ff-119">用於伺服器 GC 的堆積數目。</span><span class="sxs-lookup"><span data-stu-id="481ff-119">The number of heaps to use for server GC.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="481ff-120">子元素</span><span class="sxs-lookup"><span data-stu-id="481ff-120">Child elements</span></span>

<span data-ttu-id="481ff-121">None。</span><span class="sxs-lookup"><span data-stu-id="481ff-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="481ff-122">父元素</span><span class="sxs-lookup"><span data-stu-id="481ff-122">Parent elements</span></span>

|<span data-ttu-id="481ff-123">項目</span><span class="sxs-lookup"><span data-stu-id="481ff-123">Element</span></span>|<span data-ttu-id="481ff-124">描述</span><span class="sxs-lookup"><span data-stu-id="481ff-124">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="481ff-125">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="481ff-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="481ff-126">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="481ff-126">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="481ff-127">備註</span><span class="sxs-lookup"><span data-stu-id="481ff-127">Remarks</span></span>

<span data-ttu-id="481ff-128">根據預設，伺服器 GC 執行緒會相似化為其各自的 CPU，讓每個處理器都有一個 GC 堆積、一個伺服器 GC 執行緒，以及一個背景伺服器 GC 執行緒。</span><span class="sxs-lookup"><span data-stu-id="481ff-128">By default, server GC threads are hard-affinitized with their respective CPU so that there is one GC heap, one server GC thread, and one background server GC thread for each processor.</span></span> <span data-ttu-id="481ff-129">從 .NET Framework 4.6.2 開始，您可以使用**GCHeapCount**元素來限制應用程式用於伺服器 GC 的堆積數目。</span><span class="sxs-lookup"><span data-stu-id="481ff-129">Starting with .NET Framework 4.6.2, you can use the **GCHeapCount** element to limit the number of heaps used by your application for server GC.</span></span> <span data-ttu-id="481ff-130">限制用於伺服器 GC 的堆積數目，對於執行多個伺服器應用程式實例的系統特別有用。</span><span class="sxs-lookup"><span data-stu-id="481ff-130">Limiting the number of heaps used for server GC is particularly useful for systems that run multiple instances of a server application.</span></span>

<span data-ttu-id="481ff-131">**GCHeapCount**通常會與兩個其他旗標搭配使用：</span><span class="sxs-lookup"><span data-stu-id="481ff-131">**GCHeapCount** is typically used along with two other flags:</span></span>

- <span data-ttu-id="481ff-132">[GCNoAffinitize](gcnoaffinitize-element.md)，控制是否使用 cpu 相似化為伺服器 GC 執行緒/堆積。</span><span class="sxs-lookup"><span data-stu-id="481ff-132">[GCNoAffinitize](gcnoaffinitize-element.md), which controls whether server GC threads/heaps are affinitized with CPUs.</span></span>

- <span data-ttu-id="481ff-133">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md)，控制 GC 執行緒/堆積與 cpu 的親和性。</span><span class="sxs-lookup"><span data-stu-id="481ff-133">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), which controls the affinity of GC threads/heaps with CPUs.</span></span>

<span data-ttu-id="481ff-134">如果已設定**GCHeapCount** ，且**GCNoAffinitize**已停用（其預設值），則*nn* GC threads/堆積和第一個*nn*個處理器之間會有相似性。</span><span class="sxs-lookup"><span data-stu-id="481ff-134">If **GCHeapCount** is set and **GCNoAffinitize** is disabled (its default setting), there is an affinity between the *nn* GC threads/heaps and the first *nn* processors.</span></span> <span data-ttu-id="481ff-135">您可以使用**GCHeapAffinitizeMask**元素來指定進程的伺服器 GC 堆積所使用的處理器。</span><span class="sxs-lookup"><span data-stu-id="481ff-135">You can use the **GCHeapAffinitizeMask** element to specify which processors are used by the process's server GC heaps.</span></span> <span data-ttu-id="481ff-136">否則，如果有多個伺服器進程在系統上執行，其處理器使用量將會重迭。</span><span class="sxs-lookup"><span data-stu-id="481ff-136">Otherwise, if multiple server processes are running on a system, their processor usage will overlap.</span></span>

<span data-ttu-id="481ff-137">如果已設定**GCHeapCount**並啟用**GCNoAffinitize** ，垃圾收集行程會限制用於伺服器 GC 的處理器數目，但不會將相似化為 GC 堆積和處理器。</span><span class="sxs-lookup"><span data-stu-id="481ff-137">If **GCHeapCount** is set and **GCNoAffinitize** is enabled, the garbage collector limits the number of processors used for server GC but does not affinitize GC heaps and processors.</span></span>

## <a name="example"></a><span data-ttu-id="481ff-138">範例</span><span class="sxs-lookup"><span data-stu-id="481ff-138">Example</span></span>

<span data-ttu-id="481ff-139">下列範例指出應用程式使用具有10個堆積/執行緒的伺服器 GC。</span><span class="sxs-lookup"><span data-stu-id="481ff-139">The following example indicates that an application uses server GC with 10 heaps/threads.</span></span> <span data-ttu-id="481ff-140">由於您不想讓這些堆積與系統上執行的其他應用程式的堆積重迭，因此，您可以使用**GCHeapAffinitizeMask**來指定進程應該使用 cpu 0 到9。</span><span class="sxs-lookup"><span data-stu-id="481ff-140">Since you don't want those heaps to overlap with heaps from other applications running on the system, you use the **GCHeapAffinitizeMask** to specify that the process should use CPUs 0 through 9.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

<span data-ttu-id="481ff-141">下列範例不會將相似化為伺服器 GC 執行緒，而且會將 GC 堆積/執行緒的數目限制為10。</span><span class="sxs-lookup"><span data-stu-id="481ff-141">The following example does not affinitize server GC threads and limits the number of GC heaps/threads to 10.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="481ff-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="481ff-142">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="481ff-143">GCNoAffinitize 元素</span><span class="sxs-lookup"><span data-stu-id="481ff-143">GCNoAffinitize element</span></span>](gcnoaffinitize-element.md)
- [<span data-ttu-id="481ff-144">GCHeapAffinitizeMask 元素</span><span class="sxs-lookup"><span data-stu-id="481ff-144">GCHeapAffinitizeMask element</span></span>](gcheapaffinitizemask-element.md)
- [<span data-ttu-id="481ff-145">記憶體回收的基本概念</span><span class="sxs-lookup"><span data-stu-id="481ff-145">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="481ff-146">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="481ff-146">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="481ff-147">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="481ff-147">Configuration File Schema</span></span>](../index.md)
