---
title: "&lt;forcePerformanceCounterUniqueSharedMemoryReads&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4c90799ed2db061e8f42cde79804789eb8d2da0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltforceperformancecounteruniquesharedmemoryreadsgt-element"></a><span data-ttu-id="55cb2-102">&lt;forcePerformanceCounterUniqueSharedMemoryReads&gt;項目</span><span class="sxs-lookup"><span data-stu-id="55cb2-102">&lt;forcePerformanceCounterUniqueSharedMemoryReads&gt; Element</span></span>
<span data-ttu-id="55cb2-103">指定 PerfCounter.dll 是否在 .NET Framework 1.1 版的應用程式中使用 CategoryOptions 登錄設定，以決定要從類別特定共用記憶體或從全域記憶體載入效能計數器資料。</span><span class="sxs-lookup"><span data-stu-id="55cb2-103">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>  
  
 <span data-ttu-id="55cb2-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="55cb2-104">\<configuration></span></span>  
<span data-ttu-id="55cb2-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="55cb2-105">\<runtime></span></span>  
<span data-ttu-id="55cb2-106">\<forcePerformanceCounterUniqueSharedMemoryReads ></span><span class="sxs-lookup"><span data-stu-id="55cb2-106">\<forcePerformanceCounterUniqueSharedMemoryReads></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55cb2-107">語法</span><span class="sxs-lookup"><span data-stu-id="55cb2-107">Syntax</span></span>  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads   
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55cb2-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="55cb2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="55cb2-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="55cb2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55cb2-110">屬性</span><span class="sxs-lookup"><span data-stu-id="55cb2-110">Attributes</span></span>  
  
|<span data-ttu-id="55cb2-111">屬性</span><span class="sxs-lookup"><span data-stu-id="55cb2-111">Attribute</span></span>|<span data-ttu-id="55cb2-112">描述</span><span class="sxs-lookup"><span data-stu-id="55cb2-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="55cb2-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="55cb2-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="55cb2-114">表示是否 PerfCounter.dll 使用 CategoryOptions 登錄設定來判斷是否要從特定類別的共用的記憶體或全域記憶體中載入效能計數器資料。</span><span class="sxs-lookup"><span data-stu-id="55cb2-114">Indicates whether PerfCounter.dll uses the CategoryOptions registry setting to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="55cb2-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="55cb2-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="55cb2-116">值</span><span class="sxs-lookup"><span data-stu-id="55cb2-116">Value</span></span>|<span data-ttu-id="55cb2-117">說明</span><span class="sxs-lookup"><span data-stu-id="55cb2-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="55cb2-118">PerfCounter.dll 不會使用 CategoryOptions 登錄設定，這是預設值。</span><span class="sxs-lookup"><span data-stu-id="55cb2-118">PerfCounter.dll does not use the CategoryOptions registry setting This is the default.</span></span>|  
|`true`|<span data-ttu-id="55cb2-119">PerfCounter.dll 並使用 CategoryOptions 登錄設定。</span><span class="sxs-lookup"><span data-stu-id="55cb2-119">PerfCounter.dll does use the CategoryOptions registry setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="55cb2-120">子元素</span><span class="sxs-lookup"><span data-stu-id="55cb2-120">Child Elements</span></span>  
 <span data-ttu-id="55cb2-121">無。</span><span class="sxs-lookup"><span data-stu-id="55cb2-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="55cb2-122">父項目</span><span class="sxs-lookup"><span data-stu-id="55cb2-122">Parent Elements</span></span>  
  
