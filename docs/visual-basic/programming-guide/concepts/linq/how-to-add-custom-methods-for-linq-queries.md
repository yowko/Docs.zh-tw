---
title: 如何： 加入自訂方法的 LINQ 查詢 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 099b2e2a-83cd-45c6-aa4d-01b398b5faaf
ms.openlocfilehash: 6fa212ff05547e8edd3964a6e1c9f76c11cdbe08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644052"
---
# <a name="how-to-add-custom-methods-for-linq-queries-visual-basic"></a>如何： 加入自訂方法的 LINQ 查詢 (Visual Basic)
您可以將擴充方法新增至 <xref:System.Collections.Generic.IEnumerable%601> 介面，來延伸您可以用於 LINQ 查詢的方法組。 例如，除了標準平均值或最多作業，您可以建立自訂的彙總方法，計算一系列值的單一值。 您也可以建立一個方法，用為自訂篩選器或一系列值的特定資料轉換，並傳回新的序列。 這類方法的範例包括 <xref:System.Linq.Enumerable.Distinct%2A>、<xref:System.Linq.Enumerable.Skip%2A> 和 <xref:System.Linq.Enumerable.Reverse%2A>。  
  
 當您延伸 <xref:System.Collections.Generic.IEnumerable%601> 介面時，可將自訂方法套用至任何可列舉的集合。 如需詳細資訊，請參閱[擴充方法](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)。  
  
## <a name="adding-an-aggregate-method"></a>新增彙總方法  
 彙總方法會計算一組值的單一值。 LINQ 提供數種彙總方法，包括 <xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Min%2A> 和 <xref:System.Linq.Enumerable.Max%2A>。 您可將擴充方法新增至 <xref:System.Collections.Generic.IEnumerable%601> 介面，建立自己的彙總方法。  
  
 下列程式碼範例示範如何建立呼叫 `Median` 的擴充方法，來計算一系列類型為 `double` 的中位數。  
  
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
  
 您可以使用從 <xref:System.Collections.Generic.IEnumerable%601> 介面呼叫其他彙總方法同樣的方式，為任何可列舉集合呼叫此擴充方法。  
  
> [!NOTE]
>  在 Visual Basic 中，您可以使用方法呼叫或標準查詢語法`Aggregate`或`Group By`子句。 如需詳細資訊，請參閱[Aggregate 子句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)和[群組 By 子句](../../../../visual-basic/language-reference/queries/group-by-clause.md)。  
  
 下列程式碼範例示範如何使用 `Median` 方法處理 `double` 類型的陣列。  
  
```vb  
Dim numbers1() As Double = {1.9, 2, 8, 4, 5.7, 6, 7.2, 0}  
  
Dim query1 = Aggregate num In numbers1 Into Median()  
  
Console.WriteLine("Double: Median = " & query1)  
```  
  
```vb  
' This code produces the following output:  
'  
' Double: Median = 4.85  
```  
  

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a>多載彙總方法以接受各種類型  
 您可以多載自己的彙總方法，讓它接受各種類型的序列。 標準方法是為每種類型建立多載。 另一種方法是建立採用泛型型別的多載，使用委派將它轉換成特定的類型。 您也可以結合這兩種方法。  
  
#### <a name="to-create-an-overload-for-each-type"></a>為每種類型建立多載  
 您可以為想要支援的每種類型建立特定的多載。 下列程式碼範例示範適合 `integer` 類型之 `Median` 方法的多載。  
  
```vb  
' Integer overload  
  
<Extension()>   
Function Median(ByVal source As IEnumerable(Of Integer)) As Double  
    Return Aggregate num In source Select CDbl(num) Into med = Median()  
End Function  
```  
 您現在可以呼叫 `integer` 和 `double` 類型的 `Median` 多載，如下列程式碼所示︰  
  
```vb  
Dim numbers1() As Double = {1.9, 2, 8, 4, 5.7, 6, 7.2, 0}  
  
Dim query1 = Aggregate num In numbers1 Into Median()  
  
Console.WriteLine("Double: Median = " & query1)  
```  
  
