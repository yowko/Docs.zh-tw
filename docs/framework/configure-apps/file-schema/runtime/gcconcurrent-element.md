---
title: gc併發元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
ms.openlocfilehash: 5957337aa960a0d5f445249b410dbfaddb7b08e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400040"
---
# <a name="gcconcurrent-element"></a><span data-ttu-id="cee4a-102">\<gc併發>元素</span><span class="sxs-lookup"><span data-stu-id="cee4a-102">\<gcConcurrent> element</span></span>

<span data-ttu-id="cee4a-103">指定 Common Language Runtime 是否會在個別的執行緒執行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="cee4a-103">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>

<span data-ttu-id="cee4a-104">[\<配置>](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cee4a-104">[\<configuration>](../configuration-element.md)</span></span>\
<span data-ttu-id="cee4a-105">&nbsp;&nbsp;[\<運行時>](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="cee4a-105">&nbsp;&nbsp;[\<runtime>](runtime-element.md)</span></span>\
<span data-ttu-id="cee4a-106">&nbsp;&nbsp;&nbsp;&nbsp;\<gc 併發></span><span class="sxs-lookup"><span data-stu-id="cee4a-106">&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent></span></span>

## <a name="syntax"></a><span data-ttu-id="cee4a-107">語法</span><span class="sxs-lookup"><span data-stu-id="cee4a-107">Syntax</span></span>

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cee4a-108">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="cee4a-108">Attributes and elements</span></span>

<span data-ttu-id="cee4a-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="cee4a-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="cee4a-110">屬性</span><span class="sxs-lookup"><span data-stu-id="cee4a-110">Attributes</span></span>

|<span data-ttu-id="cee4a-111">屬性</span><span class="sxs-lookup"><span data-stu-id="cee4a-111">Attribute</span></span>|<span data-ttu-id="cee4a-112">描述</span><span class="sxs-lookup"><span data-stu-id="cee4a-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="cee4a-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="cee4a-113">Required attribute.</span></span><br /><br /><span data-ttu-id="cee4a-114">指定執行階段是否同時執行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="cee4a-114">Specifies whether the runtime runs garbage collection concurrently.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="cee4a-115">啟用的屬性</span><span class="sxs-lookup"><span data-stu-id="cee4a-115">enabled attribute</span></span>

|<span data-ttu-id="cee4a-116">值</span><span class="sxs-lookup"><span data-stu-id="cee4a-116">Value</span></span>|<span data-ttu-id="cee4a-117">描述</span><span class="sxs-lookup"><span data-stu-id="cee4a-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="cee4a-118">不同時運行垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="cee4a-118">Doesn't run garbage collection concurrently.</span></span>|
|`true`|<span data-ttu-id="cee4a-119">同時執行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="cee4a-119">Runs garbage collection concurrently.</span></span> <span data-ttu-id="cee4a-120">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="cee4a-120">This is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="cee4a-121">子元素</span><span class="sxs-lookup"><span data-stu-id="cee4a-121">Child elements</span></span>

<span data-ttu-id="cee4a-122">無。</span><span class="sxs-lookup"><span data-stu-id="cee4a-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cee4a-123">父元素</span><span class="sxs-lookup"><span data-stu-id="cee4a-123">Parent elements</span></span>

|<span data-ttu-id="cee4a-124">元素</span><span class="sxs-lookup"><span data-stu-id="cee4a-124">Element</span></span>|<span data-ttu-id="cee4a-125">描述</span><span class="sxs-lookup"><span data-stu-id="cee4a-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="cee4a-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="cee4a-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="cee4a-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="cee4a-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cee4a-128">備註</span><span class="sxs-lookup"><span data-stu-id="cee4a-128">Remarks</span></span>

<span data-ttu-id="cee4a-129">在 .NET 框架 4 之前，工作站垃圾回收支援併發垃圾回收，該回收在後臺在單獨的執行緒上執行垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="cee4a-129">Prior to .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="cee4a-130">在 .NET 框架 4 中，併發垃圾回收被後臺 GC 替換，後臺 GC 也在單獨的執行緒的後臺執行垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="cee4a-130">In .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="cee4a-131">從 .NET 框架 4.5 開始，後臺收集在伺服器垃圾回收中可用。</span><span class="sxs-lookup"><span data-stu-id="cee4a-131">Starting with .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="cee4a-132">**gcConcurrent**元素控制運行時是否執行併發或後臺垃圾回收，是否可用，或者它是否在前臺執行垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="cee4a-132">The **gcConcurrent** element controls whether the runtime performs either concurrent or background garbage collection, if it's available, or whether it performs garbage collection in the foreground.</span></span>

### <a name="to-disable-background-garbage-collection"></a><span data-ttu-id="cee4a-133">禁用後臺垃圾回收</span><span class="sxs-lookup"><span data-stu-id="cee4a-133">To disable background garbage collection</span></span>

> [!WARNING]
> <span data-ttu-id="cee4a-134">從 .NET 框架 4 開始，併發垃圾回收將被後臺垃圾回收替換。</span><span class="sxs-lookup"><span data-stu-id="cee4a-134">Starting with .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="cee4a-135">術語*併發*和*背景*在 .NET 框架文檔中可互換使用。</span><span class="sxs-lookup"><span data-stu-id="cee4a-135">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="cee4a-136">要禁用後臺垃圾回收，請使用**gcConcurrent**元素，如本文所述。</span><span class="sxs-lookup"><span data-stu-id="cee4a-136">To disable background garbage collection, use the **gcConcurrent** element, as discussed in this article.</span></span>

<span data-ttu-id="cee4a-137">依預設，執行階段會使用並行或背景記憶體回收，這已針對延遲進行最佳化。</span><span class="sxs-lookup"><span data-stu-id="cee4a-137">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="cee4a-138">如果您的應用程式與使用者互動程度極高，則請讓並行記憶體回收維持啟用狀態，藉此最小化應用程式為了執行記憶體回收而暫停的時間。</span><span class="sxs-lookup"><span data-stu-id="cee4a-138">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="cee4a-139">如果將`enabled`**gcConcurrent**元素的屬性設置為`false`，運行時將使用非併發垃圾回收，該回收針對輸送量進行了優化。</span><span class="sxs-lookup"><span data-stu-id="cee4a-139">If you set the `enabled` attribute of the **gcConcurrent** element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span>

<span data-ttu-id="cee4a-140">以下設定檔禁用後臺垃圾回收：</span><span class="sxs-lookup"><span data-stu-id="cee4a-140">The following configuration file disables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

<span data-ttu-id="cee4a-141">如果電腦設定檔中有**gcConcurrent設置，** 它將為所有 .NET Framework 應用程式定義預設值。</span><span class="sxs-lookup"><span data-stu-id="cee4a-141">If there's a **gcConcurrentSetting** setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="cee4a-142">電腦組態檔設定會覆寫應用程式組態檔設定。</span><span class="sxs-lookup"><span data-stu-id="cee4a-142">The machine configuration file setting overrides the application configuration file setting.</span></span>

<span data-ttu-id="cee4a-143">有關併發和後臺垃圾回收的詳細資訊，請參閱"[垃圾回收基礎知識](../../../../standard/garbage-collection/fundamentals.md)"一文中的[併發垃圾回收](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection)、[後臺工作站垃圾回收](../../../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection)和[後臺伺服器垃圾回收](../../../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection)部分。</span><span class="sxs-lookup"><span data-stu-id="cee4a-143">For more information on concurrent and background garbage collection, see the [Concurrent garbage collection](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection), [Background workstation garbage collection](../../../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection), and [Background server garbage collection](../../../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection) sections in the [Fundamentals of Garbage Collection](../../../../standard/garbage-collection/fundamentals.md) article.</span></span>

## <a name="example"></a><span data-ttu-id="cee4a-144">範例</span><span class="sxs-lookup"><span data-stu-id="cee4a-144">Example</span></span>

<span data-ttu-id="cee4a-145">以下示例支援後臺垃圾回收：</span><span class="sxs-lookup"><span data-stu-id="cee4a-145">The following example enables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="cee4a-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cee4a-146">See also</span></span>

- [<span data-ttu-id="cee4a-147">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="cee4a-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="cee4a-148">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="cee4a-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="cee4a-149">Fundamentals of Garbage Collection (記憶體回收的基本概念)</span><span class="sxs-lookup"><span data-stu-id="cee4a-149">Fundamentals of Garbage Collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
