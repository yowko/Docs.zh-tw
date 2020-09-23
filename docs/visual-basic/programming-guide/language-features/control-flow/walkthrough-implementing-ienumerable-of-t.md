---
title: 執行 IEnumerable
ms.date: 07/31/2018
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
ms.openlocfilehash: f1f0036c38299f2392f8c8705e67b7bb6b7db068
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058634"
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>逐步解說：在 Visual Basic 中實作 IEnumerable(Of T)

<xref:System.Collections.Generic.IEnumerable%601>介面是由可傳回一次一個專案的一系列值的類別所執行。 一次只傳回一個專案的優點是，您不需要將一組完整的資料載入記憶體中，就能使用它。 您只需要使用足夠的記憶體從資料載入單一專案。 執行介面的類別 `IEnumerable(T)` 可以搭配 `For Each` 迴圈或 LINQ 查詢使用。  
  
 例如，假設應用程式必須讀取大型文字檔，並從符合特定搜尋準則的檔案傳回每一行。 應用程式會使用 LINQ 查詢，從檔案傳回符合指定準則的行。 若要使用 LINQ 查詢來查詢檔案的內容，應用程式可以將檔案的內容載入陣列或集合中。 不過，將整個檔案載入至陣列或集合中的記憶體，會比所需的記憶體多出許多。 LINQ 查詢可以改為使用可列舉類別來查詢檔案內容，只傳回符合搜尋準則的值。 只傳回幾個相符值的查詢會耗用較少的記憶體。  
  
 您可以建立一個類別來執行 <xref:System.Collections.Generic.IEnumerable%601> 介面，以將來源資料公開為可列舉的資料。 您執行介面的類別 `IEnumerable(T)` 需要另一個類別來 <xref:System.Collections.Generic.IEnumerator%601> 執行介面，以逐一查看來源資料。 這兩個類別可讓您以特定類型的順序傳回資料的專案。  
  
 在這個逐步解說中，您將建立一個類別，它會執行 `IEnumerable(Of String)` 介面和一個類別，該類別會 `IEnumerator(Of String)` 執行介面，一次一行讀取文字檔。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a>建立可列舉類別  
  
**建立可列舉類別專案**

1. 在 Visual Basic **的 [檔案** ] 功能表上，指向 [ **新增** ]，然後按一下 [ **專案**]。

1. 在 [新增專案]**** 對話方塊的 [專案類型]**** 窗格中，確認已選取 [Windows]****。 在 [範本]**** 窗格中，選取 [類別庫]****。 在 [名稱]**** 方塊中，輸入 `StreamReaderEnumerable` 並按一下 [確定]****。 新的專案隨即顯示。

1. 在 **方案總管**中，以滑鼠右鍵按一下 Class1 檔案，然後按一下 [ **重新命名**]。 將檔案重新命名為 `StreamReaderEnumerable.vb`，然後按 ENTER。 重新命名檔案時，也會將類別重新命名為 `StreamReaderEnumerable`。 此類別會實作 `IEnumerable(Of String)` 介面。

1. 以滑鼠右鍵按一下 StreamReaderEnumerable 專案，指向 [ **加入**]，然後按一下 [ **新增專案**]。 選取 [ **類別** ] 範本。 在 [名稱]**** 方塊中輸入 `StreamReaderEnumerator.vb`，然後按一下 [確定]****。

 此專案中的第一個類別是可列舉的類別，而且將會執行 `IEnumerable(Of String)` 介面。 這個泛型介面會實 <xref:System.Collections.IEnumerable> 作為介面，並保證這個類別的取用者可以存取輸入的值 `String` 。  
  
**新增程式碼以執行 IEnumerable**

1. 開啟 StreamReaderEnumerable .vb 檔案。

2. 在 [後行] `Public Class StreamReaderEnumerable` 中，輸入下列程式碼，然後按 enter 鍵。

     [!code-vb[VbVbalrIteratorWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#1)]

   Visual Basic 會自動將介面所需的成員填入類別 `IEnumerable(Of String)` 。
  
3. 這個可列舉類別會一次從文字檔讀取一行。 將下列程式碼加入至類別，以公開接受檔案路徑做為輸入參數的公用函式。

     [!code-vb[VbVbalrIteratorWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#2)]

4. 您對介面的 <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> 方法的執行 `IEnumerable(Of String)` 將會傳回類別的新實例 `StreamReaderEnumerator` 。 `GetEnumerator` `IEnumerable` 您可以執行介面的方法 `Private` ，因為您必須只公開介面的成員 `IEnumerable(Of String)` 。 以下列程式碼取代 Visual Basic 為方法產生的程式碼 `GetEnumerator` 。

     [!code-vb[VbVbalrIteratorWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#3)]  
  
**新增程式碼以執行 IEnumerator**

1. 開啟 StreamReaderEnumerator .vb 檔案。

2. 在 [後行] `Public Class StreamReaderEnumerator` 中，輸入下列程式碼，然後按 enter 鍵。

     [!code-vb[VbVbalrIteratorWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#4)]

   Visual Basic 會自動將介面所需的成員填入類別 `IEnumerator(Of String)` 。

3. 列舉值類別會開啟文字檔，並執行檔案 i/o 以讀取檔案中的行。 將下列程式碼加入至類別，以公開公用的函式，該函式會使用檔案路徑做為輸入參數，並開啟文字檔進行讀取。

     [!code-vb[VbVbalrIteratorWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#5)]

4. `Current`和介面的屬性會 `IEnumerator(Of String)` `IEnumerator` 從文字檔傳回目前的專案做為 `String` 。 `Current` `IEnumerator` `Private` 因為您必須只公開介面的成員，所以可以執行介面的屬性 `IEnumerator(Of String)` 。 以下列程式碼取代 Visual Basic 為屬性產生的程式碼 `Current` 。

     [!code-vb[VbVbalrIteratorWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#6)]

5. `MoveNext`介面的方法會 `IEnumerator` 流覽至文字檔中的下一個專案，並更新屬性所傳回的值 `Current` 。 如果沒有其他要讀取的專案，方法會傳回 `MoveNext` `False` ; 否則， `MoveNext` 方法 `True` 會傳回。 將下列程式碼新增至 `MoveNext` 方法。

     [!code-vb[VbVbalrIteratorWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#7)]

6. `Reset`介面的方法會 `IEnumerator` 指示反覆運算器指向文字檔的開頭，並清除目前的專案值。 將下列程式碼新增至 `Reset` 方法。

     [!code-vb[VbVbalrIteratorWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#8)]

7. `Dispose`介面的方法可 `IEnumerator` 保證在反覆運算器終結之前釋放所有非受控資源。 物件所使用的檔案控制代碼 `StreamReader` 是未受管理的資源，而且必須在終結 iterator 實例之前關閉。 以下列程式碼取代 Visual Basic 為方法產生的程式碼 `Dispose` 。

     [!code-vb[VbVbalrIteratorWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#9)]
  
## <a name="using-the-sample-iterator"></a>使用範例反覆運算器

 您可以使用程式碼中的可列舉類別，以及需要執行物件（ `IEnumerable` 例如 `For Next` 迴圈或 LINQ 查詢）的控制結構。 下列範例顯示 `StreamReaderEnumerable` LINQ 查詢中的。  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/Module1.vb#10)]  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的 LINQ 簡介](../linq/introduction-to-linq.md)
- [控制流程](index.md)
- [迴圈結構](loop-structures.md)
- [For Each...Next 陳述式](../../../language-reference/statements/for-each-next-statement.md)
