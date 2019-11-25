---
title: GCNoAffinitize 元素
ms.date: 11/08/2019
helpviewer_keywords:
- gcNoAffinitize element
- <gcNoAffinitize> element
ms.openlocfilehash: 4031ff19131c905072696837d1622dbb6e54ae61
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978372"
---
# <a name="gcnoaffinitize-element"></a><span data-ttu-id="0a0cc-102">\<GCNoAffinitize > 元素</span><span class="sxs-lookup"><span data-stu-id="0a0cc-102">\<GCNoAffinitize> element</span></span>

<span data-ttu-id="0a0cc-103">指定是否要使用 Cpu 將相似化為伺服器 GC 執行緒。</span><span class="sxs-lookup"><span data-stu-id="0a0cc-103">Specifies whether or not to affinitize server GC threads with CPUs.</span></span>

<span data-ttu-id="0a0cc-104">\<設定 > </span><span class="sxs-lookup"><span data-stu-id="0a0cc-104">\<configuration></span></span>\
<span data-ttu-id="0a0cc-105">&nbsp;&nbsp;\<執行時間 > </span><span class="sxs-lookup"><span data-stu-id="0a0cc-105">&nbsp;&nbsp;\<runtime></span></span>\
<span data-ttu-id="0a0cc-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCNoAffinitize ></span><span class="sxs-lookup"><span data-stu-id="0a0cc-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCNoAffinitize></span></span>

## <a name="syntax"></a><span data-ttu-id="0a0cc-107">語法</span><span class="sxs-lookup"><span data-stu-id="0a0cc-107">Syntax</span></span>

