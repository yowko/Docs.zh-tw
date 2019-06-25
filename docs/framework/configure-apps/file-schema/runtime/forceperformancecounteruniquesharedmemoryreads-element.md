---
title: <forcePerformanceCounterUniqueSharedMemoryReads> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 00af9cf60d0bd2bac60950617b1315579d1a5a4d
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2019
ms.locfileid: "67347344"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a><span data-ttu-id="56522-102">\<forcePerformanceCounterUniqueSharedMemoryReads > 項目</span><span class="sxs-lookup"><span data-stu-id="56522-102">\<forcePerformanceCounterUniqueSharedMemoryReads> Element</span></span>
<span data-ttu-id="56522-103">指定 PerfCounter.dll 是否在 .NET Framework 1.1 版的應用程式中使用 CategoryOptions 登錄設定，以決定要從類別特定共用記憶體或從全域記憶體載入效能計數器資料。</span><span class="sxs-lookup"><span data-stu-id="56522-103">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>  
  
 <span data-ttu-id="56522-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="56522-104">\<configuration></span></span>  
<span data-ttu-id="56522-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="56522-105">\<runtime></span></span>  
<span data-ttu-id="56522-106">\<forcePerformanceCounterUniqueSharedMemoryReads></span><span class="sxs-lookup"><span data-stu-id="56522-106">\<forcePerformanceCounterUniqueSharedMemoryReads></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56522-107">語法</span><span class="sxs-lookup"><span data-stu-id="56522-107">Syntax</span></span>  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads   
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="56522-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="56522-108">Attributes and Elements</span></span>  
 <span data-ttu-id="56522-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="56522-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="56522-110">屬性</span><span class="sxs-lookup"><span data-stu-id="56522-110">Attributes</span></span>  
  
|<span data-ttu-id="56522-111">屬性</span><span class="sxs-lookup"><span data-stu-id="56522-111">Attribute</span></span>|<span data-ttu-id="56522-112">描述</span><span class="sxs-lookup"><span data-stu-id="56522-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="56522-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="56522-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="56522-114">指出 PerfCounter.dll 是否使用 CategoryOptions 登錄設定，以判斷是否要從類別特定共用的記憶體或從全域記憶體載入效能計數器資料。</span><span class="sxs-lookup"><span data-stu-id="56522-114">Indicates whether PerfCounter.dll uses the CategoryOptions registry setting to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="56522-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="56522-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="56522-116">值</span><span class="sxs-lookup"><span data-stu-id="56522-116">Value</span></span>|<span data-ttu-id="56522-117">描述</span><span class="sxs-lookup"><span data-stu-id="56522-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="56522-118">PerfCounter.dll 不會使用 CategoryOptions 登錄設定，這是預設值。</span><span class="sxs-lookup"><span data-stu-id="56522-118">PerfCounter.dll does not use the CategoryOptions registry setting This is the default.</span></span>|  
|`true`|<span data-ttu-id="56522-119">PerfCounter.dll 會使用 CategoryOptions 登錄設定。</span><span class="sxs-lookup"><span data-stu-id="56522-119">PerfCounter.dll does use the CategoryOptions registry setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="56522-120">子元素</span><span class="sxs-lookup"><span data-stu-id="56522-120">Child Elements</span></span>  
 <span data-ttu-id="56522-121">無。</span><span class="sxs-lookup"><span data-stu-id="56522-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="56522-122">父項目</span><span class="sxs-lookup"><span data-stu-id="56522-122">Parent Elements</span></span>  
  
