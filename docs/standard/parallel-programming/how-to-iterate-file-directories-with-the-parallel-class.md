---
title: "如何：使用平行類別逐一查看檔案目錄"
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
helpviewer_keywords:
- parallel loops, how to iterate directories
ms.assetid: 555e9f48-f53d-4774-9bcf-3e965c732ec5
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3ac1af7922e1bbd81f4dfcee256f5c8892294003
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-iterate-file-directories-with-the-parallel-class"></a>如何：使用平行類別逐一查看檔案目錄
在許多情況下，檔案反覆運算是一項可以輕鬆平行處理的作業。 [如何：使用 PLINQ 逐一查看檔案目錄](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md)這個主題示範針對許多案例執行此工作的最簡單方式。 不過，當您的程式碼需要處理在存取檔案系統時可能會出現的許多類型例外狀況時，便會提升此工作的複雜性。 下列範例會示範處理該問題的其中一種方式。 它會使用以堆疊為基礎的反覆運算來周遊位於特定目錄底下的所有檔案和資料夾，並能使程式碼能夠攔截並處理各種不同的例外狀況。 當然，要如何處理例外狀況仍然取決於您。  
  
## <a name="example"></a>範例  
 下列範例會循序逐一查看目錄，但是以平行方式處理檔案。 當您有大型的檔案/目錄比率時，這應該是最好的方法。 您也可以平行處理目錄反覆運算，並以循序方式存取每個檔案。 除非您是特別鎖定具有大量處理器的電腦，否則同時對兩個迴圈進行平行處理應該不會很有效率。 不過無論如何，您都應該徹底地測試應用程式以判斷最佳方法。  
  
 [!code-csharp[TPL_Parallel#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_file.cs#08)]
 [!code-vb[TPL_Parallel#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/fileiteration08.vb#08)]  
  
 在此範例中，檔案 I/O 是以同步方式執行。 處理大型檔案或低速的網路連線時，您應該考慮以非同步方式存取檔案。 您可以結合非同步 I/O 技術與平行反覆運算。 如需詳細資訊，請參閱 [TPL 和傳統 .NET Framework 非同步程式設計](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)。  
  
 這個範例會使用本機 `fileCount` 變數維護已處理檔案的總數。 由於可能會有多個工作同時存取這個變數，因此會透過呼叫 <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> 方法同步處理其存取。  
  
 請注意，若有例外狀況在主執行緒上擲出，由 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 啟動的執行緒可能會繼續執行。 若要停止這些執行緒，您可以在例外處理常式中設定布林值變數，並在平行迴圈的每個反覆運算上檢查其值。 若該值指出有擲出例外狀況，請使用 <xref:System.Threading.Tasks.ParallelLoopState> 變數來停止或中斷迴圈。 如需詳細資訊，請參閱[如何：停止或中斷 Parallel.For 迴圈](http://msdn.microsoft.com/library/de52e4f1-9346-4ad5-b582-1a4d54dc7f7e)。  
  
## <a name="see-also"></a>請參閱  
 [資料平行處理原則](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
