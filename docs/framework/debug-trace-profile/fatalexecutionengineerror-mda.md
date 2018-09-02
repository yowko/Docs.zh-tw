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
ms.openlocfilehash: f12b94198b88111d559cfe372c28bdbf4b37e3fe
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43419783"
---
# <a name="fatalexecutionengineerror-mda"></a><span data-ttu-id="4aedb-102">fatalExecutionEngineError MDA</span><span class="sxs-lookup"><span data-stu-id="4aedb-102">fatalExecutionEngineError MDA</span></span>
<span data-ttu-id="4aedb-103">在 Common Language Runtime (CLR) 中偵測到嚴重錯誤時，就會啟動 `fatalExecutionEngineError` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="4aedb-103">The `fatalExecutionEngineError` managed debugging assistant (MDA) is activated when a fatal error in the common language runtime (CLR) has been detected.</span></span> <span data-ttu-id="4aedb-104">處理程序會終止。</span><span class="sxs-lookup"><span data-stu-id="4aedb-104">The process will be terminated.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="4aedb-105">徵兆</span><span class="sxs-lookup"><span data-stu-id="4aedb-105">Symptoms</span></span>  
 <span data-ttu-id="4aedb-106">未預期的處理序終止。</span><span class="sxs-lookup"><span data-stu-id="4aedb-106">Unexpected process termination.</span></span> <span data-ttu-id="4aedb-107">因為 CLR 失敗的發生原因各種各樣，所以無法判斷其他症狀。</span><span class="sxs-lookup"><span data-stu-id="4aedb-107">Other symptoms cannot be determined because a CLR failure can occur for a variety of reasons.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="4aedb-108">原因</span><span class="sxs-lookup"><span data-stu-id="4aedb-108">Cause</span></span>  
 <span data-ttu-id="4aedb-109">CLR 已受創損毀。</span><span class="sxs-lookup"><span data-stu-id="4aedb-109">The CLR has been fatally corrupted.</span></span> <span data-ttu-id="4aedb-110">這通常是因為資料損毀所致，造成此狀況的問題很多，例如呼叫格式不正確的平台叫用函式，以及將無效的資料傳遞至 CLR。</span><span class="sxs-lookup"><span data-stu-id="4aedb-110">This is most often caused by data corruption, which can be caused by a number of problems, such as calls to malformed platform invoke functions and passing invalid data to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="4aedb-111">解決方式</span><span class="sxs-lookup"><span data-stu-id="4aedb-111">Resolution</span></span>  
 <span data-ttu-id="4aedb-112">啟用額外的 MDA 可能有助於找出問題。</span><span class="sxs-lookup"><span data-stu-id="4aedb-112">Enabling additional MDAs might help identify the problem.</span></span> <span data-ttu-id="4aedb-113">下列 MDA 在診斷此問題方面特別有幫助：</span><span class="sxs-lookup"><span data-stu-id="4aedb-113">The following MDAs can be particularly helpful in diagnosing the issue:</span></span>  
  
-   [<span data-ttu-id="4aedb-114">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="4aedb-114">invalidOverlappedToPinvoke</span></span>](../../../docs/framework/debug-trace-profile/invalidoverlappedtopinvoke-mda.md)  
  
-   [<span data-ttu-id="4aedb-115">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="4aedb-115">overlappedFreeError</span></span>](../../../docs/framework/debug-trace-profile/overlappedfreeerror-mda.md)  
  
-   [<span data-ttu-id="4aedb-116">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="4aedb-116">pInvokeStackImbalance</span></span>](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)  
  
-   [<span data-ttu-id="4aedb-117">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="4aedb-117">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)  
  
-   [<span data-ttu-id="4aedb-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="4aedb-118">gcManagedToUnmanaged</span></span>](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)  
  
-   [<span data-ttu-id="4aedb-119">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="4aedb-119">callbackOnCollectedDelegate</span></span>](../../../docs/framework/debug-trace-profile/callbackoncollecteddelegate-mda.md)  
  
-   [<span data-ttu-id="4aedb-120">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="4aedb-120">reportAvOnComRelease</span></span>](../../../docs/framework/debug-trace-profile/reportavoncomrelease-mda.md)  
  
-   [<span data-ttu-id="4aedb-121">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="4aedb-121">invalidVariant</span></span>](../../../docs/framework/debug-trace-profile/invalidvariant-mda.md)  
  
-   [<span data-ttu-id="4aedb-122">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="4aedb-122">invalidIUnknown</span></span>](../../../docs/framework/debug-trace-profile/invalidiunknown-mda.md)  
  
-   [<span data-ttu-id="4aedb-123">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="4aedb-123">raceOnRCWCleanup</span></span>](../../../docs/framework/debug-trace-profile/raceonrcwcleanup-mda.md)  
  
-   [<span data-ttu-id="4aedb-124">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="4aedb-124">invalidFunctionPointerInDelegate</span></span>](../../../docs/framework/debug-trace-profile/invalidfunctionpointerindelegate-mda.md)  
  
-   [<span data-ttu-id="4aedb-125">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="4aedb-125">invalidGCHandleCookie</span></span>](../../../docs/framework/debug-trace-profile/invalidgchandlecookie-mda.md)  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="4aedb-126">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="4aedb-126">Effect on the Runtime</span></span>  
 <span data-ttu-id="4aedb-127">此 MDA 對執行階段行為沒有影響。</span><span class="sxs-lookup"><span data-stu-id="4aedb-127">This MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="4aedb-128">輸出</span><span class="sxs-lookup"><span data-stu-id="4aedb-128">Output</span></span>  
 <span data-ttu-id="4aedb-129">造成嚴重錯誤的 CLR 函式位址、發生錯誤的執行緒識別碼，以及錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="4aedb-129">The address of the CLR function that caused the fatal error, the ID of the thread where the error occurred, and the error code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="4aedb-130">組態</span><span class="sxs-lookup"><span data-stu-id="4aedb-130">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <fatalExecutionEngineError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4aedb-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4aedb-131">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>  
 <xref:System.Runtime.ConstrainedExecution.Cer>  
 [<span data-ttu-id="4aedb-132">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="4aedb-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
