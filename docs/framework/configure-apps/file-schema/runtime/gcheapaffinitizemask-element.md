---
title: GCHeapAffinitizeMask 元素
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 09d6523fb10692dd3617a3827d5bccf112bc632b
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978379"
---
# <a name="gcheapaffinitizemask-element"></a><span data-ttu-id="a49b9-102">\<GCHeapAffinitizeMask > 元素</span><span class="sxs-lookup"><span data-stu-id="a49b9-102">\<GCHeapAffinitizeMask> element</span></span>

<span data-ttu-id="a49b9-103">定義 GC 堆積與個別處理器之間的親和性。</span><span class="sxs-lookup"><span data-stu-id="a49b9-103">Defines the affinity between GC heaps and individual processors.</span></span>

<span data-ttu-id="a49b9-104">\<設定 > </span><span class="sxs-lookup"><span data-stu-id="a49b9-104">\<configuration></span></span>\
<span data-ttu-id="a49b9-105">&nbsp;&nbsp;\<執行時間 > </span><span class="sxs-lookup"><span data-stu-id="a49b9-105">&nbsp;&nbsp;\<runtime></span></span>\
<span data-ttu-id="a49b9-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapAffinitizeMask ></span><span class="sxs-lookup"><span data-stu-id="a49b9-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapAffinitizeMask></span></span>

## <a name="syntax"></a><span data-ttu-id="a49b9-107">語法</span><span class="sxs-lookup"><span data-stu-id="a49b9-107">Syntax</span></span>

