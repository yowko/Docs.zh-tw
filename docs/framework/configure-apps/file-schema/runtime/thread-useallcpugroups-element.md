---
title: <Thread_UseAllCpuGroups> 項目
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
ms.openlocfilehash: a3a612c0ffbcb211157b9623d298ce8ad7a13e94
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115402"
---
# <a name="thread_useallcpugroups-element"></a><span data-ttu-id="99334-102">\<Thread_UseAllCpuGroups> Element</span><span class="sxs-lookup"><span data-stu-id="99334-102">\<Thread_UseAllCpuGroups> Element</span></span>

<span data-ttu-id="99334-103">指定執行階段是否會將 Managed 執行緒分散到所有 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="99334-103">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>

<span data-ttu-id="99334-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="99334-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="99334-105">&nbsp;&nbsp;[ **\<runtime>** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="99334-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="99334-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<Thread_UseAllCpuGroups>**</span><span class="sxs-lookup"><span data-stu-id="99334-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Thread_UseAllCpuGroups>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="99334-107">語法</span><span class="sxs-lookup"><span data-stu-id="99334-107">Syntax</span></span>

```xml
<Thread_UseAllCpuGroups
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="99334-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="99334-108">Attributes and Elements</span></span>

<span data-ttu-id="99334-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="99334-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="99334-110">屬性</span><span class="sxs-lookup"><span data-stu-id="99334-110">Attributes</span></span>

|<span data-ttu-id="99334-111">屬性</span><span class="sxs-lookup"><span data-stu-id="99334-111">Attribute</span></span>|<span data-ttu-id="99334-112">描述</span><span class="sxs-lookup"><span data-stu-id="99334-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="99334-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="99334-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="99334-114">指定執行階段是否會將 Managed 執行緒分散到所有 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="99334-114">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="99334-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="99334-115">enabled Attribute</span></span>

|<span data-ttu-id="99334-116">值</span><span class="sxs-lookup"><span data-stu-id="99334-116">Value</span></span>|<span data-ttu-id="99334-117">描述</span><span class="sxs-lookup"><span data-stu-id="99334-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="99334-118">The runtime does not distribute managed threads across multiple CPU groups.</span><span class="sxs-lookup"><span data-stu-id="99334-118">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="99334-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="99334-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="99334-120">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](gccpugroup-element.md) element is enabled.</span><span class="sxs-lookup"><span data-stu-id="99334-120">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](gccpugroup-element.md) element is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="99334-121">子項目</span><span class="sxs-lookup"><span data-stu-id="99334-121">Child Elements</span></span>

<span data-ttu-id="99334-122">無。</span><span class="sxs-lookup"><span data-stu-id="99334-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="99334-123">父項目</span><span class="sxs-lookup"><span data-stu-id="99334-123">Parent Elements</span></span>

|<span data-ttu-id="99334-124">項目</span><span class="sxs-lookup"><span data-stu-id="99334-124">Element</span></span>|<span data-ttu-id="99334-125">描述</span><span class="sxs-lookup"><span data-stu-id="99334-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="99334-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="99334-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="99334-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="99334-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="99334-128">備註</span><span class="sxs-lookup"><span data-stu-id="99334-128">Remarks</span></span>

<span data-ttu-id="99334-129">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span><span class="sxs-lookup"><span data-stu-id="99334-129">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="99334-130">To use this feature, you must also enable the [\<GCCpuGroup>](gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span><span class="sxs-lookup"><span data-stu-id="99334-130">To use this feature, you must also enable the [\<GCCpuGroup>](gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="99334-131">Enabling the [\<GCCpuGroup>](gccpugroup-element.md) element requires enabling the [\<gcServer>](gcserver-element.md) element.</span><span class="sxs-lookup"><span data-stu-id="99334-131">Enabling the [\<GCCpuGroup>](gccpugroup-element.md) element requires enabling the [\<gcServer>](gcserver-element.md) element.</span></span> <span data-ttu-id="99334-132">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span><span class="sxs-lookup"><span data-stu-id="99334-132">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>

## <a name="example"></a><span data-ttu-id="99334-133">範例</span><span class="sxs-lookup"><span data-stu-id="99334-133">Example</span></span>

<span data-ttu-id="99334-134">The following example shows how to enable support for multiple CPU groups.</span><span class="sxs-lookup"><span data-stu-id="99334-134">The following example shows how to enable support for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <Thread_UseAllCpuGroups enabled="true"/>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="99334-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="99334-135">See also</span></span>

- [<span data-ttu-id="99334-136">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="99334-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="99334-137">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="99334-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="99334-138">\<GCCpuGroup> Element</span><span class="sxs-lookup"><span data-stu-id="99334-138">\<GCCpuGroup> Element</span></span>](gccpugroup-element.md)
