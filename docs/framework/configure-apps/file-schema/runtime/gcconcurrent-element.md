---
title: '&lt;gcConcurrent&gt;項目'
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
ms.openlocfilehash: ee00c3a307523d2cae831274630ad6828cd9daf6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltgcconcurrentgt-element"></a><span data-ttu-id="7cb8c-102">&lt;gcConcurrent&gt;項目</span><span class="sxs-lookup"><span data-stu-id="7cb8c-102">&lt;gcConcurrent&gt; Element</span></span>
<span data-ttu-id="7cb8c-103">指定 Common Language Runtime 是否會在個別的執行緒執行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="7cb8c-103">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>  
  
 <span data-ttu-id="7cb8c-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="7cb8c-104">\<configuration></span></span>  
<span data-ttu-id="7cb8c-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="7cb8c-105">\<runtime></span></span>  
<span data-ttu-id="7cb8c-106">\<gcConcurrent ></span><span class="sxs-lookup"><span data-stu-id="7cb8c-106">\<gcConcurrent></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cb8c-107">語法</span><span class="sxs-lookup"><span data-stu-id="7cb8c-107">Syntax</span></span>  
  
```xml  
<gcConcurrent    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7cb8c-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7cb8c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7cb8c-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7cb8c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7cb8c-110">屬性</span><span class="sxs-lookup"><span data-stu-id="7cb8c-110">Attributes</span></span>  
  
|<span data-ttu-id="7cb8c-111">屬性</span><span class="sxs-lookup"><span data-stu-id="7cb8c-111">Attribute</span></span>|<span data-ttu-id="7cb8c-112">描述</span><span class="sxs-lookup"><span data-stu-id="7cb8c-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="7cb8c-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="7cb8c-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="7cb8c-114">指定執行階段是否同時執行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="7cb8c-114">Specifies whether the runtime runs garbage collection concurrently.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="7cb8c-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="7cb8c-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="7cb8c-116">值</span><span class="sxs-lookup"><span data-stu-id="7cb8c-116">Value</span></span>|<span data-ttu-id="7cb8c-117">描述</span><span class="sxs-lookup"><span data-stu-id="7cb8c-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="7cb8c-118">不會同時執行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="7cb8c-118">Does not run garbage collection concurrently.</span></span>|  
|`true`|<span data-ttu-id="7cb8c-119">同時執行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="7cb8c-119">Runs garbage collection concurrently.</span></span> <span data-ttu-id="7cb8c-120">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="7cb8c-120">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7cb8c-121">子項目</span><span class="sxs-lookup"><span data-stu-id="7cb8c-121">Child Elements</span></span>  
 <span data-ttu-id="7cb8c-122">無。</span><span class="sxs-lookup"><span data-stu-id="7cb8c-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7cb8c-123">父項目</span><span class="sxs-lookup"><span data-stu-id="7cb8c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7cb8c-124">項目</span><span class="sxs-lookup"><span data-stu-id="7cb8c-124">Element</span></span>|<span data-ttu-id="7cb8c-125">描述</span><span class="sxs-lookup"><span data-stu-id="7cb8c-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7cb8c-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="7cb8c-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="7cb8c-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="7cb8c-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7cb8c-128">備註</span><span class="sxs-lookup"><span data-stu-id="7cb8c-128">Remarks</span></span>  
 <span data-ttu-id="7cb8c-129">在 .NET Framework 4 之前，工作站記憶體回收支援並行記憶體回收，這會在另一個執行緒上，在背景中執行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="7cb8c-129">Prior to the .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="7cb8c-130">在 .NET Framework 4 中，並行記憶體回收取代為背景 GC，這也會在另一個執行緒上，在背景中執行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="7cb8c-130">In the .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="7cb8c-131">從 .NET Framework 4.5 開始，在伺服器記憶體回收中可以使用背景記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="7cb8c-131">Starting with the .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="7cb8c-132">`<gcConcurrent>` 項目可控制執行階段是否執行並行或背景記憶體回收 (如果有的話)，或是是否在前景執行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="7cb8c-132">The `<gcConcurrent>` element controls whether the runtime performs either concurrent or background garbage collection, if it is available, or whether it performs garbage collection in the foreground.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="7cb8c-133">從 .NET Framework 4 開始，背景記憶體回收就取代了並行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="7cb8c-133">Starting with the .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="7cb8c-134">條款*並行*和*背景*.NET Framework 文件中交換使用。</span><span class="sxs-lookup"><span data-stu-id="7cb8c-134">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="7cb8c-135">若要停用背景記憶體回收，請使用 `<gcConcurrent>` 項目，如本文所述。</span><span class="sxs-lookup"><span data-stu-id="7cb8c-135">To disable background garbage collection, use the `<gcConcurrent>` element, as discussed in this article.</span></span>  
  
 <span data-ttu-id="7cb8c-136">依預設，執行階段會使用並行或背景記憶體回收，這已針對延遲進行最佳化。</span><span class="sxs-lookup"><span data-stu-id="7cb8c-136">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="7cb8c-137">如果您的應用程式與使用者互動程度極高，則請讓並行記憶體回收維持啟用狀態，藉此最小化應用程式為了執行記憶體回收而暫停的時間。</span><span class="sxs-lookup"><span data-stu-id="7cb8c-137">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="7cb8c-138">如果您將 `enabled` 項目的 `<gcConcurrent>` 屬性設為 `false`，執行階段就會使用針對輸送量最佳化的非並行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="7cb8c-138">If you set the `enabled` attribute of the `<gcConcurrent>` element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span> <span data-ttu-id="7cb8c-139">下列組態檔會停用背景記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="7cb8c-139">The following configuration file disables background garbage collection.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <gcConcurrent enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="7cb8c-140">如果在電腦組態檔中有 `<gcConcurrentSetting>` 設定，則它會定義所有 .NET Framework 應用程式的預設值。</span><span class="sxs-lookup"><span data-stu-id="7cb8c-140">If there is a `<gcConcurrentSetting>` setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="7cb8c-141">電腦組態檔設定會覆寫應用程式組態檔設定。</span><span class="sxs-lookup"><span data-stu-id="7cb8c-141">The machine configuration file setting overrides the application configuration file setting.</span></span>  
  
 <span data-ttu-id="7cb8c-142">如需有關並行和背景記憶體回收，請參閱中的 < 並行記憶體回收 」 一節[Fundamentals of Garbage Collection](../../../../../docs/standard/garbage-collection/fundamentals.md)主題。</span><span class="sxs-lookup"><span data-stu-id="7cb8c-142">For more information on concurrent and background garbage collection, see the "Concurrent garbage collection" section in the [Fundamentals of Garbage Collection](../../../../../docs/standard/garbage-collection/fundamentals.md) topic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7cb8c-143">範例</span><span class="sxs-lookup"><span data-stu-id="7cb8c-143">Example</span></span>  
 <span data-ttu-id="7cb8c-144">下列範例會啟用並行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="7cb8c-144">The following example enables concurrent garbage collection.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <gcConcurrent enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7cb8c-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7cb8c-145">See Also</span></span>  
 [<span data-ttu-id="7cb8c-146">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="7cb8c-146">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="7cb8c-147">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="7cb8c-147">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="7cb8c-148">記憶體回收的基本概念</span><span class="sxs-lookup"><span data-stu-id="7cb8c-148">Fundamentals of Garbage Collection</span></span>](../../../../../docs/standard/garbage-collection/fundamentals.md)
