---
title: GCHeapAffinitizeMask 元素
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 09d6523fb10692dd3617a3827d5bccf112bc632b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73978379"
---
# <a name="gcheapaffinitizemask-element"></a><span data-ttu-id="3c452-102">\<GCHeapAffinitizeMask> 項目</span><span class="sxs-lookup"><span data-stu-id="3c452-102">\<GCHeapAffinitizeMask> element</span></span>

<span data-ttu-id="3c452-103">定義 GC 堆積與個別處理器之間的親和性。</span><span class="sxs-lookup"><span data-stu-id="3c452-103">Defines the affinity between GC heaps and individual processors.</span></span>

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapAffinitizeMask>

## <a name="syntax"></a><span data-ttu-id="3c452-104">語法</span><span class="sxs-lookup"><span data-stu-id="3c452-104">Syntax</span></span>

```xml
<GCHeapAffinitizeMask
   enabled="nnnn"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3c452-105">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="3c452-105">Attributes and elements</span></span>

<span data-ttu-id="3c452-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3c452-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="3c452-107">屬性</span><span class="sxs-lookup"><span data-stu-id="3c452-107">Attributes</span></span>

|<span data-ttu-id="3c452-108">屬性</span><span class="sxs-lookup"><span data-stu-id="3c452-108">Attribute</span></span>|<span data-ttu-id="3c452-109">描述</span><span class="sxs-lookup"><span data-stu-id="3c452-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="3c452-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="3c452-110">Required attribute.</span></span><br /><br /><span data-ttu-id="3c452-111">指定 GC 堆積與個別處理器之間的親和性。</span><span class="sxs-lookup"><span data-stu-id="3c452-111">Specifies the affinity between GC heaps and individual processors.</span></span> |

#### <a name="enabled-attribute"></a><span data-ttu-id="3c452-112">enabled 屬性</span><span class="sxs-lookup"><span data-stu-id="3c452-112">enabled attribute</span></span>

|<span data-ttu-id="3c452-113">值</span><span class="sxs-lookup"><span data-stu-id="3c452-113">Value</span></span>|<span data-ttu-id="3c452-114">描述</span><span class="sxs-lookup"><span data-stu-id="3c452-114">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="3c452-115">十進位值，形成位元遮罩，以定義伺服器 GC 堆積與個別處理器之間的親和性。</span><span class="sxs-lookup"><span data-stu-id="3c452-115">A decimal value that forms a bitmask defining the affinity between server GC heaps and individual processors.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="3c452-116">子元素</span><span class="sxs-lookup"><span data-stu-id="3c452-116">Child elements</span></span>

<span data-ttu-id="3c452-117">無。</span><span class="sxs-lookup"><span data-stu-id="3c452-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3c452-118">父元素</span><span class="sxs-lookup"><span data-stu-id="3c452-118">Parent elements</span></span>

|<span data-ttu-id="3c452-119">元素</span><span class="sxs-lookup"><span data-stu-id="3c452-119">Element</span></span>|<span data-ttu-id="3c452-120">描述</span><span class="sxs-lookup"><span data-stu-id="3c452-120">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="3c452-121">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="3c452-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="3c452-122">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="3c452-122">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3c452-123">備註</span><span class="sxs-lookup"><span data-stu-id="3c452-123">Remarks</span></span>

<span data-ttu-id="3c452-124">根據預設，伺服器 GC 執行緒會相似化為其各自的 CPU，讓每個處理器都有一個 GC 堆積、一個伺服器 GC 執行緒，以及一個背景伺服器 GC 執行緒。</span><span class="sxs-lookup"><span data-stu-id="3c452-124">By default, server GC threads are hard-affinitized with their respective CPU so that there is one GC heap, one server GC thread, and one background server GC thread for each processor.</span></span> <span data-ttu-id="3c452-125">從 .NET Framework 4.6.2 開始，當堆積數目受到**GCHeapCount**元素的限制時，您可以使用**GCHeapAffinitizeMask**元素來控制伺服器 GC 堆積和處理器之間的相似性。</span><span class="sxs-lookup"><span data-stu-id="3c452-125">Starting with .NET Framework 4.6.2, you can use the **GCHeapAffinitizeMask** element to control the affinity between server GC heaps and processors when the number of heaps is limited by the **GCHeapCount** element.</span></span>

<span data-ttu-id="3c452-126">**GCHeapAffinitizeMask**通常會與兩個其他旗標搭配使用：</span><span class="sxs-lookup"><span data-stu-id="3c452-126">**GCHeapAffinitizeMask** is typically used along with two other flags:</span></span>

- <span data-ttu-id="3c452-127">[GCNoAffinitize](gcnoaffinitize-element.md)，控制是否使用 cpu 相似化為伺服器 GC 執行緒/堆積。</span><span class="sxs-lookup"><span data-stu-id="3c452-127">[GCNoAffinitize](gcnoaffinitize-element.md), which controls whether server GC threads/heaps are affinitized with CPUs.</span></span> <span data-ttu-id="3c452-128">`enabled` [GCNoAffinitize](gcnoaffinitize-element.md)元素的屬性必須是 `false` （其預設值），才能使用**GCHeapAffinitizeMask**設定。</span><span class="sxs-lookup"><span data-stu-id="3c452-128">The `enabled` attribute of the [GCNoAffinitize](gcnoaffinitize-element.md) element must be `false` (its default value) for the **GCHeapAffinitizeMask** setting to be used.</span></span>

- <span data-ttu-id="3c452-129">[GCHeapCount](gcheapcount-element.md)，這會限制進程針對伺服器 GC 所使用的堆積數目。</span><span class="sxs-lookup"><span data-stu-id="3c452-129">[GCHeapCount](gcheapcount-element.md), which limits the number of heaps used by the process for server GC.</span></span> <span data-ttu-id="3c452-130">根據預設，每個處理器都有一個堆積。</span><span class="sxs-lookup"><span data-stu-id="3c452-130">By default, there is one heap for each processor.</span></span>

<span data-ttu-id="3c452-131">**nnnn**是以十進位值表示的位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="3c452-131">**nnnn** is a bit mask expressed as a decimal value.</span></span> <span data-ttu-id="3c452-132">位0的位元組0代表處理器0，位元組0的位1代表處理器1，依此類推。</span><span class="sxs-lookup"><span data-stu-id="3c452-132">Bit 0 of byte 0 represents processor 0, bit 1 of byte 0 represents processor 1, and so on.</span></span> <span data-ttu-id="3c452-133">例如：</span><span class="sxs-lookup"><span data-stu-id="3c452-133">For example:</span></span>

```xml
<GCHeapAffinitizeMask enabled="1023"/>
```

<span data-ttu-id="3c452-134">1023的值是0x3FF 或 0011 1111 1111b。</span><span class="sxs-lookup"><span data-stu-id="3c452-134">A value of 1023 is 0x3FF or 0011 1111 1111b.</span></span> <span data-ttu-id="3c452-135">此程式會使用10個處理器，從處理器0到處理器9。</span><span class="sxs-lookup"><span data-stu-id="3c452-135">The process uses 10 processors, from processor 0 through processor 9.</span></span>

## <a name="example"></a><span data-ttu-id="3c452-136">範例</span><span class="sxs-lookup"><span data-stu-id="3c452-136">Example</span></span>

<span data-ttu-id="3c452-137">下列範例指出應用程式使用具有10個堆積/執行緒的伺服器 GC。</span><span class="sxs-lookup"><span data-stu-id="3c452-137">The following example indicates that an application uses server GC with 10 heaps/threads.</span></span> <span data-ttu-id="3c452-138">由於您不想讓這些堆積與系統上執行的其他應用程式的堆積重迭，因此請使用**GCHeapAffinitizeMask**來指定進程應該使用 cpu 0 到9。</span><span class="sxs-lookup"><span data-stu-id="3c452-138">Since you don't want those heaps to overlap with heaps from other applications running on the system, use **GCHeapAffinitizeMask** to specify that the process should use CPUs 0 through 9.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="3c452-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c452-139">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="3c452-140">GCNoAffinitize 元素</span><span class="sxs-lookup"><span data-stu-id="3c452-140">GCNoAffinitize element</span></span>](gcnoaffinitize-element.md)
- [<span data-ttu-id="3c452-141">GCHeapCount 元素</span><span class="sxs-lookup"><span data-stu-id="3c452-141">GCHeapCount element</span></span>](gcheapcount-element.md)
- [<span data-ttu-id="3c452-142">垃圾收集的基本概念</span><span class="sxs-lookup"><span data-stu-id="3c452-142">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="3c452-143">執行時間設定架構</span><span class="sxs-lookup"><span data-stu-id="3c452-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3c452-144">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="3c452-144">Configuration File Schema</span></span>](../index.md)
