---
title: <GCCpuGroup> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: ae9c96c9d49cf3f6be94da3f77b91423cab12e0b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430489"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="c0848-102">\<GCCpuGroup > 元素</span><span class="sxs-lookup"><span data-stu-id="c0848-102">\<GCCpuGroup> Element</span></span>

<span data-ttu-id="c0848-103">指定記憶體回收是否支援多個 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="c0848-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>

<span data-ttu-id="c0848-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c0848-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c0848-105">&nbsp;&nbsp;[ **\<執行時間 >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="c0848-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="c0848-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<GCCpuGroup >**</span><span class="sxs-lookup"><span data-stu-id="c0848-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="c0848-107">語法</span><span class="sxs-lookup"><span data-stu-id="c0848-107">Syntax</span></span>

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c0848-108">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="c0848-108">Attributes and Elements</span></span>

<span data-ttu-id="c0848-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c0848-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c0848-110">屬性</span><span class="sxs-lookup"><span data-stu-id="c0848-110">Attributes</span></span>

|<span data-ttu-id="c0848-111">屬性</span><span class="sxs-lookup"><span data-stu-id="c0848-111">Attribute</span></span>|<span data-ttu-id="c0848-112">描述</span><span class="sxs-lookup"><span data-stu-id="c0848-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="c0848-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="c0848-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="c0848-114">指定記憶體回收是否支援多個 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="c0848-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="c0848-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="c0848-115">enabled Attribute</span></span>

|<span data-ttu-id="c0848-116">值</span><span class="sxs-lookup"><span data-stu-id="c0848-116">Value</span></span>|<span data-ttu-id="c0848-117">描述</span><span class="sxs-lookup"><span data-stu-id="c0848-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="c0848-118">垃圾收集不支援多個 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="c0848-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="c0848-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="c0848-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="c0848-120">如果已啟用伺服器垃圾收集，垃圾收集支援多個 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="c0848-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="c0848-121">子元素</span><span class="sxs-lookup"><span data-stu-id="c0848-121">Child Elements</span></span>

<span data-ttu-id="c0848-122">None。</span><span class="sxs-lookup"><span data-stu-id="c0848-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c0848-123">父項目</span><span class="sxs-lookup"><span data-stu-id="c0848-123">Parent Elements</span></span>

|<span data-ttu-id="c0848-124">項目</span><span class="sxs-lookup"><span data-stu-id="c0848-124">Element</span></span>|<span data-ttu-id="c0848-125">描述</span><span class="sxs-lookup"><span data-stu-id="c0848-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="c0848-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="c0848-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="c0848-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="c0848-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c0848-128">備註</span><span class="sxs-lookup"><span data-stu-id="c0848-128">Remarks</span></span>

<span data-ttu-id="c0848-129">當電腦具有多個 CPU 群組並啟用伺服器垃圾收集時（請參閱[\<gcServer >](gcserver-element.md)元素），啟用此元素會延伸所有 CPU 群組的垃圾收集，並在建立和平衡堆積時將所有核心納入考慮。</span><span class="sxs-lookup"><span data-stu-id="c0848-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>

> [!NOTE]
> <span data-ttu-id="c0848-130">這個元素只適用于垃圾收集執行緒。</span><span class="sxs-lookup"><span data-stu-id="c0848-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="c0848-131">若要讓執行時間將使用者執行緒分散到所有的 CPU 群組，您也必須啟用[\<Thread_UseAllCpuGroups >](thread-useallcpugroups-element.md)元素。</span><span class="sxs-lookup"><span data-stu-id="c0848-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span></span>

## <a name="example"></a><span data-ttu-id="c0848-132">範例</span><span class="sxs-lookup"><span data-stu-id="c0848-132">Example</span></span>

<span data-ttu-id="c0848-133">下列範例顯示如何啟用多個 CPU 群組的垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="c0848-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="c0848-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0848-134">See also</span></span>

- [<span data-ttu-id="c0848-135">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="c0848-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c0848-136">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="c0848-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="c0848-137">停用並行垃圾收集</span><span class="sxs-lookup"><span data-stu-id="c0848-137">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="c0848-138">工作站和伺服器記憶體回收</span><span class="sxs-lookup"><span data-stu-id="c0848-138">Workstation and server garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection)
