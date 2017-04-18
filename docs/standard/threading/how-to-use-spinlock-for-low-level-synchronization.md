---
title: "How to: Use SpinLock for Low-Level Synchronization | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SpinLock, how to use"
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# How to: Use SpinLock for Low-Level Synchronization
下列範例示範如何使用 <xref:System.Threading.SpinLock>。  
  
## 範例  
 在上述範例中，關鍵的區段會執行最少量的工作，因此是 <xref:System.Threading.SpinLock> 很好的候選鎖定目標。  相較於標準鎖定，小幅遞增工作量可以增加 <xref:System.Threading.SpinLock> 的效能。  但是會有臨界點，超過這個點，SpinLock 就變得比標準鎖定耗費資源。  您可以使用程式碼剖希工具中新的並行程式碼剖析功能，查看哪一種鎖定類型會在程式中提供較佳的效能。  如需詳細資訊，請參閱[並行視覺化檢視](../Topic/Concurrency%20Visualizer.md)。  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 在不會持續佔用共用資源太久的情況下，<xref:System.Threading.SpinLock> 可能會很有用。  這種情況下，在多核心電腦上讓封鎖的執行緒空轉幾個時脈週期直到釋放鎖定為止，會比較有效率。  讓執行緒多空轉一陣子，執行緒就不會一直停滯不前，但這是很耗費 CPU 資源的程序。  <xref:System.Threading.SpinLock> 可以在特定情況下停止空轉作業，以避免耗盡邏輯處理器資源，或是破壞啟用超執行緒 \(Hyper\-Threading\) 之系統上的優先權順序。  
  
 上述範例會使用 <xref:System.Collections.Generic.Queue%601?displayProperty=fullName> 類別，這個類別必須透過使用者同步處理進行多執行緒存取。  在以 .NET Framework 第 4 版 \(含\) 以後版本為目標的應用程式中有另一種選擇，即是使用 <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=fullName>，這就不需要任何使用者鎖定。  
  
 請注意 <xref:System.Threading.SpinLock.Exit%2A> 呼叫中使用的 `false` \(在 Visual Basic 為 `False`\)。  這可提供最佳的效能。  請在 IA64 架構上指定 `true` \(`True`\) 以使用記憶體柵欄，記憶體柵欄會清空寫入緩衝區，以確保其他執行緒現在可以使用鎖定來執行結束。  
  
## 請參閱  
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)