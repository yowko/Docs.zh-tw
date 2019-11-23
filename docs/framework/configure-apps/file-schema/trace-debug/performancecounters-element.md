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
ms.openlocfilehash: f52fdb2d5b0b7911de63f96663e70735d2f2496c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697159"
---
# <a name="performancecounters-element"></a><span data-ttu-id="338c6-102">\<performanceCounters > 元素</span><span class="sxs-lookup"><span data-stu-id="338c6-102">\<performanceCounters> Element</span></span>

<span data-ttu-id="338c6-103">指定效能計數器共用之全域記憶體的大小。</span><span class="sxs-lookup"><span data-stu-id="338c6-103">Specifies the size of the global memory shared by performance counters.</span></span>

[<span data-ttu-id="338c6-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="338c6-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="338c6-105">&nbsp;&nbsp;[ **\<系統診斷 >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="338c6-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="338c6-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<performanceCounters >**</span><span class="sxs-lookup"><span data-stu-id="338c6-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="338c6-107">語法</span><span class="sxs-lookup"><span data-stu-id="338c6-107">Syntax</span></span>

```xml
<performanceCounters filemappingsize="524288" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="338c6-108">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="338c6-108">Attributes and Elements</span></span>

<span data-ttu-id="338c6-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="338c6-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="338c6-110">屬性</span><span class="sxs-lookup"><span data-stu-id="338c6-110">Attributes</span></span>

|<span data-ttu-id="338c6-111">屬性</span><span class="sxs-lookup"><span data-stu-id="338c6-111">Attribute</span></span>|<span data-ttu-id="338c6-112">描述</span><span class="sxs-lookup"><span data-stu-id="338c6-112">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="338c6-113">filemappingsize</span><span class="sxs-lookup"><span data-stu-id="338c6-113">filemappingsize</span></span>|<span data-ttu-id="338c6-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="338c6-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="338c6-115">指定效能計數器共用的全域記憶體大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="338c6-115">Specifies the size, in bytes, of the global memory shared by performance counters.</span></span> <span data-ttu-id="338c6-116">預設值為 524288。</span><span class="sxs-lookup"><span data-stu-id="338c6-116">The default is 524288.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="338c6-117">子元素</span><span class="sxs-lookup"><span data-stu-id="338c6-117">Child Elements</span></span>

<span data-ttu-id="338c6-118">None。</span><span class="sxs-lookup"><span data-stu-id="338c6-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="338c6-119">父項目</span><span class="sxs-lookup"><span data-stu-id="338c6-119">Parent Elements</span></span>

|<span data-ttu-id="338c6-120">項目</span><span class="sxs-lookup"><span data-stu-id="338c6-120">Element</span></span>|<span data-ttu-id="338c6-121">描述</span><span class="sxs-lookup"><span data-stu-id="338c6-121">Description</span></span>|
|-------------|-----------------|
|`Configuration`|<span data-ttu-id="338c6-122">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="338c6-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`system.diagnostics`|<span data-ttu-id="338c6-123">指定 ASP.NET 組態區段的根項目。</span><span class="sxs-lookup"><span data-stu-id="338c6-123">Specifies the root element for the ASP.NET configuration section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="338c6-124">備註</span><span class="sxs-lookup"><span data-stu-id="338c6-124">Remarks</span></span>

<span data-ttu-id="338c6-125">效能計數器會使用記憶體對應檔案或共用記憶體來發行效能資料。</span><span class="sxs-lookup"><span data-stu-id="338c6-125">Performance counters use a memory mapped file, or shared memory, to publish performance data.</span></span>  <span data-ttu-id="338c6-126">共用記憶體的大小會決定一次可以使用多少個實例。</span><span class="sxs-lookup"><span data-stu-id="338c6-126">The size of the shared memory determines how many instances can be used at once.</span></span>  <span data-ttu-id="338c6-127">共用記憶體有兩種類型：全域共用記憶體和個別的共用記憶體。</span><span class="sxs-lookup"><span data-stu-id="338c6-127">There are two types of shared memory: global shared memory and separate shared memory.</span></span>  <span data-ttu-id="338c6-128">與 .NET Framework 版本1.0 或1.1 一起安裝的所有效能計數器類別都會使用全域共用記憶體。</span><span class="sxs-lookup"><span data-stu-id="338c6-128">The global shared memory is used by all performance counter categories installed with the .NET Framework versions 1.0 or 1.1.</span></span>  <span data-ttu-id="338c6-129">隨 .NET Framework 版本2.0 安裝的效能計數器類別會使用不同的共用記憶體，每個效能計數器類別都有自己的記憶體。</span><span class="sxs-lookup"><span data-stu-id="338c6-129">Performance counter categories installed with the .NET Framework version 2.0 use separate shared memory, with each performance counter category having its own memory.</span></span>

<span data-ttu-id="338c6-130">全域共用記憶體的大小只能使用設定檔來設定。</span><span class="sxs-lookup"><span data-stu-id="338c6-130">The size of global shared memory can be set only with a configuration file.</span></span>  <span data-ttu-id="338c6-131">預設大小為 524288 byes，大小上限為33554432個位元組，而最小大小為32768個位元組。</span><span class="sxs-lookup"><span data-stu-id="338c6-131">The default size is 524,288 byes, the maximum size is 33,554,432 bytes, and the minimum size is 32,768 bytes.</span></span>  <span data-ttu-id="338c6-132">由於全域共用記憶體是由所有進程和類別共用，因此第一個建立者會指定大小。</span><span class="sxs-lookup"><span data-stu-id="338c6-132">Since the global shared memory is shared by all processes and categories, the first creator specifies the size.</span></span>  <span data-ttu-id="338c6-133">如果您在應用程式佈建檔中定義大小，只有在您的應用程式是導致效能計數器執行的第一個應用程式時，才會使用該大小。</span><span class="sxs-lookup"><span data-stu-id="338c6-133">If you define the size in your application configuration file, that size is only used if your application is the first application that causes the performance counters to execute.</span></span>  <span data-ttu-id="338c6-134">因此，指定 `filemappingsize` 值的正確位置就是 Machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="338c6-134">Therefore the correct location to specify the `filemappingsize` value is the Machine.config file.</span></span>  <span data-ttu-id="338c6-135">個別效能計數器無法釋放全域共用記憶體中的記憶體，因此，如果建立了大量具有不同名稱的效能計數器實例，最後就會耗盡全域共用記憶體。</span><span class="sxs-lookup"><span data-stu-id="338c6-135">Memory in the global shared memory cannot be released by individual performance counters, so eventually global shared memory is exhausted if a large number of performance counter instances with different names are created.</span></span>

<span data-ttu-id="338c6-136">針對個別共用記憶體的大小，登錄機碼中的 DWORD FileMappingSize 值 HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\Services\\ *\<類別目錄名稱 >* \Performance 會先參照，後面接著針對設定檔案中的全域共用記憶體所指定的值。</span><span class="sxs-lookup"><span data-stu-id="338c6-136">For the size of separate shared memory, the DWORD FileMappingSize value in the registry key HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<category name>* \Performance is referenced first, followed by the value specified for the global shared memory in the configuration file.</span></span> <span data-ttu-id="338c6-137">如果 FileMappingSize 值不存在，則個別的共用記憶體大小會設定為設定檔中的全域設定的第四個（1/4）。</span><span class="sxs-lookup"><span data-stu-id="338c6-137">If the FileMappingSize value does not exist, then the separate shared memory size is set to one fourth (1/4) the global setting in the configuration file.</span></span>

## <a name="see-also"></a><span data-ttu-id="338c6-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="338c6-138">See also</span></span>

- <xref:System.Diagnostics.PerformanceCounter>
- <xref:System.Diagnostics.PerformanceCounterCategory>
- <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>
- <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
