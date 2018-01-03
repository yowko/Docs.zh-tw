---
title: invalidIUnknown MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ff88f8bc544c95a4fe5149cd517d9157d5ac23c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="invalidiunknown-mda"></a><span data-ttu-id="f2514-102">invalidIUnknown MDA</span><span class="sxs-lookup"><span data-stu-id="f2514-102">invalidIUnknown MDA</span></span>
<span data-ttu-id="f2514-103">當無效的 `IUnknown` 指標從原生程式碼傳遞至 Managed 程式碼時，會啟動 `invalidIUnknown` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="f2514-103">The `invalidIUnknown` managed debugging assistant (MDA) is activated when an invalid `IUnknown` pointer is passed to managed code from native code.</span></span> <span data-ttu-id="f2514-104">查詢 `IUnknown` 介面時，`IUnknown` 無法成功傳回。</span><span class="sxs-lookup"><span data-stu-id="f2514-104">The `IUnknown` fails to return success when queried for the `IUnknown` interface.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="f2514-105">徵兆 </span><span class="sxs-lookup"><span data-stu-id="f2514-105">Symptoms</span></span>  
 <span data-ttu-id="f2514-106">引數封送處理期間，在封送處理 COM 介面指標時，發生未預期的錯誤。</span><span class="sxs-lookup"><span data-stu-id="f2514-106">An unexpected error occurs when marshaling a COM interface pointer during argument marshaling.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="f2514-107">原因</span><span class="sxs-lookup"><span data-stu-id="f2514-107">Cause</span></span>  
 <span data-ttu-id="f2514-108">對於傳遞至 CLR 的 COM 介面進行了不正確的 `QueryInterface` 實作。</span><span class="sxs-lookup"><span data-stu-id="f2514-108">An incorrect `QueryInterface` implementation on the COM interface passed to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="f2514-109">解決方式</span><span class="sxs-lookup"><span data-stu-id="f2514-109">Resolution</span></span>  
 <span data-ttu-id="f2514-110">更正 `QueryInterface` 實作。</span><span class="sxs-lookup"><span data-stu-id="f2514-110">Correct the `QueryInterface` implementation.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f2514-111">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="f2514-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="f2514-112">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="f2514-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f2514-113">輸出</span><span class="sxs-lookup"><span data-stu-id="f2514-113">Output</span></span>  
 <span data-ttu-id="f2514-114">錯誤的描述。</span><span class="sxs-lookup"><span data-stu-id="f2514-114">The description of the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="f2514-115">組態</span><span class="sxs-lookup"><span data-stu-id="f2514-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f2514-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="f2514-116">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="f2514-117">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="f2514-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="f2514-118">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="f2514-118">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
