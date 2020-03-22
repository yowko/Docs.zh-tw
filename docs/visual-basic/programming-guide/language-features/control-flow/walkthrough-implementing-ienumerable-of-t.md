---
title: 實現 IE500
ms.date: 07/31/2018
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
ms.openlocfilehash: 4151a680050f234d450d8de5e67a767c54e8df68
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266907"
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>逐步解說：在 Visual Basic 中實作 IEnumerable(Of T)
介面<xref:System.Collections.Generic.IEnumerable%601>由類實現，這些類可以一次返回一個項的值序列。 一次返回一個專案的資料的優點是，您不必將完整的資料集載入到記憶體中才能使用它。 您只需要使用足夠的記憶體從資料載入單個項。 實現介面的`IEnumerable(T)`類可用於`For Each`迴圈或 LINQ 查詢。  
  
 例如，考慮一個應用程式，該應用程式必須讀取大型文字檔，並從檔返回與特定搜尋條件匹配的每行。 應用程式使用 LINQ 查詢從檔返回與指定條件匹配的行。 要使用 LINQ 查詢查詢檔的內容，應用程式可以將檔的內容載入到陣列或集合中。 但是，將整個檔載入到陣列或集合中會消耗的記憶體遠遠多於所需的記憶體。 LINQ 查詢可以使用枚舉類查詢檔內容，僅返回與搜尋條件匹配的值。 僅返回幾個匹配值的查詢消耗的記憶體要少得多。  
  
 您可以創建實現介面的類，<xref:System.Collections.Generic.IEnumerable%601>以將來源資料公開為枚舉資料。 實現介面的`IEnumerable(T)`類將需要實現<xref:System.Collections.Generic.IEnumerator%601>介面的另一個類來遍經來源資料反覆運算。 這兩個類使您能夠按順序將資料項目作為特定類型返回。  
  
 在本演練中，您將創建實現介面的`IEnumerable(Of String)`類和實現`IEnumerator(Of String)`介面一次讀取一行文字檔的類。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a>創建可枚舉類  
  
**創建枚舉類專案**

1. 在"視覺化基本"中，在 **"檔"** 功能表上，指向 **"新建"，** 然後按一下"**專案**"。

1. 在 [新增專案]**** 對話方塊的 [專案類型]**** 窗格中，確認已選取 [Windows]****。 在 [範本]**** 窗格中，選取 [類別庫]****。 在 [名稱]**** 方塊中，輸入 `StreamReaderEnumerable` 並按一下 [確定]****。 將顯示新專案。

1. 在**解決方案資源管理器**中，按右鍵 Class1.vb 檔，然後按一下 **"重命名**"。 將檔案重新命名為 `StreamReaderEnumerable.vb`，然後按 ENTER。 重新命名檔案時，也會將類別重新命名為 `StreamReaderEnumerable`。 此類別會實作 `IEnumerable(Of String)` 介面。

1. 按右鍵 StreamReaderE"專案，指向 **"添加**"，然後按一下 **"新專案**"。 選擇**類**範本。 在 [名稱]**** 方塊中輸入 `StreamReaderEnumerator.vb`，然後按一下 [確定]****。

 此專案中的第一個類是枚舉類，將實現介面`IEnumerable(Of String)`。 此泛型介面實現<xref:System.Collections.IEnumerable>介面，並保證此類的消費者可以便捷鍵入為`String`的值。  
  
**添加代碼以實現 IE500**

1. 打開流閱讀器數位.vb 檔。

2. 在`Public Class StreamReaderEnumerable`之後的行上鍵入以下內容，然後按 ENTER。

     [!code-vb[VbVbalrIteratorWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#1)]

   Visual Basic 使用`IEnumerable(Of String)`介面所需的成員自動填滿類。
  
3. 此枚舉類將一次從文字檔中讀取一行。 將以下代碼添加到類中，以公開將檔路徑作為輸入參數的公共建構函式。

     [!code-vb[VbVbalrIteratorWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#2)]

4. 介面方法的實現將返回`StreamReaderEnumerator`類的新實例。 <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> `IEnumerable(Of String)` `GetEnumerator`可以實現`IEnumerable``Private`介面的方法，因為您必須只公開`IEnumerable(Of String)`介面的成員。 將 Visual Basic 為`GetEnumerator`方法生成的代碼替換為以下代碼。

     [!code-vb[VbVbalrIteratorWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#3)]  
  
**添加代碼以實現 IEnumerator**

1. 打開流閱讀器數位器.vb 檔。

2. 在`Public Class StreamReaderEnumerator`之後的行上鍵入以下內容，然後按 ENTER。

     [!code-vb[VbVbalrIteratorWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#4)]

   Visual Basic 使用`IEnumerator(Of String)`介面所需的成員自動填滿類。

3. 枚舉器類打開文字檔並執行檔 I/O 以從檔中讀取行。 將以下代碼添加到類中，以公開將檔路徑作為輸入參數的公共建構函式，並打開文字檔進行讀取。

     [!code-vb[VbVbalrIteratorWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#5)]

4. `Current` `IEnumerator`和 介面的屬性將當前項從文字檔返回為`String` `IEnumerator(Of String)` `Current`可以實現`IEnumerator``Private`介面的屬性，因為您必須只公開`IEnumerator(Of String)`介面的成員。 將 Visual Basic 為`Current`屬性生成的代碼替換為以下代碼。

     [!code-vb[VbVbalrIteratorWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#6)]

5. 介面的方法導航到文字檔中的下一個項，並更新`Current`屬性返回的值。 `MoveNext` `IEnumerator` 如果沒有要讀取的項，`MoveNext`則方法將返回`False`;否則該方法`MoveNext`將返回`True`。 將下列程式碼新增至 `MoveNext` 方法。

     [!code-vb[VbVbalrIteratorWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#7)]

6. `IEnumerator`介面`Reset`的方法指示反覆運算器指向文字檔的開頭並清除當前項值。 將下列程式碼新增至 `Reset` 方法。

     [!code-vb[VbVbalrIteratorWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#8)]

7. `IEnumerator`介面`Dispose`的方法保證在銷毀反覆運算器之前釋放所有非託管資源。 `StreamReader`物件使用的檔案控制代碼是非託管資源，必須在銷毀反覆運算器實例之前關閉。 將為`Dispose`該方法生成的 Visual Basic 的代碼替換為以下代碼。

     [!code-vb[VbVbalrIteratorWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#9)]
  
## <a name="using-the-sample-iterator"></a>使用樣品反覆運算器

 可以在代碼中使用枚舉類以及需要實現`IEnumerable`的物件（如`For Next`迴圈或 LINQ 查詢）的控制項結構。 下面的示例顯示了 LINQ 查詢`StreamReaderEnumerable`中的 。  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/Module1.vb#10)]  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [控制流程](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [迴圈結構](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [For Each...Next 陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
