---
title: 監視鎖定爭用運行時間事件
description: 請參閱收集監視器鎖定爭用特定資訊的 ETW 事件。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- monitor lock contention events (CoreCLR)
- ETW, EventPipe, LTTng contention events (CoreCLR)
ms.openlocfilehash: 38e5f493d4b223b4839dbd6f814cf656722189b2
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "96586638"
---
# <a name="net-runtime-contention-events"></a><span data-ttu-id="7e903-103">.NET 執行時間爭用事件</span><span class="sxs-lookup"><span data-stu-id="7e903-103">.NET runtime contention events</span></span>

<span data-ttu-id="7e903-104">這些運行時間事件會捕捉有關監視器鎖定爭用的資訊，例如 with `Monitor.Enter` 或 c # lock 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="7e903-104">These runtime events capture information about monitor lock contentions such as with `Monitor.Enter` or the C# lock keyword.</span></span> <span data-ttu-id="7e903-105">如需如何基於診斷目的使用這些事件的詳細資訊，請參閱[記錄和追蹤 .net 應用程式](../../core/diagnostics/logging-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="7e903-105">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="contentionstart_v1-event"></a><span data-ttu-id="7e903-106">ContentionStart_V1 事件</span><span class="sxs-lookup"><span data-stu-id="7e903-106">ContentionStart_V1 event</span></span>

<span data-ttu-id="7e903-107">此事件是在監視器鎖定爭用開始時發出。</span><span class="sxs-lookup"><span data-stu-id="7e903-107">This event is emitted at the start of a monitor lock contention.</span></span>

|<span data-ttu-id="7e903-108">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="7e903-108">Keyword for raising the event</span></span>|<span data-ttu-id="7e903-109">層級</span><span class="sxs-lookup"><span data-stu-id="7e903-109">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="7e903-110">`ContentionKeyword` (0x4000)</span><span class="sxs-lookup"><span data-stu-id="7e903-110">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="7e903-111">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="7e903-111">Informational (4)</span></span>|

 <span data-ttu-id="7e903-112">下表顯示事件資訊。</span><span class="sxs-lookup"><span data-stu-id="7e903-112">The following table shows event information.</span></span>

|<span data-ttu-id="7e903-113">事件</span><span class="sxs-lookup"><span data-stu-id="7e903-113">Event</span></span>|<span data-ttu-id="7e903-114">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="7e903-114">Event ID</span></span>|<span data-ttu-id="7e903-115">引發的時機</span><span class="sxs-lookup"><span data-stu-id="7e903-115">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|<span data-ttu-id="7e903-116">81</span><span class="sxs-lookup"><span data-stu-id="7e903-116">81</span></span>|<span data-ttu-id="7e903-117">監視器鎖定爭用隨即啟動。</span><span class="sxs-lookup"><span data-stu-id="7e903-117">A monitor lock contention starts.</span></span>|

|<span data-ttu-id="7e903-118">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="7e903-118">Field name</span></span>|<span data-ttu-id="7e903-119">資料類型</span><span class="sxs-lookup"><span data-stu-id="7e903-119">Data type</span></span>|<span data-ttu-id="7e903-120">描述</span><span class="sxs-lookup"><span data-stu-id="7e903-120">Description</span></span>|
|----------------|---------------|-----------------|
|`Flags`|`win:UInt8`|<span data-ttu-id="7e903-121">`0` 針對 managed; `1` 適用于原生。</span><span class="sxs-lookup"><span data-stu-id="7e903-121">`0` for managed; `1` for native.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="7e903-122">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="7e903-122">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="contentionstop_v1-event"></a><span data-ttu-id="7e903-123">ContentionStop_V1 事件</span><span class="sxs-lookup"><span data-stu-id="7e903-123">ContentionStop_V1 event</span></span>

<span data-ttu-id="7e903-124">此事件是在監視器鎖定爭用結束時發出。</span><span class="sxs-lookup"><span data-stu-id="7e903-124">This event is emitted at the end of a monitor lock contention.</span></span>

|<span data-ttu-id="7e903-125">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="7e903-125">Keyword for raising the event</span></span>|<span data-ttu-id="7e903-126">層級</span><span class="sxs-lookup"><span data-stu-id="7e903-126">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="7e903-127">`ContentionKeyword` (0x4000)</span><span class="sxs-lookup"><span data-stu-id="7e903-127">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="7e903-128">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="7e903-128">Informational (4)</span></span>|

 <span data-ttu-id="7e903-129">下表顯示事件資訊。</span><span class="sxs-lookup"><span data-stu-id="7e903-129">The following table shows event information.</span></span>

|<span data-ttu-id="7e903-130">事件</span><span class="sxs-lookup"><span data-stu-id="7e903-130">Event</span></span>|<span data-ttu-id="7e903-131">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="7e903-131">Event ID</span></span>|<span data-ttu-id="7e903-132">引發的時機</span><span class="sxs-lookup"><span data-stu-id="7e903-132">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ContentionStop_V1`|<span data-ttu-id="7e903-133">91</span><span class="sxs-lookup"><span data-stu-id="7e903-133">91</span></span>|<span data-ttu-id="7e903-134">監視器鎖定爭用結束。</span><span class="sxs-lookup"><span data-stu-id="7e903-134">A monitor lock contention ends.</span></span>|

|<span data-ttu-id="7e903-135">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="7e903-135">Field name</span></span>|<span data-ttu-id="7e903-136">資料類型</span><span class="sxs-lookup"><span data-stu-id="7e903-136">Data type</span></span>|<span data-ttu-id="7e903-137">描述</span><span class="sxs-lookup"><span data-stu-id="7e903-137">Description</span></span>|
|----------------|---------------|-----------------|
|`Flags`|`win:UInt8`|<span data-ttu-id="7e903-138">`0` 針對 managed; `1` 適用于原生。</span><span class="sxs-lookup"><span data-stu-id="7e903-138">`0` for managed; `1` for native.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="7e903-139">CoreCLR 實例的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="7e903-139">Unique ID for the instance of CoreCLR.</span></span>|
|`DurationNs`|`win:Double`|<span data-ttu-id="7e903-140">爭用的持續時間（以毫微秒為單位）。</span><span class="sxs-lookup"><span data-stu-id="7e903-140">Duration of the contention in nanoseconds.</span></span>|
