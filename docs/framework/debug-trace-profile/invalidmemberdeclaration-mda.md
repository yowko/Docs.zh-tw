---
title: invalidMemberDeclaration MDA
ms.date: 03/30/2017
helpviewer_keywords:
- invalid member declaration
- InvalidMemberDeclaration MDA
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: a84dd9a3-d6cf-4824-989a-ecbbf443eeb4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c276df65497a0d8cafea80959b8193790c19ebba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667345"
---
# <a name="invalidmemberdeclaration-mda"></a><span data-ttu-id="44ded-102">invalidMemberDeclaration MDA</span><span class="sxs-lookup"><span data-stu-id="44ded-102">invalidMemberDeclaration MDA</span></span>
<span data-ttu-id="44ded-103">會啟動 `invalidMemberDeclaration` Managed 偵錯助理 (MDA) 來報告錯誤，這些錯誤發生在決定如何封送處理成員參數為由 COM 所呼叫時。</span><span class="sxs-lookup"><span data-stu-id="44ded-103">The `invalidMemberDeclaration` managed debugging assistant (MDA) is activated to report an error that occurs while determining how to marshal the parameters of a member to be called from COM.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="44ded-104">徵兆 </span><span class="sxs-lookup"><span data-stu-id="44ded-104">Symptoms</span></span>  
 <span data-ttu-id="44ded-105">失敗的 HRESULT 會傳回給 COM，而不呼叫 Managed 方法。</span><span class="sxs-lookup"><span data-stu-id="44ded-105">A failure HRESULT is returned to COM without the managed method having been called.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="44ded-106">原因</span><span class="sxs-lookup"><span data-stu-id="44ded-106">Cause</span></span>  
 <span data-ttu-id="44ded-107">最可能的原因是其中一個參數上不相容的 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="44ded-107">This is most likely due to an incompatible <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute on one of the parameters.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="44ded-108">解決方式</span><span class="sxs-lookup"><span data-stu-id="44ded-108">Resolution</span></span>  
 <span data-ttu-id="44ded-109">請在此參數上指定有效的 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="44ded-109">Specify valid <xref:System.Runtime.InteropServices.MarshalAsAttribute> attributes on the parameters.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="44ded-110">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="44ded-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="44ded-111">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="44ded-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="44ded-112">輸出</span><span class="sxs-lookup"><span data-stu-id="44ded-112">Output</span></span>  
 <span data-ttu-id="44ded-113">告知性訊息，包含成員名稱、類型名稱和錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="44ded-113">An informational message containing the member name, type name, and error message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="44ded-114">組態</span><span class="sxs-lookup"><span data-stu-id="44ded-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="44ded-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44ded-115">See also</span></span>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="44ded-116">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="44ded-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="44ded-117">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="44ded-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
