---
title: dllMainReturnsFalse MDA
description: 閱讀有關 .NET 中 dllMainReturnsFalse managed 偵錯工具的資訊。 如果 DLL 初始化失敗，就會啟用此 MDA。
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
ms.openlocfilehash: 21d5e37d6823876e07cf5b2cbb881c1cf8b47b11
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416053"
---
# <a name="dllmainreturnsfalse-mda"></a><span data-ttu-id="a694e-104">dllMainReturnsFalse MDA</span><span class="sxs-lookup"><span data-stu-id="a694e-104">dllMainReturnsFalse MDA</span></span>
<span data-ttu-id="a694e-105">如果以理由 DLL_PROCESS_ATTACH 呼叫的使用者組件 Managed `DllMain` 函式，傳回 FALSE，就會啟動 `dllMainReturnsFalse` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="a694e-105">The `dllMainReturnsFalse` managed debugging assistant (MDA) is activated if the managed `DllMain` function of a user assembly, called with reason DLL_PROCESS_ATTACH, returns FALSE.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a694e-106">徵狀</span><span class="sxs-lookup"><span data-stu-id="a694e-106">Symptoms</span></span>  
 <span data-ttu-id="a694e-107">`DllMain` 函式傳回 FALSE，指出未正確執行。</span><span class="sxs-lookup"><span data-stu-id="a694e-107">The `DllMain` function returned FALSE, indicating that it did not execute properly.</span></span> <span data-ttu-id="a694e-108">因為 `DllMain` 函式通常會包含重要的初始化程式碼，所以這會造成未定的問題。</span><span class="sxs-lookup"><span data-stu-id="a694e-108">This can cause undetermined issues because `DllMain` functions typically contain important initialization code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a694e-109">原因</span><span class="sxs-lookup"><span data-stu-id="a694e-109">Cause</span></span>  
 <span data-ttu-id="a694e-110">因為在載入時 DLL 初始化發生 DLL_PROCESS_ATTACH，所以呼叫 `DllMain` 函式。</span><span class="sxs-lookup"><span data-stu-id="a694e-110">The `DllMain` function is called with reason DLL_PROCESS_ATTACH for DLL initialization upon load.</span></span> <span data-ttu-id="a694e-111">如果它傳回 FALSE，表示該 DLL 初始化失敗。</span><span class="sxs-lookup"><span data-stu-id="a694e-111">If it returns FALSE, it means that DLL initialization failed.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a694e-112">解決方案</span><span class="sxs-lookup"><span data-stu-id="a694e-112">Resolution</span></span>  
 <span data-ttu-id="a694e-113">分析失敗 DLL 的 `DllMain` 函式程式碼，找出初始化失敗的原因。</span><span class="sxs-lookup"><span data-stu-id="a694e-113">Analyze the code of the `DllMain` function of the failed DLL and identify the cause of the initialization failure.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a694e-114">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="a694e-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="a694e-115">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="a694e-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="a694e-116">它只報告 `DllMain` 傳回值的相關資料。</span><span class="sxs-lookup"><span data-stu-id="a694e-116">It only reports data about the return value for `DllMain`.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a694e-117">輸出</span><span class="sxs-lookup"><span data-stu-id="a694e-117">Output</span></span>  
 <span data-ttu-id="a694e-118">訊息，指出因為 DLL_PROCESS_ATTACH 而呼叫的 `DllMain` 函式傳回 FALSE。</span><span class="sxs-lookup"><span data-stu-id="a694e-118">A message indicating that a `DllMain` function, called for reason DLL_PROCESS_ATTACH, returned FALSE.</span></span> <span data-ttu-id="a694e-119">請注意，只有在 Managed 程式碼中實作 `DllMain` 時，才會啟用這個 MDA。</span><span class="sxs-lookup"><span data-stu-id="a694e-119">Note that this MDA is activated only if `DllMain` is implemented in managed code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a694e-120">設定</span><span class="sxs-lookup"><span data-stu-id="a694e-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a694e-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a694e-121">See also</span></span>

- [<span data-ttu-id="a694e-122">使用 Managed 偵錯助理診斷錯誤</span><span class="sxs-lookup"><span data-stu-id="a694e-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
