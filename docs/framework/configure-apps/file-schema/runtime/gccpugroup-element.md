---
title: <GCCpuGroup> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: f1cbe5a7109d6e4aae2e92710920a1c6b3a40d00
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102888"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="def31-102">\<GCCpu組>元素</span><span class="sxs-lookup"><span data-stu-id="def31-102">\<GCCpuGroup> Element</span></span>

<span data-ttu-id="def31-103">指定記憶體回收是否支援多個 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="def31-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>

<span data-ttu-id="def31-104">[**\<設定>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="def31-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="def31-105">&nbsp;&nbsp;[**\<執行時>**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="def31-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="def31-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpu組>**</span><span class="sxs-lookup"><span data-stu-id="def31-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="def31-107">語法</span><span class="sxs-lookup"><span data-stu-id="def31-107">Syntax</span></span>

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="def31-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="def31-108">Attributes and Elements</span></span>

<span data-ttu-id="def31-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="def31-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="def31-110">屬性</span><span class="sxs-lookup"><span data-stu-id="def31-110">Attributes</span></span>

|<span data-ttu-id="def31-111">屬性</span><span class="sxs-lookup"><span data-stu-id="def31-111">Attribute</span></span>|<span data-ttu-id="def31-112">描述</span><span class="sxs-lookup"><span data-stu-id="def31-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="def31-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="def31-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="def31-114">指定記憶體回收是否支援多個 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="def31-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="def31-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="def31-115">enabled Attribute</span></span>

|<span data-ttu-id="def31-116">值</span><span class="sxs-lookup"><span data-stu-id="def31-116">Value</span></span>|<span data-ttu-id="def31-117">描述</span><span class="sxs-lookup"><span data-stu-id="def31-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="def31-118">垃圾回收不支援多個 CPU 組。</span><span class="sxs-lookup"><span data-stu-id="def31-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="def31-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="def31-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="def31-120">如果啟用了伺服器垃圾回收,垃圾回收支援多個 CPU 組。</span><span class="sxs-lookup"><span data-stu-id="def31-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="def31-121">子元素</span><span class="sxs-lookup"><span data-stu-id="def31-121">Child Elements</span></span>

<span data-ttu-id="def31-122">無。</span><span class="sxs-lookup"><span data-stu-id="def31-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="def31-123">父項目</span><span class="sxs-lookup"><span data-stu-id="def31-123">Parent Elements</span></span>

|<span data-ttu-id="def31-124">元素</span><span class="sxs-lookup"><span data-stu-id="def31-124">Element</span></span>|<span data-ttu-id="def31-125">描述</span><span class="sxs-lookup"><span data-stu-id="def31-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="def31-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="def31-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="def31-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="def31-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="def31-128">備註</span><span class="sxs-lookup"><span data-stu-id="def31-128">Remarks</span></span>

<span data-ttu-id="def31-129">當電腦具有多個 CPU 組並啟用伺服器垃圾回收時(請參閱[\<gcServer>](gcserver-element.md)元素),啟用此元素可跨所有 CPU 組擴展垃圾回收,並在創建和平衡堆時考慮所有內核。</span><span class="sxs-lookup"><span data-stu-id="def31-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>

> [!NOTE]
> <span data-ttu-id="def31-130">此元素僅適用於垃圾回收線程。</span><span class="sxs-lookup"><span data-stu-id="def31-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="def31-131">要使運行時能夠跨所有 CPU 組分發使用者線程,還必須啟用[\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md)元素。</span><span class="sxs-lookup"><span data-stu-id="def31-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span></span>

## <a name="example"></a><span data-ttu-id="def31-132">範例</span><span class="sxs-lookup"><span data-stu-id="def31-132">Example</span></span>

<span data-ttu-id="def31-133">下面的範例展示如何為多個 CPU 組啟用垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="def31-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="def31-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="def31-134">See also</span></span>

- [<span data-ttu-id="def31-135">執行時設定架構</span><span class="sxs-lookup"><span data-stu-id="def31-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="def31-136">設定檔案架構</span><span class="sxs-lookup"><span data-stu-id="def31-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="def31-137">關閉並發垃圾資源</span><span class="sxs-lookup"><span data-stu-id="def31-137">Disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="def31-138">工作站和伺服器記憶體回收</span><span class="sxs-lookup"><span data-stu-id="def31-138">Workstation and server garbage collection</span></span>](../../../../standard/garbage-collection/workstation-server-gc.md)
