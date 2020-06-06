---
title: GCNoAffinitize 元素
ms.date: 11/08/2019
helpviewer_keywords:
- gcNoAffinitize element
- <gcNoAffinitize> element
ms.openlocfilehash: 16d6e5adefe2b632d7251669650058d7df7cea70
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "84004734"
---
# <a name="gcnoaffinitize-element"></a><span data-ttu-id="8e25e-102">\<GCNoAffinitize> 項目</span><span class="sxs-lookup"><span data-stu-id="8e25e-102">\<GCNoAffinitize> element</span></span>

<span data-ttu-id="8e25e-103">指定是否要使用 Cpu 將相似化為伺服器 GC 執行緒。</span><span class="sxs-lookup"><span data-stu-id="8e25e-103">Specifies whether or not to affinitize server GC threads with CPUs.</span></span>

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCNoAffinitize>

## <a name="syntax"></a><span data-ttu-id="8e25e-104">語法</span><span class="sxs-lookup"><span data-stu-id="8e25e-104">Syntax</span></span>

```xml
<GCNoAffinitize
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8e25e-105">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="8e25e-105">Attributes and elements</span></span>

<span data-ttu-id="8e25e-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="8e25e-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8e25e-107">屬性</span><span class="sxs-lookup"><span data-stu-id="8e25e-107">Attributes</span></span>

|<span data-ttu-id="8e25e-108">屬性</span><span class="sxs-lookup"><span data-stu-id="8e25e-108">Attribute</span></span>|<span data-ttu-id="8e25e-109">描述</span><span class="sxs-lookup"><span data-stu-id="8e25e-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="8e25e-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="8e25e-110">Required attribute.</span></span><br /><br /><span data-ttu-id="8e25e-111">指定是否要使用機器上可用的處理器來相似化為伺服器 GC 執行緒/堆積。</span><span class="sxs-lookup"><span data-stu-id="8e25e-111">Specifies whether server GC threads/heaps are affinitized with the processors available on the machine.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="8e25e-112">enabled 屬性</span><span class="sxs-lookup"><span data-stu-id="8e25e-112">enabled attribute</span></span>

|<span data-ttu-id="8e25e-113">值</span><span class="sxs-lookup"><span data-stu-id="8e25e-113">Value</span></span>|<span data-ttu-id="8e25e-114">描述</span><span class="sxs-lookup"><span data-stu-id="8e25e-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="8e25e-115">具有 Cpu 的如何伺服器 GC 執行緒。</span><span class="sxs-lookup"><span data-stu-id="8e25e-115">Affinitizes server GC threads with CPUs.</span></span> <span data-ttu-id="8e25e-116">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="8e25e-116">This is the default.</span></span>|
|`true`|<span data-ttu-id="8e25e-117">不會將相似化為伺服器 GC 執行緒與 Cpu。</span><span class="sxs-lookup"><span data-stu-id="8e25e-117">Does not affinitize server GC threads with CPUs.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="8e25e-118">子元素</span><span class="sxs-lookup"><span data-stu-id="8e25e-118">Child elements</span></span>

<span data-ttu-id="8e25e-119">無。</span><span class="sxs-lookup"><span data-stu-id="8e25e-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8e25e-120">父元素</span><span class="sxs-lookup"><span data-stu-id="8e25e-120">Parent elements</span></span>

|<span data-ttu-id="8e25e-121">元素</span><span class="sxs-lookup"><span data-stu-id="8e25e-121">Element</span></span>|<span data-ttu-id="8e25e-122">描述</span><span class="sxs-lookup"><span data-stu-id="8e25e-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="8e25e-123">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="8e25e-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="8e25e-124">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="8e25e-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8e25e-125">備註</span><span class="sxs-lookup"><span data-stu-id="8e25e-125">Remarks</span></span>

<span data-ttu-id="8e25e-126">根據預設，伺服器 GC 執行緒會以其各自的 Cpu 進行硬式相似化為。</span><span class="sxs-lookup"><span data-stu-id="8e25e-126">By default, server GC threads are hard-affinitized with their respective CPUs.</span></span> <span data-ttu-id="8e25e-127">系統的每個可用處理器都有自己的 GC 堆積和執行緒。</span><span class="sxs-lookup"><span data-stu-id="8e25e-127">Each of the system's available processors has its own GC heap and thread.</span></span> <span data-ttu-id="8e25e-128">這通常是慣用的設定，因為它會優化快取使用量。</span><span class="sxs-lookup"><span data-stu-id="8e25e-128">This is typically the preferred setting since it optimizes cache usage.</span></span> <span data-ttu-id="8e25e-129">從 .NET Framework 4.6.2 開始，藉由將**GCNoAffinitize**元素的 `enabled` 屬性設定為 `true` ，您可以指定伺服器 GC 執行緒和 cpu 不應緊密結合。</span><span class="sxs-lookup"><span data-stu-id="8e25e-129">Starting with .NET Framework 4.6.2, by setting the **GCNoAffinitize** element's `enabled` attribute to `true`, you can specify that server GC threads and CPUs should not be tightly coupled.</span></span>

<span data-ttu-id="8e25e-130">您可以單獨指定**GCNoAffinitize**設定元素，而不是使用 cpu 將相似化為伺服器 GC 執行緒。</span><span class="sxs-lookup"><span data-stu-id="8e25e-130">You can specify the **GCNoAffinitize** configuration element alone to not affinitize server GC threads with CPUs.</span></span> <span data-ttu-id="8e25e-131">您也可以將它與[GCHeapCount](gcheapcount-element.md)元素搭配使用，以控制應用程式所使用的 GC 堆積和執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="8e25e-131">You can also use it along with the [GCHeapCount](gcheapcount-element.md) element to control the number of GC heaps and threads used by an application.</span></span>

<span data-ttu-id="8e25e-132">如果 GCNoAffinitize 專案的 `enabled` 屬性**GCNoAffinitize**是 `false` （其預設值），您也可以使用[GCHeapCount](gcheapcount-element.md)專案來指定 gc 執行緒和堆積的數目，以及[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md)元素，以指定 gc 執行緒和堆積相似化為的處理器。</span><span class="sxs-lookup"><span data-stu-id="8e25e-132">If the `enabled` attribute of the **GCNoAffinitize** element is `false` (its default value), you can also use the [GCHeapCount](gcheapcount-element.md) element to specify the number of GC threads and heaps, along with the [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md) element to specify the processors to which the GC threads and heaps are affinitized.</span></span>

## <a name="example"></a><span data-ttu-id="8e25e-133">範例</span><span class="sxs-lookup"><span data-stu-id="8e25e-133">Example</span></span>

<span data-ttu-id="8e25e-134">下列範例不會硬式將相似化為伺服器 GC 執行緒：</span><span class="sxs-lookup"><span data-stu-id="8e25e-134">The following example does not hard-affinitize server GC threads:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

<span data-ttu-id="8e25e-135">下列範例不會將相似化為伺服器 GC 執行緒，並將 GC 堆積/執行緒的數目限制為10個：</span><span class="sxs-lookup"><span data-stu-id="8e25e-135">The following example does not affinitize server GC threads and limits the number of GC heaps/threads to 10:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="8e25e-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e25e-136">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8e25e-137">GCHeapAffinitizeMask 元素</span><span class="sxs-lookup"><span data-stu-id="8e25e-137">GCHeapAffinitizeMask element</span></span>](gcheapaffinitizemask-element.md)
- [<span data-ttu-id="8e25e-138">GCHeapCount 元素</span><span class="sxs-lookup"><span data-stu-id="8e25e-138">GCHeapCount element</span></span>](gcheapcount-element.md)
- [<span data-ttu-id="8e25e-139">垃圾收集的基本概念</span><span class="sxs-lookup"><span data-stu-id="8e25e-139">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="8e25e-140">執行時間設定架構</span><span class="sxs-lookup"><span data-stu-id="8e25e-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="8e25e-141">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="8e25e-141">Configuration File Schema</span></span>](../index.md)
