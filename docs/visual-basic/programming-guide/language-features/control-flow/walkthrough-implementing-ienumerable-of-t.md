---
title: 執行 IEnumerable
ms.date: 07/31/2018
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
ms.openlocfilehash: f40fcf7e0724addc478b261dcd36d09e1d8a751a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333692"
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>逐步解說：在 Visual Basic 中實作 IEnumerable(Of T)
<xref:System.Collections.Generic.IEnumerable%601> 介面是由類別所實，可以一次傳回一個專案的一連串值。 將資料一次傳回一個專案的優點是，您不需要將一組完整的資料載入記憶體中，就可以使用它。 您只需要使用足夠的記憶體，即可從資料載入單一專案。 執行 `IEnumerable(T)` 介面的類別可以搭配 `For Each` 迴圈或 LINQ 查詢使用。  
  
 例如，假設有一個應用程式必須讀取大型文字檔，並從檔案傳回符合特定搜尋條件的每一行。 應用程式會使用 LINQ 查詢來傳回檔案中符合指定準則的行。 若要使用 LINQ 查詢來查詢檔案的內容，應用程式可以將檔案內容載入陣列或集合中。 不過，將整個檔案載入陣列或集合會耗用比所需更多的記憶體。 LINQ 查詢可以改為使用可列舉的類別來查詢檔案內容，只傳回符合搜尋條件的值。 只傳回幾個相符值的查詢會耗用較少的記憶體。  
  
 您可以建立一個執行 <xref:System.Collections.Generic.IEnumerable%601> 介面的類別，將來源資料公開為可列舉的資料。 您的類別若要執行 `IEnumerable(T)` 介面，將需要另一個實作為 <xref:System.Collections.Generic.IEnumerator%601> 介面的類別，以反復查看來源資料。 這兩個類別可讓您以特定類型順序傳回資料的專案。  
  
 在此逐步解說中，您將建立一個類別，它會執行 `IEnumerable(Of String)` 介面，以及一個會實作為 `IEnumerator(Of String)` 介面的類別，以便一次一行讀取文字檔。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a>建立可列舉類別  
  
**建立可列舉的類別專案**

1. **在 Visual Basic 的 [檔案**] 功能表上，指向 [**新增**]，然後按一下 [**專案**]。

1. 在 [新增專案] 對話方塊的 [專案類型] 窗格中，確認已選取 [Windows]。 在 [範本] 窗格中，選取 [類別庫]。 在 [名稱] 方塊中，輸入 `StreamReaderEnumerable` 並按一下 [確定]。 隨即顯示新專案。

1. 在**方案總管**中，以滑鼠右鍵按一下 [Class1] 檔案，然後按一下 [**重新命名**]。 將檔案重新命名為 `StreamReaderEnumerable.vb`，然後按 ENTER。 重新命名檔案時，也會將類別重新命名為 `StreamReaderEnumerable`。 此類別會實作 `IEnumerable(Of String)` 介面。

1. 以滑鼠右鍵按一下 [StreamReaderEnumerable] 專案，指向 [**加入**]，然後按一下 [**新增專案**]。 選取 [**類別**] 範本。 在 [**名稱**] 方塊中，輸入 `StreamReaderEnumerator.vb`，然後按一下 **[確定]** 。

 這個專案中的第一個類別是可列舉的類別，並將會執行 `IEnumerable(Of String)` 介面。 這個泛型介面會執行 <xref:System.Collections.IEnumerable> 介面，並保證此類別的取用者可以存取輸入為 `String`的值。  
  
**新增程式碼以執行 IEnumerable**

1. 開啟 [StreamReaderEnumerable] 檔案。

2. 在 `Public Class StreamReaderEnumerable`之後的那一行輸入下列程式碼，然後按 ENTER 鍵。

     [!code-vb[VbVbalrIteratorWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#1)]

   Visual Basic 會使用 `IEnumerable(Of String)` 介面所需的成員，自動填入類別。
  
3. 這個可列舉的類別會一次從文字檔讀取一行的程式程式碼。 將下列程式碼新增至類別，以公開公用的函式，以接受檔案路徑做為輸入參數。

     [!code-vb[VbVbalrIteratorWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#2)]

4. 您的 `IEnumerable(Of String)` 介面之 <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> 方法的執行，將會傳回 `StreamReaderEnumerator` 類別的新實例。 `IEnumerable` 介面的 `GetEnumerator` 方法可以 `Private`執行，因為您必須只公開 `IEnumerable(Of String)` 介面的成員。 使用下列程式碼取代為 `GetEnumerator` 方法所產生 Visual Basic 程式碼。

     [!code-vb[VbVbalrIteratorWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#3)]  
  
**新增程式碼以執行 IEnumerator**

1. 開啟 [StreamReaderEnumerator] 檔案。

2. 在 `Public Class StreamReaderEnumerator`之後的那一行輸入下列程式碼，然後按 ENTER 鍵。

     [!code-vb[VbVbalrIteratorWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#4)]

   Visual Basic 會使用 `IEnumerator(Of String)` 介面所需的成員，自動填入類別。

3. 列舉值類別會開啟文字檔，並執行檔案 i/o 以讀取檔案中的行。 將下列程式碼新增至類別，以公開公用的函式，以使用檔案路徑做為輸入參數，並開啟文字檔進行讀取。

     [!code-vb[VbVbalrIteratorWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#5)]

4. `IEnumerator(Of String)` 和 `IEnumerator` 介面的 `Current` 屬性都會以 `String`的形式，從文字檔傳回目前的專案。 `IEnumerator` 介面的 `Current` 屬性的執行可以 `Private`進行，因為您必須只公開 `IEnumerator(Of String)` 介面的成員。 使用下列程式碼，將 Visual Basic 為 `Current` 屬性產生的程式碼加以取代。

     [!code-vb[VbVbalrIteratorWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#6)]

5. `IEnumerator` 介面的 `MoveNext` 方法會導覽至文字檔中的下一個專案，並更新 `Current` 屬性所傳回的值。 如果沒有其他要讀取的專案，`MoveNext` 方法會傳回 `False`;否則，`MoveNext` 方法會傳回 `True`。 將下列程式碼加入至 `MoveNext` 方法。

     [!code-vb[VbVbalrIteratorWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#7)]

6. `IEnumerator` 介面的 `Reset` 方法會指示反覆運算器指向文字檔的開頭，並清除目前的專案值。 將下列程式碼加入至 `Reset` 方法。

     [!code-vb[VbVbalrIteratorWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#8)]

7. `IEnumerator` 介面的 `Dispose` 方法可確保在反覆運算器終結之前釋放所有非受控資源。 `StreamReader` 物件所使用的檔案控制代碼是非受控資源，必須在反覆運算器實例終結之前關閉。 使用下列程式碼取代為 `Dispose` 方法所產生的 Visual Basic 程式碼。

     [!code-vb[VbVbalrIteratorWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#9)] 
  
## <a name="using-the-sample-iterator"></a>使用範例反覆運算器

 您可以在程式碼中使用可列舉的類別，以及需要可執行 `IEnumerable`之物件的控制項結構，例如 `For Next` 迴圈或 LINQ 查詢。 下列範例會顯示 LINQ 查詢中的 `StreamReaderEnumerable`。  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/Module1.vb#10)]  
  
## <a name="see-also"></a>請參閱

- [Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [控制流程](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [迴圈結構](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [For Each...Next 陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
