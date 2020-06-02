---
title: 作法：使用 PLINQ 逐一查看檔案目錄
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
ms.openlocfilehash: abf31ea69af6a85140efb783959a9a586ef6a59e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277995"
---
# <a name="how-to-iterate-file-directories-with-plinq"></a>作法：使用 PLINQ 逐一查看檔案目錄

本文說明兩種在檔案目錄上平行處理作業的方式。 第一個查詢使用 <xref:System.IO.Directory.GetFiles%2A> 方法來填入目錄和所有子目錄中的檔案名稱陣列。 這個方法可能會在作業開始時引進延遲，因為在擴展整個陣列之前，它不會傳回。 不過，在填入陣列之後，PLINQ 就可以快速地平行處理。  
  
第二個查詢使用靜態 <xref:System.IO.Directory.EnumerateDirectories%2A> 和 <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> 方法，其會立即開始傳回結果。 當您反復查看大型目錄樹狀結構時，這種方法可能會更快，但相較于第一個範例，處理時間會視許多因素而定。  
  
> [!NOTE]
> 這些範例的目的是要示範使用方式，而且執行速度可能會比對等的順序 LINQ to Objects 查詢更快。 如需加速的詳細資訊，請參閱[認識 PLINQ 中的加速](understanding-speedup-in-plinq.md)。  
  
## <a name="getfiles-example"></a>GetFiles 範例

 這個範例示範當您可以存取樹狀結構中的所有目錄、檔案大小不大，且存取時間不高時，如何在簡單的案例中逐一查看檔案目錄。 此方法一開始由於正在建構檔案名稱陣列，會有一段時間的延遲。  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="enumeratefiles-example"></a>EnumerateFiles 範例

 這個範例示範當您可以存取樹狀結構中的所有目錄、檔案大小不大，且存取時間不高時，如何在簡單的案例中逐一查看檔案目錄。 此方法開始產生結果的速度會比上一個範例快。  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 使用 <xref:System.IO.Directory.GetFiles%2A> 時，請確定您有足夠的權限可以存取樹狀中的所有目錄。 否則，將會擲回例外狀況，而且不會傳回任何結果。 在 PLINQ 查詢中使用 <xref:System.IO.Directory.EnumerateDirectories%2A> 時，要以可讓您繼續逐一查看的正常方式處理 I/O 例外狀況會有困難。 如果您的程式碼必須處理 I/O 或未經授權的存取例外狀況，您應該考慮[如何：使用平行類別逐一查看檔案目錄](how-to-iterate-file-directories-with-the-parallel-class.md)中描述的方法。  
  
 如果 I/O 延遲會造成問題，例如在網路上處理檔案 I/O，請考慮使用 [TPL 和傳統 .NET Framework 非同步程式設計](tpl-and-traditional-async-programming.md)和這篇[部落格文章](https://devblogs.microsoft.com/pfxteam/parallel-extensions-and-io/)中所述的其中一項非同步 I/O 技術。  
  
## <a name="see-also"></a>另請參閱

- [平行 LINQ (PLINQ)](introduction-to-plinq.md)
