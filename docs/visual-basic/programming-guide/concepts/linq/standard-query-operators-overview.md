---
title: "標準查詢運算子概觀 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 302bd39e-2ec1-495b-94bf-37d370d6f05f
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: eb28988ef49e0583fb7e9197c4e13c84665074ac
ms.lasthandoff: 03/13/2017

---
# <a name="standard-query-operators-overview-visual-basic"></a>標準查詢運算子概觀 (Visual Basic)
*標準查詢運算子*形成 LINQ 模式的方法。 這些方法大多操作的序列，其中序列是的物件的型別會實作<xref:System.Collections.Generic.IEnumerable%601>介面或<xref:System.Linq.IQueryable%601>介面。</xref:System.Linq.IQueryable%601> </xref:System.Collections.Generic.IEnumerable%601> 標準查詢運算子會提供查詢功能包括篩選、 投影、 彙總、 排序等等。  
  
 有兩個集合的物件類型<xref:System.Collections.Generic.IEnumerable%601>和其他的<xref:System.Linq.IQueryable%601>.</xref:System.Linq.IQueryable%601>類型的物件上運作</xref:System.Collections.Generic.IEnumerable%601>的運作方式的其中一個 LINQ 標準查詢運算子 每一組所組成的方法為靜態成員的<xref:System.Linq.Enumerable>和<xref:System.Linq.Queryable>類別，分別。</xref:System.Linq.Queryable> </xref:System.Linq.Enumerable> 定義為*擴充方法*操作的型別。 這表示它們可以呼叫使用靜態方法的語法或執行個體方法語法。  
  
 此外，數個標準查詢運算子方法處理以外<xref:System.Collections.Generic.IEnumerable%601>或<xref:System.Linq.IQueryable%601>.</xref:System.Linq.IQueryable%601></xref:System.Collections.Generic.IEnumerable%601>為基礎的型別 <xref:System.Linq.Enumerable>型別定義了兩個這類方法都會<xref:System.Collections.IEnumerable>.</xref:System.Collections.IEnumerable>類型的物件上運作</xref:System.Linq.Enumerable> 這些方法，<xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29>和<xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>，讓您啟用非參數化，或非泛型集合的 LINQ 模式加以查詢。</xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29> </xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> 他們這麼做，藉由建立強型別物件的集合。 <xref:System.Linq.Queryable>類別會定義兩個類似的方法，<xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29>以及<xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>操作物件的型別<xref:System.Linq.Queryable>。</xref:System.Linq.Queryable> </xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29> </xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> </xref:System.Linq.Queryable>  
  
 標準查詢運算子的執行，根據其傳回單一值的序列時機並不相同。 傳回單一值的方法 (例如，<xref:System.Linq.Enumerable.Average%2A>和<xref:System.Linq.Enumerable.Sum%2A>) 會立即執行。</xref:System.Linq.Enumerable.Sum%2A> </xref:System.Linq.Enumerable.Average%2A> 傳回序列的方法會延後查詢執行，並傳回可列舉物件。  
  
 在集合運算記憶體中，也就是，這些方法來擴充方法的情況下<xref:System.Collections.Generic.IEnumerable%601>，傳回可列舉的物件會擷取已傳遞給方法的引數。</xref:System.Collections.Generic.IEnumerable%601> 該物件列舉時，會採用查詢運算子的邏輯，並傳回查詢結果。  
  
 相反地，方法擴充<xref:System.Linq.IQueryable%601>不會實作任何查詢的行為，但建置運算式樹狀結構，表示要執行查詢。</xref:System.Linq.IQueryable%601> 查詢處理由來源<xref:System.Linq.IQueryable%601>物件。</xref:System.Linq.IQueryable%601>  
  
 查詢方法的呼叫可以鏈結在一起在一個查詢中，可讓查詢變得很複雜。  
  
 下列程式碼範例示範如何使用標準查詢運算子，以取得序列的相關資訊。  
  
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
 某些較常使用的標準查詢運算子具有專用的 C# 和 Visual Basic 的語言關鍵字語法，可讓它們的一部分呼叫*查詢**運算式*。 如需標準查詢運算子具有專用的關鍵字和其對應的語法的詳細資訊，請參閱[標準查詢運算子 (Visual Basic) 的查詢運算式語法](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)。  
  
## <a name="extending-the-standard-query-operators"></a>擴充標準查詢運算子  
 您可以藉由建立適用於您的目標網域或技術的網域特定方法擴充一組標準查詢運算子。 您也可以使用您自己的實作，提供額外的服務，例如遠端評估、 查詢轉譯和最佳化取代標準查詢運算子。 請參閱<xref:System.Linq.Enumerable.AsEnumerable%2A>範例。</xref:System.Linq.Enumerable.AsEnumerable%2A>  
  
## <a name="related-sections"></a>相關章節  
 下列連結可讓您提供各種功能為基礎的標準查詢運算子的其他資訊的主題。  
  
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
 <xref:System.Linq.Enumerable></xref:System.Linq.Enumerable>   
 <xref:System.Linq.Queryable></xref:System.Linq.Queryable>   
 [(Visual Basic) 的 LINQ 簡介](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)   
 [查詢運算式語法的標準查詢運算子 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)   
 [依據 (Visual Basic) 的執行方式的標準查詢運算子的分類](../../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)   
 [擴充方法](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
