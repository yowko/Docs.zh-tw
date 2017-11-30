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
helpviewer_keywords: parallel loops, how to iterate directories
ms.assetid: 555e9f48-f53d-4774-9bcf-3e965c732ec5
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c21aadf70eaccafc8c8ec9c4efefff1c66abc6b5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-iterate-file-directories-with-the-parallel-class"></a>如何：使用平行類別逐一查看檔案目錄
在許多情況下，檔案反覆項目是可以輕鬆平行處理作業。 本主題[How to： 使用 PLINQ 逐一查看檔案目錄](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md)示範許多案例中執行這項工作的最簡單方式。 不過，當您的程式碼有許多類型的存取檔案系統時可能發生的例外狀況處理，可能會發生的複雜性。 下列範例會顯示問題的其中一個方法。 它會使用堆疊為基礎的反覆項目來周遊所有檔案和資料夾下指定的目錄，並且它可讓您的程式碼來攔截並處理各種例外狀況。 當然，您處理的例外狀況的方法是由您決定。  
  
## <a name="example"></a>範例  
 下列範例會循序逐一查看目錄，但是以平行方式處理檔案。 這可能是最好的方法時，您有大型的檔案到目錄比率。 它也可平行處理的目錄反覆項目，並以循序方式存取每個檔案。 可能不是有效平行處理這兩個迴圈，除非您特別的目標有大量處理器的電腦。 不過，如同所有的情況下，您應該測試您的應用程式，徹底地判斷最佳的方法。  
  
 [!code-csharp[TPL_Parallel#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_file.cs#08)]
 [!code-vb[TPL_Parallel#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/fileiteration08.vb#08)]  
  
 在此範例中，檔案 I/O 是以同步方式執行。 當處理大型檔案或低速網路連線，它可能會比以非同步方式存取的檔案。 您可以將非同步 I/O 技術結合平行反覆項目。 如需詳細資訊，請參閱 [TPL 和傳統 .NET Framework 非同步程式設計](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)。  
  
 這個範例會使用本機 `fileCount` 變數維護已處理檔案的總數。 由於可能會有多個工作同時存取這個變數，因此會透過呼叫 <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> 方法同步處理其存取。  
  
 請注意，如果例外狀況會擲回主執行緒，而啟動的執行緒<xref:System.Threading.Tasks.Parallel.ForEach%2A>方法可能會繼續執行。 若要停止這些執行緒，可以在您的例外狀況處理常式中設定布林值變數，並檢查它在平行迴圈的每個反覆項目上的值。 如果此值會指出已擲回的例外狀況，使用<xref:System.Threading.Tasks.ParallelLoopState>停止或中斷迴圈的變數。 如需詳細資訊，請參閱[如何： 停止或中斷 Parallel.For 迴圈](http://msdn.microsoft.com/en-us/de52e4f1-9346-4ad5-b582-1a4d54dc7f7e)。  
  
## <a name="see-also"></a>另請參閱  
 [資料平行處理原則](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
