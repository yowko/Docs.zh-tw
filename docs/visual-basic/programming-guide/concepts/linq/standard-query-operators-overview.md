---
title: 標準查詢運算子概觀 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 302bd39e-2ec1-495b-94bf-37d370d6f05f
ms.openlocfilehash: 27b144ae75054dbdc535b6ad894e4a5a0b8529e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653568"
---
# <a name="standard-query-operators-overview-visual-basic"></a>標準查詢運算子概觀 (Visual Basic)
「標準查詢運算子」是形成 LINQ 模式的方法。 這些方法大多會在序列上運作，而序列是指其類型會實作 <xref:System.Collections.Generic.IEnumerable%601> 介面或 <xref:System.Linq.IQueryable%601> 介面的物件。 標準查詢運算子所提供的查詢功能包括篩選、投影、彙總、排序等等。  
  
 有兩組 LINQ 標準查詢運算子，一個運作於類型 <xref:System.Collections.Generic.IEnumerable%601> 的物件，另一個則運作於類型 <xref:System.Linq.IQueryable%601> 的物件。 構成每個集合的方法分別是 <xref:System.Linq.Enumerable> 和 <xref:System.Linq.Queryable> 類別的靜態成員。 它們定義為其所運作的類型的「擴充方法」。 這表示可以使用靜態方法語法或執行個體方法語法來呼叫它們。  
  
 此外，數個標準查詢運算子方法也會根據 <xref:System.Collections.Generic.IEnumerable%601> 或 <xref:System.Linq.IQueryable%601> 之類型以外的類型運作。 <xref:System.Linq.Enumerable> 類型定義同時在 <xref:System.Collections.IEnumerable> 類型的物件上運作的兩個這類方法。 <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> 和 <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29> 這些方法可讓您查詢 LINQ 模式中的非參數化或非泛型集合。 建立物件的強類型集合即可進行這項作業。 <xref:System.Linq.Queryable> 類別定義在 <xref:System.Linq.Queryable> 類型的物件上運作的兩個類似方法 <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> 和 <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>。  
  
 根據傳回單一值還是一系列的值，標準查詢運算子的執行時機會不同。 這些傳回單一值的方法 (例如，<xref:System.Linq.Enumerable.Average%2A> 和 <xref:System.Linq.Enumerable.Sum%2A>) 就會立即執行。 傳回序列的方法會延後執行查詢，並傳回可列舉的物件。  
  
 如果是運作於記憶體內部集合的方法，即擴充 <xref:System.Collections.Generic.IEnumerable%601> 的方法，則傳回的可列舉物件會擷取已傳遞給方法的引數。 列舉該物件時，會採用查詢運算子的邏輯，並傳回查詢結果。  
  
 相反地，擴充 <xref:System.Linq.IQueryable%601> 的方法不會實作任何查詢行為，但會建置代表要執行查詢的運算式樹狀結構。 查詢處理是由來源 <xref:System.Linq.IQueryable%601> 物件所處理。  
  
 在一個查詢中，可以將查詢方法呼叫鏈結在一起，這樣會讓查詢變得更為複雜。  
  
 下列程式碼範例示範如何使用標準查詢運算子來取得序列的資訊。  
  
```vb  
Dim sentence = "the quick brown fox jumps over the lazy dog"  
' Split the string into individual words to create a collection.  
Dim words = sentence.Split(" "c)  
  
Dim query = From word In words   
            Group word.ToUpper() By word.Length Into gr = Group   
            Order By Length _  
            Select Length, GroupedWords = gr  
  
Dim output As New System.Text.StringBuilder  
For Each obj In query  
    output.AppendLine(String.Format("Words of length {0}:", obj.Length))  
    For Each word As String In obj.GroupedWords  
        output.AppendLine(word)  
    Next  
Next  
  
'Display the output  
MsgBox(output.ToString())  
  
' This code example produces the following output:  
'  
' Words of length 3:  
' THE  
' FOX  
' THE  
' DOG  
' Words of length 4:  
' OVER  
' LAZY  
' Words of length 5:  
' QUICK  
' BROWN  
' JUMPS   
```  
  
## <a name="query-expression-syntax"></a>查詢運算式語法  
 某些更常用的標準查詢運算子具有專用 C# 和 Visual Basic 語言關鍵字語法，可將它們呼叫為「查詢運算式」的一部分。 如需標準查詢運算子具有專用的關鍵字和其對應的語法的詳細資訊，請參閱[標準查詢運算子 (Visual Basic) 的查詢運算式語法](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)。  
  
## <a name="extending-the-standard-query-operators"></a>擴充標準查詢運算子  
 您可以建立適用於目標定義域或技術的定義域特定方法，來擴增一組標準查詢運算子。 您也可以將標準查詢運算子取代為提供額外服務的專屬實作，例如遠端評估、查詢轉譯和最佳化。 如需範例，請參閱 <xref:System.Linq.Enumerable.AsEnumerable%2A>。  
  
## <a name="related-sections"></a>相關章節  
 下列連結會將您帶到根據功能而提供各種標準查詢運算子的其他資訊的主題。  
  
 [排序資料](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md)  
  
 [設定作業 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/set-operations.md)  
  
 [篩選資料 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/filtering-data.md)  
  
 [數量詞作業 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)  
  
 [投影作業 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)  
  
 [資料分割 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/partitioning-data.md)  
  
 [聯結作業 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md)  
  
 [群組資料 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/grouping-data.md)  
  
 [產生作業 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/generation-operations.md)  
  
 [等號比較作業 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/equality-operations.md)  
  
 [項目作業 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/element-operations.md)  
  
 [轉換資料類型 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)  
  
 [串連作業 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/concatenation-operations.md)  
  
 [彙總作業 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Linq.Enumerable>  
 <xref:System.Linq.Queryable>  
 [LINQ 簡介 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)  
 [標準查詢運算子 (Visual Basic) 的查詢運算式語法](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)  
 [分類的標準查詢運算子的方式執行 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)  
 [擴充方法](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
