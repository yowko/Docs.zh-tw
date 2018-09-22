---
title: 在 Visual Basic 中實作 IEnumerable
ms.date: 07/31/2018
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
ms.openlocfilehash: be2eefdc52d38df3071d457b7a71dbac6eaa2657
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2018
ms.locfileid: "46580131"
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>逐步解說：在 Visual Basic 中實作 IEnumerable(Of T)
<xref:System.Collections.Generic.IEnumerable%601>可以一次傳回的值的一個項目序列的類別會實作介面。 傳回的資料一次的一個項目是您沒有將一組完整的資料載入記憶體，才能使用它的優點。 您只需要使用足夠的記憶體載入資料的單一項目。 類別實作`IEnumerable(T)`介面可與`For Each`迴圈或 LINQ 查詢。  
  
 例如，假設應用程式必須讀取大型文字檔，並傳回符合特定搜尋條件的檔案中的每一行。 應用程式會使用 LINQ 查詢，傳回符合指定的準則的檔案的行。 若要使用 LINQ 查詢來查詢檔案的內容，應用程式無法載入檔案的內容是陣列或集合。 不過，將整個檔案載入陣列或集合會耗用超過所需的更多記憶體。 LINQ 查詢可以使用 enumerable 類別，傳回符合搜尋條件的值，改為查詢的檔案內容。 傳回只有少數的查詢比對值會耗用更少的記憶體。  
  
 您可以建立可實作類別<xref:System.Collections.Generic.IEnumerable%601>介面公開為可列舉的資料來源資料。 您的類別可實作`IEnumerable(T)`介面需要實作的另一個類別<xref:System.Collections.Generic.IEnumerator%601>來逐一查看來源資料的介面。 這兩個類別可讓您依序為特定類型傳回的資料的項目。  
  
 本逐步解說中，您將建立一個類別，實作`IEnumerable(Of String)`介面和類別可實作`IEnumerator(Of String)`介面來讀取一次的文字檔案的一行。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a>建立列舉類別  
  
**建立 enumerable 類別專案**

1.  在 Visual Basic 中，在**檔案**功能表上，指向**新增**，然後按一下 **專案**。

1.  在 [新增專案] 對話方塊的 [專案類型] 窗格中，確認已選取 [Windows]。 在 [範本] 窗格中，選取 [類別庫]。 在 [名稱] 方塊中，輸入 `StreamReaderEnumerable` 並按一下 [確定]。 新的專案會顯示。

1.  在 **方案總管**，以滑鼠右鍵按一下 Class1.vb 檔案，然後按一下**重新命名**。 將檔案重新命名為 `StreamReaderEnumerable.vb`，然後按 ENTER。 重新命名檔案時，也會將類別重新命名為 `StreamReaderEnumerable`。 此類別會實作 `IEnumerable(Of String)` 介面。

1.  StreamReaderEnumerable 專案上按一下滑鼠右鍵，指向**新增**，然後按一下**新項目**。 選取 **類別**範本。 在 **名稱**方塊中，輸入`StreamReaderEnumerator.vb`然後按一下**確定**。

 在此專案中的第一個類別是 enumerable 類別，並且會實作`IEnumerable(Of String)`介面。 這個泛型介面實作<xref:System.Collections.IEnumerable>介面和這個類別的取用者可以存取做為輸入值的保證`String`。  
  
**加入程式碼以實作 IEnumerable**

1. 開啟 StreamReaderEnumerable.vb 檔案。

2. 之後的行上`Public Class StreamReaderEnumerable`，輸入下列命令並按 ENTER。

   [!code-vb[VbVbalrIteratorWalkthrough#1](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_1.vb)]

   Visual Basic 會自動填入所需的成員類別`IEnumerable(Of String)`介面。
  
3. 這個可列舉的類別會一次讀取行從文字檔案一列。 將下列程式碼加入至類別公開的公用建構函式做為輸入參數的檔案路徑。

   [!code-vb[VbVbalrIteratorWalkthrough#2](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_2.vb)]

4. 您實作<xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>方法`IEnumerable(Of String)`介面會傳回的新執行個體`StreamReaderEnumerator`類別。 實作`GetEnumerator`方法`IEnumerable`介面可以成為`Private`，因為您不必只成員公開`IEnumerable(Of String)`介面。 取代為所產生的 Visual Basic 程式碼`GetEnumerator`為下列程式碼的方法。

   [!code-vb[VbVbalrIteratorWalkthrough#3](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_3.vb)]  
  
**加入程式碼以實作 IEnumerator**

1. 開啟 StreamReaderEnumerator.vb 檔案。

2. 之後的行上`Public Class StreamReaderEnumerator`，輸入下列命令並按 ENTER。

   [!code-vb[VbVbalrIteratorWalkthrough#4](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_4.vb)]

   Visual Basic 會自動填入所需的成員類別`IEnumerator(Of String)`介面。

3. 列舉值類別開啟文字檔，並執行檔案 I/O，若要從檔案讀取的行。 將下列程式碼加入至類別公開的公用建構函式做為輸入參數的檔案路徑，並開啟文字檔案進行讀取。

   [!code-vb[VbVbalrIteratorWalkthrough#5](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_5.vb)]

4. `Current`屬性兩者`IEnumerator(Of String)`並`IEnumerator`介面會傳回目前的項目從文字檔`String`。 實作`Current`的屬性`IEnumerator`介面可以成為`Private`，因為您不必只成員公開`IEnumerator(Of String)`介面。 取代為所產生的 Visual Basic 程式碼`Current`為下列程式碼的屬性。

   [!code-vb[VbVbalrIteratorWalkthrough#6](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_6.vb)]

5. `MoveNext`方法`IEnumerator`介面瀏覽到文字檔中的下一個項目，並更新所傳回的值`Current`屬性。 若要閱讀，沒有其他項目是否`MoveNext`方法會傳回`False`; 否則為`MoveNext`方法會傳回`True`。 將下列程式碼加入至 `MoveNext` 方法。

   [!code-vb[VbVbalrIteratorWalkthrough#7](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_7.vb)]

6. `Reset`方法的`IEnumerator`介面會指示迭代器，指向 文字檔的開始，並清除目前的項目值。 將下列程式碼加入至 `Reset` 方法。

   [!code-vb[VbVbalrIteratorWalkthrough#8](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_8.vb)]

7. `Dispose`方法的`IEnumerator`介面可確保提供迭代器終結之前，就會釋放所有的 unmanaged 的資源。 檔案控制代碼，以供`StreamReader`物件是 unmanaged 的資源，而且必須先關閉終結迭代器執行個體。 取代為所產生的 Visual Basic 程式碼`Dispose`為下列程式碼的方法。

   [!code-vb[VbVbalrIteratorWalkthrough#9](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_9.vb)] 
  
## <a name="using-the-sample-iterator"></a>使用範例迭代器

 您可以使用 enumerable 類別，在您的程式碼，以及需要實作的物件的控制結構`IEnumerable`，例如`For Next`迴圈或 LINQ 查詢。 下列範例所示`StreamReaderEnumerable`LINQ 查詢中。  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_10.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [控制流程](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [迴圈結構](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [For Each...Next 陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
