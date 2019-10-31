---
title: <forcePerformanceCounterUniqueSharedMemoryReads> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
ms.openlocfilehash: efa6dce1035f7d2cf63b74c6a03d911b5dede722
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116958"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a><span data-ttu-id="73550-102">\<forcePerformanceCounterUniqueSharedMemoryReads> Element</span><span class="sxs-lookup"><span data-stu-id="73550-102">\<forcePerformanceCounterUniqueSharedMemoryReads> Element</span></span>
<span data-ttu-id="73550-103">指定 PerfCounter.dll 是否在 .NET Framework 1.1 版的應用程式中使用 CategoryOptions 登錄設定，以決定要從類別特定共用記憶體或從全域記憶體載入效能計數器資料。</span><span class="sxs-lookup"><span data-stu-id="73550-103">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>  
  
<span data-ttu-id="73550-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="73550-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="73550-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="73550-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="73550-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<forcePerformanceCounterUniqueSharedMemoryReads>**</span><span class="sxs-lookup"><span data-stu-id="73550-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<forcePerformanceCounterUniqueSharedMemoryReads>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73550-107">語法</span><span class="sxs-lookup"><span data-stu-id="73550-107">Syntax</span></span>  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads   
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73550-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="73550-108">Attributes and Elements</span></span>  
 <span data-ttu-id="73550-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="73550-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73550-110">屬性</span><span class="sxs-lookup"><span data-stu-id="73550-110">Attributes</span></span>  
  
|<span data-ttu-id="73550-111">屬性</span><span class="sxs-lookup"><span data-stu-id="73550-111">Attribute</span></span>|<span data-ttu-id="73550-112">描述</span><span class="sxs-lookup"><span data-stu-id="73550-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="73550-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="73550-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="73550-114">Indicates whether PerfCounter.dll uses the CategoryOptions registry setting to determine whether to load performance counter data from category-specific shared memory or global memory.</span><span class="sxs-lookup"><span data-stu-id="73550-114">Indicates whether PerfCounter.dll uses the CategoryOptions registry setting to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="73550-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="73550-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="73550-116">值</span><span class="sxs-lookup"><span data-stu-id="73550-116">Value</span></span>|<span data-ttu-id="73550-117">描述</span><span class="sxs-lookup"><span data-stu-id="73550-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="73550-118">PerfCounter.dll does not use the CategoryOptions registry setting This is the default.</span><span class="sxs-lookup"><span data-stu-id="73550-118">PerfCounter.dll does not use the CategoryOptions registry setting This is the default.</span></span>|  
|`true`|<span data-ttu-id="73550-119">PerfCounter.dll does use the CategoryOptions registry setting.</span><span class="sxs-lookup"><span data-stu-id="73550-119">PerfCounter.dll does use the CategoryOptions registry setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73550-120">子項目</span><span class="sxs-lookup"><span data-stu-id="73550-120">Child Elements</span></span>  
 <span data-ttu-id="73550-121">無。</span><span class="sxs-lookup"><span data-stu-id="73550-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="73550-122">父項目</span><span class="sxs-lookup"><span data-stu-id="73550-122">Parent Elements</span></span>  
  
