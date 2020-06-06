---
title: gcServer 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
ms.openlocfilehash: 8eab5e36bab90510aff4f1a3e15328197ac59ed7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73968939"
---
# <a name="gcserver-element"></a><span data-ttu-id="62ac1-102">\<gcServer> 項目</span><span class="sxs-lookup"><span data-stu-id="62ac1-102">\<gcServer> element</span></span>

<span data-ttu-id="62ac1-103">指定 Common Language Runtime 是否執行伺服器記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="62ac1-103">Specifies whether the common language runtime runs server garbage collection.</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gcServer>

## <a name="syntax"></a><span data-ttu-id="62ac1-104">語法</span><span class="sxs-lookup"><span data-stu-id="62ac1-104">Syntax</span></span>

```xml
<gcServer
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="62ac1-105">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="62ac1-105">Attributes and elements</span></span>

<span data-ttu-id="62ac1-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="62ac1-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="62ac1-107">屬性</span><span class="sxs-lookup"><span data-stu-id="62ac1-107">Attributes</span></span>

|<span data-ttu-id="62ac1-108">屬性</span><span class="sxs-lookup"><span data-stu-id="62ac1-108">Attribute</span></span>|<span data-ttu-id="62ac1-109">描述</span><span class="sxs-lookup"><span data-stu-id="62ac1-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="62ac1-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="62ac1-110">Required attribute.</span></span><br /><br /><span data-ttu-id="62ac1-111">指定執行階段是否執行伺服器記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="62ac1-111">Specifies whether the runtime runs server garbage collection.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="62ac1-112">enabled 屬性</span><span class="sxs-lookup"><span data-stu-id="62ac1-112">enabled attribute</span></span>

|<span data-ttu-id="62ac1-113">值</span><span class="sxs-lookup"><span data-stu-id="62ac1-113">Value</span></span>|<span data-ttu-id="62ac1-114">描述</span><span class="sxs-lookup"><span data-stu-id="62ac1-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="62ac1-115">不執行伺服器記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="62ac1-115">Does not run server garbage collection.</span></span> <span data-ttu-id="62ac1-116">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="62ac1-116">This is the default.</span></span>|
|`true`|<span data-ttu-id="62ac1-117">執行伺服器記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="62ac1-117">Runs server garbage collection.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="62ac1-118">子元素</span><span class="sxs-lookup"><span data-stu-id="62ac1-118">Child elements</span></span>

<span data-ttu-id="62ac1-119">無。</span><span class="sxs-lookup"><span data-stu-id="62ac1-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="62ac1-120">父元素</span><span class="sxs-lookup"><span data-stu-id="62ac1-120">Parent elements</span></span>

|<span data-ttu-id="62ac1-121">元素</span><span class="sxs-lookup"><span data-stu-id="62ac1-121">Element</span></span>|<span data-ttu-id="62ac1-122">描述</span><span class="sxs-lookup"><span data-stu-id="62ac1-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="62ac1-123">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="62ac1-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="62ac1-124">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="62ac1-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="62ac1-125">備註</span><span class="sxs-lookup"><span data-stu-id="62ac1-125">Remarks</span></span>

<span data-ttu-id="62ac1-126">Common Language Runtime (CLR) 支援兩種類型的記憶體回收：工作站記憶體回收 (可用於所有系統)，以及伺服器記憶體回收 (可用於多處理器系統)。</span><span class="sxs-lookup"><span data-stu-id="62ac1-126">The common language runtime (CLR) supports two types of garbage collection: workstation garbage collection, which is available on all systems, and server garbage collection, which is available on multiprocessor systems.</span></span> <span data-ttu-id="62ac1-127">使用**gcServer**元素來控制 CLR 執行的垃圾收集類型。</span><span class="sxs-lookup"><span data-stu-id="62ac1-127">Use the **gcServer** element to control the type of garbage collection the CLR performs.</span></span> <span data-ttu-id="62ac1-128">使用 <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> 屬性來決定是否啟用伺服器記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="62ac1-128">Use the <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> property to determine if server garbage collection is enabled.</span></span>

<span data-ttu-id="62ac1-129">針對單一處理器電腦，預設的工作站記憶體回收應該是最快的選項。</span><span class="sxs-lookup"><span data-stu-id="62ac1-129">For single-processor computers, the default workstation garbage collection should be the fastest option.</span></span> <span data-ttu-id="62ac1-130">無論是工作站或伺服器，都可以用於兩個處理器的電腦。</span><span class="sxs-lookup"><span data-stu-id="62ac1-130">Either workstation or server can be used for two-processor computers.</span></span> <span data-ttu-id="62ac1-131">針對兩個以上的處理器，伺服器記憶體回收應該是最快的選項。</span><span class="sxs-lookup"><span data-stu-id="62ac1-131">Server garbage collection should be the fastest option for more than two processors.</span></span> <span data-ttu-id="62ac1-132">最常見的是多處理器伺服器系統會停用伺服器 GC，而當伺服器應用程式的許多實例都在同一部電腦上執行時，會改為使用工作站 GC。</span><span class="sxs-lookup"><span data-stu-id="62ac1-132">Most commonly, multiprocessor server systems disable server GC and use workstation GC instead when many instances of a server app run on the same machine.</span></span>

<span data-ttu-id="62ac1-133">此項目只能用在應用程式組態檔中；如果是在或電腦組態檔中，就會忽略此項目。</span><span class="sxs-lookup"><span data-stu-id="62ac1-133">This element can be used only in the application configuration file; it is ignored if it is in the machine configuration file.</span></span>

> [!NOTE]
> <span data-ttu-id="62ac1-134">在 .NET Framework 4 (含) 以前版本中，當伺服器記憶體回收啟用時，無法使用並行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="62ac1-134">In the .NET Framework 4 and earlier versions, concurrent garbage collection is not available when server garbage collection is enabled.</span></span> <span data-ttu-id="62ac1-135">從 .NET Framework 4.5 開始，伺服器記憶體回收為並行。</span><span class="sxs-lookup"><span data-stu-id="62ac1-135">Starting with the .NET Framework 4.5, server garbage collection is concurrent.</span></span> <span data-ttu-id="62ac1-136">若要使用非並行伺服器垃圾收集，請將**gcServer**元素設定為 `true` ，並將[gcConcurrent 元素](gcconcurrent-element.md)設為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="62ac1-136">To use non-concurrent server garbage collection, set the **gcServer** element to `true` and the [gcConcurrent element](gcconcurrent-element.md) to `false`.</span></span>

<span data-ttu-id="62ac1-137">從 .NET Framework 4.6.2 開始，您也可以使用下列元素來設定伺服器 GC：</span><span class="sxs-lookup"><span data-stu-id="62ac1-137">Starting with .NET Framework 4.6.2, you can also use the following elements to configure server GC:</span></span>

- <span data-ttu-id="62ac1-138">[GCNoAffinitize](gcnoaffinitize-element.md)，指定伺服器 GC 堆積和處理器之間是否有相似性。</span><span class="sxs-lookup"><span data-stu-id="62ac1-138">[GCNoAffinitize](gcnoaffinitize-element.md), which specifies whether there is an affinity between server GC heaps and processors.</span></span> <span data-ttu-id="62ac1-139">根據預設，每個處理器都有一個伺服器 GC 堆積。</span><span class="sxs-lookup"><span data-stu-id="62ac1-139">By default, there is one server GC heap for each processor.</span></span>

- <span data-ttu-id="62ac1-140">[GCHeapCount](gcheapcount-element.md)，這會限制進程所使用的堆積數目。</span><span class="sxs-lookup"><span data-stu-id="62ac1-140">[GCHeapCount](gcheapcount-element.md), which limits the number of heaps used by a process.</span></span>

- <span data-ttu-id="62ac1-141">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md)，定義可用伺服器 GC 堆積與個別處理器之間的親和性。</span><span class="sxs-lookup"><span data-stu-id="62ac1-141">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), which defines the affinity between the available server GC heaps and individual processors.</span></span>

## <a name="example"></a><span data-ttu-id="62ac1-142">範例</span><span class="sxs-lookup"><span data-stu-id="62ac1-142">Example</span></span>

<span data-ttu-id="62ac1-143">下列範例會啟用伺服器垃圾收集：</span><span class="sxs-lookup"><span data-stu-id="62ac1-143">The following example enables server garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="62ac1-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62ac1-144">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="62ac1-145">執行時間設定架構</span><span class="sxs-lookup"><span data-stu-id="62ac1-145">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="62ac1-146">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="62ac1-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="62ac1-147">停用並行垃圾收集</span><span class="sxs-lookup"><span data-stu-id="62ac1-147">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
