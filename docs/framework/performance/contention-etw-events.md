---
title: 爭用 ETW 事件-.NET
description: 取得爭用 ETW 事件的詳細資料，這會在每次發生爭用時引發，並會在執行時間所使用的執行緒監視器鎖定或原生鎖定時發生。
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
ms.openlocfilehash: a36b091e0896562fffdb66e895d70049ce0667d7
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309595"
---
# <a name="contention-etw-events"></a><span data-ttu-id="3cc79-103">爭用 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="3cc79-103">Contention ETW events</span></span>

<span data-ttu-id="3cc79-104">只要爭用執行階段所使用的 <xref:System.Threading.Monitor?displayProperty=nameWithType> 鎖定或原生鎖定，就會引發爭用事件。</span><span class="sxs-lookup"><span data-stu-id="3cc79-104">Contention events are raised whenever there is contention for <xref:System.Threading.Monitor?displayProperty=nameWithType> locks or native locks used by the runtime.</span></span> <span data-ttu-id="3cc79-105">如果某個執行緒等待鎖定，而另一個執行緒擁有該鎖定，則會發生爭用。</span><span class="sxs-lookup"><span data-stu-id="3cc79-105">Contention occurs when a thread is waiting for a lock while another thread possesses the lock.</span></span>

<span data-ttu-id="3cc79-106">下表顯示引發爭用事件的關鍵字以及事件層級。</span><span class="sxs-lookup"><span data-stu-id="3cc79-106">The following table shows the keyword under which contention events are raised, and the level of the events.</span></span> <span data-ttu-id="3cc79-107">如需詳細資訊，請參閱[CLR ETW 關鍵字和層級](clr-etw-keywords-and-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="3cc79-107">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="3cc79-108">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="3cc79-108">Keyword for raising the event</span></span>|<span data-ttu-id="3cc79-109">層級</span><span class="sxs-lookup"><span data-stu-id="3cc79-109">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="3cc79-110">`ContentionKeyword` (0x4000)</span><span class="sxs-lookup"><span data-stu-id="3cc79-110">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="3cc79-111">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="3cc79-111">Informational (4)</span></span>|

<span data-ttu-id="3cc79-112">下表顯示事件資訊：</span><span class="sxs-lookup"><span data-stu-id="3cc79-112">The following table shows event information:</span></span>

|<span data-ttu-id="3cc79-113">事件</span><span class="sxs-lookup"><span data-stu-id="3cc79-113">Event</span></span>|<span data-ttu-id="3cc79-114">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="3cc79-114">Event ID</span></span>|<span data-ttu-id="3cc79-115">引發的時機</span><span class="sxs-lookup"><span data-stu-id="3cc79-115">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|<span data-ttu-id="3cc79-116">81</span><span class="sxs-lookup"><span data-stu-id="3cc79-116">81</span></span>|<span data-ttu-id="3cc79-117">爭用開始。</span><span class="sxs-lookup"><span data-stu-id="3cc79-117">Contention starts.</span></span> <span data-ttu-id="3cc79-118">此事件未包含執行緒等候取得鎖定之前的微調時間量；只有在執行緒等候取得鎖定時才會引發此事件。</span><span class="sxs-lookup"><span data-stu-id="3cc79-118">This event does not include the amount of spinning time before a thread waits to acquire a lock; it is raised only when the thread waits to acquire a lock.</span></span>|
|`ContentionStop`|<span data-ttu-id="3cc79-119">91</span><span class="sxs-lookup"><span data-stu-id="3cc79-119">91</span></span>|<span data-ttu-id="3cc79-120">爭用結束。</span><span class="sxs-lookup"><span data-stu-id="3cc79-120">Contention ends.</span></span>|

<span data-ttu-id="3cc79-121">下表顯示事件資料：</span><span class="sxs-lookup"><span data-stu-id="3cc79-121">The following table shows event data:</span></span>

|<span data-ttu-id="3cc79-122">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="3cc79-122">Field name</span></span>|<span data-ttu-id="3cc79-123">資料類型</span><span class="sxs-lookup"><span data-stu-id="3cc79-123">Data type</span></span>|<span data-ttu-id="3cc79-124">描述</span><span class="sxs-lookup"><span data-stu-id="3cc79-124">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="3cc79-125">Flags</span><span class="sxs-lookup"><span data-stu-id="3cc79-125">Flags</span></span>|<span data-ttu-id="3cc79-126">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="3cc79-126">win:UInt8</span></span>|<span data-ttu-id="3cc79-127">0 表示 Managed；1 表示原生。</span><span class="sxs-lookup"><span data-stu-id="3cc79-127">0 for managed; 1 for native.</span></span>|
|<span data-ttu-id="3cc79-128">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="3cc79-128">ClrInstanceID</span></span>|<span data-ttu-id="3cc79-129">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="3cc79-129">win:UInt16</span></span>|<span data-ttu-id="3cc79-130">CLR 執行個體的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="3cc79-130">Unique ID for the instance of CLR.</span></span>|

## <a name="see-also"></a><span data-ttu-id="3cc79-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3cc79-131">See also</span></span>

- [<span data-ttu-id="3cc79-132">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="3cc79-132">CLR ETW Events</span></span>](clr-etw-events.md)
