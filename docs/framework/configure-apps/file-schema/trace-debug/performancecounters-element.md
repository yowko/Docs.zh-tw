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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "71697159"
---
# <a name="performancecounters-element"></a><span data-ttu-id="5c07b-102">\<performanceCounters> 項目</span><span class="sxs-lookup"><span data-stu-id="5c07b-102">\<performanceCounters> Element</span></span>

<span data-ttu-id="5c07b-103">指定效能計數器共用之全域記憶體的大小。</span><span class="sxs-lookup"><span data-stu-id="5c07b-103">Specifies the size of the global memory shared by performance counters.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**  

## <a name="syntax"></a><span data-ttu-id="5c07b-104">語法</span><span class="sxs-lookup"><span data-stu-id="5c07b-104">Syntax</span></span>

```xml
<performanceCounters filemappingsize="524288" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5c07b-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5c07b-105">Attributes and Elements</span></span>

<span data-ttu-id="5c07b-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5c07b-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="5c07b-107">屬性</span><span class="sxs-lookup"><span data-stu-id="5c07b-107">Attributes</span></span>

|<span data-ttu-id="5c07b-108">屬性</span><span class="sxs-lookup"><span data-stu-id="5c07b-108">Attribute</span></span>|<span data-ttu-id="5c07b-109">描述</span><span class="sxs-lookup"><span data-stu-id="5c07b-109">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="5c07b-110">filemappingsize</span><span class="sxs-lookup"><span data-stu-id="5c07b-110">filemappingsize</span></span>|<span data-ttu-id="5c07b-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="5c07b-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="5c07b-112">指定效能計數器所共用之全域記憶體的大小 (以位元組計)。</span><span class="sxs-lookup"><span data-stu-id="5c07b-112">Specifies the size, in bytes, of the global memory shared by performance counters.</span></span> <span data-ttu-id="5c07b-113">預設值為 524288。</span><span class="sxs-lookup"><span data-stu-id="5c07b-113">The default is 524288.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="5c07b-114">子元素</span><span class="sxs-lookup"><span data-stu-id="5c07b-114">Child Elements</span></span>

<span data-ttu-id="5c07b-115">無。</span><span class="sxs-lookup"><span data-stu-id="5c07b-115">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5c07b-116">父項目</span><span class="sxs-lookup"><span data-stu-id="5c07b-116">Parent Elements</span></span>

|<span data-ttu-id="5c07b-117">元素</span><span class="sxs-lookup"><span data-stu-id="5c07b-117">Element</span></span>|<span data-ttu-id="5c07b-118">描述</span><span class="sxs-lookup"><span data-stu-id="5c07b-118">Description</span></span>|
|-------------|-----------------|
|`Configuration`|<span data-ttu-id="5c07b-119">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="5c07b-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`system.diagnostics`|<span data-ttu-id="5c07b-120">指定 ASP.NET 組態區段的根項目。</span><span class="sxs-lookup"><span data-stu-id="5c07b-120">Specifies the root element for the ASP.NET configuration section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5c07b-121">備註</span><span class="sxs-lookup"><span data-stu-id="5c07b-121">Remarks</span></span>

<span data-ttu-id="5c07b-122">效能計數器會使用記憶體對應檔案或共用記憶體來發行效能資料。</span><span class="sxs-lookup"><span data-stu-id="5c07b-122">Performance counters use a memory mapped file, or shared memory, to publish performance data.</span></span>  <span data-ttu-id="5c07b-123">共用記憶體的大小會決定一次可以使用多少個實例。</span><span class="sxs-lookup"><span data-stu-id="5c07b-123">The size of the shared memory determines how many instances can be used at once.</span></span>  <span data-ttu-id="5c07b-124">共用記憶體有兩種類型：全域共用記憶體和個別的共用記憶體。</span><span class="sxs-lookup"><span data-stu-id="5c07b-124">There are two types of shared memory: global shared memory and separate shared memory.</span></span>  <span data-ttu-id="5c07b-125">與 .NET Framework 版本1.0 或1.1 一起安裝的所有效能計數器類別都會使用全域共用記憶體。</span><span class="sxs-lookup"><span data-stu-id="5c07b-125">The global shared memory is used by all performance counter categories installed with the .NET Framework versions 1.0 or 1.1.</span></span>  <span data-ttu-id="5c07b-126">隨 .NET Framework 版本2.0 安裝的效能計數器類別會使用不同的共用記憶體，每個效能計數器類別都有自己的記憶體。</span><span class="sxs-lookup"><span data-stu-id="5c07b-126">Performance counter categories installed with the .NET Framework version 2.0 use separate shared memory, with each performance counter category having its own memory.</span></span>

<span data-ttu-id="5c07b-127">全域共用記憶體的大小只能使用設定檔來設定。</span><span class="sxs-lookup"><span data-stu-id="5c07b-127">The size of global shared memory can be set only with a configuration file.</span></span>  <span data-ttu-id="5c07b-128">預設大小為 524288 byes，大小上限為33554432個位元組，而最小大小為32768個位元組。</span><span class="sxs-lookup"><span data-stu-id="5c07b-128">The default size is 524,288 byes, the maximum size is 33,554,432 bytes, and the minimum size is 32,768 bytes.</span></span>  <span data-ttu-id="5c07b-129">由於全域共用記憶體是由所有進程和類別共用，因此第一個建立者會指定大小。</span><span class="sxs-lookup"><span data-stu-id="5c07b-129">Since the global shared memory is shared by all processes and categories, the first creator specifies the size.</span></span>  <span data-ttu-id="5c07b-130">如果您在應用程式佈建檔中定義大小，只有在您的應用程式是導致效能計數器執行的第一個應用程式時，才會使用該大小。</span><span class="sxs-lookup"><span data-stu-id="5c07b-130">If you define the size in your application configuration file, that size is only used if your application is the first application that causes the performance counters to execute.</span></span>  <span data-ttu-id="5c07b-131">因此，指定值的正確位置 `filemappingsize` 就是 machine.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="5c07b-131">Therefore the correct location to specify the `filemappingsize` value is the Machine.config file.</span></span>  <span data-ttu-id="5c07b-132">個別效能計數器無法釋放全域共用記憶體中的記憶體，因此，如果建立了大量具有不同名稱的效能計數器實例，最後就會耗盡全域共用記憶體。</span><span class="sxs-lookup"><span data-stu-id="5c07b-132">Memory in the global shared memory cannot be released by individual performance counters, so eventually global shared memory is exhausted if a large number of performance counter instances with different names are created.</span></span>

<span data-ttu-id="5c07b-133">針對個別共用記憶體的大小，會先參考登錄機碼中的 DWORD FileMappingSize 值 HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\Services \\ *\<category name>* \Performance，後面接著針對設定檔案中的全域共用記憶體所指定的值。</span><span class="sxs-lookup"><span data-stu-id="5c07b-133">For the size of separate shared memory, the DWORD FileMappingSize value in the registry key HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<category name>* \Performance is referenced first, followed by the value specified for the global shared memory in the configuration file.</span></span> <span data-ttu-id="5c07b-134">如果 FileMappingSize 值不存在，則個別的共用記憶體大小會設定為設定檔中的全域設定的第四個（1/4）。</span><span class="sxs-lookup"><span data-stu-id="5c07b-134">If the FileMappingSize value does not exist, then the separate shared memory size is set to one fourth (1/4) the global setting in the configuration file.</span></span>

## <a name="see-also"></a><span data-ttu-id="5c07b-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c07b-135">See also</span></span>

- <xref:System.Diagnostics.PerformanceCounter>
- <xref:System.Diagnostics.PerformanceCounterCategory>
- <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>
- <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
