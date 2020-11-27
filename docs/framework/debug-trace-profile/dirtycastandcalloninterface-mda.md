---
title: dirtyCastAndCallOnInterface MDA
description: 檢查 dirtyCastAndCallOnInterface managed 偵錯工具，這是在晚期繫結的類別介面上進行早期繫結的 vtable 呼叫時所叫用的協助工具。
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), early bound calls AutoDispatch
- dispatch-only mode
- dirtyCastAndCallOnInterface
- early-bound managed classes
- early bound calls on AutoDispatch
- MDAs (managed debugging assistants), early bound calls AutoDispatch
- EarlyBoundCallOnAutorDispatchClassInteface MDA
ms.assetid: aa388ed3-7e3d-48ea-a0b5-c47ae19cec38
ms.openlocfilehash: 49a2930d91e76856436480512360e8b9f9fd3d7a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273577"
---
# <a name="dirtycastandcalloninterface-mda"></a><span data-ttu-id="64af8-103">dirtyCastAndCallOnInterface MDA</span><span class="sxs-lookup"><span data-stu-id="64af8-103">dirtyCastAndCallOnInterface MDA</span></span>

<span data-ttu-id="64af8-104">在已標記為僅限晚期繫結的類別介面上，嘗試透過 vtable 進行早期繫結呼叫時，會啟動 `dirtyCastAndCallOnInterface` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="64af8-104">The `dirtyCastAndCallOnInterface` managed debugging assistant (MDA) is activated when an early-bound call through a vtable is attempted on a class interface that has been marked late-bound only.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="64af8-105">徵狀</span><span class="sxs-lookup"><span data-stu-id="64af8-105">Symptoms</span></span>  

 <span data-ttu-id="64af8-106">將經由 COM 進行的早期繫結呼叫置入 CLR 時，應用程式會擲回存取違規或發生未預期的行為。</span><span class="sxs-lookup"><span data-stu-id="64af8-106">An application throws an access violation or has unexpected behavior when placing an early-bound call via COM into the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="64af8-107">原因</span><span class="sxs-lookup"><span data-stu-id="64af8-107">Cause</span></span>  

 <span data-ttu-id="64af8-108">程式碼嘗試經由僅限晚期繫結的類別介面，透過 vtable 進行早期繫結呼叫。</span><span class="sxs-lookup"><span data-stu-id="64af8-108">Code is attempting an early-bound call through a vtable via a class interface that is late-bound only.</span></span> <span data-ttu-id="64af8-109">請注意，預設會將類別介面識別為僅限晚期繫結。</span><span class="sxs-lookup"><span data-stu-id="64af8-109">Note that by default class interfaces are identified as being late-bound only.</span></span> <span data-ttu-id="64af8-110">使用 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 屬性搭配 <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> 值 (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`)，也可能將類別介面識別為晚期繫結。</span><span class="sxs-lookup"><span data-stu-id="64af8-110">They can also be identified as late-bound with the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute with an <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> value (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="64af8-111">解決方法</span><span class="sxs-lookup"><span data-stu-id="64af8-111">Resolution</span></span>  

 <span data-ttu-id="64af8-112">建議的解決方式是定義明確介面以供 COM 使用，並讓 COM 用戶端透過這個介面 (而不是透過自動產生的類別介面) 進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="64af8-112">The recommended resolution is to define an explicit interface for use by COM and have the COM clients call through this interface instead of through the automatically generated class interface.</span></span> <span data-ttu-id="64af8-113">或者，從 COM 的呼叫也可以轉換成經由 `IDispatch` 的晚期繫結程序呼叫。</span><span class="sxs-lookup"><span data-stu-id="64af8-113">Alternatively, the call from COM can be transformed into a late-bound call via `IDispatch`.</span></span>  
  
 <span data-ttu-id="64af8-114">最後，您可以將類別識別為 <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`)，以允許從 COM 發出早期繫結呼叫；不過由於 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 中所述的版本控制限制，強烈不建議使用 <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual>。</span><span class="sxs-lookup"><span data-stu-id="64af8-114">Finally, it is possible to identify the class as <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) to allow early bound calls to be placed from COM; however, using <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> is strongly discouraged because of the versioning limitations described in <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="64af8-115">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="64af8-115">Effect on the Runtime</span></span>  

 <span data-ttu-id="64af8-116">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="64af8-116">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="64af8-117">它只會報告有關晚期繫結介面上之早期繫結呼叫的資料。</span><span class="sxs-lookup"><span data-stu-id="64af8-117">It only reports data about early-bound calls on late-bound interfaces.</span></span>  
  
## <a name="output"></a><span data-ttu-id="64af8-118">輸出</span><span class="sxs-lookup"><span data-stu-id="64af8-118">Output</span></span>  

 <span data-ttu-id="64af8-119">以早期繫結存取之方法或欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="64af8-119">The name of the method or name of the field being accessed early-bound.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="64af8-120">設定</span><span class="sxs-lookup"><span data-stu-id="64af8-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dirtyCastAndCallOnInterface />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="64af8-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64af8-121">See also</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [<span data-ttu-id="64af8-122">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="64af8-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