|<span data-ttu-id="73550-123">項目</span><span class="sxs-lookup"><span data-stu-id="73550-123">Element</span></span>|<span data-ttu-id="73550-124">描述</span><span class="sxs-lookup"><span data-stu-id="73550-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="73550-125">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="73550-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="73550-126">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="73550-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73550-127">備註</span><span class="sxs-lookup"><span data-stu-id="73550-127">Remarks</span></span>  
 <span data-ttu-id="73550-128">In versions of the .NET Framework before the .NET Framework 4, the version of PerfCounter.dll that was loaded corresponded to the runtime that was loaded in the process.</span><span class="sxs-lookup"><span data-stu-id="73550-128">In versions of the .NET Framework before the .NET Framework 4, the version of PerfCounter.dll that was loaded corresponded to the runtime that was loaded in the process.</span></span> <span data-ttu-id="73550-129">If a computer had both the .NET Framework version 1.1 and the .NET Framework 2.0 installed, a .NET Framework 1.1 application would load the .NET Framework 1.1 version of PerfCounter.dll.</span><span class="sxs-lookup"><span data-stu-id="73550-129">If a computer had both the .NET Framework version 1.1 and the .NET Framework 2.0 installed, a .NET Framework 1.1 application would load the .NET Framework 1.1 version of PerfCounter.dll.</span></span> <span data-ttu-id="73550-130">Starting with the .NET Framework 4, the newest installed version of PerfCounter.dll is loaded.</span><span class="sxs-lookup"><span data-stu-id="73550-130">Starting with the .NET Framework 4, the newest installed version of PerfCounter.dll is loaded.</span></span> <span data-ttu-id="73550-131">This means that a .NET Framework 1.1 application will load the .NET Framework 4 version of PerfCounter.dll if the .NET Framework 4 is installed on the computer.</span><span class="sxs-lookup"><span data-stu-id="73550-131">This means that a .NET Framework 1.1 application will load the .NET Framework 4 version of PerfCounter.dll if the .NET Framework 4 is installed on the computer.</span></span>  
  
 <span data-ttu-id="73550-132">Starting with the .NET Framework 4, when consuming performance counters, PerfCounter.dll checks the CategoryOptions registry entry for each provider to determine whether it should read from category-specific shared memory or global shared memory.</span><span class="sxs-lookup"><span data-stu-id="73550-132">Starting with the .NET Framework 4, when consuming performance counters, PerfCounter.dll checks the CategoryOptions registry entry for each provider to determine whether it should read from category-specific shared memory or global shared memory.</span></span> <span data-ttu-id="73550-133">The .NET Framework 1.1 PerfCounter.dll does not read that registry entry, because it is not aware of category-specific shared memory; it always reads from global shared memory.</span><span class="sxs-lookup"><span data-stu-id="73550-133">The .NET Framework 1.1 PerfCounter.dll does not read that registry entry, because it is not aware of category-specific shared memory; it always reads from global shared memory.</span></span>  
  
 <span data-ttu-id="73550-134">For backward compatibility, the .NET Framework 4 PerfCounter.dll does not check the CategoryOptions registry entry when running in a .NET Framework 1.1 application.</span><span class="sxs-lookup"><span data-stu-id="73550-134">For backward compatibility, the .NET Framework 4 PerfCounter.dll does not check the CategoryOptions registry entry when running in a .NET Framework 1.1 application.</span></span> <span data-ttu-id="73550-135">它只會使用全域共用記憶體，如同 .NET Framework 1.1 PerfCounter。</span><span class="sxs-lookup"><span data-stu-id="73550-135">It simply uses global shared memory, just like the .NET Framework 1.1 PerfCounter.dll.</span></span> <span data-ttu-id="73550-136">不過，您可以藉由啟用 `<forcePerformanceCounterUniqueSharedMemoryReads>` 元素，指示 .NET Framework 4 PerfCounter 檢查登錄設定。</span><span class="sxs-lookup"><span data-stu-id="73550-136">However, you can instruct the .NET Framework 4 PerfCounter.dll to check the registry setting by enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73550-137">啟用 `<forcePerformanceCounterUniqueSharedMemoryReads>` 元素並不保證會使用類別特定的共用記憶體。</span><span class="sxs-lookup"><span data-stu-id="73550-137">Enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element does not guarantee that category-specific shared memory will be used.</span></span> <span data-ttu-id="73550-138">將 [已啟用] 設定為 `true` 只會導致 PerfCounter 參考 CategoryOptions 登錄設定。</span><span class="sxs-lookup"><span data-stu-id="73550-138">Setting enabled to `true` only causes PerfCounter.dll to reference the CategoryOptions registry setting.</span></span> <span data-ttu-id="73550-139">CategoryOptions 的預設設定是使用類別特定的共用記憶體;不過，您可以變更 CategoryOptions，以指出應該使用全域共用記憶體。</span><span class="sxs-lookup"><span data-stu-id="73550-139">The default setting for CategoryOptions is to use category-specific shared memory; however, you can change CategoryOptions to indicate that global shared memory should be used.</span></span>  
  
 <span data-ttu-id="73550-140">包含 CategoryOptions 設定的登錄機碼是 HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\< 類別名稱\>\Performance。</span><span class="sxs-lookup"><span data-stu-id="73550-140">The registry key that contains the CategoryOptions setting is HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance.</span></span> <span data-ttu-id="73550-141">根據預設，CategoryOptions 會設為3，指示 PerfCounter 使用類別特定的共用記憶體。</span><span class="sxs-lookup"><span data-stu-id="73550-141">By default, CategoryOptions is set to 3, which instructs PerfCounter.dll to use category-specific shared memory.</span></span> <span data-ttu-id="73550-142">如果 CategoryOptions 設定為0，則 PerfCounter 會使用全域共用記憶體。</span><span class="sxs-lookup"><span data-stu-id="73550-142">If CategoryOptions is set to 0, PerfCounter.dll uses global shared memory.</span></span> <span data-ttu-id="73550-143">只有當所建立之實例的名稱與要重複使用的實例相同時，才會重複使用實例資料。</span><span class="sxs-lookup"><span data-stu-id="73550-143">Instance data will be reused only if the name of the instance being created is identical to the instance being reused.</span></span> <span data-ttu-id="73550-144">所有版本都可以寫入類別目錄。</span><span class="sxs-lookup"><span data-stu-id="73550-144">All versions will be able to write to the category.</span></span> <span data-ttu-id="73550-145">如果 CategoryOptions 設為1，則會使用全域共用記憶體，但是如果類別目錄名稱的長度與要重複使用的類別相同，就可以重複使用實例資料。</span><span class="sxs-lookup"><span data-stu-id="73550-145">If CategoryOptions is set to 1, global shared memory is used, but instance data can be reused if the category name is the same length as the category being reused.</span></span>  
  
 <span data-ttu-id="73550-146">設定0和1可能會導致記憶體流失，並填滿效能計數器記憶體。</span><span class="sxs-lookup"><span data-stu-id="73550-146">The settings 0 and 1 can lead to memory leaks and the filling up of performance counter memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73550-147">範例</span><span class="sxs-lookup"><span data-stu-id="73550-147">Example</span></span>  
 <span data-ttu-id="73550-148">下列範例示範如何指定 PerfCounter 應該參考 CategoryOptions 登錄專案，以判斷它是否應該使用類別特定的共用記憶體。</span><span class="sxs-lookup"><span data-stu-id="73550-148">The following example shows how to specify that PerfCounter.dll should reference the CategoryOptions registry entry to determine whether it should use category-specific shared memory.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="73550-149">請參閱</span><span class="sxs-lookup"><span data-stu-id="73550-149">See also</span></span>

- [<span data-ttu-id="73550-150">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="73550-150">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="73550-151">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="73550-151">Configuration File Schema</span></span>](../index.md)
