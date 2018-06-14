---
title: 在 Visual Basic 中實作 IEnumerable
ms.date: 07/20/2015
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
ms.openlocfilehash: 2c2012261f38bccb704fe1a0300d496785e2129c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656323"
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>逐步解說：在 Visual Basic 中實作 IEnumerable(Of T)
<xref:System.Collections.Generic.IEnumerable%601>可以一次傳回一個項目值序列的類別會實作介面。 傳回的資料一次的一個項目是您沒有將一組完整的資料載入記憶體，才能使用它的優點。 您只需要使用足夠的記憶體載入資料的單一項目。 類別可實作`IEnumerable(T)`介面可以搭配`For Each`迴圈或 LINQ 查詢。  
  
 例如，請考慮必須讀取大型文字檔，並傳回每一行從符合特定的搜尋準則的檔案的應用程式。 應用程式會使用 LINQ 查詢，傳回符合指定的準則的檔案的行。 若要使用 LINQ 查詢來查詢檔案的內容，應用程式無法載入檔案的內容是陣列或集合。 不過，將整個檔案載入到陣列或集合，會消耗更多超過所需的記憶體。 LINQ 查詢無法使用的可列舉的類別，傳回符合搜尋條件的值，改為查詢的檔案內容。 傳回只有少數的查詢相符的值，會消耗更少的記憶體。  
  
 您可以建立一個類別，實作<xref:System.Collections.Generic.IEnumerable%601>介面，以公開為可列舉的資料來源資料。 類別可實作`IEnumerable(T)`介面則需要另一個類別可實作<xref:System.Collections.Generic.IEnumerator%601>來逐一查看來源資料的介面。 這兩種類別可讓您依序為特定類型傳回資料的項目。  
  
 在本逐步解說中，您將建立一個類別，實作`IEnumerable(Of String)`介面和類別可實作`IEnumerator(Of String)`介面，以讀取一次的文字檔案一行。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a>建立可列舉類別  
  
|若要建立可列舉類別專案|  
|---|  
|1.在 Visual Basic 中，在**檔案**功能表上，指向**新增**，然後按一下 **專案**。<br />2.在 [新增專案] 對話方塊的 [專案類型] 窗格中，確認已選取 [Windows]。 在 [範本] 窗格中，選取 [類別庫]。 在 [名稱] 方塊中，輸入 `StreamReaderEnumerable` 並按一下 [確定]。 新的專案隨即顯示。<br />3.在**方案總管 中**，Class1.vb 檔案上按一下滑鼠右鍵，然後按一下**重新命名**。 將檔案重新命名為 `StreamReaderEnumerable.vb`，然後按 ENTER。 重新命名檔案時，也會將類別重新命名為 `StreamReaderEnumerable`。 此類別會實作 `IEnumerable(Of String)` 介面。<br />4.StreamReaderEnumerable 專案上按一下滑鼠右鍵，指向**新增**，然後按一下 **新項目**。 選取**類別**範本。 在**名稱**方塊中，輸入`StreamReaderEnumerator.vb`按一下**確定**。|  
  
 此專案中的第一個類別的可列舉的類別，而且會實作`IEnumerable(Of String)`介面。 這個泛型介面實作<xref:System.Collections.IEnumerable>介面與這個類別的取用者可以存取做為輸入值保證`String`。  
  
|若要加入程式碼來實作 IEnumerable|  
|---|  
|1.開啟 StreamReaderEnumerable.vb 檔案。<br />2.之後的行上`Public Class StreamReaderEnumerable`中，輸入下列命令，然後按 ENTER。<br />     [!code-vb[VbVbalrIteratorWalkthrough#1](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_1.vb)]<br />     Visual Basic 會自動填入所需的成員類別`IEnumerable(Of String)`介面。<br />3.這個列舉的類別會從文字檔案一行讀取行一次。 將下列程式碼加入至要公開 （expose） 會將檔案路徑，做為輸入參數的公用建構函式的類別。<br />     [!code-vb[VbVbalrIteratorWalkthrough#2](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_2.vb)]<br />4.實作<xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>方法`IEnumerable(Of String)`介面會傳回的新執行個體`StreamReaderEnumerator`類別。 實作`GetEnumerator`方法`IEnumerable`介面可以成為`Private`，因為您不必只成員公開`IEnumerable(Of String)`介面。 Visual Basic 為產生的程式碼取代`GetEnumerator`為下列程式碼的方法。<br />     [!code-vb[VbVbalrIteratorWalkthrough#3](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_3.vb)]|  
  
|若要加入程式碼來實作 IEnumerator|  
|---|  
|1.開啟 StreamReaderEnumerator.vb 檔案。<br />2.之後的行上`Public Class StreamReaderEnumerator`中，輸入下列命令，然後按 ENTER。<br />     [!code-vb[VbVbalrIteratorWalkthrough#4](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_4.vb)]<br />     Visual Basic 會自動填入所需的成員類別`IEnumerator(Of String)`介面。<br />3.列舉值類別會開啟文字檔案，並執行檔案 I/O 以從檔案讀取的行。 將下列程式碼加入至開啟文字檔來讀取和公開的公用建構函式接受檔案路徑，做為輸入參數的類別。<br />     [!code-vb[VbVbalrIteratorWalkthrough#5](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_5.vb)]<br />4.`Current`兩個屬性`IEnumerator(Of String)`和`IEnumerator`介面從文字檔案，以傳回目前的項目`String`。 實作`Current`屬性`IEnumerator`介面可以成為`Private`，因為您不必只成員公開`IEnumerator(Of String)`介面。 Visual Basic 為產生的程式碼取代`Current`為下列程式碼的屬性。<br />     [!code-vb[VbVbalrIteratorWalkthrough#6](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_6.vb)]<br />5.`MoveNext`方法`IEnumerator`介面瀏覽到文字檔案中的下一個項目，並更新所傳回的值`Current`屬性。 如果沒有更多的項目，若要閱讀，`MoveNext`方法會傳回`False`，否則為`MoveNext`方法會傳回`True`。 將下列程式碼加入至 `MoveNext` 方法。<br />     [!code-vb[VbVbalrIteratorWalkthrough#7](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_7.vb)]<br />6.`Reset`方法`IEnumerator`介面會指示以指向文字檔案開頭的迭代器，並且清除目前的項目值。 將下列程式碼加入至 `Reset` 方法。<br />     [!code-vb[VbVbalrIteratorWalkthrough#8](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_8.vb)]<br />7.`Dispose`方法`IEnumerator`介面可確保提供的迭代器終結之前，並釋出所有 unmanaged 的資源。 檔案控制代碼，以供`StreamReader`物件是 unmanaged 的資源，而且必須先關閉然後終結迭代器執行個體。 Visual Basic 為產生的程式碼取代`Dispose`方法取代下列程式碼。<br />     [!code-vb[VbVbalrIteratorWalkthrough#9](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_9.vb)]|  
  
## <a name="using-the-sample-iterator"></a>使用範例迭代器  
 您可以搭配需要實作的物件的控制結構的程式碼中使用的可列舉類別`IEnumerable`，例如`For Next`迴圈或 LINQ 查詢。 下列範例所示`StreamReaderEnumerable`LINQ 查詢中。  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_10.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [控制流程](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [迴圈結構](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [For Each...Next 陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
