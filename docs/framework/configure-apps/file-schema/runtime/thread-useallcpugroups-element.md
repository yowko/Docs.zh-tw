---
title: <Thread_UseAllCpuGroups> 項目
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
ms.openlocfilehash: a3a612c0ffbcb211157b9623d298ce8ad7a13e94
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115402"
---
# <a name="thread_useallcpugroups-element"></a><span data-ttu-id="355b2-102">\<Thread_UseAllCpuGroups> 項目</span><span class="sxs-lookup"><span data-stu-id="355b2-102">\<Thread_UseAllCpuGroups> Element</span></span>

<span data-ttu-id="355b2-103">指定執行階段是否會將 Managed 執行緒分散到所有 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="355b2-103">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<Thread_UseAllCpuGroups>**  

## <a name="syntax"></a><span data-ttu-id="355b2-104">語法</span><span class="sxs-lookup"><span data-stu-id="355b2-104">Syntax</span></span>

```xml
<Thread_UseAllCpuGroups
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="355b2-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="355b2-105">Attributes and Elements</span></span>

<span data-ttu-id="355b2-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="355b2-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="355b2-107">屬性</span><span class="sxs-lookup"><span data-stu-id="355b2-107">Attributes</span></span>

|<span data-ttu-id="355b2-108">屬性</span><span class="sxs-lookup"><span data-stu-id="355b2-108">Attribute</span></span>|<span data-ttu-id="355b2-109">描述</span><span class="sxs-lookup"><span data-stu-id="355b2-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="355b2-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="355b2-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="355b2-111">指定執行階段是否會將 Managed 執行緒分散到所有 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="355b2-111">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="355b2-112">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="355b2-112">enabled Attribute</span></span>

|<span data-ttu-id="355b2-113">值</span><span class="sxs-lookup"><span data-stu-id="355b2-113">Value</span></span>|<span data-ttu-id="355b2-114">描述</span><span class="sxs-lookup"><span data-stu-id="355b2-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="355b2-115">執行時間不會將受控執行緒分散到多個 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="355b2-115">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="355b2-116">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="355b2-116">This is the default.</span></span>|
|`true`|<span data-ttu-id="355b2-117">如果電腦有多個 CPU 群組且已啟用元素，則執行時間會將受控執行緒分散到多個 CPU 群組 [\<GCCpuGroup>](gccpugroup-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="355b2-117">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](gccpugroup-element.md) element is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="355b2-118">子元素</span><span class="sxs-lookup"><span data-stu-id="355b2-118">Child Elements</span></span>

<span data-ttu-id="355b2-119">無。</span><span class="sxs-lookup"><span data-stu-id="355b2-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="355b2-120">父項目</span><span class="sxs-lookup"><span data-stu-id="355b2-120">Parent Elements</span></span>

|<span data-ttu-id="355b2-121">元素</span><span class="sxs-lookup"><span data-stu-id="355b2-121">Element</span></span>|<span data-ttu-id="355b2-122">描述</span><span class="sxs-lookup"><span data-stu-id="355b2-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="355b2-123">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="355b2-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="355b2-124">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="355b2-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="355b2-125">備註</span><span class="sxs-lookup"><span data-stu-id="355b2-125">Remarks</span></span>

<span data-ttu-id="355b2-126">當電腦具有多個 CPU 群組時，啟用此元素會導致執行時間將受控執行緒分散到所有 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="355b2-126">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="355b2-127">若要使用這項功能，您也必須啟用 [\<GCCpuGroup>](gccpugroup-element.md) 元素，此專案會將垃圾收集延伸至所有 CPU 群組，並在建立和平衡堆積時將所有核心納入考慮。</span><span class="sxs-lookup"><span data-stu-id="355b2-127">To use this feature, you must also enable the [\<GCCpuGroup>](gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="355b2-128">啟用 [\<GCCpuGroup>](gccpugroup-element.md) 元素需要啟用專案 [\<gcServer>](gcserver-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="355b2-128">Enabling the [\<GCCpuGroup>](gccpugroup-element.md) element requires enabling the [\<gcServer>](gcserver-element.md) element.</span></span> <span data-ttu-id="355b2-129">如果未啟用這些元素，啟用元素將 `<Thread_UseAllCpuGroups>` 不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="355b2-129">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>

## <a name="example"></a><span data-ttu-id="355b2-130">範例</span><span class="sxs-lookup"><span data-stu-id="355b2-130">Example</span></span>

<span data-ttu-id="355b2-131">下列範例顯示如何啟用多個 CPU 群組的支援。</span><span class="sxs-lookup"><span data-stu-id="355b2-131">The following example shows how to enable support for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <Thread_UseAllCpuGroups enabled="true"/>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="355b2-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="355b2-132">See also</span></span>

- [<span data-ttu-id="355b2-133">執行時間設定架構</span><span class="sxs-lookup"><span data-stu-id="355b2-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="355b2-134">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="355b2-134">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="355b2-135">\<GCCpuGroup>元素</span><span class="sxs-lookup"><span data-stu-id="355b2-135">\<GCCpuGroup> Element</span></span>](gccpugroup-element.md)
