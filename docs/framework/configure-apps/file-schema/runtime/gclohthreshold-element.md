---
title: GCLOHThreshold element
ms.date: 11/20/2019
helpviewer_keywords:
- GCLOHThreshold element
- <GCLOHThreshold> element
ms.openlocfilehash: d72dc9d27984f60dfb6296217263ce8b176093c6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451217"
---
# <a name="gclohthreshold-element"></a><span data-ttu-id="fedaa-102">GCLOHThreshold element</span><span class="sxs-lookup"><span data-stu-id="fedaa-102">GCLOHThreshold element</span></span>

<span data-ttu-id="fedaa-103">Specifies the threshold size, in bytes, that causes the garbage collector to put objects on the large object heap (LOH).</span><span class="sxs-lookup"><span data-stu-id="fedaa-103">Specifies the threshold size, in bytes, that causes the garbage collector to put objects on the large object heap (LOH).</span></span>

<span data-ttu-id="fedaa-104">[\<configuration>](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fedaa-104">[\<configuration>](../configuration-element.md)</span></span>\
<span data-ttu-id="fedaa-105">&nbsp;&nbsp;[\<runtime>](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="fedaa-105">&nbsp;&nbsp;[\<runtime>](runtime-element.md)</span></span>\
<span data-ttu-id="fedaa-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold></span><span class="sxs-lookup"><span data-stu-id="fedaa-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold></span></span>

## <a name="syntax"></a><span data-ttu-id="fedaa-107">語法</span><span class="sxs-lookup"><span data-stu-id="fedaa-107">Syntax</span></span>

```xml
<GCLOHThreshold
   enabled="nnnn"/>
```

## <a name="attributes"></a><span data-ttu-id="fedaa-108">屬性</span><span class="sxs-lookup"><span data-stu-id="fedaa-108">Attributes</span></span>

|<span data-ttu-id="fedaa-109">屬性</span><span class="sxs-lookup"><span data-stu-id="fedaa-109">Attribute</span></span>|<span data-ttu-id="fedaa-110">描述</span><span class="sxs-lookup"><span data-stu-id="fedaa-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="fedaa-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="fedaa-111">Required attribute.</span></span><br /><br /><span data-ttu-id="fedaa-112">Specifies the threshold size that causes objects to go on the large object heap.</span><span class="sxs-lookup"><span data-stu-id="fedaa-112">Specifies the threshold size that causes objects to go on the large object heap.</span></span>|

### <a name="enabled-attribute"></a><span data-ttu-id="fedaa-113">enabled attribute</span><span class="sxs-lookup"><span data-stu-id="fedaa-113">enabled attribute</span></span>

|<span data-ttu-id="fedaa-114">值</span><span class="sxs-lookup"><span data-stu-id="fedaa-114">Value</span></span>|<span data-ttu-id="fedaa-115">描述</span><span class="sxs-lookup"><span data-stu-id="fedaa-115">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="fedaa-116">The threshold size, in bytes, that causes objects to go on the large object heap.</span><span class="sxs-lookup"><span data-stu-id="fedaa-116">The threshold size, in bytes, that causes objects to go on the large object heap.</span></span>|

## <a name="child-elements"></a><span data-ttu-id="fedaa-117">子元素</span><span class="sxs-lookup"><span data-stu-id="fedaa-117">Child elements</span></span>

<span data-ttu-id="fedaa-118">無。</span><span class="sxs-lookup"><span data-stu-id="fedaa-118">None.</span></span>

## <a name="parent-elements"></a><span data-ttu-id="fedaa-119">父元素</span><span class="sxs-lookup"><span data-stu-id="fedaa-119">Parent elements</span></span>

|<span data-ttu-id="fedaa-120">項目</span><span class="sxs-lookup"><span data-stu-id="fedaa-120">Element</span></span>|<span data-ttu-id="fedaa-121">描述</span><span class="sxs-lookup"><span data-stu-id="fedaa-121">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="fedaa-122">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="fedaa-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="fedaa-123">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="fedaa-123">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fedaa-124">備註</span><span class="sxs-lookup"><span data-stu-id="fedaa-124">Remarks</span></span>

<span data-ttu-id="fedaa-125">This setting was introduced in .NET Framework 4.8.</span><span class="sxs-lookup"><span data-stu-id="fedaa-125">This setting was introduced in .NET Framework 4.8.</span></span>

## <a name="see-also"></a><span data-ttu-id="fedaa-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="fedaa-126">See also</span></span>

- [<span data-ttu-id="fedaa-127">Run-time settings schema</span><span class="sxs-lookup"><span data-stu-id="fedaa-127">Run-time settings schema</span></span>](index.md)
- [<span data-ttu-id="fedaa-128">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="fedaa-128">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="fedaa-129">記憶體回收的基本概念</span><span class="sxs-lookup"><span data-stu-id="fedaa-129">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="fedaa-130">NET Core run-time config options for GC</span><span class="sxs-lookup"><span data-stu-id="fedaa-130">NET Core run-time config options for GC</span></span>](../../../../core/run-time-config/garbage-collector.md)
