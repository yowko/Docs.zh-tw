---
title: GCLOHThreshold 元素
ms.date: 11/20/2019
helpviewer_keywords:
- GCLOHThreshold element
- <GCLOHThreshold> element
ms.openlocfilehash: d72dc9d27984f60dfb6296217263ce8b176093c6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "74451217"
---
# <a name="gclohthreshold-element"></a><span data-ttu-id="6b021-102">GCLOHThreshold 元素</span><span class="sxs-lookup"><span data-stu-id="6b021-102">GCLOHThreshold element</span></span>

<span data-ttu-id="6b021-103">指定導致垃圾收集行程將物件放在大型物件堆積（LOH）上的閾值大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="6b021-103">Specifies the threshold size, in bytes, that causes the garbage collector to put objects on the large object heap (LOH).</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold>

## <a name="syntax"></a><span data-ttu-id="6b021-104">語法</span><span class="sxs-lookup"><span data-stu-id="6b021-104">Syntax</span></span>

```xml
<GCLOHThreshold
   enabled="nnnn"/>
```

## <a name="attributes"></a><span data-ttu-id="6b021-105">屬性</span><span class="sxs-lookup"><span data-stu-id="6b021-105">Attributes</span></span>

|<span data-ttu-id="6b021-106">屬性</span><span class="sxs-lookup"><span data-stu-id="6b021-106">Attribute</span></span>|<span data-ttu-id="6b021-107">描述</span><span class="sxs-lookup"><span data-stu-id="6b021-107">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="6b021-108">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="6b021-108">Required attribute.</span></span><br /><br /><span data-ttu-id="6b021-109">指定導致物件在大型物件堆積上執行的臨界值大小。</span><span class="sxs-lookup"><span data-stu-id="6b021-109">Specifies the threshold size that causes objects to go on the large object heap.</span></span>|

### <a name="enabled-attribute"></a><span data-ttu-id="6b021-110">enabled 屬性</span><span class="sxs-lookup"><span data-stu-id="6b021-110">enabled attribute</span></span>

|<span data-ttu-id="6b021-111">值</span><span class="sxs-lookup"><span data-stu-id="6b021-111">Value</span></span>|<span data-ttu-id="6b021-112">描述</span><span class="sxs-lookup"><span data-stu-id="6b021-112">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="6b021-113">導致物件在大型物件堆積上執行的臨界值大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="6b021-113">The threshold size, in bytes, that causes objects to go on the large object heap.</span></span>|

## <a name="child-elements"></a><span data-ttu-id="6b021-114">子元素</span><span class="sxs-lookup"><span data-stu-id="6b021-114">Child elements</span></span>

<span data-ttu-id="6b021-115">無。</span><span class="sxs-lookup"><span data-stu-id="6b021-115">None.</span></span>

## <a name="parent-elements"></a><span data-ttu-id="6b021-116">父元素</span><span class="sxs-lookup"><span data-stu-id="6b021-116">Parent elements</span></span>

|<span data-ttu-id="6b021-117">元素</span><span class="sxs-lookup"><span data-stu-id="6b021-117">Element</span></span>|<span data-ttu-id="6b021-118">描述</span><span class="sxs-lookup"><span data-stu-id="6b021-118">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="6b021-119">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="6b021-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="6b021-120">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="6b021-120">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6b021-121">備註</span><span class="sxs-lookup"><span data-stu-id="6b021-121">Remarks</span></span>

<span data-ttu-id="6b021-122">這項設定是在 .NET Framework 4.8 中引進。</span><span class="sxs-lookup"><span data-stu-id="6b021-122">This setting was introduced in .NET Framework 4.8.</span></span>

## <a name="see-also"></a><span data-ttu-id="6b021-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b021-123">See also</span></span>

- [<span data-ttu-id="6b021-124">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="6b021-124">Run-time settings schema</span></span>](index.md)
- [<span data-ttu-id="6b021-125">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="6b021-125">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="6b021-126">垃圾收集的基本概念</span><span class="sxs-lookup"><span data-stu-id="6b021-126">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="6b021-127">GC 的 NET Core 執行時間設定選項</span><span class="sxs-lookup"><span data-stu-id="6b021-127">NET Core run-time config options for GC</span></span>](../../../../core/run-time-config/garbage-collector.md)
