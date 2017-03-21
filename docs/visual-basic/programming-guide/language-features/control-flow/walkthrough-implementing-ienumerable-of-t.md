---
title: "在 Visual Basic 中實作 IEnumerable |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures, optimizing performance
- control flow
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
caps.latest.revision: 15
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 68c37c46cbceb1056d50972cdc58ddb7c7577447
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>逐步解說：在 Visual Basic 中實作 IEnumerable(Of T)
<xref:System.Collections.Generic.IEnumerable%601>可以一次傳回一個項目值序列的類別會實作介面。</xref:System.Collections.Generic.IEnumerable%601> 傳回的資料一次一個項目是您不需要完整的資料載入至記憶體，以使用它的優點。 您只需要使用足夠的記憶體載入資料的單一項目。 類別實作`IEnumerable(T)`介面可以搭配`For Each`迴圈或 LINQ 查詢。  
  
 例如，請考慮必須讀取大型文字檔，並傳回符合特定搜尋準則之檔案中的每一行的應用程式。 應用程式會使用 LINQ 查詢，傳回符合指定的條件的檔案的行。 若要使用 LINQ 查詢來查詢檔案的內容，應用程式無法載入檔案的內容至陣列或集合。 不過，將整個檔案載入陣列或集合，會消耗更多的記憶體超過所需。 LINQ 查詢可以使用 enumerable 類別，傳回符合搜尋準則的值，改為查詢檔案內容。 傳回只有少數的查詢相符的值，會消耗更少的記憶體。  
  
 您可以建立一個類別，實作<xref:System.Collections.Generic.IEnumerable%601>介面，以公開可列舉的資料來源資料。</xref:System.Collections.Generic.IEnumerable%601> 您的類別實作`IEnumerable(T)`介面則需要另一個類別可實作<xref:System.Collections.Generic.IEnumerator%601>來逐一查看來源資料的介面。</xref:System.Collections.Generic.IEnumerator%601> 這兩種類別可讓您依序為特定型別傳回資料的項目。  
  
 在本逐步解說中，您將建立一個類別，實作`IEnumerable(Of String)`介面和類別以實作`IEnumerator(Of String)`介面，以讀取一次的文字檔案的一行。  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## <a name="creating-the-enumerable-class"></a>建立列舉類別  
  
|若要建立 enumerable 類別專案|  
|---|  
|1.在[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]上**檔案**功能表上，指向**新增**然後按一下 **專案**。<br />2.在**新的專案**對話方塊中，於**專案類型** 窗格中，請確定**Windows**已選取。 選取**類別庫**中**範本**窗格。 在**名稱**方塊中，輸入`StreamReaderEnumerable`，然後按一下 **確定**。 會顯示新的專案。<br />3.在**方案總管 中**，Class1.vb 檔案上按一下滑鼠右鍵，然後按一下**重新命名**。 若要將檔案重新命名`StreamReaderEnumerable.vb`按下 ENTER。 重新命名檔案也會重新命名類別來`StreamReaderEnumerable`。 這個類別會實作`IEnumerable(Of String)`介面。<br />4.StreamReaderEnumerable 專案上按一下滑鼠右鍵，指向**新增**，然後按一下 **新項目**。 選取**類別**範本。 在**名稱**方塊中，輸入`StreamReaderEnumerator.vb`按一下**確定**。|  
  
 此專案中的第一個類別 enumerable 類別，而且會實作`IEnumerable(Of String)`介面。 這個泛型介面會實作<xref:System.Collections.IEnumerable>介面，以及保證這個類別的取用者可以存取值的型別為`String`。</xref:System.Collections.IEnumerable>  
  