```xml
<GCHeapAffinitizeMask
   enabled="nnnn"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a49b9-108">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="a49b9-108">Attributes and elements</span></span>

<span data-ttu-id="a49b9-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a49b9-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a49b9-110">屬性</span><span class="sxs-lookup"><span data-stu-id="a49b9-110">Attributes</span></span>

|<span data-ttu-id="a49b9-111">屬性</span><span class="sxs-lookup"><span data-stu-id="a49b9-111">Attribute</span></span>|<span data-ttu-id="a49b9-112">描述</span><span class="sxs-lookup"><span data-stu-id="a49b9-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="a49b9-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="a49b9-113">Required attribute.</span></span><br /><br /><span data-ttu-id="a49b9-114">指定 GC 堆積與個別處理器之間的親和性。</span><span class="sxs-lookup"><span data-stu-id="a49b9-114">Specifies the affinity between GC heaps and individual processors.</span></span> |

#### <a name="enabled-attribute"></a><span data-ttu-id="a49b9-115">enabled 屬性</span><span class="sxs-lookup"><span data-stu-id="a49b9-115">enabled attribute</span></span>

|<span data-ttu-id="a49b9-116">值</span><span class="sxs-lookup"><span data-stu-id="a49b9-116">Value</span></span>|<span data-ttu-id="a49b9-117">描述</span><span class="sxs-lookup"><span data-stu-id="a49b9-117">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="a49b9-118">十進位值，形成位元遮罩，以定義伺服器 GC 堆積與個別處理器之間的親和性。</span><span class="sxs-lookup"><span data-stu-id="a49b9-118">A decimal value that forms a bitmask defining the affinity between server GC heaps and individual processors.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="a49b9-119">子元素</span><span class="sxs-lookup"><span data-stu-id="a49b9-119">Child elements</span></span>

<span data-ttu-id="a49b9-120">無。</span><span class="sxs-lookup"><span data-stu-id="a49b9-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a49b9-121">父元素</span><span class="sxs-lookup"><span data-stu-id="a49b9-121">Parent elements</span></span>

|<span data-ttu-id="a49b9-122">項目</span><span class="sxs-lookup"><span data-stu-id="a49b9-122">Element</span></span>|<span data-ttu-id="a49b9-123">描述</span><span class="sxs-lookup"><span data-stu-id="a49b9-123">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="a49b9-124">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="a49b9-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="a49b9-125">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="a49b9-125">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a49b9-126">備註</span><span class="sxs-lookup"><span data-stu-id="a49b9-126">Remarks</span></span>

<span data-ttu-id="a49b9-127">根據預設，伺服器 GC 執行緒會相似化為其各自的 CPU，讓每個處理器都有一個 GC 堆積、一個伺服器 GC 執行緒，以及一個背景伺服器 GC 執行緒。</span><span class="sxs-lookup"><span data-stu-id="a49b9-127">By default, server GC threads are hard-affinitized with their respective CPU so that there is one GC heap, one server GC thread, and one background server GC thread for each processor.</span></span> <span data-ttu-id="a49b9-128">從 .NET Framework 4.6.2 開始，當堆積數目受到**GCHeapCount**元素的限制時，您可以使用**GCHeapAffinitizeMask**元素來控制伺服器 GC 堆積和處理器之間的相似性。</span><span class="sxs-lookup"><span data-stu-id="a49b9-128">Starting with .NET Framework 4.6.2, you can use the **GCHeapAffinitizeMask** element to control the affinity between server GC heaps and processors when the number of heaps is limited by the **GCHeapCount** element.</span></span>

<span data-ttu-id="a49b9-129">**GCHeapAffinitizeMask**通常會與兩個其他旗標搭配使用：</span><span class="sxs-lookup"><span data-stu-id="a49b9-129">**GCHeapAffinitizeMask** is typically used along with two other flags:</span></span>

- <span data-ttu-id="a49b9-130">[GCNoAffinitize](gcnoaffinitize-element.md)，控制是否使用 cpu 相似化為伺服器 GC 執行緒/堆積。</span><span class="sxs-lookup"><span data-stu-id="a49b9-130">[GCNoAffinitize](gcnoaffinitize-element.md), which controls whether server GC threads/heaps are affinitized with CPUs.</span></span> <span data-ttu-id="a49b9-131">[GCNoAffinitize](gcnoaffinitize-element.md)元素的 `enabled` 屬性必須是要使用之**GCHeapAffinitizeMask**設定的 `false` （其預設值）。</span><span class="sxs-lookup"><span data-stu-id="a49b9-131">The `enabled` attribute of the [GCNoAffinitize](gcnoaffinitize-element.md) element must be `false` (its default value) for the **GCHeapAffinitizeMask** setting to be used.</span></span>

- <span data-ttu-id="a49b9-132">[GCHeapCount](gcheapcount-element.md)，這會限制進程針對伺服器 GC 所使用的堆積數目。</span><span class="sxs-lookup"><span data-stu-id="a49b9-132">[GCHeapCount](gcheapcount-element.md), which limits the number of heaps used by the process for server GC.</span></span> <span data-ttu-id="a49b9-133">根據預設，每個處理器都有一個堆積。</span><span class="sxs-lookup"><span data-stu-id="a49b9-133">By default, there is one heap for each processor.</span></span>

<span data-ttu-id="a49b9-134">**nnnn**是以十進位值表示的位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="a49b9-134">**nnnn** is a bit mask expressed as a decimal value.</span></span> <span data-ttu-id="a49b9-135">位0的位元組0代表處理器0，位元組0的位1代表處理器1，依此類推。</span><span class="sxs-lookup"><span data-stu-id="a49b9-135">Bit 0 of byte 0 represents processor 0, bit 1 of byte 0 represents processor 1, and so on.</span></span> <span data-ttu-id="a49b9-136">例如:</span><span class="sxs-lookup"><span data-stu-id="a49b9-136">For example:</span></span>

```xml
<GCHeapAffinitizeMask enabled="1023"/>
```

<span data-ttu-id="a49b9-137">1023的值是0x3FF 或 0011 1111 1111b。</span><span class="sxs-lookup"><span data-stu-id="a49b9-137">A value of 1023 is 0x3FF or 0011 1111 1111b.</span></span> <span data-ttu-id="a49b9-138">此程式會使用10個處理器，從處理器0到處理器9。</span><span class="sxs-lookup"><span data-stu-id="a49b9-138">The process uses 10 processors, from processor 0 through processor 9.</span></span>

## <a name="example"></a><span data-ttu-id="a49b9-139">範例</span><span class="sxs-lookup"><span data-stu-id="a49b9-139">Example</span></span>

<span data-ttu-id="a49b9-140">下列範例指出應用程式使用具有10個堆積/執行緒的伺服器 GC。</span><span class="sxs-lookup"><span data-stu-id="a49b9-140">The following example indicates that an application uses server GC with 10 heaps/threads.</span></span> <span data-ttu-id="a49b9-141">由於您不想讓這些堆積與系統上執行的其他應用程式的堆積重迭，因此請使用**GCHeapAffinitizeMask**來指定進程應該使用 cpu 0 到9。</span><span class="sxs-lookup"><span data-stu-id="a49b9-141">Since you don't want those heaps to overlap with heaps from other applications running on the system, use **GCHeapAffinitizeMask** to specify that the process should use CPUs 0 through 9.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="a49b9-142">請參閱</span><span class="sxs-lookup"><span data-stu-id="a49b9-142">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a49b9-143">GCNoAffinitize 元素</span><span class="sxs-lookup"><span data-stu-id="a49b9-143">GCNoAffinitize element</span></span>](gcnoaffinitize-element.md)
- [<span data-ttu-id="a49b9-144">GCHeapCount 元素</span><span class="sxs-lookup"><span data-stu-id="a49b9-144">GCHeapCount element</span></span>](gcheapcount-element.md)
- [<span data-ttu-id="a49b9-145">記憶體回收的基本概念</span><span class="sxs-lookup"><span data-stu-id="a49b9-145">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="a49b9-146">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="a49b9-146">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a49b9-147">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="a49b9-147">Configuration File Schema</span></span>](../index.md)