|<span data-ttu-id="56522-123">項目</span><span class="sxs-lookup"><span data-stu-id="56522-123">Element</span></span>|<span data-ttu-id="56522-124">描述</span><span class="sxs-lookup"><span data-stu-id="56522-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="56522-125">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="56522-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="56522-126">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="56522-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56522-127">備註</span><span class="sxs-lookup"><span data-stu-id="56522-127">Remarks</span></span>  
 <span data-ttu-id="56522-128">在.NET Framework 4 之前的.NET Framework 版本中，PerfCounter.dll 載入的版本會對應至執行階段載入處理序中。</span><span class="sxs-lookup"><span data-stu-id="56522-128">In versions of the .NET Framework before the .NET Framework 4, the version of PerfCounter.dll that was loaded corresponded to the runtime that was loaded in the process.</span></span> <span data-ttu-id="56522-129">如果電腦已安裝.NET Framework 2.0 和.NET Framework 1.1 版，.NET Framework 1.1 應用程式會載入 PerfCounter.dll.NET Framework 1.1 版。</span><span class="sxs-lookup"><span data-stu-id="56522-129">If a computer had both the .NET Framework version 1.1 and the .NET Framework 2.0 installed, a .NET Framework 1.1 application would load the .NET Framework 1.1 version of PerfCounter.dll.</span></span> <span data-ttu-id="56522-130">從.NET Framework 4 開始，載入 PerfCounter.dll 已安裝最新版本。</span><span class="sxs-lookup"><span data-stu-id="56522-130">Starting with the .NET Framework 4, the newest installed version of PerfCounter.dll is loaded.</span></span> <span data-ttu-id="56522-131">這表示如果在電腦上安裝.NET Framework 4 的.NET Framework 1.1 應用程式會載入 PerfCounter.dll 的.NET Framework 4 版本。</span><span class="sxs-lookup"><span data-stu-id="56522-131">This means that a .NET Framework 1.1 application will load the .NET Framework 4 version of PerfCounter.dll if the .NET Framework 4 is installed on the computer.</span></span>  
  
 <span data-ttu-id="56522-132">從.NET Framework 4 中，使用效能計數器時，PerfCounter.dll 會檢查每個提供者，以判斷它是否應該從類別特定共用的記憶體或全域共用的記憶體讀取的 CategoryOptions 登錄項目。</span><span class="sxs-lookup"><span data-stu-id="56522-132">Starting with the .NET Framework 4, when consuming performance counters, PerfCounter.dll checks the CategoryOptions registry entry for each provider to determine whether it should read from category-specific shared memory or global shared memory.</span></span> <span data-ttu-id="56522-133">.NET Framework 1.1 PerfCounter.dll 不會讀取該登錄項目，因為它並不知道特定類別的共用記憶體中;它一律會從全域共用記憶體讀取。</span><span class="sxs-lookup"><span data-stu-id="56522-133">The .NET Framework 1.1 PerfCounter.dll does not read that registry entry, because it is not aware of category-specific shared memory; it always reads from global shared memory.</span></span>  
  
 <span data-ttu-id="56522-134">.NET Framework 4 PerfCounter.dll 回溯相容性，它不會檢查 CategoryOptions 登錄項目中的.NET Framework 1.1 應用程式執行時。</span><span class="sxs-lookup"><span data-stu-id="56522-134">For backward compatibility, the .NET Framework 4 PerfCounter.dll does not check the CategoryOptions registry entry when running in a .NET Framework 1.1 application.</span></span> <span data-ttu-id="56522-135">它會直接使用全域共用的記憶體的詳細資訊，就像.NET Framework 1.1 PerfCounter.dll 一樣。</span><span class="sxs-lookup"><span data-stu-id="56522-135">It simply uses global shared memory, just like the .NET Framework 1.1 PerfCounter.dll.</span></span> <span data-ttu-id="56522-136">不過，您可以指示檢查登錄設定，藉由啟用.NET Framework 4 PerfCounter.dll`<forcePerformanceCounterUniqueSharedMemoryReads>`項目。</span><span class="sxs-lookup"><span data-stu-id="56522-136">However, you can instruct the .NET Framework 4 PerfCounter.dll to check the registry setting by enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56522-137">啟用`<forcePerformanceCounterUniqueSharedMemoryReads>`項目並不保證就會使用該特定類別的共用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="56522-137">Enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element does not guarantee that category-specific shared memory will be used.</span></span> <span data-ttu-id="56522-138">若要啟用設定`true`只會導致 PerfCounter.dll 參考 CategoryOptions 登錄設定。</span><span class="sxs-lookup"><span data-stu-id="56522-138">Setting enabled to `true` only causes PerfCounter.dll to reference the CategoryOptions registry setting.</span></span> <span data-ttu-id="56522-139">CategoryOptions 的預設設定為使用特定類別的共用的記憶體中;不過，您可以變更 CategoryOptions 以指出應該使用全域共用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="56522-139">The default setting for CategoryOptions is to use category-specific shared memory; however, you can change CategoryOptions to indicate that global shared memory should be used.</span></span>  
  
 <span data-ttu-id="56522-140">包含 CategoryOptions 設定的登錄機碼是 HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\< categoryName\>\Performance。</span><span class="sxs-lookup"><span data-stu-id="56522-140">The registry key that contains the CategoryOptions setting is HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance.</span></span> <span data-ttu-id="56522-141">根據預設，CategoryOptions 設為 3，這個值會指示 PerfCounter.dll 使用特定類別的共用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="56522-141">By default, CategoryOptions is set to 3, which instructs PerfCounter.dll to use category-specific shared memory.</span></span> <span data-ttu-id="56522-142">如果 CategoryOptions 設定為 0，PerfCounter.dll 會使用全域共用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="56522-142">If CategoryOptions is set to 0, PerfCounter.dll uses global shared memory.</span></span> <span data-ttu-id="56522-143">正在建立的執行個體的名稱是與重複使用執行個體相同時，才會重複使用執行個體資料。</span><span class="sxs-lookup"><span data-stu-id="56522-143">Instance data will be reused only if the name of the instance being created is identical to the instance being reused.</span></span> <span data-ttu-id="56522-144">所有版本都都能夠寫入該類別。</span><span class="sxs-lookup"><span data-stu-id="56522-144">All versions will be able to write to the category.</span></span> <span data-ttu-id="56522-145">如果 CategoryOptions 設定為 1 時，使用全域共用的記憶體時，但類別目錄名稱是否為重複使用的類別相同的長度，可以重複使用執行個體資料。</span><span class="sxs-lookup"><span data-stu-id="56522-145">If CategoryOptions is set to 1, global shared memory is used, but instance data can be reused if the category name is the same length as the category being reused.</span></span>  
  
 <span data-ttu-id="56522-146">0 和 1 的設定可能會導致記憶體流失和效能計數器記憶體填滿。</span><span class="sxs-lookup"><span data-stu-id="56522-146">The settings 0 and 1 can lead to memory leaks and the filling up of performance counter memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56522-147">範例</span><span class="sxs-lookup"><span data-stu-id="56522-147">Example</span></span>  
 <span data-ttu-id="56522-148">下列範例示範如何指定 PerfCounter.dll 應該參考 CategoryOptions 登錄項目，以判斷是否應該使用特定類別的共用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="56522-148">The following example shows how to specify that PerfCounter.dll should reference the CategoryOptions registry entry to determine whether it should use category-specific shared memory.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="56522-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56522-149">See also</span></span>

- [<span data-ttu-id="56522-150">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="56522-150">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="56522-151">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="56522-151">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
