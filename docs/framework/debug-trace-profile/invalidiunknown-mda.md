---
title: invalidIUnknown MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
author: mairaw
ms.author: mairaw
ms.openlocfilehash: db360a3b7c5f70596d5d5855b8e38dae5d484c42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390171"
---
# <a name="invalidiunknown-mda"></a><span data-ttu-id="7b9e0-102">invalidIUnknown MDA</span><span class="sxs-lookup"><span data-stu-id="7b9e0-102">invalidIUnknown MDA</span></span>
<span data-ttu-id="7b9e0-103">當無效的 `IUnknown` 指標從原生程式碼傳遞至 Managed 程式碼時，會啟動 `invalidIUnknown` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="7b9e0-103">The `invalidIUnknown` managed debugging assistant (MDA) is activated when an invalid `IUnknown` pointer is passed to managed code from native code.</span></span> <span data-ttu-id="7b9e0-104">查詢 `IUnknown` 介面時，`IUnknown` 無法成功傳回。</span><span class="sxs-lookup"><span data-stu-id="7b9e0-104">The `IUnknown` fails to return success when queried for the `IUnknown` interface.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="7b9e0-105">徵兆 </span><span class="sxs-lookup"><span data-stu-id="7b9e0-105">Symptoms</span></span>  
 <span data-ttu-id="7b9e0-106">引數封送處理期間，在封送處理 COM 介面指標時，發生未預期的錯誤。</span><span class="sxs-lookup"><span data-stu-id="7b9e0-106">An unexpected error occurs when marshaling a COM interface pointer during argument marshaling.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="7b9e0-107">原因</span><span class="sxs-lookup"><span data-stu-id="7b9e0-107">Cause</span></span>  
 <span data-ttu-id="7b9e0-108">對於傳遞至 CLR 的 COM 介面進行了不正確的 `QueryInterface` 實作。</span><span class="sxs-lookup"><span data-stu-id="7b9e0-108">An incorrect `QueryInterface` implementation on the COM interface passed to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="7b9e0-109">解決方式</span><span class="sxs-lookup"><span data-stu-id="7b9e0-109">Resolution</span></span>  
 <span data-ttu-id="7b9e0-110">更正 `QueryInterface` 實作。</span><span class="sxs-lookup"><span data-stu-id="7b9e0-110">Correct the `QueryInterface` implementation.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="7b9e0-111">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="7b9e0-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="7b9e0-112">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="7b9e0-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="7b9e0-113">輸出</span><span class="sxs-lookup"><span data-stu-id="7b9e0-113">Output</span></span>  
 <span data-ttu-id="7b9e0-114">錯誤的描述。</span><span class="sxs-lookup"><span data-stu-id="7b9e0-114">The description of the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="7b9e0-115">組態</span><span class="sxs-lookup"><span data-stu-id="7b9e0-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7b9e0-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b9e0-116">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="7b9e0-117">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="7b9e0-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="7b9e0-118">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="7b9e0-118">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
