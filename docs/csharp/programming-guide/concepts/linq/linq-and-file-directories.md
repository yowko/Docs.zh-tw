---
title: LINQ 和檔案目錄 (C#)
ms.date: 07/20/2015
ms.assetid: b66c55e4-0f72-44e5-b086-519f9962335c
ms.openlocfilehash: 4bdd21cf4d8558f140b265f195368082964c34c4
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44252709"
---
# <a name="linq-and-file-directories-c"></a>LINQ 和檔案目錄 (C#)
許多檔案系統作業基本上就是查詢，因此很適合使用 LINQ 方法。  
  
 請注意，本節中的查詢不具破壞性。 這些查詢不會用來變更原始檔案或資料夾的內容。 這是依照查詢不應該造成任何副作用的規則。 一般而言，任何修改來源資料的程式碼 (包括執行 create/update/delete 運算子的查詢)，都應該與單純查詢資料的程式碼分開。  
  
 本節包含下列主題：  
  
 [如何：查詢具有指定之屬性或名稱的檔案 (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 示範如何檢查檔案之 <xref:System.IO.FileInfo> 物件的一或多個屬性來搜尋檔案。  
  
 [如何：依副檔名分組檔案 (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 示範如何依據檔案的副檔名來傳回 <xref:System.IO.FileInfo> 物件的群組。  
  
 [如何：查詢一組資料夾中的位元組總數 (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)  
 示範如何傳回指定之樹狀目錄中所有檔案的位元組總數。  
  
 [如何：比較兩個資料夾的內容 (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)  
 示範如何傳回同時出現在兩個指定資料夾中的所有檔案，以及只出現在其中一個資料夾中的所有檔案。  
  
 [如何：查詢樹狀目錄中的最大檔案 (LINQ)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)  
 示範如何傳回樹狀目錄中的最大檔案或最小檔案，或是指定數目的檔案。  
  
 [如何：查詢樹狀目錄中的重複檔案 (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 示範如何將出現在指定樹狀目錄中多個位置的所有檔案名稱群組在一起。 同時示範如何根據自訂比較子，來執行更複雜的比較。  
  
 [如何：查詢資料夾中的檔案內容 (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-the-contents-of-files-in-a-folder-lin.md)  
 示範如何逐一查看樹狀目錄中的資料夾、開啟每個檔案，並查詢檔案的內容。  
  
## <a name="comments"></a>註解  
 要建立能夠精確代表檔案系統內容，同時又能順利處理例外狀況的資料來源，其實是件複雜的工作。 本節中的範例會建立 <xref:System.IO.FileInfo> 物件的快照集合，以代表所指定根資料夾和其所有子資料夾下的所有檔案。 從您開始到結束執行查詢的這段期間，每個 <xref:System.IO.FileInfo> 的實際狀態都可能會變更。 例如，您可以建立 <xref:System.IO.FileInfo> 物件的清單來用作資料來源。 如果您嘗試在查詢中存取 `Length` 屬性，<xref:System.IO.FileInfo> 物件會嘗試存取檔案系統以更新 `Length` 的值。 如果檔案不再存在，即使您未直接查詢檔案系統，也會在查詢中收到 <xref:System.IO.FileNotFoundException>。 本節中的某些查詢會另外使用一個方法，來解決某些情況下的特定例外狀況。 另一個選項是使用 <xref:System.IO.FileSystemWatcher> 持續動態更新資料來源。  
  
## <a name="see-also"></a>請參閱

- [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
