---
title: '&lt;performanceCounters&gt;項目'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
- <perfomanceCounters> element
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: cb4af08095c14c0c748a79f53104d8454d3dcd47
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltperformancecountersgt-element"></a><span data-ttu-id="49a50-102">&lt;performanceCounters&gt;項目</span><span class="sxs-lookup"><span data-stu-id="49a50-102">&lt;performanceCounters&gt; Element</span></span>
<span data-ttu-id="49a50-103">指定效能計數器共用之全域記憶體的大小。</span><span class="sxs-lookup"><span data-stu-id="49a50-103">Specifies the size of the global memory shared by performance counters.</span></span>  
  
 <span data-ttu-id="49a50-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="49a50-104">\<configuration></span></span>  
<span data-ttu-id="49a50-105">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="49a50-105">\<system.diagnostics></span></span>  
<span data-ttu-id="49a50-106">\<performanceCounters></span><span class="sxs-lookup"><span data-stu-id="49a50-106">\<performanceCounters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49a50-107">語法</span><span class="sxs-lookup"><span data-stu-id="49a50-107">Syntax</span></span>  
  
```xml  
<performanceCounters filemappingsize="524288" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="49a50-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="49a50-108">Attributes and Elements</span></span>  
 <span data-ttu-id="49a50-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="49a50-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="49a50-110">屬性</span><span class="sxs-lookup"><span data-stu-id="49a50-110">Attributes</span></span>  
  
|<span data-ttu-id="49a50-111">屬性</span><span class="sxs-lookup"><span data-stu-id="49a50-111">Attribute</span></span>|<span data-ttu-id="49a50-112">描述</span><span class="sxs-lookup"><span data-stu-id="49a50-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="49a50-113">filemappingsize</span><span class="sxs-lookup"><span data-stu-id="49a50-113">filemappingsize</span></span>|<span data-ttu-id="49a50-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="49a50-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="49a50-115">指定的大小，以位元組為單位的效能計數器所共用的全域記憶體。</span><span class="sxs-lookup"><span data-stu-id="49a50-115">Specifies the size, in bytes, of the global memory shared by performance counters.</span></span> <span data-ttu-id="49a50-116">預設值為 524288。</span><span class="sxs-lookup"><span data-stu-id="49a50-116">The default is 524288.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="49a50-117">子項目</span><span class="sxs-lookup"><span data-stu-id="49a50-117">Child Elements</span></span>  
 <span data-ttu-id="49a50-118">無。</span><span class="sxs-lookup"><span data-stu-id="49a50-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="49a50-119">父項目</span><span class="sxs-lookup"><span data-stu-id="49a50-119">Parent Elements</span></span>  
  
|<span data-ttu-id="49a50-120">項目</span><span class="sxs-lookup"><span data-stu-id="49a50-120">Element</span></span>|<span data-ttu-id="49a50-121">描述</span><span class="sxs-lookup"><span data-stu-id="49a50-121">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="49a50-122">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="49a50-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="49a50-123">指定 ASP.NET 組態區段的根項目。</span><span class="sxs-lookup"><span data-stu-id="49a50-123">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49a50-124">備註</span><span class="sxs-lookup"><span data-stu-id="49a50-124">Remarks</span></span>  
 <span data-ttu-id="49a50-125">效能計數器會使用記憶體對應檔案或共用的記憶體，來發行效能資料。</span><span class="sxs-lookup"><span data-stu-id="49a50-125">Performance counters use a memory mapped file, or shared memory, to publish performance data.</span></span>  <span data-ttu-id="49a50-126">共用記憶體的大小會決定可以一次使用多少個執行個體。</span><span class="sxs-lookup"><span data-stu-id="49a50-126">The size of the shared memory determines how many instances can be used at once.</span></span>  <span data-ttu-id="49a50-127">有兩種類型的共用記憶體： 全域共用記憶體和不同的共用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="49a50-127">There are two types of shared memory: global shared memory and separate shared memory.</span></span>  <span data-ttu-id="49a50-128">.NET framework 1.0 或 1.1 與安裝的所有效能計數器分類會都使用全域共用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="49a50-128">The global shared memory is used by all performance counter categories installed with the .NET Framework versions 1.0 or 1.1.</span></span>  <span data-ttu-id="49a50-129">安裝.NET framework 2.0 版的效能計數器分類使用不同的共用的記憶體，且每個效能計數器分類有它自己的記憶體。</span><span class="sxs-lookup"><span data-stu-id="49a50-129">Performance counter categories installed with the .NET Framework version 2.0 use separate shared memory, with each performance counter category having its own memory.</span></span>  
  
 <span data-ttu-id="49a50-130">僅使用組態檔，可以設定全域共用記憶體的大小。</span><span class="sxs-lookup"><span data-stu-id="49a50-130">The size of global shared memory can be set only with a configuration file.</span></span>  <span data-ttu-id="49a50-131">預設大小為 524288 個位元組，大小上限為 33554432 個位元組，而最小大小為 32,768 位元組。</span><span class="sxs-lookup"><span data-stu-id="49a50-131">The default size is 524,288 byes, the maximum size is 33,554,432 bytes, and the minimum size is 32,768 bytes.</span></span>  <span data-ttu-id="49a50-132">由於全域共用的記憶體共用的所有處理程序與類別，第一個建立者指定的大小。</span><span class="sxs-lookup"><span data-stu-id="49a50-132">Since the global shared memory is shared by all processes and categories, the first creator specifies the size.</span></span>  <span data-ttu-id="49a50-133">如果您在應用程式組態檔中定義的大小，如果您的應用程式會導致效能計數器執行第一個應用程式只使用該大小。</span><span class="sxs-lookup"><span data-stu-id="49a50-133">If you define the size in your application configuration file, that size is only used if your application is the first application that causes the performance counters to execute.</span></span>  <span data-ttu-id="49a50-134">因此正確的位置來指定`filemappingsize`值是在 Machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="49a50-134">Therefore the correct location to specify the `filemappingsize` value is the Machine.config file.</span></span>  <span data-ttu-id="49a50-135">無法由個別效能計數器，因此最後還是會建立大量的效能計數器執行個體使用不同的名稱，如果已用完全域共用的記憶體釋放中全域共用記憶體的記憶體。</span><span class="sxs-lookup"><span data-stu-id="49a50-135">Memory in the global shared memory cannot be released by individual performance counters, so eventually global shared memory is exhausted if a large number of performance counter instances with different names are created.</span></span>  
  
 <span data-ttu-id="49a50-136">對於不同的共用記憶體的大小，DWORD FileMappingSize 在登錄機碼值 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<類別名稱 >* \Performance 參考首先，後面接著全域共用記憶體，在組態檔中指定的值。</span><span class="sxs-lookup"><span data-stu-id="49a50-136">For the size of separate shared memory, the DWORD FileMappingSize value in the registry key HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<category name>* \Performance is referenced first, followed by the value specified for the global shared memory in the configuration file.</span></span> <span data-ttu-id="49a50-137">如果 FileMappingSize 值不存在，則不同的共用的記憶體大小會設定一個第四個 (1/4) 組態檔中的全域設定。</span><span class="sxs-lookup"><span data-stu-id="49a50-137">If the FileMappingSize value does not exist, then the separate shared memory size is set to one fourth (1/4) the global setting in the configuration file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49a50-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49a50-138">See Also</span></span>  
 <xref:System.Diagnostics.PerformanceCounter>  
 <xref:System.Diagnostics.PerformanceCounterCategory>  
 <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>  
 <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
