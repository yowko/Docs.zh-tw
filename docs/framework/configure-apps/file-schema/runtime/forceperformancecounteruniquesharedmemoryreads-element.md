---
title: <forcePerformanceCounterUniqueSharedMemoryReads> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
ms.openlocfilehash: 719448ba3de2aca0621fc17b9fadbdd3b8588f2e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178238"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a><span data-ttu-id="2fc02-102">\<forcePerformanceCounterUniqueSharedMemoryReads> 項目</span><span class="sxs-lookup"><span data-stu-id="2fc02-102">\<forcePerformanceCounterUniqueSharedMemoryReads> Element</span></span>

<span data-ttu-id="2fc02-103">指定 PerfCounter.dll 是否在 .NET Framework 1.1 版的應用程式中使用 CategoryOptions 登錄設定，以決定要從類別特定共用記憶體或從全域記憶體載入效能計數器資料。</span><span class="sxs-lookup"><span data-stu-id="2fc02-103">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<forcePerformanceCounterUniqueSharedMemoryReads>**  
  
## <a name="syntax"></a><span data-ttu-id="2fc02-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="2fc02-104">Syntax</span></span>  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2fc02-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2fc02-105">Attributes and Elements</span></span>  

 <span data-ttu-id="2fc02-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2fc02-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2fc02-107">屬性</span><span class="sxs-lookup"><span data-stu-id="2fc02-107">Attributes</span></span>  
  
|<span data-ttu-id="2fc02-108">屬性</span><span class="sxs-lookup"><span data-stu-id="2fc02-108">Attribute</span></span>|<span data-ttu-id="2fc02-109">描述</span><span class="sxs-lookup"><span data-stu-id="2fc02-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="2fc02-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="2fc02-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="2fc02-111">指出 PerfCounter.dll 是否使用 CategoryOptions 登錄設定來判斷是否要從類別專用的共用記憶體或全域記憶體載入效能計數器資料。</span><span class="sxs-lookup"><span data-stu-id="2fc02-111">Indicates whether PerfCounter.dll uses the CategoryOptions registry setting to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="2fc02-112">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="2fc02-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="2fc02-113">值</span><span class="sxs-lookup"><span data-stu-id="2fc02-113">Value</span></span>|<span data-ttu-id="2fc02-114">描述</span><span class="sxs-lookup"><span data-stu-id="2fc02-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="2fc02-115">PerfCounter.dll 不使用 CategoryOptions 登錄設定，這是預設值。</span><span class="sxs-lookup"><span data-stu-id="2fc02-115">PerfCounter.dll does not use the CategoryOptions registry setting This is the default.</span></span>|  
|`true`|<span data-ttu-id="2fc02-116">PerfCounter.dll 會使用 CategoryOptions 登錄設定。</span><span class="sxs-lookup"><span data-stu-id="2fc02-116">PerfCounter.dll does use the CategoryOptions registry setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2fc02-117">子元素</span><span class="sxs-lookup"><span data-stu-id="2fc02-117">Child Elements</span></span>  

 <span data-ttu-id="2fc02-118">無。</span><span class="sxs-lookup"><span data-stu-id="2fc02-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2fc02-119">父項目</span><span class="sxs-lookup"><span data-stu-id="2fc02-119">Parent Elements</span></span>  
  
