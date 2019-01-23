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
ms.openlocfilehash: c3cccb94268264217a1e6a1b5def71c6c433b820
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614779"
---
# <a name="invalidcercall-mda"></a>invalidCERCall MDA
當方法的限制執行區域 (CER) 圖形內的呼叫沒有可靠性合約或過度弱式合約時，就會啟動 `invalidCERCall` Managed 偵錯助理 (MDA)。 弱式合約是宣告最差狀態損毀範圍超過執行個體傳遞至呼叫的範圍，也就是 <xref:System.AppDomain> 或處理序狀態可能會損毀，或在 CER 內呼叫時，其結果不一定是決定性可計算結果。  
  
## <a name="symptoms"></a>徵兆  
 在 CER 中執行程式碼時出現非預期的結果。 沒有特定的徵兆。 它們可能是未預期的 <xref:System.OutOfMemoryException>、<xref:System.Threading.ThreadAbortException> 或在呼叫不可靠的方法時發生的其他例外狀況，因為執行階段未事先準備或保護它免於執行階段的 <xref:System.Threading.ThreadAbortException> 例外狀況。 更大的威脅就是，在執行階段因方法造成的任何例外狀況，都可能讓 <xref:System.AppDomain> 或處理序處於不穩定的狀態，違反 CER 目標。 建立 CER 的原因是為了避免這類的狀態損毀。 損毀狀態的徵兆隨應用程式而異，因為應用程式之間的一致狀態定義各不相同。  
  
## <a name="cause"></a>原因  
 CER 中的程式碼要呼叫沒有 <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> 的函式，或使用與 CER 中所執行者不相容之弱式 <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> 的函式。  
  
 就可靠性合約語法而言，弱式合約是未指定 <xref:System.Runtime.ConstrainedExecution.Consistency> 列舉值或指定 <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>、<xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain> 或 <xref:System.Runtime.ConstrainedExecution.Cer.None> 之 <xref:System.Runtime.ConstrainedExecution.Consistency> 值的合約。 任何這些狀況都指出，呼叫的程式碼可能會阻礙 CER 中其他程式碼的工作，以維護一致的狀態。  CER 允許程式碼以非常確定的方式處理錯誤，維護對應用程式相當重要的內部非變異值，並讓它繼續在記憶體不足例外狀況等暫時性錯誤的情況下執行。  
  
 啟動此 MDA 指出在 CER 中呼叫方法，可能會因為呼叫端未預期的方式，或讓 <xref:System.AppDomain> 或處理序保持損毀或無法修復的狀態而失敗。 當然，呼叫的程式碼可能會正確執行，而此問題只是遺漏合約。 不過，有關撰寫可靠程式碼的問題是很微妙的，缺少合約明顯表示程式碼可能不會正確執行。 合約表示程式設計人員是以可靠方式編寫程式碼，並承諾在未來修訂程式碼時也不會變更這些保證。  也就是說，合約宣告的是意圖，而不僅是實作的詳細資料。  
  
 因為任何具有弱式或不存在合約的方法，可能以許多無法預測的方式失敗，所以執行階段不會嘗試從方法中移除任何它本身無法預測的失敗；例如，從延遲的 JIT 編譯、泛型字典母體擴展或執行緒中止所導入的失敗。 亦即，啟動此 MDA 時，它會指出執行階段未包含要定義之 CER 中的呼叫方法；這個節點已終止呼叫歷程圖，因為繼續準備此子樹狀結構會幫助遮罩潛在的錯誤。  
  
## <a name="resolution"></a>解決方式  
 將有效的可靠性合約新增至函式，或避免使用該函式呼叫。  
  
## <a name="effect-on-the-runtime"></a>對執行階段的影響  
 從 CER 呼叫弱式合約的效果，可能會讓 CER 無法完成其作業。 這可能會導致 <xref:System.AppDomain> 處理序狀態損毀。  
  
## <a name="output"></a>輸出  
 下列是來自此 MDA 的輸出範例。  
  
 `Method 'MethodWithCer', while executing within a constrained execution region, makes a call at IL offset 0x000C to 'MethodWithWeakContract', which does not have a sufficiently strong reliability contract and might cause non-deterministic results.`  
  
## <a name="configuration"></a>組態  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution>
- [診斷 Managed 偵錯助理的錯誤](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