```vb  
Dim numbers2() As Integer = {1, 2, 3, 4, 5}  
  
Dim query2 = Aggregate num In numbers2 Into Median()  
  
Console.WriteLine("Integer: Median = " & query2)  
```  
  
```vb  
' This code produces the following output:  
'  
' Double: Median = 4.85  
' Integer: Median = 3  
```  
  
 
#### <a name="to-create-a-generic-overload"></a>建立一般多載  
 您也可以建立接受一系列泛型物件的多載。 這個多載會接受委派作為參數，並使用它將泛型型別物件的序列轉換成特定的類型。  
  
 下列程式碼顯示 `Median` 方法的多載，接受 <xref:System.Func%602> 委派為參數。 這個委派會接受泛型型別 T 的物件，並傳回 `double` 類型的物件。  
  
```vb  
' Generic overload.  
  
<Extension()>   
Function Median(Of T)(ByVal source As IEnumerable(Of T),   
                      ByVal selector As Func(Of T, Double)) As Double  
    Return Aggregate num In source Select selector(num) Into med = Median()  
End Function  
```  
  
 您現在可以針對一系列的類型物件呼叫 `Median` 方法。 如果類型沒有自己的方法多載，您就必須傳遞委派參數。 在 Visual Basic 中，您可以針對此用途使用 lambda 運算式。 此外，如果您使用`Aggregate`或`Group By`子句而不是在方法呼叫中的，您可以傳遞任何值或運算式，這是在範圍中這個子句。  
  
 下列程式碼範例示範如何呼叫 `Median` 方法，處理整數陣列及字串陣列。 針對字串，會計算陣列字串長度的中間值。 此範例會示範如何將 <xref:System.Func%602> 委派參數傳遞至每個案例的 `Median` 方法。  
  
```vb  
Dim numbers3() As Integer = {1, 2, 3, 4, 5}  
  
' You can use num as a parameter for the Median method   
' so that the compiler will implicitly convert its value to double.  
' If there is no implicit conversion, the compiler will  
' display an error message.  
  
Dim query3 = Aggregate num In numbers3 Into Median(num)  
  
Console.WriteLine("Integer: Median = " & query3)  
  
Dim numbers4() As String = {"one", "two", "three", "four", "five"}  
  
' With the generic overload, you can also use numeric properties of objects.  
  
Dim query4 = Aggregate str In numbers4 Into Median(str.Length)  
  
Console.WriteLine("String: Median = " & query4)  
  
' This code produces the following output:  
'  
' Integer: Median = 3  
' String: Median = 4  
```  
## <a name="adding-a-method-that-returns-a-collection"></a>新增傳回集合的方法  
 您可以使用傳回一系列值的自訂查詢方法來延伸 <xref:System.Collections.Generic.IEnumerable%601> 介面。 在此情況下，方法必須傳回型別 <xref:System.Collections.Generic.IEnumerable%601> 的集合。 此等方法可用來將篩選條件或資料轉換套用至一系列的值。  
  
 下例示範如何建立名為 `AlternateElements` 的擴充方法，傳回集合中的每隔個項目，從第一個項目開始。  
  
```vb  
' Extension method for the IEnumerable(of T) interface.   
' The method returns every other element of a sequence.  
  
<Extension()>   
Function AlternateElements(Of T)(  
    ByVal source As IEnumerable(Of T)  
    ) As IEnumerable(Of T)  
  
    Dim list As New List(Of T)  
    Dim i = 0  
    For Each element In source  
        If (i Mod 2 = 0) Then  
            list.Add(element)  
        End If  
        i = i + 1  
    Next  
    Return list  
End Function  
```  
 您可為任何可列舉集合呼叫此擴充方法，就和您從 <xref:System.Collections.Generic.IEnumerable%601> 介面呼叫其他方法一樣，如下列程式碼所示：  
  
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
 <xref:System.Collections.Generic.IEnumerable%601>  
 [擴充方法](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
