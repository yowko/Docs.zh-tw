---
title: <forcePerformanceCounterUniqueSharedMemoryReads> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
ms.openlocfilehash: 742b444c445ba67d6977b622e615a6a8f591826e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154136"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a><span data-ttu-id="76937-102">\<強制效能計數器唯一共用記憶體讀取>元素</span><span class="sxs-lookup"><span data-stu-id="76937-102">\<forcePerformanceCounterUniqueSharedMemoryReads> Element</span></span>
<span data-ttu-id="76937-103">指定 PerfCounter.dll 是否在 .NET Framework 1.1 版的應用程式中使用 CategoryOptions 登錄設定，以決定要從類別特定共用記憶體或從全域記憶體載入效能計數器資料。</span><span class="sxs-lookup"><span data-stu-id="76937-103">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>  
  
<span data-ttu-id="76937-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="76937-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="76937-105">&nbsp;&nbsp;[**\<運行時>**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="76937-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="76937-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<強制效能計數器唯一共用記憶體讀取>**</span><span class="sxs-lookup"><span data-stu-id="76937-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<forcePerformanceCounterUniqueSharedMemoryReads>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76937-107">語法</span><span class="sxs-lookup"><span data-stu-id="76937-107">Syntax</span></span>  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76937-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="76937-108">Attributes and Elements</span></span>  
 <span data-ttu-id="76937-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="76937-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76937-110">屬性</span><span class="sxs-lookup"><span data-stu-id="76937-110">Attributes</span></span>  
  
|<span data-ttu-id="76937-111">屬性</span><span class="sxs-lookup"><span data-stu-id="76937-111">Attribute</span></span>|<span data-ttu-id="76937-112">描述</span><span class="sxs-lookup"><span data-stu-id="76937-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="76937-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="76937-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="76937-114">指示 PerfCounter.dll 是否使用"類別選項"註冊表設置來確定是從特定于類別的共用記憶體或全域記憶體載入效能計數器資料。</span><span class="sxs-lookup"><span data-stu-id="76937-114">Indicates whether PerfCounter.dll uses the CategoryOptions registry setting to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="76937-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="76937-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="76937-116">值</span><span class="sxs-lookup"><span data-stu-id="76937-116">Value</span></span>|<span data-ttu-id="76937-117">描述</span><span class="sxs-lookup"><span data-stu-id="76937-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="76937-118">PerfCounter.dll 不使用類別選項註冊表設置這是預設值。</span><span class="sxs-lookup"><span data-stu-id="76937-118">PerfCounter.dll does not use the CategoryOptions registry setting This is the default.</span></span>|  
|`true`|<span data-ttu-id="76937-119">PerfCounter.dll 確實使用類別選項註冊表設置。</span><span class="sxs-lookup"><span data-stu-id="76937-119">PerfCounter.dll does use the CategoryOptions registry setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="76937-120">子元素</span><span class="sxs-lookup"><span data-stu-id="76937-120">Child Elements</span></span>  
 <span data-ttu-id="76937-121">無。</span><span class="sxs-lookup"><span data-stu-id="76937-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="76937-122">父項目</span><span class="sxs-lookup"><span data-stu-id="76937-122">Parent Elements</span></span>  
  
|<span data-ttu-id="76937-123">元素</span><span class="sxs-lookup"><span data-stu-id="76937-123">Element</span></span>|<span data-ttu-id="76937-124">描述</span><span class="sxs-lookup"><span data-stu-id="76937-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="76937-125">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="76937-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="76937-126">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="76937-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76937-127">備註</span><span class="sxs-lookup"><span data-stu-id="76937-127">Remarks</span></span>  
 <span data-ttu-id="76937-128">在 .NET 框架 4 之前的 .NET 框架版本中，載入的 PerfCounter.dll 版本對應于進程中載入的運行時。</span><span class="sxs-lookup"><span data-stu-id="76937-128">In versions of the .NET Framework before the .NET Framework 4, the version of PerfCounter.dll that was loaded corresponded to the runtime that was loaded in the process.</span></span> <span data-ttu-id="76937-129">如果電腦同時安裝了 .NET 框架版本 1.1 和 .NET Framework 2.0，則 .NET 框架 1.1 應用程式將載入 PerfCounter.dll 的 .NET 框架 1.1 版本。</span><span class="sxs-lookup"><span data-stu-id="76937-129">If a computer had both the .NET Framework version 1.1 and the .NET Framework 2.0 installed, a .NET Framework 1.1 application would load the .NET Framework 1.1 version of PerfCounter.dll.</span></span> <span data-ttu-id="76937-130">從 .NET 框架 4 開始，將載入最新的已安裝版本的 PerfCounter.dll。</span><span class="sxs-lookup"><span data-stu-id="76937-130">Starting with the .NET Framework 4, the newest installed version of PerfCounter.dll is loaded.</span></span> <span data-ttu-id="76937-131">這意味著.NET 框架 1.1 應用程式將載入 .NET 框架 4 版本的 PerfCounter.dll，如果 .NET 框架 4 安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="76937-131">This means that a .NET Framework 1.1 application will load the .NET Framework 4 version of PerfCounter.dll if the .NET Framework 4 is installed on the computer.</span></span>  
  
 <span data-ttu-id="76937-132">從 .NET 框架 4 開始，使用效能計數器時，PerfCounter.dll 會檢查每個提供程式的類別選項登錄機碼，以確定是否應從特定于類別的共用記憶體或全域共用記憶體讀取該條目。</span><span class="sxs-lookup"><span data-stu-id="76937-132">Starting with the .NET Framework 4, when consuming performance counters, PerfCounter.dll checks the CategoryOptions registry entry for each provider to determine whether it should read from category-specific shared memory or global shared memory.</span></span> <span data-ttu-id="76937-133">.NET 框架 1.1 PerfCounter.dll 不讀取該登錄機碼，因為它不知道特定于類別的共用記憶體;它總是從全域共用記憶體讀取。</span><span class="sxs-lookup"><span data-stu-id="76937-133">The .NET Framework 1.1 PerfCounter.dll does not read that registry entry, because it is not aware of category-specific shared memory; it always reads from global shared memory.</span></span>  
  
 <span data-ttu-id="76937-134">對於向後相容性，.NET 框架 4 PerfCounter.dll 在 .NET 框架 1.1 應用程式中運行時不檢查類別選項登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="76937-134">For backward compatibility, the .NET Framework 4 PerfCounter.dll does not check the CategoryOptions registry entry when running in a .NET Framework 1.1 application.</span></span> <span data-ttu-id="76937-135">它只使用全域共用記憶體，就像 .NET 框架 1.1 PerfCounter.dll 一樣。</span><span class="sxs-lookup"><span data-stu-id="76937-135">It simply uses global shared memory, just like the .NET Framework 1.1 PerfCounter.dll.</span></span> <span data-ttu-id="76937-136">但是，您可以指示 .NET 框架 4 PerfCounter.dll 通過啟用`<forcePerformanceCounterUniqueSharedMemoryReads>`該元素來檢查註冊表設置。</span><span class="sxs-lookup"><span data-stu-id="76937-136">However, you can instruct the .NET Framework 4 PerfCounter.dll to check the registry setting by enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="76937-137">啟用該`<forcePerformanceCounterUniqueSharedMemoryReads>`元素並不保證將使用特定于類別的共用記憶體。</span><span class="sxs-lookup"><span data-stu-id="76937-137">Enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element does not guarantee that category-specific shared memory will be used.</span></span> <span data-ttu-id="76937-138">設置為僅啟用`true`PerfCounter.dll 以引用類別選項註冊表設置。</span><span class="sxs-lookup"><span data-stu-id="76937-138">Setting enabled to `true` only causes PerfCounter.dll to reference the CategoryOptions registry setting.</span></span> <span data-ttu-id="76937-139">"類別選項"的預設設置是使用特定于類別的共用記憶體;但是，您可以更改類別選項以指示應使用全域共用記憶體。</span><span class="sxs-lookup"><span data-stu-id="76937-139">The default setting for CategoryOptions is to use category-specific shared memory; however, you can change CategoryOptions to indicate that global shared memory should be used.</span></span>  
  
 <span data-ttu-id="76937-140">包含"類別選項"設置的登錄機碼HKEY_LOCAL_MACHINE_System_CurrentControlSet_服務\\<類別名稱\>\性能。</span><span class="sxs-lookup"><span data-stu-id="76937-140">The registry key that contains the CategoryOptions setting is HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance.</span></span> <span data-ttu-id="76937-141">預設情況下，類別選項設置為 3，指示 PerfCounter.dll 使用特定于類別的共用記憶體。</span><span class="sxs-lookup"><span data-stu-id="76937-141">By default, CategoryOptions is set to 3, which instructs PerfCounter.dll to use category-specific shared memory.</span></span> <span data-ttu-id="76937-142">如果類別選項設置為 0，PerfCounter.dll 將使用全域共用記憶體。</span><span class="sxs-lookup"><span data-stu-id="76937-142">If CategoryOptions is set to 0, PerfCounter.dll uses global shared memory.</span></span> <span data-ttu-id="76937-143">僅當要創建的實例的名稱與正在重用的實例相同時，才會重用實例資料。</span><span class="sxs-lookup"><span data-stu-id="76937-143">Instance data will be reused only if the name of the instance being created is identical to the instance being reused.</span></span> <span data-ttu-id="76937-144">所有版本將能夠寫入類別。</span><span class="sxs-lookup"><span data-stu-id="76937-144">All versions will be able to write to the category.</span></span> <span data-ttu-id="76937-145">如果"類別選項"設置為 1，則使用全域共用記憶體，但如果類別名稱的長度與正在重用的類別長度相同，則可以重複使用實例資料。</span><span class="sxs-lookup"><span data-stu-id="76937-145">If CategoryOptions is set to 1, global shared memory is used, but instance data can be reused if the category name is the same length as the category being reused.</span></span>  
  
 <span data-ttu-id="76937-146">設置 0 和 1 可能導致記憶體洩漏和效能計數器記憶體填滿。</span><span class="sxs-lookup"><span data-stu-id="76937-146">The settings 0 and 1 can lead to memory leaks and the filling up of performance counter memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76937-147">範例</span><span class="sxs-lookup"><span data-stu-id="76937-147">Example</span></span>  
 <span data-ttu-id="76937-148">下面的示例演示如何指定 PerfCounter.dll 應引用類別選項登錄機碼以確定是否應使用特定于類別的共用記憶體。</span><span class="sxs-lookup"><span data-stu-id="76937-148">The following example shows how to specify that PerfCounter.dll should reference the CategoryOptions registry entry to determine whether it should use category-specific shared memory.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="76937-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76937-149">See also</span></span>

- [<span data-ttu-id="76937-150">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="76937-150">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="76937-151">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="76937-151">Configuration File Schema</span></span>](../index.md)
