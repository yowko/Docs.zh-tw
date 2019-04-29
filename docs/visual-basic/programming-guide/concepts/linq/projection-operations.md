---
title: 投影作業 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b8d38e6d-21cf-4619-8dbb-94476f4badc7
ms.openlocfilehash: e2af45f9cbbed9eb88095a30e2b77a7730740898
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766685"
---
# <a name="projection-operations-visual-basic"></a>投影作業 (Visual Basic)
投影是指將物件轉換成新形式的作業，而這個形式通常僅包含後續即將使用的屬性。 透過使用投影，您可以建構根據每個物件所建立的新型別。 您可以投影屬性並對其執行數學函式。 您也可以投影原始物件，而不進行任何變更。  
  
 執行投影的標準查詢運算子方法詳列於下一節。  
  
## <a name="methods"></a>方法  
  
|方法名稱|描述|Visual Basic 查詢運算式語法|更多資訊|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|選用版|投影以轉換函式為基礎的值。|`Select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|SelectMany|投影一連串以轉換函式為基礎的值，然後將這些值壓平合併成一個序列。|使用多個 `From` 子句|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>查詢運算式語法範例  
  
### <a name="select"></a>選用版  
 下列範例使用 `Select` 子句，來投影字串清單中每個字串的第一個字母。  
  
```vb  
Dim words = New List(Of String) From {"an", "apple", "a", "day"}  
  
Dim query = From word In words   
            Select word.Substring(0, 1)  
  
Dim sb As New System.Text.StringBuilder()  
For Each letter As String In query  
    sb.AppendLine(letter)  
Next  
  
' Display the output.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' a  
' a  
' a  
' d  
```  
  
### <a name="selectmany"></a>SelectMany  
 下列範例會使用多個`From`子句，來投影字串清單中每個字串的每個字。  
  
```vb  
Dim phrases = New List(Of String) From {"an apple a day", "the quick brown fox"}  
  
Dim query = From phrase In phrases   
            From word In phrase.Split(" "c)   
            Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In query  
    sb.AppendLine(str)  
Next  
  
' Display the output.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' an  
' apple  
' a  
' day  
' the  
' quick  
' brown  
' fox  
```  
  
## <a name="select-versus-selectmany"></a>Select 與 SelectMany 的比較  
 `Select()` 和 `SelectMany()` 的工作是從來源值產生一或多個結果值。 `Select()` 會針對每個來源值產生一個結果值。 因此，整體結果是集合與來源集合中的項目數相同。 相反地，`SelectMany()` 會產生單一整體結果，其中包含串連自每個來源值的子集合。 當做引數傳遞至 `SelectMany()` 的轉換函式必須傳回每個來源值的可列舉值序列。 `SelectMany()` 會接著串連這些可列舉的序列，以建立一個大型的序列。  
  
 下列兩個圖顯示這兩個方法的動作之間的概念差異。 在每個案例中，假設選取器 (轉換) 函式會從每個來源值選取花朵陣列。  
  
 下圖描述 `Select()` 如何傳回其中的項目數與來源集合相同的集合。  
  
 ![顯示 Select&#40;&#41; 之動作的圖形](./media/projection-operations/select-action-graphic.png)  
  
 下圖描述 `SelectMany()` 如何將中繼陣列序列串連成一個最終結果值，其中包含每個中繼陣列中的所有值。  
  
 ![顯示 SelectMany&#40;&#41; 之動作的圖形。](./media/projection-operations/select-many-action-graphic.png )  
  
### <a name="code-example"></a>程式碼範例  
 下列範例會比較 `Select()` 和 `SelectMany()` 的行為。 程式碼會從來源集合的每個花名清單中擷取前兩個項目，以建立「花束」(Bouquet)。 在此範例中，轉換函式 <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> 所使用的「單一值」本身就是值集合。 這需要額外的 `For Each` 迴圈，以列舉每個子序列中的每個字串。  
  
```vb  
Class Bouquet  
    Public Flowers As List(Of String)  
End Class  
  
Sub SelectVsSelectMany()  
    Dim bouquets = New List(Of Bouquet) From {   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"sunflower", "daisy", "daffodil", "larkspur"})},   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"tulip", "rose", "orchid"})},   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"gladiolis", "lily", "snapdragon", "aster", "protea"})},   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"larkspur", "lilac", "iris", "dahlia"})}}  
  
    Dim output As New System.Text.StringBuilder  
  
    ' Select()  
    Dim query1 = bouquets.Select(Function(b) b.Flowers)  
  
    output.AppendLine("Using Select():")  
    For Each flowerList In query1  
        For Each str As String In flowerList  
            output.AppendLine(str)  
        Next  
    Next  
  
    ' SelectMany()  
    Dim query2 = bouquets.SelectMany(Function(b) b.Flowers)  
  
    output.AppendLine(vbCrLf & "Using SelectMany():")  
    For Each str As String In query2  
        output.AppendLine(str)  
    Next  
  
    ' Display the output  
    MsgBox(output.ToString())  
  
    ' This code produces the following output:  
    '  
    ' Using Select():  
    ' sunflower  
    ' daisy  
    ' daffodil  
    ' larkspur  
    ' tulip  
    ' rose  
    ' orchid  
    ' gladiolis  
    ' lily  
    ' snapdragon  
    ' aster  
    ' protea  
    ' larkspur  
    ' lilac  
    ' iris  
    ' dahlia  
  
    ' Using SelectMany()  
    ' sunflower  
    ' daisy  
    ' daffodil  
    ' larkspur  
    ' tulip  
    ' rose  
    ' orchid  
    ' gladiolis  
    ' lily  
    ' snapdragon  
    ' aster  
    ' protea  
    ' larkspur  
    ' lilac  
    ' iris  
    ' dahlia  
  
End Sub  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Linq>
- [標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Select 子句](../../../../visual-basic/language-reference/queries/select-clause.md)
- [如何：使用 Joins 合併資料](../../../../visual-basic/programming-guide/language-features/linq/how-to-combine-data-with-linq-by-using-joins.md)
- [如何：填入物件集合，從多個來源 (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
- [如何：將 LINQ 查詢結果傳回成特定的類型](../../../../visual-basic/programming-guide/language-features/linq/how-to-return-a-linq-query-result-as-a-specific-type.md)
- [如何：使用群組 (LINQ) (Visual Basic)，將檔案分割成許多檔案](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
