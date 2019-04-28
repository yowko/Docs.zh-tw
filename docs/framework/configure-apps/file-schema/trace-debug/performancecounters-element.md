---
title: <performanceCounters> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
- <performanceCounters> element
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
ms.openlocfilehash: 6144bcbda69b2ba799e87c3e7fa2118fbe4d9bf6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673729"
---
# <a name="performancecounters-element"></a><span data-ttu-id="c4d25-102">\<performanceCounters > 項目</span><span class="sxs-lookup"><span data-stu-id="c4d25-102">\<performanceCounters> Element</span></span>

<span data-ttu-id="c4d25-103">指定效能計數器共用之全域記憶體的大小。</span><span class="sxs-lookup"><span data-stu-id="c4d25-103">Specifies the size of the global memory shared by performance counters.</span></span>

 <span data-ttu-id="c4d25-104">\<configuration>\\</span><span class="sxs-lookup"><span data-stu-id="c4d25-104">\<configuration>\\</span></span>
<span data-ttu-id="c4d25-105">\<system.diagnostics>\\</span><span class="sxs-lookup"><span data-stu-id="c4d25-105">\<system.diagnostics>\\</span></span>
<span data-ttu-id="c4d25-106">\<performanceCounters></span><span class="sxs-lookup"><span data-stu-id="c4d25-106">\<performanceCounters></span></span>

## <a name="syntax"></a><span data-ttu-id="c4d25-107">語法</span><span class="sxs-lookup"><span data-stu-id="c4d25-107">Syntax</span></span>

