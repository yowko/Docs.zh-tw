---
title: <GCCpuGroup> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 197ab9dbc1ec85bf8961f60bb26496eab788e63f
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663693"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="a2d8d-102">\<GCCpuGroup > 元素</span><span class="sxs-lookup"><span data-stu-id="a2d8d-102">\<GCCpuGroup> Element</span></span>

<span data-ttu-id="a2d8d-103">指定記憶體回收是否支援多個 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="a2d8d-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>

<span data-ttu-id="a2d8d-104">\<configuration > </span><span class="sxs-lookup"><span data-stu-id="a2d8d-104">\<configuration></span></span>\
<span data-ttu-id="a2d8d-105">\<執行時間 > </span><span class="sxs-lookup"><span data-stu-id="a2d8d-105">\<runtime></span></span>\
<span data-ttu-id="a2d8d-106">\<GCCpuGroup></span><span class="sxs-lookup"><span data-stu-id="a2d8d-106">\<GCCpuGroup></span></span>

## <a name="syntax"></a><span data-ttu-id="a2d8d-107">語法</span><span class="sxs-lookup"><span data-stu-id="a2d8d-107">Syntax</span></span>

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a2d8d-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a2d8d-108">Attributes and Elements</span></span>

<span data-ttu-id="a2d8d-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a2d8d-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a2d8d-110">屬性</span><span class="sxs-lookup"><span data-stu-id="a2d8d-110">Attributes</span></span>

|<span data-ttu-id="a2d8d-111">屬性</span><span class="sxs-lookup"><span data-stu-id="a2d8d-111">Attribute</span></span>|<span data-ttu-id="a2d8d-112">說明</span><span class="sxs-lookup"><span data-stu-id="a2d8d-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="a2d8d-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="a2d8d-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="a2d8d-114">指定記憶體回收是否支援多個 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="a2d8d-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="a2d8d-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="a2d8d-115">enabled Attribute</span></span>

|<span data-ttu-id="a2d8d-116">值</span><span class="sxs-lookup"><span data-stu-id="a2d8d-116">Value</span></span>|<span data-ttu-id="a2d8d-117">說明</span><span class="sxs-lookup"><span data-stu-id="a2d8d-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="a2d8d-118">垃圾收集不支援多個 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="a2d8d-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="a2d8d-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="a2d8d-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="a2d8d-120">如果已啟用伺服器垃圾收集, 垃圾收集支援多個 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="a2d8d-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="a2d8d-121">子元素</span><span class="sxs-lookup"><span data-stu-id="a2d8d-121">Child Elements</span></span>

<span data-ttu-id="a2d8d-122">無。</span><span class="sxs-lookup"><span data-stu-id="a2d8d-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a2d8d-123">父項目</span><span class="sxs-lookup"><span data-stu-id="a2d8d-123">Parent Elements</span></span>

|<span data-ttu-id="a2d8d-124">項目</span><span class="sxs-lookup"><span data-stu-id="a2d8d-124">Element</span></span>|<span data-ttu-id="a2d8d-125">描述</span><span class="sxs-lookup"><span data-stu-id="a2d8d-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="a2d8d-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="a2d8d-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="a2d8d-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="a2d8d-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a2d8d-128">備註</span><span class="sxs-lookup"><span data-stu-id="a2d8d-128">Remarks</span></span>

<span data-ttu-id="a2d8d-129">當電腦具有多個 cpu 群組並啟用伺服器垃圾收集時 (請參閱[ \<gcServer >](gcserver-element.md)元素), 啟用此元素會延伸所有 CPU 群組的垃圾收集, 並在建立和時將所有核心納入考慮平衡堆積。</span><span class="sxs-lookup"><span data-stu-id="a2d8d-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>

> [!NOTE]
> <span data-ttu-id="a2d8d-130">這個元素只適用于垃圾收集執行緒。</span><span class="sxs-lookup"><span data-stu-id="a2d8d-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="a2d8d-131">若要讓執行時間將使用者執行緒分散到所有的 CPU 群組, 您也必須啟用[ \<Thread_UseAllCpuGroups >](thread-useallcpugroups-element.md)元素。</span><span class="sxs-lookup"><span data-stu-id="a2d8d-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span></span>

## <a name="example"></a><span data-ttu-id="a2d8d-132">範例</span><span class="sxs-lookup"><span data-stu-id="a2d8d-132">Example</span></span>

<span data-ttu-id="a2d8d-133">下列範例顯示如何啟用多個 CPU 群組的垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="a2d8d-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="a2d8d-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2d8d-134">See also</span></span>

- [<span data-ttu-id="a2d8d-135">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="a2d8d-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a2d8d-136">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="a2d8d-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a2d8d-137">停用並行垃圾收集</span><span class="sxs-lookup"><span data-stu-id="a2d8d-137">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="a2d8d-138">工作站和伺服器記憶體回收</span><span class="sxs-lookup"><span data-stu-id="a2d8d-138">Workstation and server garbage collection</span></span>](../../../../../docs/standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
