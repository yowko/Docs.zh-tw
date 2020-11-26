---
title: fatalExecutionEngineError MDA
description: 請參閱 .NET 中的 fatalExecutionEngineError managed 偵錯工具 (MDA) ，因為未預期的進程終止，可能會啟用此功能。
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
ms.openlocfilehash: a9347338d53755b74b3ff291f75cb6b221134130
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244271"
---
# <a name="fatalexecutionengineerror-mda"></a><span data-ttu-id="82b61-103">fatalExecutionEngineError MDA</span><span class="sxs-lookup"><span data-stu-id="82b61-103">fatalExecutionEngineError MDA</span></span>

<span data-ttu-id="82b61-104">在 Common Language Runtime (CLR) 中偵測到嚴重錯誤時，就會啟動 `fatalExecutionEngineError` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="82b61-104">The `fatalExecutionEngineError` managed debugging assistant (MDA) is activated when a fatal error in the common language runtime (CLR) has been detected.</span></span> <span data-ttu-id="82b61-105">處理程序會終止。</span><span class="sxs-lookup"><span data-stu-id="82b61-105">The process will be terminated.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="82b61-106">徵狀</span><span class="sxs-lookup"><span data-stu-id="82b61-106">Symptoms</span></span>  

 <span data-ttu-id="82b61-107">未預期的處理序終止。</span><span class="sxs-lookup"><span data-stu-id="82b61-107">Unexpected process termination.</span></span> <span data-ttu-id="82b61-108">因為 CLR 失敗的發生原因各種各樣，所以無法判斷其他症狀。</span><span class="sxs-lookup"><span data-stu-id="82b61-108">Other symptoms cannot be determined because a CLR failure can occur for a variety of reasons.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="82b61-109">原因</span><span class="sxs-lookup"><span data-stu-id="82b61-109">Cause</span></span>  

 <span data-ttu-id="82b61-110">CLR 已受創損毀。</span><span class="sxs-lookup"><span data-stu-id="82b61-110">The CLR has been fatally corrupted.</span></span> <span data-ttu-id="82b61-111">這通常是因為資料損毀所致，造成此狀況的問題很多，例如呼叫格式不正確的平台叫用函式，以及將無效的資料傳遞至 CLR。</span><span class="sxs-lookup"><span data-stu-id="82b61-111">This is most often caused by data corruption, which can be caused by a number of problems, such as calls to malformed platform invoke functions and passing invalid data to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="82b61-112">解決方法</span><span class="sxs-lookup"><span data-stu-id="82b61-112">Resolution</span></span>  

 <span data-ttu-id="82b61-113">啟用額外的 MDA 可能有助於找出問題。</span><span class="sxs-lookup"><span data-stu-id="82b61-113">Enabling additional MDAs might help identify the problem.</span></span> <span data-ttu-id="82b61-114">下列 MDA 在診斷此問題方面特別有幫助：</span><span class="sxs-lookup"><span data-stu-id="82b61-114">The following MDAs can be particularly helpful in diagnosing the issue:</span></span>  
  
- [<span data-ttu-id="82b61-115">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="82b61-115">invalidOverlappedToPinvoke</span></span>](invalidoverlappedtopinvoke-mda.md)  
  
- [<span data-ttu-id="82b61-116">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="82b61-116">overlappedFreeError</span></span>](overlappedfreeerror-mda.md)  
  
- [<span data-ttu-id="82b61-117">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="82b61-117">pInvokeStackImbalance</span></span>](pinvokestackimbalance-mda.md)  
  
- [<span data-ttu-id="82b61-118">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="82b61-118">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)  
  
- [<span data-ttu-id="82b61-119">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="82b61-119">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)  
  
- [<span data-ttu-id="82b61-120">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="82b61-120">callbackOnCollectedDelegate</span></span>](callbackoncollecteddelegate-mda.md)  
  
- [<span data-ttu-id="82b61-121">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="82b61-121">reportAvOnComRelease</span></span>](reportavoncomrelease-mda.md)  
  
- [<span data-ttu-id="82b61-122">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="82b61-122">invalidVariant</span></span>](invalidvariant-mda.md)  
  
- [<span data-ttu-id="82b61-123">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="82b61-123">invalidIUnknown</span></span>](invalidiunknown-mda.md)  
  
- [<span data-ttu-id="82b61-124">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="82b61-124">raceOnRCWCleanup</span></span>](raceonrcwcleanup-mda.md)  
  
- [<span data-ttu-id="82b61-125">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="82b61-125">invalidFunctionPointerInDelegate</span></span>](invalidfunctionpointerindelegate-mda.md)  
  
- [<span data-ttu-id="82b61-126">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="82b61-126">invalidGCHandleCookie</span></span>](invalidgchandlecookie-mda.md)  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="82b61-127">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="82b61-127">Effect on the Runtime</span></span>  

 <span data-ttu-id="82b61-128">此 MDA 對執行階段行為沒有影響。</span><span class="sxs-lookup"><span data-stu-id="82b61-128">This MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="82b61-129">輸出</span><span class="sxs-lookup"><span data-stu-id="82b61-129">Output</span></span>  

 <span data-ttu-id="82b61-130">造成嚴重錯誤的 CLR 函式位址、發生錯誤的執行緒識別碼，以及錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="82b61-130">The address of the CLR function that caused the fatal error, the ID of the thread where the error occurred, and the error code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="82b61-131">設定</span><span class="sxs-lookup"><span data-stu-id="82b61-131">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <fatalExecutionEngineError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="82b61-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82b61-132">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution.Cer>
- [<span data-ttu-id="82b61-133">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="82b61-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
