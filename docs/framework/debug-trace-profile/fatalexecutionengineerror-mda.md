---
title: fatalExecutionEngineError MDA
ms.date: 03/30/2017
helpviewer_keywords:
- corrupted CLR
- fatal execution error
- terminated processes
- unexpected terminations
- fatal errors
- MDAs (managed debugging assistants), fatal errors
- process termination
- FatalExecutionEngineError MDA
- managed debugging assistants (MDAs), fatal errors
ms.assetid: 8b559e44-2393-4e4e-8160-7558d37a4a89
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3fd58ae8f73fd932df641ea96a44ff618dd139e2
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052798"
---
# <a name="fatalexecutionengineerror-mda"></a><span data-ttu-id="90eee-102">fatalExecutionEngineError MDA</span><span class="sxs-lookup"><span data-stu-id="90eee-102">fatalExecutionEngineError MDA</span></span>
<span data-ttu-id="90eee-103">在 Common Language Runtime (CLR) 中偵測到嚴重錯誤時，就會啟動 `fatalExecutionEngineError` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="90eee-103">The `fatalExecutionEngineError` managed debugging assistant (MDA) is activated when a fatal error in the common language runtime (CLR) has been detected.</span></span> <span data-ttu-id="90eee-104">處理程序會終止。</span><span class="sxs-lookup"><span data-stu-id="90eee-104">The process will be terminated.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="90eee-105">徵兆</span><span class="sxs-lookup"><span data-stu-id="90eee-105">Symptoms</span></span>  
 <span data-ttu-id="90eee-106">未預期的處理序終止。</span><span class="sxs-lookup"><span data-stu-id="90eee-106">Unexpected process termination.</span></span> <span data-ttu-id="90eee-107">因為 CLR 失敗的發生原因各種各樣，所以無法判斷其他症狀。</span><span class="sxs-lookup"><span data-stu-id="90eee-107">Other symptoms cannot be determined because a CLR failure can occur for a variety of reasons.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="90eee-108">原因</span><span class="sxs-lookup"><span data-stu-id="90eee-108">Cause</span></span>  
 <span data-ttu-id="90eee-109">CLR 已受創損毀。</span><span class="sxs-lookup"><span data-stu-id="90eee-109">The CLR has been fatally corrupted.</span></span> <span data-ttu-id="90eee-110">這通常是因為資料損毀所致，造成此狀況的問題很多，例如呼叫格式不正確的平台叫用函式，以及將無效的資料傳遞至 CLR。</span><span class="sxs-lookup"><span data-stu-id="90eee-110">This is most often caused by data corruption, which can be caused by a number of problems, such as calls to malformed platform invoke functions and passing invalid data to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="90eee-111">解決方式</span><span class="sxs-lookup"><span data-stu-id="90eee-111">Resolution</span></span>  
 <span data-ttu-id="90eee-112">啟用額外的 MDA 可能有助於找出問題。</span><span class="sxs-lookup"><span data-stu-id="90eee-112">Enabling additional MDAs might help identify the problem.</span></span> <span data-ttu-id="90eee-113">下列 MDA 在診斷此問題方面特別有幫助：</span><span class="sxs-lookup"><span data-stu-id="90eee-113">The following MDAs can be particularly helpful in diagnosing the issue:</span></span>  
  
- [<span data-ttu-id="90eee-114">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="90eee-114">invalidOverlappedToPinvoke</span></span>](invalidoverlappedtopinvoke-mda.md)  
  
- [<span data-ttu-id="90eee-115">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="90eee-115">overlappedFreeError</span></span>](overlappedfreeerror-mda.md)  
  
- [<span data-ttu-id="90eee-116">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="90eee-116">pInvokeStackImbalance</span></span>](pinvokestackimbalance-mda.md)  
  
- [<span data-ttu-id="90eee-117">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="90eee-117">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)  
  
- [<span data-ttu-id="90eee-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="90eee-118">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)  
  
- [<span data-ttu-id="90eee-119">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="90eee-119">callbackOnCollectedDelegate</span></span>](callbackoncollecteddelegate-mda.md)  
  
- [<span data-ttu-id="90eee-120">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="90eee-120">reportAvOnComRelease</span></span>](reportavoncomrelease-mda.md)  
  
- [<span data-ttu-id="90eee-121">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="90eee-121">invalidVariant</span></span>](invalidvariant-mda.md)  
  
- [<span data-ttu-id="90eee-122">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="90eee-122">invalidIUnknown</span></span>](invalidiunknown-mda.md)  
  
- [<span data-ttu-id="90eee-123">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="90eee-123">raceOnRCWCleanup</span></span>](raceonrcwcleanup-mda.md)  
  
- [<span data-ttu-id="90eee-124">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="90eee-124">invalidFunctionPointerInDelegate</span></span>](invalidfunctionpointerindelegate-mda.md)  
  
- [<span data-ttu-id="90eee-125">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="90eee-125">invalidGCHandleCookie</span></span>](invalidgchandlecookie-mda.md)  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="90eee-126">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="90eee-126">Effect on the Runtime</span></span>  
 <span data-ttu-id="90eee-127">此 MDA 對執行階段行為沒有影響。</span><span class="sxs-lookup"><span data-stu-id="90eee-127">This MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="90eee-128">Output</span><span class="sxs-lookup"><span data-stu-id="90eee-128">Output</span></span>  
 <span data-ttu-id="90eee-129">造成嚴重錯誤的 CLR 函式位址、發生錯誤的執行緒識別碼，以及錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="90eee-129">The address of the CLR function that caused the fatal error, the ID of the thread where the error occurred, and the error code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="90eee-130">組態</span><span class="sxs-lookup"><span data-stu-id="90eee-130">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <fatalExecutionEngineError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="90eee-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90eee-131">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution.Cer>
- [<span data-ttu-id="90eee-132">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="90eee-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
