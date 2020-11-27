---
title: invalidIUnknown MDA
description: 請參閱 invalidIUnknown managed 偵錯工具 (MDA) ，這會在不正確 IUnknown 指標從機器碼傳遞給 managed 程式碼時啟動。
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
ms.openlocfilehash: 8e7ca6c9c43c4f507d235c879498b2e831c6eba9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272536"
---
# <a name="invalidiunknown-mda"></a><span data-ttu-id="0329d-103">invalidIUnknown MDA</span><span class="sxs-lookup"><span data-stu-id="0329d-103">invalidIUnknown MDA</span></span>

<span data-ttu-id="0329d-104">當無效的 `IUnknown` 指標從原生程式碼傳遞至 Managed 程式碼時，會啟動 `invalidIUnknown` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="0329d-104">The `invalidIUnknown` managed debugging assistant (MDA) is activated when an invalid `IUnknown` pointer is passed to managed code from native code.</span></span> <span data-ttu-id="0329d-105">查詢 `IUnknown` 介面時，`IUnknown` 無法成功傳回。</span><span class="sxs-lookup"><span data-stu-id="0329d-105">The `IUnknown` fails to return success when queried for the `IUnknown` interface.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="0329d-106">徵狀</span><span class="sxs-lookup"><span data-stu-id="0329d-106">Symptoms</span></span>  

 <span data-ttu-id="0329d-107">引數封送處理期間，在封送處理 COM 介面指標時，發生未預期的錯誤。</span><span class="sxs-lookup"><span data-stu-id="0329d-107">An unexpected error occurs when marshaling a COM interface pointer during argument marshaling.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="0329d-108">原因</span><span class="sxs-lookup"><span data-stu-id="0329d-108">Cause</span></span>  

 <span data-ttu-id="0329d-109">對於傳遞至 CLR 的 COM 介面進行了不正確的 `QueryInterface` 實作。</span><span class="sxs-lookup"><span data-stu-id="0329d-109">An incorrect `QueryInterface` implementation on the COM interface passed to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="0329d-110">解決方法</span><span class="sxs-lookup"><span data-stu-id="0329d-110">Resolution</span></span>  

 <span data-ttu-id="0329d-111">更正 `QueryInterface` 實作。</span><span class="sxs-lookup"><span data-stu-id="0329d-111">Correct the `QueryInterface` implementation.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="0329d-112">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="0329d-112">Effect on the Runtime</span></span>  

 <span data-ttu-id="0329d-113">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="0329d-113">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="0329d-114">輸出</span><span class="sxs-lookup"><span data-stu-id="0329d-114">Output</span></span>  

 <span data-ttu-id="0329d-115">錯誤的描述。</span><span class="sxs-lookup"><span data-stu-id="0329d-115">The description of the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="0329d-116">設定</span><span class="sxs-lookup"><span data-stu-id="0329d-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0329d-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0329d-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="0329d-118">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="0329d-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="0329d-119">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="0329d-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
