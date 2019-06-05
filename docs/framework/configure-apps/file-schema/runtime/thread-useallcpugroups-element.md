---
title: <Thread_UseAllCpuGroups> 項目
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9758e009e012c8af5f5f7bd19dcd21f34b8c7d96
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "66689730"
---
# <a name="threaduseallcpugroups-element"></a><span data-ttu-id="4c91d-102">\<Thread_UseAllCpuGroups > 項目</span><span class="sxs-lookup"><span data-stu-id="4c91d-102">\<Thread_UseAllCpuGroups> Element</span></span>

<span data-ttu-id="4c91d-103">指定執行階段是否會將 Managed 執行緒分散到所有 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="4c91d-103">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>

<span data-ttu-id="4c91d-104">\<configuration>\\</span><span class="sxs-lookup"><span data-stu-id="4c91d-104">\<configuration>\\</span></span>
<span data-ttu-id="4c91d-105">\<runtime>\\</span><span class="sxs-lookup"><span data-stu-id="4c91d-105">\<runtime>\\</span></span>
<span data-ttu-id="4c91d-106">\<Thread_UseAllCpuGroups></span><span class="sxs-lookup"><span data-stu-id="4c91d-106">\<Thread_UseAllCpuGroups></span></span>

## <a name="syntax"></a><span data-ttu-id="4c91d-107">語法</span><span class="sxs-lookup"><span data-stu-id="4c91d-107">Syntax</span></span>

```xml
<Thread_UseAllCpuGroups
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4c91d-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4c91d-108">Attributes and Elements</span></span>

<span data-ttu-id="4c91d-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="4c91d-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="4c91d-110">屬性</span><span class="sxs-lookup"><span data-stu-id="4c91d-110">Attributes</span></span>

|<span data-ttu-id="4c91d-111">屬性</span><span class="sxs-lookup"><span data-stu-id="4c91d-111">Attribute</span></span>|<span data-ttu-id="4c91d-112">描述</span><span class="sxs-lookup"><span data-stu-id="4c91d-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="4c91d-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="4c91d-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="4c91d-114">指定執行階段是否會將 Managed 執行緒分散到所有 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="4c91d-114">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="4c91d-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="4c91d-115">enabled Attribute</span></span>

|<span data-ttu-id="4c91d-116">值</span><span class="sxs-lookup"><span data-stu-id="4c91d-116">Value</span></span>|<span data-ttu-id="4c91d-117">描述</span><span class="sxs-lookup"><span data-stu-id="4c91d-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="4c91d-118">執行階段不會跨多個 CPU 群組分配 managed 的執行緒。</span><span class="sxs-lookup"><span data-stu-id="4c91d-118">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="4c91d-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="4c91d-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="4c91d-120">執行階段會分散到多個 CPU 群組，managed 的執行緒如果電腦有多個 CPU 群組及[ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)項目已啟用。</span><span class="sxs-lookup"><span data-stu-id="4c91d-120">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="4c91d-121">子元素</span><span class="sxs-lookup"><span data-stu-id="4c91d-121">Child Elements</span></span>

<span data-ttu-id="4c91d-122">無。</span><span class="sxs-lookup"><span data-stu-id="4c91d-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4c91d-123">父項目</span><span class="sxs-lookup"><span data-stu-id="4c91d-123">Parent Elements</span></span>

|<span data-ttu-id="4c91d-124">項目</span><span class="sxs-lookup"><span data-stu-id="4c91d-124">Element</span></span>|<span data-ttu-id="4c91d-125">描述</span><span class="sxs-lookup"><span data-stu-id="4c91d-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="4c91d-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="4c91d-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="4c91d-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="4c91d-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4c91d-128">備註</span><span class="sxs-lookup"><span data-stu-id="4c91d-128">Remarks</span></span>

<span data-ttu-id="4c91d-129">當電腦具有多個 CPU 群組時，啟用這個項目會導致執行階段的所有 CPU 群組分配 managed 的執行緒。</span><span class="sxs-lookup"><span data-stu-id="4c91d-129">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="4c91d-130">若要使用這項功能，您也必須啟用[ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)元素，其記憶體回收會延伸到所有 CPU 群組並考量所有的核心建立，並平衡堆積時。</span><span class="sxs-lookup"><span data-stu-id="4c91d-130">To use this feature, you must also enable the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="4c91d-131">啟用[ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)項目時，必須啟用[ \<Gcserver> >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)項目。</span><span class="sxs-lookup"><span data-stu-id="4c91d-131">Enabling the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element requires enabling the [\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element.</span></span> <span data-ttu-id="4c91d-132">如果未啟用這些項目，則啟用`<Thread_UseAllCpuGroups>`項目沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="4c91d-132">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>

## <a name="example"></a><span data-ttu-id="4c91d-133">範例</span><span class="sxs-lookup"><span data-stu-id="4c91d-133">Example</span></span>

<span data-ttu-id="4c91d-134">下列範例示範如何啟用多個 CPU 群組的支援。</span><span class="sxs-lookup"><span data-stu-id="4c91d-134">The following example shows how to enable support for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <Thread_UseAllCpuGroups enabled="true"/>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="4c91d-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c91d-135">See also</span></span>

- [<span data-ttu-id="4c91d-136">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="4c91d-136">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="4c91d-137">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="4c91d-137">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="4c91d-138">\<GCCpuGroup > 項目</span><span class="sxs-lookup"><span data-stu-id="4c91d-138">\<GCCpuGroup> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)
