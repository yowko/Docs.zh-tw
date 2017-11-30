---
title: "如何：使用 PLINQ 逐一查看檔案目錄"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 40fd9f64b5702f5205b7817f3de1e0a8709c5a63
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-iterate-file-directories-with-plinq"></a>如何：使用 PLINQ 逐一查看檔案目錄
此範例示範兩個簡單的方式，來平行化檔案目錄的作業。 第一個查詢使用<xref:System.IO.Directory.GetFiles%2A>方法來填入的目錄和所有子目錄中的檔案名稱的陣列。 這個方法不會傳回，直到整個陣列已填入，因此它可能會導致在作業開始時的延遲。 不過，填入陣列之後，PLINQ 可以處理它以平行方式非常快速。  
  
 第二個查詢會使用靜態<xref:System.IO.Directory.EnumerateDirectories%2A>和<xref:System.IO.DirectoryInfo.EnumerateFiles%2A>開始立即傳回結果的方法。 這種方法可以更快時反覆大型目錄樹狀結構中，雖然相較於第一個範例中的處理時間可能取決於許多因素而定。  
  
> [!WARNING]
>  這些範例為了示範用法，並執行速度可能比不上對應的循序 LINQ to Objects 查詢。 提升速度的詳細資訊，請參閱[PLINQ 中的了解加速](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。  
  
## <a name="example"></a>範例  
 下列範例會示範如何逐一查看檔案目錄，在簡單的案例時您可以在樹狀目錄中的所有目錄存取、 檔案大小不是非常大，和存取時間皆屬於不顯著。 檔案名稱的陣列會在建構時，這種方法牽涉到一段延遲開頭。  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="example"></a>範例  
 下列範例會示範如何逐一查看檔案目錄，在簡單的案例時您可以在樹狀目錄中的所有目錄存取、 檔案大小不是非常大，和存取時間皆屬於不顯著。 這種方法開始速度比前一個範例產生的結果。  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 當使用<xref:System.IO.Directory.GetFiles%2A>，確定您在樹狀目錄中的所有目錄上有足夠的權限。 否則將擲回例外狀況，而且會傳回任何結果。 當使用<xref:System.IO.Directory.EnumerateDirectories%2A>在 PLINQ 查詢中，會有問題，可讓您在繼續重複執行以正常方式處理 I/O 例外狀況。 如果您的程式碼必須處理 I/O 或未經授權的存取例外狀況，那麼您應該考慮中描述的方法[How to： 使用平行類別逐一查看檔案目錄](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md)。  
  
 如果 I/O 延遲問題，例如在網路上的檔案 I/O 請考慮使用非同步技術中所述的其中一個[TPL 和傳統.NET Framework 非同步程式設計](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)和此[部落格文章](http://go.microsoft.com/fwlink/?LinkID=186458).  
  
## <a name="see-also"></a>另請參閱  
 [平行 LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
