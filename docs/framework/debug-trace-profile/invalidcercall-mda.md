---
title: "invalidCERCall MDA | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "invalid CER calls"
  - "InvalidCERCall MDA"
  - "MDAs (managed debugging assistants), CER calls"
  - "constrained execution regions"
  - "CER calls"
  - "managed debugging assistants (MDAs), CER calls"
ms.assetid: c4577410-602e-44e5-9dab-fea7c55bcdfe
caps.latest.revision: 14
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 14
---
# invalidCERCall MDA
當限制的執行區域 \(CER\) 圖形內有一個方法的呼叫，而此方法沒有任何可靠性合約或有弱式合約時，即會啟動 `invalidCERCall` Managed 偵錯助理 \(MDA\)。  弱式合約是指宣告最糟的狀態損毀具有的範圍比傳遞給呼叫之執行個體範圍更大的合約，也就是說，<xref:System.AppDomain> 或處理序狀態可能會損毀，或是在 CER 內呼叫時，它的結果不一定是可以運算的。  
  
## 症狀  
 在 CER 內執行程式碼時，發生了非預期的結果。  這些症狀並非特定的，  可能是非預期的 <xref:System.OutOfMemoryException>、<xref:System.Threading.ThreadAbortException>，或是因為執行階段未事先準備或是防止在執行階段發生 <xref:System.Threading.ThreadAbortException> 例外狀況時，呼叫不可靠的方法時產生的其他例外狀況。  更大的威脅是在執行階段時，從方法產生的任何例外狀況，都可能會讓 <xref:System.AppDomain> 或處理序處於不穩定的狀態，這會與 CER 的目的產生對立。  建立 CER 的原因是要避免類似這種狀態損毀的發生；  損毀狀態的症狀是應用程式特定的，因為一致狀態之定義會因應用程式而不同。  
  
## 原因  
 CER 內的程式碼正在呼叫沒有 <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> 的函式，或是函式中包含了與在 CER 中的執行作業不相符的弱式 <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute>。  
  
 就可靠性合約的語法而言，弱式合約是指未指定 <xref:System.Runtime.ConstrainedExecution.Consistency> 列舉值或指定 <xref:System.Runtime.ConstrainedExecution.Consistency>、<xref:System.Runtime.ConstrainedExecution.Consistency> 或 <xref:System.Runtime.ConstrainedExecution.Cer> 之 <xref:System.Runtime.ConstrainedExecution.Consistency> 值的合約。  上面任何情況都表示呼叫的程式碼可能會阻礙 CER 中的其他程式碼為了維護一致狀態而做的努力。CER 可讓程式碼以非常確定的方式處理錯誤、處理對應用程式非常重要的內部不變項目，並讓它在面臨暫時性錯誤 \(例如，記憶體不足的例外狀況\) 之下，仍繼續執行。  
  
 這個 MDA 的啟動表示在 CER 中呼叫的方法有可能會發生讓呼叫端未預期到的失敗，或是有可能發生讓 <xref:System.AppDomain> 或處理序狀態損毀或無法復原的失敗。  當然，呼叫的程式碼有可能會正確執行，而這個問題只是遺漏合約而已；  但是，與編寫可靠程式碼有關的問題是很敏感的，而缺少合約則是程式碼可能無法正確執行的一個很好的指標。  合約是一種指標，表示程式設計人員已經編寫可靠的程式碼，而且承諾這些保證將不會在未來程式碼修訂中變更。也就是說，合約是很有意義的宣告，而不只是實作的細節。  
  
 因為任何具有弱式或不存在之合約的方法可能會以許多無法預測的方式來產生失敗，所以執行階段不會嘗試從類似懶惰式的 JIT 編譯、泛型字典擴展或執行緒中止所引入的方法中，移除其本身的任何無法預期的失敗。  也就是說，當啟動這個 MDA 時，它會指示執行階段未在所定義的 CER 中加入呼叫的方法；呼叫圖形會在這個節點上結束，因為繼續準備這個樹狀子目錄將有助於遮蔽可能的錯誤。  
  
## 解決方式  
 將有效的可靠性合約加入到函式中，或是避免使用該函式呼叫。  
  
## 對執行階段的影響  
 從 CER 呼叫弱式合約所產生的影響，可能會讓 CER 無法完成其作業，  而這可能會導致 <xref:System.AppDomain> 處理序狀態的損毀。  
  
## Output  
 下列是來自這個 MDA 的範例輸出。  
  
 `Method 'MethodWithCer', while executing within a constrained execution region, makes a call at IL offset 0x000C to 'MethodWithWeakContract', which does not have a sufficiently strong reliability contract and might cause non-deterministic results.`  
  
## Configuration  
  
```  
<mdaConfig>  
  <assistants>  
    <invalidCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## 請參閱  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>   
 <xref:System.Runtime.ConstrainedExecution>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)