---
title: "如何︰ 新增 LINQ 查詢 (Visual Basic) 的自訂方法 |Microsoft 文件"
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
ms.assetid: 099b2e2a-83cd-45c6-aa4d-01b398b5faaf
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 166eb731d41e009c374ba55f929eed302793ecd0
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-add-custom-methods-for-linq-queries-visual-basic"></a>如何︰ 新增 LINQ 查詢 (Visual Basic) 的自訂方法
您可以擴充一組您可以加入的擴充方法使用 LINQ 查詢的方法<xref:System.Collections.Generic.IEnumerable%601>介面。</xref:System.Collections.Generic.IEnumerable%601> 例如，除了標準的平均值或最大作業中，您可以建立自訂的彙總方法，以計算值序列的單一值。 您也可以建立自訂篩選器為特定的資料轉換的值序列的運作方式，並傳回新的順序的方法。 這類方法的範例包括<xref:System.Linq.Enumerable.Distinct%2A>， <xref:System.Linq.Enumerable.Skip%2A>，和<xref:System.Linq.Enumerable.Reverse%2A>.</xref:System.Linq.Enumerable.Reverse%2A> </xref:System.Linq.Enumerable.Skip%2A> </xref:System.Linq.Enumerable.Distinct%2A>  
  
 當您延伸<xref:System.Collections.Generic.IEnumerable%601>介面，您可以將自訂的方法套用至任何可列舉集合。</xref:System.Collections.Generic.IEnumerable%601> 如需詳細資訊，請參閱[擴充方法](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)。  
  
## <a name="adding-an-aggregate-method"></a>加入彙總的方法  
 彙總方法會計算一組值的單一值。 LINQ 提供數種彙總的方法，包括<xref:System.Linq.Enumerable.Average%2A>， <xref:System.Linq.Enumerable.Min%2A>，和<xref:System.Linq.Enumerable.Max%2A>.</xref:System.Linq.Enumerable.Max%2A> </xref:System.Linq.Enumerable.Min%2A> </xref:System.Linq.Enumerable.Average%2A> 您可以藉由新增擴充方法來建立您自己的彙總方法<xref:System.Collections.Generic.IEnumerable%601>介面。</xref:System.Collections.Generic.IEnumerable%601>  
  
 下列程式碼範例示範如何建立擴充方法呼叫`Median`來計算類型的數字序列的中位數`double`。  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module LINQExtension  
  
    ' Extension method for the IEnumerable(of T) interface.   
    ' The method accepts only values of the Double type.  
    <Extension()>   
    Function Median(ByVal source As IEnumerable(Of Double)) As Double  
        If source.Count = 0 Then  
            Throw New InvalidOperationException("Cannot compute median for an empty set.")  
        End If  
  
        Dim sortedSource = From number In source   
                           Order By number  
  
        Dim itemIndex = sortedSource.Count \ 2  
  
        If sortedSource.Count Mod 2 = 0 Then  
            ' Even number of items in list.  
            Return (sortedSource(itemIndex) + sortedSource(itemIndex - 1)) / 2  
        Else  
            ' Odd number of items in list.  
            Return sortedSource(itemIndex)  
        End If  
    End Function  
End Module  
```  
  
 任何可列舉集合呼叫此擴充方法呼叫從其他彙總方法的方式相同<xref:System.Collections.Generic.IEnumerable%601>介面。</xref:System.Collections.Generic.IEnumerable%601>  
  
> [!NOTE]
>  在 Visual Basic 中，您可以使用方法呼叫或標準查詢語法`Aggregate`或`Group By`子句。 如需詳細資訊，請參閱[Aggregate 子句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)和[By 子句群組](../../../../visual-basic/language-reference/queries/group-by-clause.md)。  
  
 下列程式碼範例示範如何使用`Median`方法類型的陣列`double`。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
### <a name="overloading-an-aggregate-method-to-accept-various-types"></a>多載接受各種類型的彙總方法  
 您可以多載您彙總的方法，讓它可接受各種類型的序列。 標準的方法是建立每種類型的多載。 另一種方法是建立多載會採用泛型型別，並使用委派來將它轉換成特定的型別。 您也可以結合這兩種方法。  
  
#### <a name="to-create-an-overload-for-each-type"></a>若要建立每種類型的多載  
 您可以建立您想要支援每種類型的特定多載。 下列程式碼範例顯示的多載`Median`方法`integer`型別。  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
 您現在可以呼叫`Median`兩個多載`integer`和`double`型別，如下列程式碼所示︰  
  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
#### <a name="to-create-a-generic-overload"></a>若要建立泛型多載  
 您也可以建立多載可接受的泛型物件序列。 這個多載會接受委派做為參數，並使用該物件的泛型型別序列轉換成特定的型別。  
  
 下列程式碼顯示的多載`Median`採用方法<xref:System.Func%602>委派做為參數。</xref:System.Func%602> 這個委派會採用泛型型別 T 的物件，並傳回型別的物件`double`。  
  
```vb  
' Generic overload.  
  
<Extension()>   
Function Median(Of T)(ByVal source As IEnumerable(Of T),   
                      ByVal selector As Func(Of T, Double)) As Double  
    Return Aggregate num In source Select selector(num) Into med = Median()  
End Function  
```  
  
 您現在可以呼叫`Median`方法序列的任何類型的物件。 如果型別沒有自己的方法多載，您必須傳遞委派參數。 在 Visual Basic 中，您可以使用 lambda 運算式，針對此目的。 此外，如果您使用`Aggregate`或`Group By`子句，而不是方法呼叫，您可以傳遞任何值或運算式，這個子句會在範圍。  
  
 下列程式碼範例示範如何呼叫`Median`整數的陣列和字串陣列的方法。 字串，計算中間值的陣列中的字串長度。 此範例顯示如何傳遞<xref:System.Func%602>委派參數`Median`每個案例的方法。</xref:System.Func%602>  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
## <a name="adding-a-method-that-returns-a-collection"></a>加入可傳回集合的方法  
 您可以擴充<xref:System.Collections.Generic.IEnumerable%601>介面的自訂查詢方法，傳回的值序列。</xref:System.Collections.Generic.IEnumerable%601> 在此情況下，此方法必須傳回型別<xref:System.Collections.Generic.IEnumerable%601>.</xref:System.Collections.Generic.IEnumerable%601>集合 這種方法可用來將篩選條件或資料轉換套用至值的序列。  
  
 下列範例示範如何建立名為擴充方法`AlternateElements`傳回每個項目在集合中，從第一個項目開始。  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
 您可以呼叫這個擴充方法的任何可列舉集合，就像您就可以呼叫其他方法，從<xref:System.Collections.Generic.IEnumerable%601>介面，如下列程式碼所示︰</xref:System.Collections.Generic.IEnumerable%601>  
  
```vb  
Dim strings() As String = {"a", "b", "c", "d", "e"}  
  
Dim query = strings.AlternateElements()  
  
For Each element In query  
    Console.WriteLine(element)  
Next  
  
' This code produces the following output:  
'  
' a  
' c  
' e  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>   
 [擴充方法](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
