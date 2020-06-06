---
title: <GCCpuGroup> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: f1cbe5a7109d6e4aae2e92710920a1c6b3a40d00
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "82102888"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="1c64b-102">\<GCCpuGroup> 項目</span><span class="sxs-lookup"><span data-stu-id="1c64b-102">\<GCCpuGroup> Element</span></span>

<span data-ttu-id="1c64b-103">指定記憶體回收是否支援多個 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="1c64b-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**

## <a name="syntax"></a><span data-ttu-id="1c64b-104">語法</span><span class="sxs-lookup"><span data-stu-id="1c64b-104">Syntax</span></span>

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1c64b-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1c64b-105">Attributes and Elements</span></span>

<span data-ttu-id="1c64b-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1c64b-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="1c64b-107">屬性</span><span class="sxs-lookup"><span data-stu-id="1c64b-107">Attributes</span></span>

|<span data-ttu-id="1c64b-108">屬性</span><span class="sxs-lookup"><span data-stu-id="1c64b-108">Attribute</span></span>|<span data-ttu-id="1c64b-109">描述</span><span class="sxs-lookup"><span data-stu-id="1c64b-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="1c64b-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="1c64b-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="1c64b-111">指定記憶體回收是否支援多個 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="1c64b-111">Specifies whether garbage collection supports multiple CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="1c64b-112">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="1c64b-112">enabled Attribute</span></span>

|<span data-ttu-id="1c64b-113">值</span><span class="sxs-lookup"><span data-stu-id="1c64b-113">Value</span></span>|<span data-ttu-id="1c64b-114">描述</span><span class="sxs-lookup"><span data-stu-id="1c64b-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="1c64b-115">垃圾收集不支援多個 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="1c64b-115">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="1c64b-116">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="1c64b-116">This is the default.</span></span>|
|`true`|<span data-ttu-id="1c64b-117">如果已啟用伺服器垃圾收集，垃圾收集支援多個 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="1c64b-117">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="1c64b-118">子元素</span><span class="sxs-lookup"><span data-stu-id="1c64b-118">Child Elements</span></span>

<span data-ttu-id="1c64b-119">無。</span><span class="sxs-lookup"><span data-stu-id="1c64b-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1c64b-120">父項目</span><span class="sxs-lookup"><span data-stu-id="1c64b-120">Parent Elements</span></span>

|<span data-ttu-id="1c64b-121">元素</span><span class="sxs-lookup"><span data-stu-id="1c64b-121">Element</span></span>|<span data-ttu-id="1c64b-122">描述</span><span class="sxs-lookup"><span data-stu-id="1c64b-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="1c64b-123">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="1c64b-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="1c64b-124">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="1c64b-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1c64b-125">備註</span><span class="sxs-lookup"><span data-stu-id="1c64b-125">Remarks</span></span>

<span data-ttu-id="1c64b-126">當電腦具有多個 CPU 群組並已啟用伺服器垃圾收集時（請參閱 [\<gcServer>](gcserver-element.md) 元素），啟用此元素會延伸所有 CPU 群組的垃圾收集，並在建立和平衡堆積時將所有核心納入考慮。</span><span class="sxs-lookup"><span data-stu-id="1c64b-126">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>

> [!NOTE]
> <span data-ttu-id="1c64b-127">這個元素只適用于垃圾收集執行緒。</span><span class="sxs-lookup"><span data-stu-id="1c64b-127">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="1c64b-128">若要讓執行時間將使用者執行緒分散到所有的 CPU 群組，您也必須啟用 [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="1c64b-128">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span></span>

## <a name="example"></a><span data-ttu-id="1c64b-129">範例</span><span class="sxs-lookup"><span data-stu-id="1c64b-129">Example</span></span>

<span data-ttu-id="1c64b-130">下列範例顯示如何啟用多個 CPU 群組的垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="1c64b-130">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="1c64b-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c64b-131">See also</span></span>

- [<span data-ttu-id="1c64b-132">執行時間設定架構</span><span class="sxs-lookup"><span data-stu-id="1c64b-132">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="1c64b-133">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="1c64b-133">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="1c64b-134">停用並行垃圾收集</span><span class="sxs-lookup"><span data-stu-id="1c64b-134">Disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="1c64b-135">工作站和伺服器記憶體回收</span><span class="sxs-lookup"><span data-stu-id="1c64b-135">Workstation and server garbage collection</span></span>](../../../../standard/garbage-collection/workstation-server-gc.md)
