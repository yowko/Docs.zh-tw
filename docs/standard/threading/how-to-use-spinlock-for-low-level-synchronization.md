---
title: 操作說明：使用 SpinLock 進行低階同步處理
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
ms.openlocfilehash: 3fb19c2b36d97710685cac4ecd10f47a119814ce
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2020
ms.locfileid: "93189182"
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a>操作說明：使用 SpinLock 進行低階同步處理

下列範例示範如何使用 <xref:System.Threading.SpinLock>。 在此範例中，重要的區段會執行最少量的工作，因此適合作為 <xref:System.Threading.SpinLock> 的候選項。 相較於標準鎖定，少量增加工作可提升 <xref:System.Threading.SpinLock> 的效能。 不過，在增加到達某一程度後，SpinLock 的成本就會變成高於標準鎖定。 您可以使用程式碼剖析工具中的並行分析功能，來查看哪一種鎖定型別可在您的程式中提供較佳的效能。 如需詳細資訊，請參閱[並行視覺化檢視](/visualstudio/profiling/concurrency-visualizer)。  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 當共用資源的鎖定不會保留很久時，<xref:System.Threading.SpinLock> 可能很實用。 在這類情況下，多核心電腦上的已封鎖執行緒可以有效率地微調幾個週期，直到鎖定釋放為止。 藉由微調，執行緒不會變成鎖定狀態 (這是需要大量 CPU 的程序)。 在某些情況下，<xref:System.Threading.SpinLock> 將停止微調，以避免耗盡邏輯處理器或在具備超執行緒的系統上反轉優先順序。  
  
 這個範例會使用 <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> 類別，此類別需要使用者同步處理以進行多執行緒存取。 另一個選項是使用 <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> ，這不需要任何使用者鎖定。  
  
 請注意 `false` 在的呼叫中使用 <xref:System.Threading.SpinLock.Exit%2A?displayProperty=nameWithType> 。 這可提供最佳效能。 `true`在 IA64 架構上指定以使用記憶體隔離，這會清除寫入緩衝區，以確保鎖定現已可供其他執行緒結束。  
  
## <a name="see-also"></a>另請參閱

- [執行緒物件和功能](threading-objects-and-features.md)
- [lock 陳述式 (C#)](../../csharp/language-reference/keywords/lock-statement.md)
- [SyncLock 陳述式 (Visual Basic)](../../visual-basic/language-reference/statements/synclock-statement.md)
