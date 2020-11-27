---
title: invalidMemberDeclaration MDA
description: 請參閱 invalidMemberDeclaration managed 偵錯工具，這是在不呼叫 managed 方法的情況下，將失敗的 HRESULT 傳回給 COM 時所叫用的協助工具。
ms.date: 03/30/2017
helpviewer_keywords:
- invalid member declaration
- InvalidMemberDeclaration MDA
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: a84dd9a3-d6cf-4824-989a-ecbbf443eeb4
ms.openlocfilehash: c8d6c69fc6eb4f5f690b02809fdc492da675c3b1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272549"
---
# <a name="invalidmemberdeclaration-mda"></a><span data-ttu-id="56da5-103">invalidMemberDeclaration MDA</span><span class="sxs-lookup"><span data-stu-id="56da5-103">invalidMemberDeclaration MDA</span></span>

<span data-ttu-id="56da5-104">會啟動 `invalidMemberDeclaration` Managed 偵錯助理 (MDA) 來報告錯誤，這些錯誤發生在決定如何封送處理成員參數為由 COM 所呼叫時。</span><span class="sxs-lookup"><span data-stu-id="56da5-104">The `invalidMemberDeclaration` managed debugging assistant (MDA) is activated to report an error that occurs while determining how to marshal the parameters of a member to be called from COM.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="56da5-105">徵狀</span><span class="sxs-lookup"><span data-stu-id="56da5-105">Symptoms</span></span>  

 <span data-ttu-id="56da5-106">失敗的 HRESULT 會傳回給 COM，而不呼叫 Managed 方法。</span><span class="sxs-lookup"><span data-stu-id="56da5-106">A failure HRESULT is returned to COM without the managed method having been called.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="56da5-107">原因</span><span class="sxs-lookup"><span data-stu-id="56da5-107">Cause</span></span>  

 <span data-ttu-id="56da5-108">最可能的原因是其中一個參數上不相容的 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="56da5-108">This is most likely due to an incompatible <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute on one of the parameters.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="56da5-109">解決方法</span><span class="sxs-lookup"><span data-stu-id="56da5-109">Resolution</span></span>  

 <span data-ttu-id="56da5-110">請在此參數上指定有效的 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="56da5-110">Specify valid <xref:System.Runtime.InteropServices.MarshalAsAttribute> attributes on the parameters.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="56da5-111">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="56da5-111">Effect on the Runtime</span></span>  

 <span data-ttu-id="56da5-112">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="56da5-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="56da5-113">輸出</span><span class="sxs-lookup"><span data-stu-id="56da5-113">Output</span></span>  

 <span data-ttu-id="56da5-114">告知性訊息，包含成員名稱、類型名稱和錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="56da5-114">An informational message containing the member name, type name, and error message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="56da5-115">設定</span><span class="sxs-lookup"><span data-stu-id="56da5-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="56da5-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56da5-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="56da5-117">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="56da5-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="56da5-118">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="56da5-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
