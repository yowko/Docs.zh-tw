---
title: "LINQ 和檔案目錄 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 159fd5c3-3926-4071-ae78-d8e423287eb7
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5536ae95b42cdaddda2c4cae97a114681e94b0ab
ms.lasthandoff: 03/13/2017

---
# <a name="linq-and-file-directories-visual-basic"></a>LINQ 和檔案目錄 (Visual Basic)
許多檔案系統作業基本上是查詢，因此適合的 LINQ 方法。  
  
 請注意，本節中的查詢非破壞性。 它們不會用來變更原始的檔案或資料夾的內容。 這會遵循規則，查詢應該不會造成任何副作用。 一般情況下，修改來源資料的任何程式碼 （包括執行的查詢建立 / 更新 / 刪除運算子） 應該是分開的程式碼，只會查詢的資料。  
  
 本節包含下列主題：  
  
 [如何︰ 查詢具有指定之的屬性或名稱 (Visual Basic) 的檔案](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 示範如何藉由檢查的一個或多個屬性搜尋的檔案其<xref:System.IO.FileInfo>物件。</xref:System.IO.FileInfo>  
  
 [如何︰ 依副檔名 (LINQ) (Visual Basic) 的檔案群組](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 示範如何傳回群組<xref:System.IO.FileInfo>物件會根據其副檔名。</xref:System.IO.FileInfo>  
  
 [如何︰ 查詢一組資料夾 (LINQ) (Visual Basic) 中的位元組總數](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)  
 示範如何傳回指定的目錄樹狀結構中的所有檔案的位元組總數。  
  
 [如何︰ 比較兩個資料夾內容 (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)s  
 示範如何傳回有兩個指定的資料夾中的所有檔案以及所有檔案，但未在另一個資料夾中。  
  
 [如何︰ 查詢的最大檔案或目錄樹狀結構 (LINQ) (Visual Basic) 中的檔案](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)  
 示範如何在目錄樹狀結構中傳回的最大或最小的檔案或指定的檔案數目。  
  
 [如何︰ 查詢目錄樹狀結構 (LINQ) (Visual Basic) 中的重複檔案](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 顯示如何將所有出現在指定的目錄樹狀結構中的多個位置的檔案名稱。 也說明如何執行更複雜的比較為基礎的自訂比較子。  
  
 [如何︰ 查詢資料夾 (LINQ) (Visual Basic) 中的檔案的內容](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-the-contents-of-files-in-a-folder-linq.md)  
 示範如何逐一查看樹狀結構中的資料夾、 開啟每個檔案，並查詢檔案的內容。  
  
## <a name="comments"></a>註解  
 建立資料來源正確代表檔案系統的內容，並適當地處理例外狀況是一些複雜性。 本章節中的範例建立的快照集集合<xref:System.IO.FileInfo>物件，表示指定的根資料夾下的所有檔案和所有子資料夾。</xref:System.IO.FileInfo> 每個的實際狀態<xref:System.IO.FileInfo>中開始和結束執行查詢之間的時間可能會變更。</xref:System.IO.FileInfo> 例如，您可以建立一份<xref:System.IO.FileInfo>物件做為資料來源使用。</xref:System.IO.FileInfo> 如果您嘗試存取`Length`屬性在查詢中，<xref:System.IO.FileInfo>物件將會嘗試存取檔案系統來更新值`Length`。</xref:System.IO.FileInfo> 如果檔案不存在，就會<xref:System.IO.FileNotFoundException>在查詢中，即使您不在檔案系統直接查詢。</xref:System.IO.FileNotFoundException> 本章節中的某些查詢會使用不同的方法使用這些特定的例外狀況，在某些情況下。 另一個選擇是讓您使用<xref:System.IO.FileSystemWatcher>.</xref:System.IO.FileSystemWatcher>動態更新的資料來源  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
