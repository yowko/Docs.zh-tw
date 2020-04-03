---
title: 如何：使用 PLINQ 逐一查看檔案目錄
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
ms.openlocfilehash: 208076cb9b7b56ab13458fa0dd4d92f2023106b9
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635837"
---
# <a name="how-to-iterate-file-directories-with-plinq"></a>如何：使用 PLINQ 逐一查看檔案目錄

本文介紹了兩種並行化文件目錄操作的方法。 第一個查詢使用 <xref:System.IO.Directory.GetFiles%2A> 方法來填入目錄和所有子目錄中的檔案名稱陣列。 此方法可以在操作開始時引入延遲,因為它不會返回,直到填充整個陣列。 但是,填充陣列后,PLINQ 可以快速並行處理它。  
  
第二個查詢使用靜態<xref:System.IO.Directory.EnumerateDirectories%2A>和<xref:System.IO.DirectoryInfo.EnumerateFiles%2A>方法 ,這些靜態和方法立即開始返回結果。 當您反覆運算大型目錄樹時,此方法可以更快,但與第一個示例相比,處理時間取決於許多因素。  
  
> [!NOTE]
> 這些示例旨在演示使用方式,並且可能不會比等效的連續 LINQ 到物件查詢運行得更快。 如需加速的詳細資訊，請參閱[認識 PLINQ 中的加速](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。  
  
## <a name="getfiles-example"></a>取得檔案範例

 此示例演示如何在簡單方案中反覆運算檔目錄,當您有權訪問樹中的所有目錄、檔大小不大且訪問時間不顯著時。 此方法一開始由於正在建構檔案名稱陣列，會有一段時間的延遲。  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="enumeratefiles-example"></a>列舉檔案範例

 此示例演示如何在簡單方案中反覆運算檔目錄,當您有權訪問樹中的所有目錄、檔大小不大且訪問時間不顯著時。 此方法開始產生結果的速度會比上一個範例快。  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 使用 <xref:System.IO.Directory.GetFiles%2A> 時，請確定您有足夠的權限可以存取樹狀中的所有目錄。 否則,將引發異常,不會返回任何結果。 在 PLINQ 查詢中使用 <xref:System.IO.Directory.EnumerateDirectories%2A> 時，要以可讓您繼續逐一查看的正常方式處理 I/O 例外狀況會有困難。 如果您的程式碼必須處理 I/O 或未經授權的存取例外狀況，您應該考慮[如何：使用平行類別逐一查看檔案目錄](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md)中描述的方法。  
  
 如果 I/O 延遲會造成問題，例如在網路上處理檔案 I/O，請考慮使用 [TPL 和傳統 .NET Framework 非同步程式設計](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)和這篇[部落格文章](https://devblogs.microsoft.com/pfxteam/parallel-extensions-and-io/)中所述的其中一項非同步 I/O 技術。  
  
## <a name="see-also"></a>另請參閱

- [平行 LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
