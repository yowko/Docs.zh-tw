---
title: dirtyCastAndCallOnInterface MDA
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5a28820479ca15ad72475ae9a7754bbbf99ce5c5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108585"
---
# <a name="dirtycastandcalloninterface-mda"></a><span data-ttu-id="218d9-102">dirtyCastAndCallOnInterface MDA</span><span class="sxs-lookup"><span data-stu-id="218d9-102">dirtyCastAndCallOnInterface MDA</span></span>
<span data-ttu-id="218d9-103">在已標記為僅限晚期繫結的類別介面上，嘗試透過 vtable 進行早期繫結呼叫時，會啟動 `dirtyCastAndCallOnInterface` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="218d9-103">The `dirtyCastAndCallOnInterface` managed debugging assistant (MDA) is activated when an early-bound call through a vtable is attempted on a class interface that has been marked late-bound only.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="218d9-104">徵兆</span><span class="sxs-lookup"><span data-stu-id="218d9-104">Symptoms</span></span>  
 <span data-ttu-id="218d9-105">將經由 COM 進行的早期繫結呼叫置入 CLR 時，應用程式會擲回存取違規或發生未預期的行為。</span><span class="sxs-lookup"><span data-stu-id="218d9-105">An application throws an access violation or has unexpected behavior when placing an early-bound call via COM into the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="218d9-106">原因</span><span class="sxs-lookup"><span data-stu-id="218d9-106">Cause</span></span>  
 <span data-ttu-id="218d9-107">程式碼嘗試經由僅限晚期繫結的類別介面，透過 vtable 進行早期繫結呼叫。</span><span class="sxs-lookup"><span data-stu-id="218d9-107">Code is attempting an early-bound call through a vtable via a class interface that is late-bound only.</span></span> <span data-ttu-id="218d9-108">請注意，預設會將類別介面識別為僅限晚期繫結。</span><span class="sxs-lookup"><span data-stu-id="218d9-108">Note that by default class interfaces are identified as being late-bound only.</span></span> <span data-ttu-id="218d9-109">使用 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 屬性搭配 <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> 值 (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`)，也可能將類別介面識別為晚期繫結。</span><span class="sxs-lookup"><span data-stu-id="218d9-109">They can also be identified as late-bound with the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute with an <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> value (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="218d9-110">解決方式</span><span class="sxs-lookup"><span data-stu-id="218d9-110">Resolution</span></span>  
 <span data-ttu-id="218d9-111">建議的解決方式是定義明確介面以供 COM 使用，並讓 COM 用戶端透過這個介面 (而不是透過自動產生的類別介面) 進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="218d9-111">The recommended resolution is to define an explicit interface for use by COM and have the COM clients call through this interface instead of through the automatically generated class interface.</span></span> <span data-ttu-id="218d9-112">或者，從 COM 的呼叫也可以轉換成經由 `IDispatch` 的晚期繫結程序呼叫。</span><span class="sxs-lookup"><span data-stu-id="218d9-112">Alternatively, the call from COM can be transformed into a late-bound call via `IDispatch`.</span></span>  
  
 <span data-ttu-id="218d9-113">最後，您可以將類別識別為 <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`)，以允許從 COM 發出早期繫結呼叫；不過由於 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 中所述的版本控制限制，強烈不建議使用 <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual>。</span><span class="sxs-lookup"><span data-stu-id="218d9-113">Finally, it is possible to identify the class as <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) to allow early bound calls to be placed from COM; however, using <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> is strongly discouraged because of the versioning limitations described in <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="218d9-114">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="218d9-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="218d9-115">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="218d9-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="218d9-116">它只會報告有關晚期繫結介面上之早期繫結呼叫的資料。</span><span class="sxs-lookup"><span data-stu-id="218d9-116">It only reports data about early-bound calls on late-bound interfaces.</span></span>  
  
## <a name="output"></a><span data-ttu-id="218d9-117">Output</span><span class="sxs-lookup"><span data-stu-id="218d9-117">Output</span></span>  
 <span data-ttu-id="218d9-118">以早期繫結存取之方法或欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="218d9-118">The name of the method or name of the field being accessed early-bound.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="218d9-119">組態</span><span class="sxs-lookup"><span data-stu-id="218d9-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dirtyCastAndCallOnInterface />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="218d9-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="218d9-120">See also</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [<span data-ttu-id="218d9-121">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="218d9-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
