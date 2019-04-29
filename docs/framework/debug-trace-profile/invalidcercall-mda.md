---
title: invalidCERCall MDA
ms.date: 03/30/2017
helpviewer_keywords:
- invalid CER calls
- InvalidCERCall MDA
- MDAs (managed debugging assistants), CER calls
- constrained execution regions
- CER calls
- managed debugging assistants (MDAs), CER calls
ms.assetid: c4577410-602e-44e5-9dab-fea7c55bcdfe
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1a68aac2a92a0569e288da858e4a4e4695fd5eaa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754423"
---
# <a name="invalidcercall-mda"></a><span data-ttu-id="eb715-102">invalidCERCall MDA</span><span class="sxs-lookup"><span data-stu-id="eb715-102">invalidCERCall MDA</span></span>
<span data-ttu-id="eb715-103">當方法的限制執行區域 (CER) 圖形內的呼叫沒有可靠性合約或過度弱式合約時，就會啟動 `invalidCERCall` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="eb715-103">The `invalidCERCall` managed debugging assistant (MDA) is activated when there is a call within the constrained execution region (CER) graph to a method that has no reliability contract or an excessively weak contract.</span></span> <span data-ttu-id="eb715-104">弱式合約是宣告最差狀態損毀範圍超過執行個體傳遞至呼叫的範圍，也就是 <xref:System.AppDomain> 或處理序狀態可能會損毀，或在 CER 內呼叫時，其結果不一定是決定性可計算結果。</span><span class="sxs-lookup"><span data-stu-id="eb715-104">A weak contract is a contract that declares that the worst case state corruption is of greater scope than the instance passed to the call, that is, the <xref:System.AppDomain> or process state may become corrupted or that its result is not always deterministically computable when called within a CER.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="eb715-105">徵兆</span><span class="sxs-lookup"><span data-stu-id="eb715-105">Symptoms</span></span>  
 <span data-ttu-id="eb715-106">在 CER 中執行程式碼時出現非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="eb715-106">Unexpected results when executing code in a CER.</span></span> <span data-ttu-id="eb715-107">沒有特定的徵兆。</span><span class="sxs-lookup"><span data-stu-id="eb715-107">The symptoms are not specific.</span></span> <span data-ttu-id="eb715-108">它們可能是未預期的 <xref:System.OutOfMemoryException>、<xref:System.Threading.ThreadAbortException> 或在呼叫不可靠的方法時發生的其他例外狀況，因為執行階段未事先準備或保護它免於執行階段的 <xref:System.Threading.ThreadAbortException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="eb715-108">They could be an unexpected <xref:System.OutOfMemoryException>, a <xref:System.Threading.ThreadAbortException>, or other exceptions at the call into the unreliable method because the runtime did not prepare it ahead of time or protect it from <xref:System.Threading.ThreadAbortException> exceptions at run time.</span></span> <span data-ttu-id="eb715-109">更大的威脅就是，在執行階段因方法造成的任何例外狀況，都可能讓 <xref:System.AppDomain> 或處理序處於不穩定的狀態，違反 CER 目標。</span><span class="sxs-lookup"><span data-stu-id="eb715-109">A greater threat is that any exception resulting from the method at run time could leave the <xref:System.AppDomain> or process in an unstable state, which is contrary to the objective of a CER.</span></span> <span data-ttu-id="eb715-110">建立 CER 的原因是為了避免這類的狀態損毀。</span><span class="sxs-lookup"><span data-stu-id="eb715-110">The reason a CER is created is to avoid state corruptions such as this.</span></span> <span data-ttu-id="eb715-111">損毀狀態的徵兆隨應用程式而異，因為應用程式之間的一致狀態定義各不相同。</span><span class="sxs-lookup"><span data-stu-id="eb715-111">The symptoms of corrupt state are application specific because the definition of consistent state is different between applications.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="eb715-112">原因</span><span class="sxs-lookup"><span data-stu-id="eb715-112">Cause</span></span>  
 <span data-ttu-id="eb715-113">CER 中的程式碼要呼叫沒有 <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> 的函式，或使用與 CER 中所執行者不相容之弱式 <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> 的函式。</span><span class="sxs-lookup"><span data-stu-id="eb715-113">Code within a CER is calling a function with no <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> or with a weak <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> that is not compatible with running in a CER.</span></span>  
  
 <span data-ttu-id="eb715-114">就可靠性合約語法而言，弱式合約是未指定 <xref:System.Runtime.ConstrainedExecution.Consistency> 列舉值或指定 <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>、<xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain> 或 <xref:System.Runtime.ConstrainedExecution.Cer.None> 之 <xref:System.Runtime.ConstrainedExecution.Consistency> 值的合約。</span><span class="sxs-lookup"><span data-stu-id="eb715-114">In terms of reliability contract syntax, a weak contract is a contract that does not specify a <xref:System.Runtime.ConstrainedExecution.Consistency> enumeration value or specifies a <xref:System.Runtime.ConstrainedExecution.Consistency> value of <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>, <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain>, or <xref:System.Runtime.ConstrainedExecution.Cer.None>.</span></span> <span data-ttu-id="eb715-115">任何這些狀況都指出，呼叫的程式碼可能會阻礙 CER 中其他程式碼的工作，以維護一致的狀態。</span><span class="sxs-lookup"><span data-stu-id="eb715-115">Any of these conditions indicates that the code called may impede the efforts of the other code in the CER to maintain consistent state.</span></span>  <span data-ttu-id="eb715-116">CER 允許程式碼以非常確定的方式處理錯誤，維護對應用程式相當重要的內部非變異值，並讓它繼續在記憶體不足例外狀況等暫時性錯誤的情況下執行。</span><span class="sxs-lookup"><span data-stu-id="eb715-116">CERs allow code to treat errors in a very deterministic manner, maintaining internal invariants that are important to the application and allowing it to continue running in the face of transient errors such as out-of-memory exceptions.</span></span>  
  
 <span data-ttu-id="eb715-117">啟動此 MDA 指出在 CER 中呼叫方法，可能會因為呼叫端未預期的方式，或讓 <xref:System.AppDomain> 或處理序保持損毀或無法修復的狀態而失敗。</span><span class="sxs-lookup"><span data-stu-id="eb715-117">The activation of this MDA indicates a possibility the method being called in the CER can fail in a way that the caller did not expect or that leaves the <xref:System.AppDomain> or process state corrupted or unrecoverable.</span></span> <span data-ttu-id="eb715-118">當然，呼叫的程式碼可能會正確執行，而此問題只是遺漏合約。</span><span class="sxs-lookup"><span data-stu-id="eb715-118">Of course, the called code might execute correctly and the problem is simply a missing contract.</span></span> <span data-ttu-id="eb715-119">不過，有關撰寫可靠程式碼的問題是很微妙的，缺少合約明顯表示程式碼可能不會正確執行。</span><span class="sxs-lookup"><span data-stu-id="eb715-119">However, the issues involved in writing reliable code are subtle and the absence of a contract is a good indicator the code might not execute correctly.</span></span> <span data-ttu-id="eb715-120">合約表示程式設計人員是以可靠方式編寫程式碼，並承諾在未來修訂程式碼時也不會變更這些保證。</span><span class="sxs-lookup"><span data-stu-id="eb715-120">The contracts are indicators that the programmer has coded reliably and also promises that these guarantees will not change in future revisions of the code.</span></span>  <span data-ttu-id="eb715-121">也就是說，合約宣告的是意圖，而不僅是實作的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="eb715-121">That is, the contracts are declarations of intent and not just implementation details.</span></span>  
  
 <span data-ttu-id="eb715-122">因為任何具有弱式或不存在合約的方法，可能以許多無法預測的方式失敗，所以執行階段不會嘗試從方法中移除任何它本身無法預測的失敗；例如，從延遲的 JIT 編譯、泛型字典母體擴展或執行緒中止所導入的失敗。</span><span class="sxs-lookup"><span data-stu-id="eb715-122">Because any method with a weak or nonexistent contract can potentially fail in many unpredictable ways, the runtime does not attempt to remove any of its own unpredictable failures from the method  that are introduced by lazy JIT-compiling, generics dictionary population, or thread aborts, for example.</span></span> <span data-ttu-id="eb715-123">亦即，啟動此 MDA 時，它會指出執行階段未包含要定義之 CER 中的呼叫方法；這個節點已終止呼叫歷程圖，因為繼續準備此子樹狀結構會幫助遮罩潛在的錯誤。</span><span class="sxs-lookup"><span data-stu-id="eb715-123">That is, when this MDA is activated, it indicates that the runtime did not include the called method in the CER being defined; the call graph was terminated at this node because continuing to prepare this subtree would help mask the potential error.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="eb715-124">解決方式</span><span class="sxs-lookup"><span data-stu-id="eb715-124">Resolution</span></span>  
 <span data-ttu-id="eb715-125">將有效的可靠性合約新增至函式，或避免使用該函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="eb715-125">Add a valid reliability contract to the function or avoid using that function call.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="eb715-126">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="eb715-126">Effect on the Runtime</span></span>  
 <span data-ttu-id="eb715-127">從 CER 呼叫弱式合約的效果，可能會讓 CER 無法完成其作業。</span><span class="sxs-lookup"><span data-stu-id="eb715-127">The effect of calling a weak contract from a CER could be the CER failure to complete its operations.</span></span> <span data-ttu-id="eb715-128">這可能會導致 <xref:System.AppDomain> 處理序狀態損毀。</span><span class="sxs-lookup"><span data-stu-id="eb715-128">This could lead to corruption of the <xref:System.AppDomain> process state.</span></span>  
  
## <a name="output"></a><span data-ttu-id="eb715-129">Output</span><span class="sxs-lookup"><span data-stu-id="eb715-129">Output</span></span>  
 <span data-ttu-id="eb715-130">下列是來自此 MDA 的輸出範例。</span><span class="sxs-lookup"><span data-stu-id="eb715-130">The following is sample output from this MDA.</span></span>  
  
 `Method 'MethodWithCer', while executing within a constrained execution region, makes a call at IL offset 0x000C to 'MethodWithWeakContract', which does not have a sufficiently strong reliability contract and might cause non-deterministic results.`  
  
## <a name="configuration"></a><span data-ttu-id="eb715-131">組態</span><span class="sxs-lookup"><span data-stu-id="eb715-131">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="eb715-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb715-132">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution>
- [<span data-ttu-id="eb715-133">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="eb715-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