```xml
<GCNoAffinitize
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0a0cc-108">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="0a0cc-108">Attributes and elements</span></span>

<span data-ttu-id="0a0cc-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0a0cc-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0a0cc-110">屬性</span><span class="sxs-lookup"><span data-stu-id="0a0cc-110">Attributes</span></span>

|<span data-ttu-id="0a0cc-111">屬性</span><span class="sxs-lookup"><span data-stu-id="0a0cc-111">Attribute</span></span>|<span data-ttu-id="0a0cc-112">描述</span><span class="sxs-lookup"><span data-stu-id="0a0cc-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="0a0cc-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="0a0cc-113">Required attribute.</span></span><br /><br /><span data-ttu-id="0a0cc-114">指定是否要使用機器上可用的處理器來相似化為伺服器 GC 執行緒/堆積。</span><span class="sxs-lookup"><span data-stu-id="0a0cc-114">Specifies whether server GC threads/heaps are affinitized with the processors available on the machine.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="0a0cc-115">enabled 屬性</span><span class="sxs-lookup"><span data-stu-id="0a0cc-115">enabled attribute</span></span>

|<span data-ttu-id="0a0cc-116">值</span><span class="sxs-lookup"><span data-stu-id="0a0cc-116">Value</span></span>|<span data-ttu-id="0a0cc-117">描述</span><span class="sxs-lookup"><span data-stu-id="0a0cc-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="0a0cc-118">具有 Cpu 的如何伺服器 GC 執行緒。</span><span class="sxs-lookup"><span data-stu-id="0a0cc-118">Affinitizes server GC threads with CPUs.</span></span> <span data-ttu-id="0a0cc-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="0a0cc-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="0a0cc-120">不會將相似化為伺服器 GC 執行緒與 Cpu。</span><span class="sxs-lookup"><span data-stu-id="0a0cc-120">Does not affinitize server GC threads with CPUs.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="0a0cc-121">子元素</span><span class="sxs-lookup"><span data-stu-id="0a0cc-121">Child elements</span></span>

<span data-ttu-id="0a0cc-122">無。</span><span class="sxs-lookup"><span data-stu-id="0a0cc-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0a0cc-123">父元素</span><span class="sxs-lookup"><span data-stu-id="0a0cc-123">Parent elements</span></span>

|<span data-ttu-id="0a0cc-124">項目</span><span class="sxs-lookup"><span data-stu-id="0a0cc-124">Element</span></span>|<span data-ttu-id="0a0cc-125">描述</span><span class="sxs-lookup"><span data-stu-id="0a0cc-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="0a0cc-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="0a0cc-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="0a0cc-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="0a0cc-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0a0cc-128">備註</span><span class="sxs-lookup"><span data-stu-id="0a0cc-128">Remarks</span></span>

<span data-ttu-id="0a0cc-129">根據預設，伺服器 GC 執行緒會以其各自的 Cpu 進行硬式相似化為。</span><span class="sxs-lookup"><span data-stu-id="0a0cc-129">By default, server GC threads are hard-affinitized with their respective CPUs.</span></span> <span data-ttu-id="0a0cc-130">系統的每個可用處理器都有自己的 GC 堆積和執行緒。</span><span class="sxs-lookup"><span data-stu-id="0a0cc-130">Each of the system's available processors has its own GC heap and thread.</span></span> <span data-ttu-id="0a0cc-131">這通常是慣用的設定，因為它會優化快取使用量。</span><span class="sxs-lookup"><span data-stu-id="0a0cc-131">This is typically the preferred setting since it optimizes cache usage.</span></span> <span data-ttu-id="0a0cc-132">從 .NET Framework 4.6.2 開始，藉由將**GCNoAffinitize**專案的 `enabled` 屬性設定為 `false`，您可以指定伺服器 GC 執行緒和 cpu 不應緊密結合。</span><span class="sxs-lookup"><span data-stu-id="0a0cc-132">Starting with .NET Framework 4.6.2, by setting the **GCNoAffinitize** element's `enabled` attribute to `false`, you can specify that server GC threads and CPUs should not be tightly coupled.</span></span>

<span data-ttu-id="0a0cc-133">您可以單獨指定**GCNoAffinitize**設定元素，而不是使用 cpu 將相似化為伺服器 GC 執行緒。</span><span class="sxs-lookup"><span data-stu-id="0a0cc-133">You can specify the **GCNoAffinitize** configuration element alone to not affinitize server GC threads with CPUs.</span></span> <span data-ttu-id="0a0cc-134">您也可以將它與[GCHeapCount](gcheapcount-element.md)元素搭配使用，以控制應用程式所使用的 GC 堆積和執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="0a0cc-134">You can also use it along with the [GCHeapCount](gcheapcount-element.md) element to control the number of GC heaps and threads used by an application.</span></span>

<span data-ttu-id="0a0cc-135">如果**GCNoAffinitize**專案的 `enabled` 屬性是 `false` （其預設值），您也可以使用[GCHeapCount](gcheapcount-element.md)專案來指定 gc 執行緒和堆積的數目，以及[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md)元素來指定要相似化為 gc 執行緒和堆積的處理器。</span><span class="sxs-lookup"><span data-stu-id="0a0cc-135">If the `enabled` attribute of the **GCNoAffinitize** element is `false` (its default value), you can also use the [GCHeapCount](gcheapcount-element.md) element to specify the number of GC threads and heaps, along with the [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md) element to specify the processors to which the GC threads and heaps are affinitized.</span></span>

## <a name="example"></a><span data-ttu-id="0a0cc-136">範例</span><span class="sxs-lookup"><span data-stu-id="0a0cc-136">Example</span></span>

<span data-ttu-id="0a0cc-137">下列範例不會硬式將相似化為伺服器 GC 執行緒：</span><span class="sxs-lookup"><span data-stu-id="0a0cc-137">The following example does not hard-affinitize server GC threads:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

<span data-ttu-id="0a0cc-138">下列範例不會將相似化為伺服器 GC 執行緒，並將 GC 堆積/執行緒的數目限制為10個：</span><span class="sxs-lookup"><span data-stu-id="0a0cc-138">The following example does not affinitize server GC threads and limits the number of GC heaps/threads to 10:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="0a0cc-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="0a0cc-139">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="0a0cc-140">GCHeapAffinitizeMask 元素</span><span class="sxs-lookup"><span data-stu-id="0a0cc-140">GCHeapAffinitizeMask element</span></span>](gcheapaffinitizemask-element.md)
- [<span data-ttu-id="0a0cc-141">GCHeapCount 元素</span><span class="sxs-lookup"><span data-stu-id="0a0cc-141">GCHeapCount element</span></span>](gcheapcount-element.md)
- [<span data-ttu-id="0a0cc-142">記憶體回收的基本概念</span><span class="sxs-lookup"><span data-stu-id="0a0cc-142">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="0a0cc-143">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="0a0cc-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0a0cc-144">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="0a0cc-144">Configuration File Schema</span></span>](../index.md)
