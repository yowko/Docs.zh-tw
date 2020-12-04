---
title: 輸入系統運行時間事件
description: 請參閱收集 .NET 類型系統特定診斷資訊的 .NET 運行時間事件，例如 TypeLoadStart 和 TypeLoadStop。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- type system events (CoreCLR)
- ETW, EventPipe, LTTng type system events (CoreCLR)
ms.openlocfilehash: 8eee89cddb0098da2cb449a4be21945adac725e3
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "96586633"
---
# <a name="net-runtime-type-events"></a><span data-ttu-id="fc6f2-103">.NET 執行時間類型事件</span><span class="sxs-lookup"><span data-stu-id="fc6f2-103">.NET runtime type events</span></span>

<span data-ttu-id="fc6f2-104">這些事件會收集與載入類型相關的資訊。</span><span class="sxs-lookup"><span data-stu-id="fc6f2-104">These events collect information relating to loading types.</span></span> <span data-ttu-id="fc6f2-105">如需如何基於診斷目的使用這些事件的詳細資訊，請參閱[記錄和追蹤 .net 應用程式](../../core/diagnostics/logging-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="fc6f2-105">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="typeloadstart-event"></a><span data-ttu-id="fc6f2-106">TypeLoadStart 事件</span><span class="sxs-lookup"><span data-stu-id="fc6f2-106">TypeLoadStart Event</span></span>

|<span data-ttu-id="fc6f2-107">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="fc6f2-107">Keyword for raising the event</span></span>|<span data-ttu-id="fc6f2-108">事件</span><span class="sxs-lookup"><span data-stu-id="fc6f2-108">Event</span></span>|<span data-ttu-id="fc6f2-109">層級</span><span class="sxs-lookup"><span data-stu-id="fc6f2-109">Level</span></span>|  
|-----------------------------------|-----------|-----------|  
|<span data-ttu-id="fc6f2-110">`TypeDiagnosticKeyword` (0x8000000000) </span><span class="sxs-lookup"><span data-stu-id="fc6f2-110">`TypeDiagnosticKeyword` (0x8000000000)</span></span>|<span data-ttu-id="fc6f2-111">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="fc6f2-111">Informational (4)</span></span>|  

|<span data-ttu-id="fc6f2-112">事件</span><span class="sxs-lookup"><span data-stu-id="fc6f2-112">Event</span></span>|<span data-ttu-id="fc6f2-113">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="fc6f2-113">Event ID</span></span>|<span data-ttu-id="fc6f2-114">描述</span><span class="sxs-lookup"><span data-stu-id="fc6f2-114">Description</span></span>|  
|-----------|--------------|-----------------|  
|`TypeLoadStart`|<span data-ttu-id="fc6f2-115">73</span><span class="sxs-lookup"><span data-stu-id="fc6f2-115">73</span></span>|<span data-ttu-id="fc6f2-116">類型載入已開始。</span><span class="sxs-lookup"><span data-stu-id="fc6f2-116">A type load has started.</span></span>|

|<span data-ttu-id="fc6f2-117">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="fc6f2-117">Field name</span></span>|<span data-ttu-id="fc6f2-118">資料類型</span><span class="sxs-lookup"><span data-stu-id="fc6f2-118">Data type</span></span>|<span data-ttu-id="fc6f2-119">描述</span><span class="sxs-lookup"><span data-stu-id="fc6f2-119">Description</span></span>|  
|----------------|---------------|-----------------|  
|`TypeLoadStartID`|`win:UInt32`|<span data-ttu-id="fc6f2-120">類型載入作業的識別碼。</span><span class="sxs-lookup"><span data-stu-id="fc6f2-120">ID for the type load operation.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="fc6f2-121">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="fc6f2-121">Unique ID for the instance of CLR or CoreCLR.</span></span>|  

## <a name="typeloadstop-event"></a><span data-ttu-id="fc6f2-122">TypeLoadStop 事件</span><span class="sxs-lookup"><span data-stu-id="fc6f2-122">TypeLoadStop Event</span></span>

|<span data-ttu-id="fc6f2-123">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="fc6f2-123">Keyword for raising the event</span></span>|<span data-ttu-id="fc6f2-124">層級</span><span class="sxs-lookup"><span data-stu-id="fc6f2-124">Level</span></span>|  
|-----------------------------------|-----------|-----------|  
|<span data-ttu-id="fc6f2-125">`TypeDiagnosticKeyword` (0x8000000000) </span><span class="sxs-lookup"><span data-stu-id="fc6f2-125">`TypeDiagnosticKeyword` (0x8000000000)</span></span>|<span data-ttu-id="fc6f2-126">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="fc6f2-126">Informational (4)</span></span>|  

|<span data-ttu-id="fc6f2-127">事件</span><span class="sxs-lookup"><span data-stu-id="fc6f2-127">Event</span></span>|<span data-ttu-id="fc6f2-128">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="fc6f2-128">Event ID</span></span>|<span data-ttu-id="fc6f2-129">描述</span><span class="sxs-lookup"><span data-stu-id="fc6f2-129">Description</span></span>|  
|-----------|--------------|-----------------|  
|`TypeLoadStop`|<span data-ttu-id="fc6f2-130">74</span><span class="sxs-lookup"><span data-stu-id="fc6f2-130">74</span></span>|<span data-ttu-id="fc6f2-131">類型載入已完成。</span><span class="sxs-lookup"><span data-stu-id="fc6f2-131">A type load is finished.</span></span>|

|<span data-ttu-id="fc6f2-132">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="fc6f2-132">Field name</span></span>|<span data-ttu-id="fc6f2-133">資料類型</span><span class="sxs-lookup"><span data-stu-id="fc6f2-133">Data type</span></span>|<span data-ttu-id="fc6f2-134">描述</span><span class="sxs-lookup"><span data-stu-id="fc6f2-134">Description</span></span>|  
|----------------|---------------|-----------------|  
|`TypeLoadStartID`|`win:UInt32`|<span data-ttu-id="fc6f2-135">類型載入作業的識別碼 (符合對應的 TypeLoadStart 事件的 TypeLoadStartID) 。</span><span class="sxs-lookup"><span data-stu-id="fc6f2-135">ID for the type load operation (matches the corresponding TypeLoadStart event's TypeLoadStartID).</span></span>|
|`LoadLevel`|`win:UInt16`|<span data-ttu-id="fc6f2-136">輸入負載層級。</span><span class="sxs-lookup"><span data-stu-id="fc6f2-136">Type load level.</span></span>|
|`TypeID`|`win:UInt64`|<span data-ttu-id="fc6f2-137">型別控制碼的指標。</span><span class="sxs-lookup"><span data-stu-id="fc6f2-137">Pointer to the type handle.</span></span>|
|`TypeName`|`win:UnicodeString`|<span data-ttu-id="fc6f2-138">類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="fc6f2-138">Name of the type.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="fc6f2-139">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="fc6f2-139">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
