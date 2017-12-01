---
title: "如何：使用 SpinLock 進行低階同步處理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 30ddc7d340b210aaad4a04ea43e89555d2701f20
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a>如何：使用 SpinLock 進行低階同步處理
下列範例示範如何使用<xref:System.Threading.SpinLock>。  
  
## <a name="example"></a>範例  
 在此範例中，關鍵區段執行少量工作，讓它的絕佳候選<xref:System.Threading.SpinLock>。 增加工作只需要編寫小量會增加的效能<xref:System.Threading.SpinLock>相較於標準的鎖定。 不過，在增加到達某一程度後，SpinLock 的成本就會變成高於標準鎖定。 您可以使用程式碼剖析工具中的並行分析功能，來查看哪一種鎖定型別可在您的程式中提供較佳的效能。 如需詳細資訊，請參閱[並行視覺化檢視](/visualstudio/profiling/concurrency-visualizer)。  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <xref:System.Threading.SpinLock>可能會很有用，當共用資源上的鎖定並不會保留很長。 在這類情況下，多核心電腦上的已封鎖執行緒可以有效率地微調幾個週期，直到鎖定釋放為止。 藉由微調，執行緒不會變成鎖定狀態 (這是需要大量 CPU 的程序)。 <xref:System.Threading.SpinLock>將會停止微調，以避免不足邏輯處理器或優先順序反轉具有超執行緒的系統上的某些條件下。  
  
 這個範例會使用<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>類別，需要進行多執行緒存取的使用者同步處理。 在.NET Framework 第 4 版為目標的應用程式，另一個選項是使用<xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>，不需要任何使用者的鎖定。  
  
 請注意使用`false`(`False`在 Visual Basic 中) 的呼叫中<xref:System.Threading.SpinLock.Exit%2A>。 這可提供最佳效能。 在 IA64 架構上指定 `true` (`True`) 以使用記憶體範圍，記憶體範圍可排清寫入緩衝區以確保鎖定現已可供其他執行緒來結束。  
  
## <a name="see-also"></a>另請參閱  
 [執行緒物件和功能](../../../docs/standard/threading/threading-objects-and-features.md)
