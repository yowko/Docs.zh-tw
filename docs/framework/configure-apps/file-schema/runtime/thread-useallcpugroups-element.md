---
title: <Thread_UseAllCpuGroups> 項目
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e9ee6bdb7094ea2bc9e283e331c0f6ad9b68e4f9
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663416"
---
# <a name="thread_useallcpugroups-element"></a><span data-ttu-id="bb0f6-102">\<Thread_UseAllCpuGroups > 元素</span><span class="sxs-lookup"><span data-stu-id="bb0f6-102">\<Thread_UseAllCpuGroups> Element</span></span>

<span data-ttu-id="bb0f6-103">指定執行階段是否會將 Managed 執行緒分散到所有 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="bb0f6-103">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>

<span data-ttu-id="bb0f6-104">\<configuration > </span><span class="sxs-lookup"><span data-stu-id="bb0f6-104">\<configuration></span></span>\
<span data-ttu-id="bb0f6-105">\<執行時間 > </span><span class="sxs-lookup"><span data-stu-id="bb0f6-105">\<runtime></span></span>\
<span data-ttu-id="bb0f6-106">\<Thread_UseAllCpuGroups></span><span class="sxs-lookup"><span data-stu-id="bb0f6-106">\<Thread_UseAllCpuGroups></span></span>

## <a name="syntax"></a><span data-ttu-id="bb0f6-107">語法</span><span class="sxs-lookup"><span data-stu-id="bb0f6-107">Syntax</span></span>

```xml
<Thread_UseAllCpuGroups
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bb0f6-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bb0f6-108">Attributes and Elements</span></span>

<span data-ttu-id="bb0f6-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="bb0f6-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="bb0f6-110">屬性</span><span class="sxs-lookup"><span data-stu-id="bb0f6-110">Attributes</span></span>

|<span data-ttu-id="bb0f6-111">屬性</span><span class="sxs-lookup"><span data-stu-id="bb0f6-111">Attribute</span></span>|<span data-ttu-id="bb0f6-112">描述</span><span class="sxs-lookup"><span data-stu-id="bb0f6-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="bb0f6-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="bb0f6-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="bb0f6-114">指定執行階段是否會將 Managed 執行緒分散到所有 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="bb0f6-114">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="bb0f6-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="bb0f6-115">enabled Attribute</span></span>

|<span data-ttu-id="bb0f6-116">值</span><span class="sxs-lookup"><span data-stu-id="bb0f6-116">Value</span></span>|<span data-ttu-id="bb0f6-117">說明</span><span class="sxs-lookup"><span data-stu-id="bb0f6-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="bb0f6-118">執行時間不會將受控執行緒分散到多個 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="bb0f6-118">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="bb0f6-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="bb0f6-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="bb0f6-120">如果電腦有多個 cpu 群組, 而且[ \<已啟用 GCCpuGroup >](gccpugroup-element.md)元素, 則執行時間會將受控執行緒分散到多個 cpu 群組。</span><span class="sxs-lookup"><span data-stu-id="bb0f6-120">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](gccpugroup-element.md) element is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="bb0f6-121">子元素</span><span class="sxs-lookup"><span data-stu-id="bb0f6-121">Child Elements</span></span>

<span data-ttu-id="bb0f6-122">無。</span><span class="sxs-lookup"><span data-stu-id="bb0f6-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bb0f6-123">父項目</span><span class="sxs-lookup"><span data-stu-id="bb0f6-123">Parent Elements</span></span>

|<span data-ttu-id="bb0f6-124">項目</span><span class="sxs-lookup"><span data-stu-id="bb0f6-124">Element</span></span>|<span data-ttu-id="bb0f6-125">描述</span><span class="sxs-lookup"><span data-stu-id="bb0f6-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="bb0f6-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="bb0f6-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="bb0f6-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="bb0f6-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bb0f6-128">備註</span><span class="sxs-lookup"><span data-stu-id="bb0f6-128">Remarks</span></span>

<span data-ttu-id="bb0f6-129">當電腦具有多個 CPU 群組時, 啟用此元素會導致執行時間將受控執行緒分散到所有 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="bb0f6-129">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="bb0f6-130">若要使用這項功能, 您也必須啟用[ \<GCCpuGroup >](gccpugroup-element.md)元素, 這會將垃圾收集延伸到所有 CPU 群組, 並在建立和平衡堆積時將所有核心納入考慮。</span><span class="sxs-lookup"><span data-stu-id="bb0f6-130">To use this feature, you must also enable the [\<GCCpuGroup>](gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="bb0f6-131">啟用 GCCpuGroup [ >元素需要啟用gcServer>元素。\< ](gccpugroup-element.md) [ \< ](gcserver-element.md)</span><span class="sxs-lookup"><span data-stu-id="bb0f6-131">Enabling the [\<GCCpuGroup>](gccpugroup-element.md) element requires enabling the [\<gcServer>](gcserver-element.md) element.</span></span> <span data-ttu-id="bb0f6-132">如果未啟用這些元素, 啟用元素將`<Thread_UseAllCpuGroups>`不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="bb0f6-132">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>

## <a name="example"></a><span data-ttu-id="bb0f6-133">範例</span><span class="sxs-lookup"><span data-stu-id="bb0f6-133">Example</span></span>

<span data-ttu-id="bb0f6-134">下列範例顯示如何啟用多個 CPU 群組的支援。</span><span class="sxs-lookup"><span data-stu-id="bb0f6-134">The following example shows how to enable support for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <Thread_UseAllCpuGroups enabled="true"/>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="bb0f6-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb0f6-135">See also</span></span>

- [<span data-ttu-id="bb0f6-136">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="bb0f6-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="bb0f6-137">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="bb0f6-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="bb0f6-138">\<GCCpuGroup > 元素</span><span class="sxs-lookup"><span data-stu-id="bb0f6-138">\<GCCpuGroup> Element</span></span>](gccpugroup-element.md)
