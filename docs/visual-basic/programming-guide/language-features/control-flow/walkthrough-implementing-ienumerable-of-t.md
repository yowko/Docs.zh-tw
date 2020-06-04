---
title: 執行 IEnumerable
ms.date: 07/31/2018
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
ms.openlocfilehash: 582957c91eac63cf7f72dd2f6c0cf40e627be686
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402027"
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>逐步解說：在 Visual Basic 中實作 IEnumerable(Of T)
<xref:System.Collections.Generic.IEnumerable%601>介面是由類別所實，可以一次傳回一個專案的一連串值。 將資料一次傳回一個專案的優點是，您不需要將一組完整的資料載入記憶體中，就可以使用它。 您只需要使用足夠的記憶體，即可從資料載入單一專案。 執行介面的類別 `IEnumerable(T)` 可以搭配 `For Each` 迴圈或 LINQ 查詢使用。  
  
 例如，假設有一個應用程式必須讀取大型文字檔，並從檔案傳回符合特定搜尋條件的每一行。 應用程式會使用 LINQ 查詢來傳回檔案中符合指定準則的行。 若要使用 LINQ 查詢來查詢檔案的內容，應用程式可以將檔案內容載入陣列或集合中。 不過，將整個檔案載入陣列或集合會耗用比所需更多的記憶體。 LINQ 查詢可以改為使用可列舉的類別來查詢檔案內容，只傳回符合搜尋條件的值。 只傳回幾個相符值的查詢會耗用較少的記憶體。  
  
 您可以建立一個類別來執行 <xref:System.Collections.Generic.IEnumerable%601> 介面，以將來源資料公開為可列舉的資料。 您的類別若 `IEnumerable(T)` 要執行介面，將需要另一個實作為介面的類別， <xref:System.Collections.Generic.IEnumerator%601> 以反復處理來源資料。 這兩個類別可讓您以特定類型順序傳回資料的專案。  
  
 在此逐步解說中，您將建立一個執行介面的類別，以及一個執行介面的類別，以便一 `IEnumerable(Of String)` `IEnumerator(Of String)` 次一行讀取文字檔。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a>建立可列舉類別  
  
**建立可列舉的類別專案**

1. **在 Visual Basic 的 [檔案**] 功能表上，指向 [**新增**]，然後按一下 [**專案**]。

1. 在 [新增專案]**** 對話方塊的 [專案類型]**** 窗格中，確認已選取 [Windows]****。 在 [範本]**** 窗格中，選取 [類別庫]****。 在 [名稱]**** 方塊中，輸入 `StreamReaderEnumerable` 並按一下 [確定]****。 隨即顯示新專案。

1. 在**方案總管**中，以滑鼠右鍵按一下 [Class1] 檔案，然後按一下 [**重新命名**]。 將檔案重新命名為 `StreamReaderEnumerable.vb`，然後按 ENTER。 重新命名檔案時，也會將類別重新命名為 `StreamReaderEnumerable`。 此類別會實作 `IEnumerable(Of String)` 介面。

1. 以滑鼠右鍵按一下 [StreamReaderEnumerable] 專案，指向 [**加入**]，然後按一下 [**新增專案**]。 選取 [**類別**] 範本。 在 [名稱]**** 方塊中輸入 `StreamReaderEnumerator.vb`，然後按一下 [確定]****。

 這個專案中的第一個類別是可列舉的類別，並會執行 `IEnumerable(Of String)` 介面。 這個泛型介面會執行 <xref:System.Collections.IEnumerable> 介面，並保證這個類別的取用者可以存取輸入為的值 `String` 。  
  
**新增程式碼以執行 IEnumerable**

1. 開啟 [StreamReaderEnumerable] 檔案。

2. 在後面的一行 `Public Class StreamReaderEnumerable` 中，輸入下列程式碼，然後按 enter 鍵。

     [!code-vb[VbVbalrIteratorWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#1)]

   Visual Basic 會使用介面所需的成員，自動填入類別 `IEnumerable(Of String)` 。
  
3. 這個可列舉的類別會一次從文字檔讀取一行的程式程式碼。 將下列程式碼新增至類別，以公開公用的函式，以接受檔案路徑做為輸入參數。

     [!code-vb[VbVbalrIteratorWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#2)]

4. 介面的方法執行 <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> `IEnumerable(Of String)` 將會傳回類別的新實例 `StreamReaderEnumerator` 。 可以執行介面的 `GetEnumerator` 方法 `IEnumerable` `Private` ，因為您必須只公開介面的成員 `IEnumerable(Of String)` 。 使用下列程式碼取代為方法所產生的程式碼 Visual Basic `GetEnumerator` 。

     [!code-vb[VbVbalrIteratorWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#3)]  
  
**新增程式碼以執行 IEnumerator**

1. 開啟 [StreamReaderEnumerator] 檔案。

2. 在後面的一行 `Public Class StreamReaderEnumerator` 中，輸入下列程式碼，然後按 enter 鍵。

     [!code-vb[VbVbalrIteratorWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#4)]

   Visual Basic 會使用介面所需的成員，自動填入類別 `IEnumerator(Of String)` 。

3. 列舉值類別會開啟文字檔，並執行檔案 i/o 以讀取檔案中的行。 將下列程式碼新增至類別，以公開公用的函式，以使用檔案路徑做為輸入參數，並開啟文字檔進行讀取。

     [!code-vb[VbVbalrIteratorWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#5)]

4. `Current`和介面的屬性會 `IEnumerator(Of String)` `IEnumerator` 從文字檔傳回目前的專案做為 `String` 。 可以執行介面的 `Current` 屬性 `IEnumerator` `Private` ，因為您必須只公開介面的成員 `IEnumerator(Of String)` 。 使用下列程式碼取代為屬性所產生的程式碼 Visual Basic `Current` 。

     [!code-vb[VbVbalrIteratorWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#6)]

5. `MoveNext`介面的方法會 `IEnumerator` 導覽至文字檔中的下一個專案，並更新屬性所傳回的值 `Current` 。 如果沒有其他要讀取的專案，方法會傳回， `MoveNext` `False` 否則方法會傳回 `MoveNext` `True` 。 將下列程式碼新增至 `MoveNext` 方法。

     [!code-vb[VbVbalrIteratorWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#7)]

6. `Reset`介面的方法會 `IEnumerator` 指示反覆運算器指向文字檔的開頭，並清除目前的專案值。 將下列程式碼新增至 `Reset` 方法。

     [!code-vb[VbVbalrIteratorWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#8)]

7. `Dispose`介面的方法可 `IEnumerator` 保證在反覆運算器終結之前釋放所有非受控資源。 物件所使用的檔案控制代碼 `StreamReader` 是非受控資源，必須在反覆運算器實例終結之前關閉。 使用下列程式碼取代為方法所產生的程式碼 Visual Basic `Dispose` 。

     [!code-vb[VbVbalrIteratorWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#9)]
  
## <a name="using-the-sample-iterator"></a>使用範例反覆運算器

 您可以在程式碼中使用可列舉的類別，以及需要可執行之物件的控制項結構 `IEnumerable` ，例如 `For Next` 迴圈或 LINQ 查詢。 下列範例會顯示 `StreamReaderEnumerable` LINQ 查詢中的。  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/Module1.vb#10)]  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的 LINQ 簡介](../linq/introduction-to-linq.md)
- [控制流程](index.md)
- [迴圈結構](loop-structures.md)
- [For Each...Next 陳述式](../../../language-reference/statements/for-each-next-statement.md)
