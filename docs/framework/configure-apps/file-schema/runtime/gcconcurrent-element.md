---
title: <gcConcurrent> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e2be4d9384f1e1ef73ce6064184aa2621a517a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674099"
---
# <a name="gcconcurrent-element"></a><span data-ttu-id="2caf6-102">\<gcConcurrent > 項目</span><span class="sxs-lookup"><span data-stu-id="2caf6-102">\<gcConcurrent> Element</span></span>

<span data-ttu-id="2caf6-103">指定 Common Language Runtime 是否會在個別的執行緒執行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="2caf6-103">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>

<span data-ttu-id="2caf6-104">\<configuration>\\</span><span class="sxs-lookup"><span data-stu-id="2caf6-104">\<configuration>\\</span></span>
<span data-ttu-id="2caf6-105">\<runtime>\\</span><span class="sxs-lookup"><span data-stu-id="2caf6-105">\<runtime>\\</span></span>
<span data-ttu-id="2caf6-106">\<gcConcurrent></span><span class="sxs-lookup"><span data-stu-id="2caf6-106">\<gcConcurrent></span></span>

## <a name="syntax"></a><span data-ttu-id="2caf6-107">語法</span><span class="sxs-lookup"><span data-stu-id="2caf6-107">Syntax</span></span>

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2caf6-108">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="2caf6-108">Attributes and elements</span></span>

<span data-ttu-id="2caf6-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2caf6-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="2caf6-110">屬性</span><span class="sxs-lookup"><span data-stu-id="2caf6-110">Attributes</span></span>

|<span data-ttu-id="2caf6-111">屬性</span><span class="sxs-lookup"><span data-stu-id="2caf6-111">Attribute</span></span>|<span data-ttu-id="2caf6-112">描述</span><span class="sxs-lookup"><span data-stu-id="2caf6-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="2caf6-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="2caf6-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="2caf6-114">指定執行階段是否同時執行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="2caf6-114">Specifies whether the runtime runs garbage collection concurrently.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="2caf6-115">啟用的屬性</span><span class="sxs-lookup"><span data-stu-id="2caf6-115">enabled attribute</span></span>

|<span data-ttu-id="2caf6-116">值</span><span class="sxs-lookup"><span data-stu-id="2caf6-116">Value</span></span>|<span data-ttu-id="2caf6-117">描述</span><span class="sxs-lookup"><span data-stu-id="2caf6-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="2caf6-118">不會同時執行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="2caf6-118">Doesn't run garbage collection concurrently.</span></span>|
|`true`|<span data-ttu-id="2caf6-119">同時執行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="2caf6-119">Runs garbage collection concurrently.</span></span> <span data-ttu-id="2caf6-120">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="2caf6-120">This is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="2caf6-121">子元素</span><span class="sxs-lookup"><span data-stu-id="2caf6-121">Child elements</span></span>

<span data-ttu-id="2caf6-122">無。</span><span class="sxs-lookup"><span data-stu-id="2caf6-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2caf6-123">父元素</span><span class="sxs-lookup"><span data-stu-id="2caf6-123">Parent elements</span></span>

|<span data-ttu-id="2caf6-124">元素</span><span class="sxs-lookup"><span data-stu-id="2caf6-124">Element</span></span>|<span data-ttu-id="2caf6-125">描述</span><span class="sxs-lookup"><span data-stu-id="2caf6-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="2caf6-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="2caf6-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="2caf6-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="2caf6-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2caf6-128">備註</span><span class="sxs-lookup"><span data-stu-id="2caf6-128">Remarks</span></span>

