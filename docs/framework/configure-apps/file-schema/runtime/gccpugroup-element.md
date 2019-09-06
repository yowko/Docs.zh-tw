---
title: <GCCpuGroup> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ff646f13c5619b0bfca1b61c86013a981c274e3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252567"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="7a51b-102">\<GCCpuGroup > 元素</span><span class="sxs-lookup"><span data-stu-id="7a51b-102">\<GCCpuGroup> Element</span></span>

<span data-ttu-id="7a51b-103">指定記憶體回收是否支援多個 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="7a51b-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>

<span data-ttu-id="7a51b-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7a51b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7a51b-105">&nbsp;&nbsp;[ **\<執行時間 >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="7a51b-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="7a51b-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<GCCpuGroup>**</span><span class="sxs-lookup"><span data-stu-id="7a51b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="7a51b-107">語法</span><span class="sxs-lookup"><span data-stu-id="7a51b-107">Syntax</span></span>

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7a51b-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7a51b-108">Attributes and Elements</span></span>

<span data-ttu-id="7a51b-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7a51b-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="7a51b-110">屬性</span><span class="sxs-lookup"><span data-stu-id="7a51b-110">Attributes</span></span>

|<span data-ttu-id="7a51b-111">屬性</span><span class="sxs-lookup"><span data-stu-id="7a51b-111">Attribute</span></span>|<span data-ttu-id="7a51b-112">描述</span><span class="sxs-lookup"><span data-stu-id="7a51b-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="7a51b-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="7a51b-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="7a51b-114">指定記憶體回收是否支援多個 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="7a51b-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="7a51b-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="7a51b-115">enabled Attribute</span></span>

|<span data-ttu-id="7a51b-116">值</span><span class="sxs-lookup"><span data-stu-id="7a51b-116">Value</span></span>|<span data-ttu-id="7a51b-117">描述</span><span class="sxs-lookup"><span data-stu-id="7a51b-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="7a51b-118">垃圾收集不支援多個 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="7a51b-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="7a51b-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="7a51b-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="7a51b-120">如果已啟用伺服器垃圾收集，垃圾收集支援多個 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="7a51b-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="7a51b-121">子元素</span><span class="sxs-lookup"><span data-stu-id="7a51b-121">Child Elements</span></span>

<span data-ttu-id="7a51b-122">無。</span><span class="sxs-lookup"><span data-stu-id="7a51b-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7a51b-123">父項目</span><span class="sxs-lookup"><span data-stu-id="7a51b-123">Parent Elements</span></span>

|<span data-ttu-id="7a51b-124">項目</span><span class="sxs-lookup"><span data-stu-id="7a51b-124">Element</span></span>|<span data-ttu-id="7a51b-125">描述</span><span class="sxs-lookup"><span data-stu-id="7a51b-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="7a51b-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="7a51b-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="7a51b-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="7a51b-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7a51b-128">備註</span><span class="sxs-lookup"><span data-stu-id="7a51b-128">Remarks</span></span>

<span data-ttu-id="7a51b-129">當電腦具有多個 cpu 群組並啟用伺服器垃圾收集時（請參閱[ \<gcServer >](gcserver-element.md)元素），啟用此元素會延伸所有 CPU 群組的垃圾收集，並在建立和時將所有核心納入考慮平衡堆積。</span><span class="sxs-lookup"><span data-stu-id="7a51b-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>

> [!NOTE]
> <span data-ttu-id="7a51b-130">這個元素只適用于垃圾收集執行緒。</span><span class="sxs-lookup"><span data-stu-id="7a51b-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="7a51b-131">若要讓執行時間將使用者執行緒分散到所有的 CPU 群組，您也必須啟用[ \<Thread_UseAllCpuGroups >](thread-useallcpugroups-element.md)元素。</span><span class="sxs-lookup"><span data-stu-id="7a51b-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span></span>

## <a name="example"></a><span data-ttu-id="7a51b-132">範例</span><span class="sxs-lookup"><span data-stu-id="7a51b-132">Example</span></span>

<span data-ttu-id="7a51b-133">下列範例顯示如何啟用多個 CPU 群組的垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="7a51b-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="7a51b-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a51b-134">See also</span></span>

- [<span data-ttu-id="7a51b-135">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="7a51b-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7a51b-136">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="7a51b-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="7a51b-137">停用並行垃圾收集</span><span class="sxs-lookup"><span data-stu-id="7a51b-137">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="7a51b-138">工作站和伺服器記憶體回收</span><span class="sxs-lookup"><span data-stu-id="7a51b-138">Workstation and server garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