|<span data-ttu-id="55cb2-123">項目</span><span class="sxs-lookup"><span data-stu-id="55cb2-123">Element</span></span>|<span data-ttu-id="55cb2-124">描述</span><span class="sxs-lookup"><span data-stu-id="55cb2-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="55cb2-125">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="55cb2-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="55cb2-126">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="55cb2-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55cb2-127">備註</span><span class="sxs-lookup"><span data-stu-id="55cb2-127">Remarks</span></span>  
 <span data-ttu-id="55cb2-128">在之前的.NET Framework 的版本中[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]，PerfCounter.dll 載入的版本對應到已載入到處理序的執行階段。</span><span class="sxs-lookup"><span data-stu-id="55cb2-128">In versions of the .NET Framework before the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], the version of PerfCounter.dll that was loaded corresponded to the runtime that was loaded in the process.</span></span> <span data-ttu-id="55cb2-129">如果電腦已同時以.NET Framework 1.1 版和[!INCLUDE[dnprdnlong](../../../../../includes/dnprdnlong-md.md)]安裝，.NET Framework 1.1 應用程式會載入 PerfCounter.dll.NET Framework 1.1 版。</span><span class="sxs-lookup"><span data-stu-id="55cb2-129">If a computer had both the .NET Framework version 1.1 and the [!INCLUDE[dnprdnlong](../../../../../includes/dnprdnlong-md.md)] installed, a .NET Framework 1.1 application would load the .NET Framework 1.1 version of PerfCounter.dll.</span></span> <span data-ttu-id="55cb2-130">從開始[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]，已載入 PerfCounter.dll 已安裝最新版本。</span><span class="sxs-lookup"><span data-stu-id="55cb2-130">Starting with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], the newest installed version of PerfCounter.dll is loaded.</span></span> <span data-ttu-id="55cb2-131">這表示，.NET Framework 1.1 應用程式將會載入[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]PerfCounter.dll 版本如果[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="55cb2-131">This means that a .NET Framework 1.1 application will load the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] version of PerfCounter.dll if the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] is installed on the computer.</span></span>  
  
 <span data-ttu-id="55cb2-132">從開始[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]，PerfCounter.dll 取用時效能計數器，檢查每個提供者，以判斷它是否應該從特定類別的共用的記憶體或全域共用的記憶體讀取的 CategoryOptions 登錄項目。</span><span class="sxs-lookup"><span data-stu-id="55cb2-132">Starting with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], when consuming performance counters, PerfCounter.dll checks the CategoryOptions registry entry for each provider to determine whether it should read from category-specific shared memory or global shared memory.</span></span> <span data-ttu-id="55cb2-133">.NET Framework 1.1 PerfCounter.dll 不會讀取該登錄項目，因為它並不知道特定類別的共用記憶體。它一定會讀取從全域共用記憶體。</span><span class="sxs-lookup"><span data-stu-id="55cb2-133">The .NET Framework 1.1 PerfCounter.dll does not read that registry entry, because it is not aware of category-specific shared memory; it always reads from global shared memory.</span></span>  
  
 <span data-ttu-id="55cb2-134">回溯相容性， [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll 在.NET Framework 1.1 應用程式中執行時不會檢查 CategoryOptions 登錄項目。</span><span class="sxs-lookup"><span data-stu-id="55cb2-134">For backward compatibility, the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll does not check the CategoryOptions registry entry when running in a .NET Framework 1.1 application.</span></span> <span data-ttu-id="55cb2-135">它只會使用全域共用的記憶體，如同.NET Framework 1.1 PerfCounter.dll。</span><span class="sxs-lookup"><span data-stu-id="55cb2-135">It simply uses global shared memory, just like the .NET Framework 1.1 PerfCounter.dll.</span></span> <span data-ttu-id="55cb2-136">不過，您可以指示[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]檢查登錄設定，藉由啟用 PerfCounter.dll`<forcePerformanceCounterUniqueSharedMemoryReads>`項目。</span><span class="sxs-lookup"><span data-stu-id="55cb2-136">However, you can instruct the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll to check the registry setting by enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55cb2-137">啟用`<forcePerformanceCounterUniqueSharedMemoryReads>`項目並不保證就會使用該特定類別的共用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="55cb2-137">Enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element does not guarantee that category-specific shared memory will be used.</span></span> <span data-ttu-id="55cb2-138">若要啟用設定`true`只會導致 PerfCounter.dll 參考 CategoryOptions 登錄設定。</span><span class="sxs-lookup"><span data-stu-id="55cb2-138">Setting enabled to `true` only causes PerfCounter.dll to reference the CategoryOptions registry setting.</span></span> <span data-ttu-id="55cb2-139">CategoryOptions 的預設值是使用特定類別的共用的記憶體。不過，您可以變更 CategoryOptions 以指出應該使用全域共用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="55cb2-139">The default setting for CategoryOptions is to use category-specific shared memory; however, you can change CategoryOptions to indicate that global shared memory should be used.</span></span>  
  
 <span data-ttu-id="55cb2-140">包含 CategoryOptions 設定的登錄機碼是 HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\< 類別名稱\>\Performance。</span><span class="sxs-lookup"><span data-stu-id="55cb2-140">The registry key that contains the CategoryOptions setting is HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance.</span></span> <span data-ttu-id="55cb2-141">根據預設，CategoryOptions 設為 3，它會指示 PerfCounter.dll 使用特定類別目錄的共用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="55cb2-141">By default, CategoryOptions is set to 3, which instructs PerfCounter.dll to use category-specific shared memory.</span></span> <span data-ttu-id="55cb2-142">如果 CategoryOptions 設定為 0，PerfCounter.dll 會使用全域共用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="55cb2-142">If CategoryOptions is set to 0, PerfCounter.dll uses global shared memory.</span></span> <span data-ttu-id="55cb2-143">正在建立的執行個體的名稱是等於重複使用的執行個體時，才會重複使用執行個體資料。</span><span class="sxs-lookup"><span data-stu-id="55cb2-143">Instance data will be reused only if the name of the instance being created is identical to the instance being reused.</span></span> <span data-ttu-id="55cb2-144">所有版本將都能夠寫入該類別。</span><span class="sxs-lookup"><span data-stu-id="55cb2-144">All versions will be able to write to the category.</span></span> <span data-ttu-id="55cb2-145">如果 CategoryOptions 設定為 1 時，使用全域共用的記憶體，但類別名稱是否為類別重複使用相同的長度，可以重複使用執行個體資料。</span><span class="sxs-lookup"><span data-stu-id="55cb2-145">If CategoryOptions is set to 1, global shared memory is used, but instance data can be reused if the category name is the same length as the category being reused.</span></span>  
  
 <span data-ttu-id="55cb2-146">0 和 1 的設定可能會導致記憶體流失和效能計數器記憶體填滿。</span><span class="sxs-lookup"><span data-stu-id="55cb2-146">The settings 0 and 1 can lead to memory leaks and the filling up of performance counter memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55cb2-147">範例</span><span class="sxs-lookup"><span data-stu-id="55cb2-147">Example</span></span>  
 <span data-ttu-id="55cb2-148">下列範例會示範如何指定 PerfCounter.dll 應該參考 CategoryOptions 登錄項目，以判斷是否應該使用特定類別的共用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="55cb2-148">The following example shows how to specify that PerfCounter.dll should reference the CategoryOptions registry entry to determine whether it should use category-specific shared memory.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="55cb2-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55cb2-149">See Also</span></span>  
 [<span data-ttu-id="55cb2-150">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="55cb2-150">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="55cb2-151">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="55cb2-151">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