<span data-ttu-id="2caf6-129">在 .NET Framework 4 之前，工作站記憶體回收支援並行記憶體回收，這會在另一個執行緒上，在背景中執行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="2caf6-129">Prior to the .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="2caf6-130">在 .NET Framework 4 中，並行記憶體回收取代為背景 GC，這也會在另一個執行緒上，在背景中執行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="2caf6-130">In the .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="2caf6-131">從 .NET Framework 4.5 開始，在伺服器記憶體回收中可以使用背景記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="2caf6-131">Starting with the .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="2caf6-132">`<gcConcurrent>`元素可讓您控制執行階段是否執行並行或背景記憶體回收，如果有的話，還是在前景執行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="2caf6-132">The `<gcConcurrent>` element controls whether the runtime performs either concurrent or background garbage collection, if it's available, or whether it performs garbage collection in the foreground.</span></span>

### <a name="to-disable-background-garbage-collection"></a><span data-ttu-id="2caf6-133">若要停用背景記憶體回收</span><span class="sxs-lookup"><span data-stu-id="2caf6-133">To disable background garbage collection</span></span>

> [!WARNING]
> <span data-ttu-id="2caf6-134">從 .NET Framework 4 開始，背景記憶體回收就取代了並行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="2caf6-134">Starting with the .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="2caf6-135">條款*並行*並*背景*.NET Framework 文件中交替使用。</span><span class="sxs-lookup"><span data-stu-id="2caf6-135">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="2caf6-136">若要停用背景記憶體回收，請使用 `<gcConcurrent>` 項目，如本文所述。</span><span class="sxs-lookup"><span data-stu-id="2caf6-136">To disable background garbage collection, use the `<gcConcurrent>` element, as discussed in this article.</span></span>

<span data-ttu-id="2caf6-137">依預設，執行階段會使用並行或背景記憶體回收，這已針對延遲進行最佳化。</span><span class="sxs-lookup"><span data-stu-id="2caf6-137">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="2caf6-138">如果您的應用程式與使用者互動程度極高，則請讓並行記憶體回收維持啟用狀態，藉此最小化應用程式為了執行記憶體回收而暫停的時間。</span><span class="sxs-lookup"><span data-stu-id="2caf6-138">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="2caf6-139">如果您將 `enabled` 項目的 `<gcConcurrent>` 屬性設為 `false`，執行階段就會使用針對輸送量最佳化的非並行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="2caf6-139">If you set the `enabled` attribute of the `<gcConcurrent>` element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span> <span data-ttu-id="2caf6-140">下列組態檔會停用背景記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="2caf6-140">The following configuration file disables background garbage collection.</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

 <span data-ttu-id="2caf6-141">如果沒有`<gcConcurrentSetting>`機器組態檔中設定，定義所有的.NET Framework 應用程式的預設值。</span><span class="sxs-lookup"><span data-stu-id="2caf6-141">If there's a `<gcConcurrentSetting>` setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="2caf6-142">電腦組態檔設定會覆寫應用程式組態檔設定。</span><span class="sxs-lookup"><span data-stu-id="2caf6-142">The machine configuration file setting overrides the application configuration file setting.</span></span>

 <span data-ttu-id="2caf6-143">如需有關並行和背景記憶體回收，請參閱[並行記憶體回收](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection)一節[Fundamentals of Garbage Collection](../../../../standard/garbage-collection/fundamentals.md)文章。</span><span class="sxs-lookup"><span data-stu-id="2caf6-143">For more information on concurrent and background garbage collection, see the [Concurrent garbage collection](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection) section in the [Fundamentals of Garbage Collection](../../../../standard/garbage-collection/fundamentals.md) article.</span></span>

## <a name="example"></a><span data-ttu-id="2caf6-144">範例</span><span class="sxs-lookup"><span data-stu-id="2caf6-144">Example</span></span>

<span data-ttu-id="2caf6-145">下列範例會啟用並行記憶體回收：</span><span class="sxs-lookup"><span data-stu-id="2caf6-145">The following example enables concurrent garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="2caf6-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2caf6-146">See also</span></span>

- [<span data-ttu-id="2caf6-147">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="2caf6-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2caf6-148">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="2caf6-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="2caf6-149">記憶體回收的基本概念</span><span class="sxs-lookup"><span data-stu-id="2caf6-149">Fundamentals of Garbage Collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