```xml
<performanceCounters filemappingsize="524288" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c4d25-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c4d25-108">Attributes and Elements</span></span>

<span data-ttu-id="c4d25-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c4d25-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c4d25-110">屬性</span><span class="sxs-lookup"><span data-stu-id="c4d25-110">Attributes</span></span>

|<span data-ttu-id="c4d25-111">屬性</span><span class="sxs-lookup"><span data-stu-id="c4d25-111">Attribute</span></span>|<span data-ttu-id="c4d25-112">描述</span><span class="sxs-lookup"><span data-stu-id="c4d25-112">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="c4d25-113">filemappingsize</span><span class="sxs-lookup"><span data-stu-id="c4d25-113">filemappingsize</span></span>|<span data-ttu-id="c4d25-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="c4d25-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="c4d25-115">指定的大小，以位元組為單位，效能計數器所共用之全域記憶體。</span><span class="sxs-lookup"><span data-stu-id="c4d25-115">Specifies the size, in bytes, of the global memory shared by performance counters.</span></span> <span data-ttu-id="c4d25-116">預設值為 524288。</span><span class="sxs-lookup"><span data-stu-id="c4d25-116">The default is 524288.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="c4d25-117">子元素</span><span class="sxs-lookup"><span data-stu-id="c4d25-117">Child Elements</span></span>

<span data-ttu-id="c4d25-118">無。</span><span class="sxs-lookup"><span data-stu-id="c4d25-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c4d25-119">父項目</span><span class="sxs-lookup"><span data-stu-id="c4d25-119">Parent Elements</span></span>

|<span data-ttu-id="c4d25-120">項目</span><span class="sxs-lookup"><span data-stu-id="c4d25-120">Element</span></span>|<span data-ttu-id="c4d25-121">描述</span><span class="sxs-lookup"><span data-stu-id="c4d25-121">Description</span></span>|
|-------------|-----------------|
|`Configuration`|<span data-ttu-id="c4d25-122">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="c4d25-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`system.diagnostics`|<span data-ttu-id="c4d25-123">指定 ASP.NET 組態區段的根項目。</span><span class="sxs-lookup"><span data-stu-id="c4d25-123">Specifies the root element for the ASP.NET configuration section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c4d25-124">備註</span><span class="sxs-lookup"><span data-stu-id="c4d25-124">Remarks</span></span>

<span data-ttu-id="c4d25-125">效能計數器會使用記憶體對應檔案或共用的記憶體，來發行效能資料。</span><span class="sxs-lookup"><span data-stu-id="c4d25-125">Performance counters use a memory mapped file, or shared memory, to publish performance data.</span></span>  <span data-ttu-id="c4d25-126">共用記憶體的大小會決定可以一次使用多少個執行個體。</span><span class="sxs-lookup"><span data-stu-id="c4d25-126">The size of the shared memory determines how many instances can be used at once.</span></span>  <span data-ttu-id="c4d25-127">有兩種類型的共用記憶體： 全域共用記憶體和不同的共用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="c4d25-127">There are two types of shared memory: global shared memory and separate shared memory.</span></span>  <span data-ttu-id="c4d25-128">1.0 或 1.1 版的.NET Framework 版本與安裝的所有效能計數器分類會都使用全域共用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="c4d25-128">The global shared memory is used by all performance counter categories installed with the .NET Framework versions 1.0 or 1.1.</span></span>  <span data-ttu-id="c4d25-129">安裝.NET framework 2.0 版的效能計數器類別會使用不同的共用的記憶體，與每個效能計數器分類都有它自己的記憶體。</span><span class="sxs-lookup"><span data-stu-id="c4d25-129">Performance counter categories installed with the .NET Framework version 2.0 use separate shared memory, with each performance counter category having its own memory.</span></span>

<span data-ttu-id="c4d25-130">僅使用組態檔，可以設定全域共用記憶體的大小。</span><span class="sxs-lookup"><span data-stu-id="c4d25-130">The size of global shared memory can be set only with a configuration file.</span></span>  <span data-ttu-id="c4d25-131">預設大小為 524288 個位元組，大小上限是 33,554,432 位元組為單位，最小大小為 32768 個位元組。</span><span class="sxs-lookup"><span data-stu-id="c4d25-131">The default size is 524,288 byes, the maximum size is 33,554,432 bytes, and the minimum size is 32,768 bytes.</span></span>  <span data-ttu-id="c4d25-132">因為所有的處理程序與類別共用通用的共用的記憶體，第一次的建立者指定的大小。</span><span class="sxs-lookup"><span data-stu-id="c4d25-132">Since the global shared memory is shared by all processes and categories, the first creator specifies the size.</span></span>  <span data-ttu-id="c4d25-133">如果您在應用程式組態檔中定義的大小，是只會使用該大小，您的應用程式是否會導致要執行的效能計數器的第一個應用程式。</span><span class="sxs-lookup"><span data-stu-id="c4d25-133">If you define the size in your application configuration file, that size is only used if your application is the first application that causes the performance counters to execute.</span></span>  <span data-ttu-id="c4d25-134">因此正確的位置來指定`filemappingsize`值是在 Machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="c4d25-134">Therefore the correct location to specify the `filemappingsize` value is the Machine.config file.</span></span>  <span data-ttu-id="c4d25-135">無法釋放中全域共用記憶體的記憶體，由個別的效能計數器，因此最後還是全域共用的記憶體用完，如果會建立大量的效能計數器執行個體，以不同的名稱。</span><span class="sxs-lookup"><span data-stu-id="c4d25-135">Memory in the global shared memory cannot be released by individual performance counters, so eventually global shared memory is exhausted if a large number of performance counter instances with different names are created.</span></span>

<span data-ttu-id="c4d25-136">針對不同的共用記憶體的大小，在登錄中的 DWORD FileMappingSize 值索引鍵 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<類別名稱 >* \Performance 參考首先，後面接著全域共用記憶體的組態檔中指定的值。</span><span class="sxs-lookup"><span data-stu-id="c4d25-136">For the size of separate shared memory, the DWORD FileMappingSize value in the registry key HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<category name>* \Performance is referenced first, followed by the value specified for the global shared memory in the configuration file.</span></span> <span data-ttu-id="c4d25-137">如果 FileMappingSize 值不存在，則不同的共用的記憶體大小設定為其中一個第四個 (1/4) 組態檔中的全域設定。</span><span class="sxs-lookup"><span data-stu-id="c4d25-137">If the FileMappingSize value does not exist, then the separate shared memory size is set to one fourth (1/4) the global setting in the configuration file.</span></span>

## <a name="see-also"></a><span data-ttu-id="c4d25-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4d25-138">See also</span></span>

- <xref:System.Diagnostics.PerformanceCounter>
- <xref:System.Diagnostics.PerformanceCounterCategory>
- <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>
- <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