|若要加入程式碼以實作 IEnumerable|  
|---|  
|1.開啟 StreamReaderEnumerable.vb 檔案。<br />2.之後的字行上`Public Class StreamReaderEnumerable`，輸入下列命令，然後按下 ENTER。<br />     [!code-vb[VbVbalrIteratorWalkthrough #&1;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_1.vb)]<br />     [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]會自動填入的類別與成員所需的`IEnumerable(Of String)`介面。<br />3.此 enumerable 類別會從文字檔案一行讀取行一次。 將下列程式碼加入至要公開 （expose） 會將檔案路徑，做為輸入參數的公用建構函式的類別。<br />     [!code-vb[VbVbalrIteratorWalkthrough #&2;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_2.vb)]<br />4.實作<xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>方法`IEnumerable(Of String)`介面會傳回的新執行個體`StreamReaderEnumerator`類別</xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> 實作`GetEnumerator`方法`IEnumerable`介面可以成為`Private`，因為您必須公開 （expose） 只有`IEnumerable(Of String)`介面。 將程式碼，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]產生`GetEnumerator`為下列程式碼的方法。<br />     [!code-vb[VbVbalrIteratorWalkthrough #&3;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_3.vb)]|  
  
|若要加入程式碼以實作 IEnumerator|  
|---|  
|1.開啟 StreamReaderEnumerator.vb 檔案。<br />2.之後的字行上`Public Class StreamReaderEnumerator`，輸入下列命令，然後按下 ENTER。<br />     [!code-vb[VbVbalrIteratorWalkthrough #&4;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_4.vb)]<br />     [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]會自動填入的類別與成員所需的`IEnumerator(Of String)`介面。<br />3.列舉值類別會開啟文字檔案，並執行檔案 I/O 來讀取檔案的程式碼行。 將下列程式碼加入至類別來公開公用建構函式做為輸入參數的檔案路徑及開啟文字檔來讀取。<br />     [!code-vb[VbVbalrIteratorWalkthrough #&5;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_5.vb)]<br />4.`Current`屬性同時`IEnumerator(Of String)`和`IEnumerator`介面傳回從文字檔案做為目前的項目`String`。 實作`Current`屬性`IEnumerator`介面可以成為`Private`，因為您必須公開 （expose） 只有`IEnumerator(Of String)`介面。 將程式碼，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]產生`Current`為下列程式碼的屬性。<br />     [!code-vb[VbVbalrIteratorWalkthrough #&6;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_6.vb)]<br />5.`MoveNext`方法`IEnumerator`介面巡覽至文字檔案中的下一個項目，並且更新所傳回的值`Current`屬性。 如果沒有更多的項目讀取，`MoveNext`方法會傳回`False`，否則為`MoveNext`方法會傳回`True`。 將下列程式碼加入至 `MoveNext` 方法。<br />     [!code-vb[VbVbalrIteratorWalkthrough #&7;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_7.vb)]<br />6.`Reset`方法`IEnumerator`介面會指示指向文字檔案開頭的迭代器，並且清除目前的項目值。 將下列程式碼加入至 `Reset` 方法。<br />     [!code-vb[VbVbalrIteratorWalkthrough #&8;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_8.vb)]<br />7.`Dispose`方法`IEnumerator`介面可保證迭代器被終結之前，就會釋放所有的 unmanaged 的資源。 檔案控制代碼，可由`StreamReader`物件是 unmanaged 的資源，而且必須先關閉終結迭代器執行個體。 將程式碼，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]產生`Dispose`為下列程式碼的方法。<br />     [!code-vb[VbVbalrIteratorWalkthrough #&9;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_9.vb)]|  
  
## <a name="using-the-sample-iterator"></a>使用範例迭代器  
 您可以使用 enumerable 類別，以及需要實作的物件的控制結構的程式碼中`IEnumerable`，例如`For Next`迴圈或 LINQ 查詢。 下列範例所示`StreamReaderEnumerable`LINQ 查詢中。  
  
 [!code-vb[VbVbalrIteratorWalkthrough #&10;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_10.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [控制流程](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [迴圈結構](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [For Each...Next 陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)

