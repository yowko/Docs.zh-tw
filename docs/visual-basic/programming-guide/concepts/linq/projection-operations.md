---
title: "投影作業 (Visual Basic) |Microsoft 文件"
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
ms.assetid: b8d38e6d-21cf-4619-8dbb-94476f4badc7
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
ms.openlocfilehash: 8876e65e752e0b18404ec32aecdcad7805533840
ms.lasthandoff: 03/13/2017

---
# <a name="projection-operations-visual-basic"></a>投影作業 (Visual Basic)
投影指的是指將物件轉換成新的表單通常僅包含後續即將使用這些屬性的作業。 透過使用投影，您可以建構根據每個物件所建立的新型別。 您可以投影屬性並針對它執行數學函式。 您也可以投影原始物件，而不變更它。  
  
 執行投影的標準查詢運算子方法詳列於下一節。  
  
## <a name="methods"></a>方法  
  
|方法名稱|描述|Visual Basic 查詢運算式語法|更多資訊|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|選取|轉換函式為基礎的專案值。|`Select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Select%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=fullName></xref:System.Linq.Queryable.Select%2A?displayProperty=fullName>|  
|SelectMany|專案的值為基礎的轉換函式，然後將它們簡化成單一序列的順序。|使用多個`From`子句|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=fullName></xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=fullName></xref:System.Linq.Queryable.SelectMany%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-examples"></a>查詢運算式語法範例  
  
### <a name="select"></a>選取  
 下列範例會使用`Select`子句，以專案從每個字串的字串清單中的第一個字母。  
  
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
 下列範例會使用多個`From`專案從每個字串的字串清單中的每個單字的子句。  
  
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
  
## <a name="select-versus-selectmany"></a>選取與 SelectMany  
 這兩者的工作`Select()`和`SelectMany()`取自來源值來產生結果值 （或值）。 `Select()`會產生一個結果值的每個來源值。 整體的結果，因此是具有相同數目的元素與來源集合的集合。 相反地，`SelectMany()`會產生單一的整體結果，其中包含從每個來源值串連的子集合。 轉換函式的引數傳遞之`SelectMany()`必須傳回可列舉序列的每個來源值的值。 這些可列舉序列然後串連`SelectMany()`建立一個大型的順序。  
  
 下列兩張圖顯示這兩種方法在動作之間的概念差異。 在每個案例中，假設選取器 （轉換） 函式會從每個來源值選取花卉陣列。  
  
 下圖說明如何`Select()`傳回具有相同數目的元素與來源集合的集合。  
  
 ![Select （） 動作的概念圖例](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")  
  
 下圖說明如何`SelectMany()`串連成一個最後的結果值，其中包含每個中繼陣列中的每個值的陣列中繼序列。  
  
 ![顯示 selectmany （） 的動作圖形。] (../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "SelectMany")  
  
### <a name="code-example"></a>程式碼範例  
 下列範例會比較的行為`Select()`和`SelectMany()`。 程式碼會建立 「 花束 」 的 「 花 」 的名稱的每個清單中的前兩個項目來源集合中。 在此範例中，「 單值 」 的轉換函式<xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>使用本身就是值的集合。</xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> 這需要額外`For Each`迴圈來列舉每一個子序列中的每個字串。  
  
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
 <xref:System.Linq></xref:System.Linq>   
 [標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Select 子句](../../../../visual-basic/language-reference/queries/select-clause.md)   
 [如何︰ 使用 Joins 合併資料](../../../../visual-basic/programming-guide/language-features/linq/how-to-combine-data-with-linq-by-using-joins.md)   
 [如何︰ 填入物件集合，從多個來源 (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)   
 [如何︰ 將 LINQ 查詢結果，當做特定類型傳回](../../../../visual-basic/programming-guide/language-features/linq/how-to-return-a-linq-query-result-as-a-specific-type.md)   
 [如何︰ 使用群組 (LINQ) (Visual Basic)，將檔案分割成許多檔案](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