|<span data-ttu-id="2fc02-120">項目</span><span class="sxs-lookup"><span data-stu-id="2fc02-120">Element</span></span>|<span data-ttu-id="2fc02-121">描述</span><span class="sxs-lookup"><span data-stu-id="2fc02-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2fc02-122">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="2fc02-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="2fc02-123">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="2fc02-123">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2fc02-124">備註</span><span class="sxs-lookup"><span data-stu-id="2fc02-124">Remarks</span></span>  

 <span data-ttu-id="2fc02-125">在 .NET Framework 4 之前的 .NET Framework 版本中，已載入的 PerfCounter.dll 版本會對應至在進程中載入的執行時間。</span><span class="sxs-lookup"><span data-stu-id="2fc02-125">In versions of the .NET Framework before the .NET Framework 4, the version of PerfCounter.dll that was loaded corresponded to the runtime that was loaded in the process.</span></span> <span data-ttu-id="2fc02-126">如果電腦同時安裝了 .NET Framework 1.1 版和 .NET Framework 2.0，則 .NET Framework 1.1 應用程式會載入 .NET Framework 1.1 版的 PerfCounter.dll。</span><span class="sxs-lookup"><span data-stu-id="2fc02-126">If a computer had both the .NET Framework version 1.1 and the .NET Framework 2.0 installed, a .NET Framework 1.1 application would load the .NET Framework 1.1 version of PerfCounter.dll.</span></span> <span data-ttu-id="2fc02-127">從 .NET Framework 4 開始，會載入 PerfCounter.dll 的最新安裝版本。</span><span class="sxs-lookup"><span data-stu-id="2fc02-127">Starting with the .NET Framework 4, the newest installed version of PerfCounter.dll is loaded.</span></span> <span data-ttu-id="2fc02-128">這表示，如果電腦上已安裝 .NET Framework 4，.NET Framework 1.1 應用程式將會載入 .NET Framework 4 版的 PerfCounter.dll。</span><span class="sxs-lookup"><span data-stu-id="2fc02-128">This means that a .NET Framework 1.1 application will load the .NET Framework 4 version of PerfCounter.dll if the .NET Framework 4 is installed on the computer.</span></span>  
  
 <span data-ttu-id="2fc02-129">從 .NET Framework 4 開始，使用效能計數器時，PerfCounter.dll 會檢查每個提供者的 CategoryOptions 登錄專案，以判斷是否應該從類別特定的共用記憶體或全域共用記憶體讀取。</span><span class="sxs-lookup"><span data-stu-id="2fc02-129">Starting with the .NET Framework 4, when consuming performance counters, PerfCounter.dll checks the CategoryOptions registry entry for each provider to determine whether it should read from category-specific shared memory or global shared memory.</span></span> <span data-ttu-id="2fc02-130">.NET Framework 1.1 PerfCounter.dll 不會讀取該登錄專案，因為它不知道類別專用的共用記憶體;它一律會從全域共用記憶體中讀取。</span><span class="sxs-lookup"><span data-stu-id="2fc02-130">The .NET Framework 1.1 PerfCounter.dll does not read that registry entry, because it is not aware of category-specific shared memory; it always reads from global shared memory.</span></span>  
  
 <span data-ttu-id="2fc02-131">為了與舊版相容，.NET Framework 4 PerfCounter.dll 不會在 .NET Framework 1.1 應用程式中執行時檢查 CategoryOptions 登錄專案。</span><span class="sxs-lookup"><span data-stu-id="2fc02-131">For backward compatibility, the .NET Framework 4 PerfCounter.dll does not check the CategoryOptions registry entry when running in a .NET Framework 1.1 application.</span></span> <span data-ttu-id="2fc02-132">它只會使用全域共用記憶體，就像 .NET Framework 1.1 PerfCounter.dll 一樣。</span><span class="sxs-lookup"><span data-stu-id="2fc02-132">It simply uses global shared memory, just like the .NET Framework 1.1 PerfCounter.dll.</span></span> <span data-ttu-id="2fc02-133">不過，您可以藉由啟用元素來指示 .NET Framework 4 PerfCounter.dll 檢查登錄設定 `<forcePerformanceCounterUniqueSharedMemoryReads>` 。</span><span class="sxs-lookup"><span data-stu-id="2fc02-133">However, you can instruct the .NET Framework 4 PerfCounter.dll to check the registry setting by enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2fc02-134">啟用專案 `<forcePerformanceCounterUniqueSharedMemoryReads>` 並不保證將會使用類別特定的共用記憶體。</span><span class="sxs-lookup"><span data-stu-id="2fc02-134">Enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element does not guarantee that category-specific shared memory will be used.</span></span> <span data-ttu-id="2fc02-135">將啟用設定為 `true` 只會導致 PerfCounter.dll 參考 CategoryOptions 登錄設定。</span><span class="sxs-lookup"><span data-stu-id="2fc02-135">Setting enabled to `true` only causes PerfCounter.dll to reference the CategoryOptions registry setting.</span></span> <span data-ttu-id="2fc02-136">CategoryOptions 的預設設定是使用類別專用的共用記憶體;不過，您可以變更 CategoryOptions，以指出應該使用全域共用記憶體。</span><span class="sxs-lookup"><span data-stu-id="2fc02-136">The default setting for CategoryOptions is to use category-specific shared memory; however, you can change CategoryOptions to indicate that global shared memory should be used.</span></span>  
  
 <span data-ttu-id="2fc02-137">包含 CategoryOptions 設定的登錄機碼是 HKEY_LOCAL_MACHINE \System\CurrentControlSet\Services \\<類別名稱 \> \Performance。</span><span class="sxs-lookup"><span data-stu-id="2fc02-137">The registry key that contains the CategoryOptions setting is HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance.</span></span> <span data-ttu-id="2fc02-138">根據預設，CategoryOptions 會設定為3，這會指示 PerfCounter.dll 使用分類專屬的共用記憶體。</span><span class="sxs-lookup"><span data-stu-id="2fc02-138">By default, CategoryOptions is set to 3, which instructs PerfCounter.dll to use category-specific shared memory.</span></span> <span data-ttu-id="2fc02-139">如果 CategoryOptions 設定為0，PerfCounter.dll 會使用全域共用記憶體。</span><span class="sxs-lookup"><span data-stu-id="2fc02-139">If CategoryOptions is set to 0, PerfCounter.dll uses global shared memory.</span></span> <span data-ttu-id="2fc02-140">只有當要建立的實例名稱與要重複使用的實例相同時，才會重複使用實例資料。</span><span class="sxs-lookup"><span data-stu-id="2fc02-140">Instance data will be reused only if the name of the instance being created is identical to the instance being reused.</span></span> <span data-ttu-id="2fc02-141">所有版本都將能夠寫入至類別目錄。</span><span class="sxs-lookup"><span data-stu-id="2fc02-141">All versions will be able to write to the category.</span></span> <span data-ttu-id="2fc02-142">如果 CategoryOptions 設定為1，則會使用全域共用記憶體，但如果類別目錄名稱的長度與要重複使用的類別相同，則可重複使用實例資料。</span><span class="sxs-lookup"><span data-stu-id="2fc02-142">If CategoryOptions is set to 1, global shared memory is used, but instance data can be reused if the category name is the same length as the category being reused.</span></span>  
  
 <span data-ttu-id="2fc02-143">設定0和1可能會導致記憶體流失，以及填滿效能計數器記憶體。</span><span class="sxs-lookup"><span data-stu-id="2fc02-143">The settings 0 and 1 can lead to memory leaks and the filling up of performance counter memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2fc02-144">範例</span><span class="sxs-lookup"><span data-stu-id="2fc02-144">Example</span></span>  

 <span data-ttu-id="2fc02-145">下列範例示範如何指定 PerfCounter.dll 應該參考 CategoryOptions 登錄專案，以判斷是否應該使用類別專用的共用記憶體。</span><span class="sxs-lookup"><span data-stu-id="2fc02-145">The following example shows how to specify that PerfCounter.dll should reference the CategoryOptions registry entry to determine whether it should use category-specific shared memory.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2fc02-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2fc02-146">See also</span></span>

- [<span data-ttu-id="2fc02-147">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="2fc02-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2fc02-148">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="2fc02-148">Configuration File Schema</span></span>](../index.md)
