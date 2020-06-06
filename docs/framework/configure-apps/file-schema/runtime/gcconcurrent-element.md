---
title: gcConcurrent 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
ms.openlocfilehash: 249518ae7477d284d50f9010757db83b7752c657
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "82102914"
---
# <a name="gcconcurrent-element"></a><span data-ttu-id="45111-102">\<gcConcurrent> 項目</span><span class="sxs-lookup"><span data-stu-id="45111-102">\<gcConcurrent> element</span></span>

<span data-ttu-id="45111-103">指定 Common Language Runtime 是否會在個別的執行緒執行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="45111-103">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent>

## <a name="syntax"></a><span data-ttu-id="45111-104">語法</span><span class="sxs-lookup"><span data-stu-id="45111-104">Syntax</span></span>

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="45111-105">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="45111-105">Attributes and elements</span></span>

<span data-ttu-id="45111-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="45111-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="45111-107">屬性</span><span class="sxs-lookup"><span data-stu-id="45111-107">Attributes</span></span>

|<span data-ttu-id="45111-108">屬性</span><span class="sxs-lookup"><span data-stu-id="45111-108">Attribute</span></span>|<span data-ttu-id="45111-109">描述</span><span class="sxs-lookup"><span data-stu-id="45111-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="45111-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="45111-110">Required attribute.</span></span><br /><br /><span data-ttu-id="45111-111">指定執行階段是否同時執行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="45111-111">Specifies whether the runtime runs garbage collection concurrently.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="45111-112">enabled 屬性</span><span class="sxs-lookup"><span data-stu-id="45111-112">enabled attribute</span></span>

|<span data-ttu-id="45111-113">值</span><span class="sxs-lookup"><span data-stu-id="45111-113">Value</span></span>|<span data-ttu-id="45111-114">描述</span><span class="sxs-lookup"><span data-stu-id="45111-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="45111-115">不會同時執行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="45111-115">Doesn't run garbage collection concurrently.</span></span>|
|`true`|<span data-ttu-id="45111-116">同時執行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="45111-116">Runs garbage collection concurrently.</span></span> <span data-ttu-id="45111-117">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="45111-117">This is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="45111-118">子元素</span><span class="sxs-lookup"><span data-stu-id="45111-118">Child elements</span></span>

<span data-ttu-id="45111-119">無。</span><span class="sxs-lookup"><span data-stu-id="45111-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="45111-120">父元素</span><span class="sxs-lookup"><span data-stu-id="45111-120">Parent elements</span></span>

|<span data-ttu-id="45111-121">元素</span><span class="sxs-lookup"><span data-stu-id="45111-121">Element</span></span>|<span data-ttu-id="45111-122">描述</span><span class="sxs-lookup"><span data-stu-id="45111-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="45111-123">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="45111-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="45111-124">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="45111-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="45111-125">備註</span><span class="sxs-lookup"><span data-stu-id="45111-125">Remarks</span></span>

<span data-ttu-id="45111-126">在 .NET Framework 4 之前，工作站垃圾收集支援並行垃圾收集，這會在個別執行緒的背景中執行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="45111-126">Prior to .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="45111-127">在 .NET Framework 4 中，並行垃圾收集已由背景 GC 取代，這也會在另一個執行緒的背景中執行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="45111-127">In .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="45111-128">從 .NET Framework 4.5 開始，會在伺服器垃圾收集中提供背景集合。</span><span class="sxs-lookup"><span data-stu-id="45111-128">Starting with .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="45111-129">**GcConcurrent**元素會控制執行時間是否執行並行或背景垃圾收集（如果有的話），或是是否在前景執行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="45111-129">The **gcConcurrent** element controls whether the runtime performs either concurrent or background garbage collection, if it's available, or whether it performs garbage collection in the foreground.</span></span>

### <a name="to-disable-background-garbage-collection"></a><span data-ttu-id="45111-130">若要停用背景垃圾收集</span><span class="sxs-lookup"><span data-stu-id="45111-130">To disable background garbage collection</span></span>

> [!WARNING]
> <span data-ttu-id="45111-131">從 .NET Framework 4 開始，並行垃圾收集會由背景垃圾收集取代。</span><span class="sxs-lookup"><span data-stu-id="45111-131">Starting with .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="45111-132">.NET Framework 檔中會交替使用「*並行*」和「*背景*」這兩個詞彙。</span><span class="sxs-lookup"><span data-stu-id="45111-132">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="45111-133">若要停用背景垃圾收集，請使用**gcConcurrent**元素，如本文中所述。</span><span class="sxs-lookup"><span data-stu-id="45111-133">To disable background garbage collection, use the **gcConcurrent** element, as discussed in this article.</span></span>

<span data-ttu-id="45111-134">依預設，執行階段會使用並行或背景記憶體回收，這已針對延遲進行最佳化。</span><span class="sxs-lookup"><span data-stu-id="45111-134">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="45111-135">如果您的應用程式與使用者互動程度極高，則請讓並行記憶體回收維持啟用狀態，藉此最小化應用程式為了執行記憶體回收而暫停的時間。</span><span class="sxs-lookup"><span data-stu-id="45111-135">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="45111-136">如果您將 `enabled` **gcConcurrent**元素的屬性設定為 `false` ，執行時間會使用非並行垃圾收集，這會針對輸送量進行優化。</span><span class="sxs-lookup"><span data-stu-id="45111-136">If you set the `enabled` attribute of the **gcConcurrent** element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span>

<span data-ttu-id="45111-137">下列設定檔會停用背景垃圾收集：</span><span class="sxs-lookup"><span data-stu-id="45111-137">The following configuration file disables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

<span data-ttu-id="45111-138">如果電腦設定檔中有**gcConcurrentSetting**設定，它會定義所有 .NET Framework 應用程式的預設值。</span><span class="sxs-lookup"><span data-stu-id="45111-138">If there's a **gcConcurrentSetting** setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="45111-139">電腦組態檔設定會覆寫應用程式組態檔設定。</span><span class="sxs-lookup"><span data-stu-id="45111-139">The machine configuration file setting overrides the application configuration file setting.</span></span>

<span data-ttu-id="45111-140">如需並行和背景垃圾收集的詳細資訊，請參閱[背景垃圾收集](../../../../standard/garbage-collection/background-gc.md)。</span><span class="sxs-lookup"><span data-stu-id="45111-140">For more information on concurrent and background garbage collection, see [Background garbage collection](../../../../standard/garbage-collection/background-gc.md).</span></span>

## <a name="example"></a><span data-ttu-id="45111-141">範例</span><span class="sxs-lookup"><span data-stu-id="45111-141">Example</span></span>

<span data-ttu-id="45111-142">下列範例會啟用背景垃圾收集：</span><span class="sxs-lookup"><span data-stu-id="45111-142">The following example enables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="45111-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45111-143">See also</span></span>

- [<span data-ttu-id="45111-144">執行時間設定架構</span><span class="sxs-lookup"><span data-stu-id="45111-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="45111-145">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="45111-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="45111-146">Fundamentals of Garbage Collection (記憶體回收的基本概念)</span><span class="sxs-lookup"><span data-stu-id="45111-146">Fundamentals of Garbage Collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
