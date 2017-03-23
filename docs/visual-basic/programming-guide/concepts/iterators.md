---
title: "Iterator (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
ms.assetid: f26b5c1e-fe9d-4004-b287-da7919d717ae
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
ms.openlocfilehash: 4ea1e21bd8cc392889c477e78338384ed05d4cbb
ms.lasthandoff: 03/13/2017

---
# <a name="iterators-visual-basic"></a>Iterator (Visual Basic)
*迭代器*可用來逐步執行集合例如列出與陣列。  
  
 Iterator 方法或`get`存取子集合上執行自訂的反覆項目。 Iterator 方法會使用[產生](../../../visual-basic/language-reference/statements/yield-statement.md)陳述式來傳回一個元素一次。 當`Yield`陳述式為止，程式碼中的目前位置會記住。 已重新開始執行從該位置下一次呼叫 iterator 函式。  
  
 您可以使用迭代器，從用戶端程式碼使用[每個...下一步](../../../visual-basic/language-reference/statements/for-each-next-statement.md)陳述式，或使用 LINQ 查詢。  
  
 在下列範例中，第一次反覆運算`For Each`迴圈會繼續執行`SomeNumbers`iterator 方法，直到第一個`Yield`陳述式為止。 這個反覆項目會傳回值為 3，並保留 iterator 方法中目前的位置。 在迴圈的下一個反覆項目上執行 iterator 方法中的會繼續從何處中斷，並且在到達時再次停止`Yield`陳述式。 這個反覆項目傳回的值為 5，而一次保留 iterator 方法中目前的位置。 在迴圈完成，當 iterator 方法結束為止。  
  
```vb  
Sub Main()  
    For Each number As Integer In SomeNumbers()  
        Console.Write(number & " ")  
    Next  
    ' Output: 3 5 8  
    Console.ReadKey()  
End Sub  
  
Private Iterator Function SomeNumbers() As System.Collections.IEnumerable  
    Yield 3  
    Yield 5  
    Yield 8  
End Function  
```  
  
 Iterator 方法的傳回型別或`get`存取子可以是<xref:System.Collections.IEnumerable>， <xref:System.Collections.Generic.IEnumerable%601>， <xref:System.Collections.IEnumerator>，或<xref:System.Collections.Generic.IEnumerator%601>.</xref:System.Collections.Generic.IEnumerator%601> </xref:System.Collections.IEnumerator> </xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.IEnumerable>  
  
 您可以使用`Exit Function`或`Return`陳述式結束反覆項目。  
  
 Visual Basic 迭代器函式或`get`存取子宣告包含[迭代器](../../../visual-basic/language-reference/modifiers/iterator.md)修飾詞。  
  
 在 Visual Basic，Visual Studio 2012 中引進迭代器。  
  
 **本主題內容**  
  
-   [簡單的 Iterator](#BKMK_SimpleIterator)  
  
-   [建立集合類別](#BKMK_CollectionClass)  
  
-   [Try 區塊](#BKMK_TryBlocks)  
  
-   [匿名方法](#BKMK_AnonymousMethods)  
  
-   [迭代器使用的泛型清單](#BKMK_GenericList)  
  
-   [語法資訊](#BKMK_SyntaxInformation)  
  
-   [技術實作](#BKMK_Technical)  
  
-   [迭代器的使用](#BKMK_UseOfIterators)  
  
> [!NOTE]
>  除了簡單的 Iterator 範例主題中的所有範例，包括[匯入](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)陳述式`System.Collections`和`System.Collections.Generic`命名空間。  
  
##  <a name="BKMK_SimpleIterator"></a>簡單的 Iterator  
 下列範例具有單一`Yield`陳述式內[For...下一步](../../../visual-basic/language-reference/statements/for-next-statement.md)迴圈。 在`Main`，每個反覆項目`For Each`陳述式主體會建立呼叫 iterator 函式，繼續進行下一個`Yield`陳述式。  
  
```vb  
Sub Main()  
    For Each number As Integer In EvenSequence(5, 18)  
        Console.Write(number & " ")  
    Next  
    ' Output: 6 8 10 12 14 16 18  
    Console.ReadKey()  
End Sub  
  
Private Iterator Function EvenSequence(  
ByVal firstNumber As Integer, ByVal lastNumber As Integer) _  
As System.Collections.Generic.IEnumerable(Of Integer)  
  
    ' Yield even numbers in the range.  
    For number As Integer = firstNumber To lastNumber  
        If number Mod 2 = 0 Then  
            Yield number  
        End If  
    Next  
End Function  
```  
  
##  <a name="BKMK_CollectionClass"></a>建立集合類別  
 在下列範例中，`DaysOfTheWeek`類別會實作<xref:System.Collections.IEnumerable>介面，這需要<xref:System.Collections.IEnumerable.GetEnumerator%2A>方法。</xref:System.Collections.IEnumerable.GetEnumerator%2A> </xref:System.Collections.IEnumerable> 編譯器會隱含地呼叫`GetEnumerator`方法，傳回<xref:System.Collections.IEnumerator>。</xref:System.Collections.IEnumerator>  
  
 `GetEnumerator`方法會傳回每個字串一次使用`Yield`陳述式，和`Iterator`修飾詞是函式宣告中。  
  
```vb  
Sub Main()  
    Dim days As New DaysOfTheWeek()  
    For Each day As String In days  
        Console.Write(day & " ")  
    Next  
    ' Output: Sun Mon Tue Wed Thu Fri Sat  
    Console.ReadKey()  
End Sub  
  
Private Class DaysOfTheWeek  
    Implements IEnumerable  
  
    Public days =  
        New String() {"Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"}  
  
    Public Iterator Function GetEnumerator() As IEnumerator _  
        Implements IEnumerable.GetEnumerator  
  
        ' Yield each day of the week.  
        For i As Integer = 0 To days.Length - 1  
            Yield days(i)  
        Next  
    End Function  
End Class  
```  
  
 下列範例會建立`Zoo`類別，其中包含動物的集合。  
  
 `For Each`參考的類別執行個體的陳述式 (`theZoo`) 會隱含地呼叫`GetEnumerator`方法。 `For Each`陳述式，請參閱`Birds`和`Mammals`屬性使用`AnimalsForType`名為 iterator 方法。  
  
```vb  
Sub Main()  
    Dim theZoo As New Zoo()  
  
    theZoo.AddMammal("Whale")  
    theZoo.AddMammal("Rhinoceros")  
    theZoo.AddBird("Penguin")  
    theZoo.AddBird("Warbler")  
  
    For Each name As String In theZoo  
        Console.Write(name & " ")  
    Next  
    Console.WriteLine()  
    ' Output: Whale Rhinoceros Penguin Warbler  
  
    For Each name As String In theZoo.Birds  
        Console.Write(name & " ")  
    Next  
    Console.WriteLine()  
    ' Output: Penguin Warbler  
  
    For Each name As String In theZoo.Mammals  
        Console.Write(name & " ")  
    Next  
    Console.WriteLine()  
    ' Output: Whale Rhinoceros  
  
    Console.ReadKey()  
End Sub  
  
Public Class Zoo  
    Implements IEnumerable  
  
    ' Private members.  
    Private animals As New List(Of Animal)  
  
    ' Public methods.  
    Public Sub AddMammal(ByVal name As String)  
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Mammal})  
    End Sub  
  
    Public Sub AddBird(ByVal name As String)  
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Bird})  
    End Sub  
  
    Public Iterator Function GetEnumerator() As IEnumerator _  
        Implements IEnumerable.GetEnumerator  
  
        For Each theAnimal As Animal In animals  
            Yield theAnimal.Name  
        Next  
    End Function  
  
    ' Public members.  
    Public ReadOnly Property Mammals As IEnumerable  
        Get  
            Return AnimalsForType(Animal.TypeEnum.Mammal)  
        End Get  
    End Property  
  
    Public ReadOnly Property Birds As IEnumerable  
        Get  
            Return AnimalsForType(Animal.TypeEnum.Bird)  
        End Get  
    End Property  
  
    ' Private methods.  
    Private Iterator Function AnimalsForType( _  
    ByVal type As Animal.TypeEnum) As IEnumerable  
        For Each theAnimal As Animal In animals  
            If (theAnimal.Type = type) Then  
                Yield theAnimal.Name  
            End If  
        Next  
    End Function  
  
    ' Private class.  
    Private Class Animal  
        Public Enum TypeEnum  
            Bird  
            Mammal  
        End Enum  
  
        Public Property Name As String  
        Public Property Type As TypeEnum  
    End Class  
End Class  
```  
  
##  <a name="BKMK_TryBlocks"></a>Try 區塊  
 Visual Basic 可讓`Yield`陳述式中的`Try`區塊[試...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。 A`Try`區塊具有`Yield`陳述式可以有`Catch`區塊，而且可以有`Finally`區塊。  
  
 下列範例會加入`Try`， `Catch`，和`Finally`iterator 函式中的區塊。 `Finally`區塊中的迭代器函式執行之前`For Each`反覆項目完成。  
  
```vb  
Sub Main()  
    For Each number As Integer In Test()  
        Console.WriteLine(number)  
    Next  
    Console.WriteLine("For Each is done.")  
  
    ' Output:  
    '  3  
    '  4  
    '  Something happened. Yields are done.  
    '  Finally is called.  
    '  For Each is done.  
    Console.ReadKey()  
End Sub  
  
Private Iterator Function Test() As IEnumerable(Of Integer)  
    Try  
        Yield 3  
        Yield 4  
        Throw New Exception("Something happened. Yields are done.")  
        Yield 5  
        Yield 6  
    Catch ex As Exception  
        Console.WriteLine(ex.Message)  
    Finally  
        Console.WriteLine("Finally is called.")  
    End Try  
End Function  
```  
  
 A`Yield`陳述式不能在`Catch`區塊或`Finally`區塊。  
  
 如果`For Each`（而不是迭代器的方法） 的主體擲回例外狀況， `Catch` iterator 函式中的區塊不會執行，但`Finally`就會執行 iterator 函式中的區塊。 A `Catch` iterator 函式區塊攔截函式迭代器內發生的例外狀況。  
  
##  <a name="BKMK_AnonymousMethods"></a>匿名方法  
 在 Visual Basic 中的匿名函式可以是 iterator 函式。 下列範例將說明這點。  
  
```vb  
Dim iterateSequence = Iterator Function() _  
                      As IEnumerable(Of Integer)  
                          Yield 1  
                          Yield 2  
                      End Function  
  
For Each number As Integer In iterateSequence()  
    Console.Write(number & " ")  
Next  
' Output: 1 2  
Console.ReadKey()  
```  
  
 下列範例具有驗證引數的非迭代器方法。 方法會傳回描述的集合項目之匿名迭代器的結果。  
  
```vb  
Sub Main()  
    For Each number As Integer In GetSequence(5, 10)  
        Console.Write(number & " ")  
    Next  
    ' Output: 5 6 7 8 9 10  
    Console.ReadKey()  
End Sub  
  
Public Function GetSequence(ByVal low As Integer, ByVal high As Integer) _  
As IEnumerable  
    ' Validate the arguments.  
    If low < 1 Then  
        Throw New ArgumentException("low is too low")  
    End If  
    If high > 140 Then  
        Throw New ArgumentException("high is too high")  
    End If  
  
    ' Return an anonymous iterator function.  
    Dim iterateSequence = Iterator Function() As IEnumerable  
                              For index = low To high  
                                  Yield index  
                              Next  
                          End Function  
    Return iterateSequence()  
End Function  
```  
  
 如果驗證改為迭代器函數內，無法執行驗證的第一個反覆項目啟動前`For Each`主體。  
  
##  <a name="BKMK_GenericList"></a>迭代器使用的泛型清單  
 在下列範例中，`Stack(Of T)`泛型類別會實作<xref:System.Collections.Generic.IEnumerable%601>泛型介面。</xref:System.Collections.Generic.IEnumerable%601> `Push`方法會將值指派給類型的陣列`T`。 <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>方法會傳回陣列的值使用`Yield`陳述式。</xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>  
  
 除了一般<xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>方法中，非泛型<xref:System.Collections.IEnumerable.GetEnumerator%2A>也必須實作方法。</xref:System.Collections.IEnumerable.GetEnumerator%2A> </xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> 這是因為<xref:System.Collections.Generic.IEnumerable%601>繼承自<xref:System.Collections.IEnumerable>。</xref:System.Collections.IEnumerable> </xref:System.Collections.Generic.IEnumerable%601> 非泛型實作會延後的泛型實作。  
  
 範例會使用具名的迭代器，以支援逐一查看相同的資料集合的各種方式。 這些已命名的迭代器是`TopToBottom`和`BottomToTop`屬性，而`TopN`方法。  
  
 `BottomToTop`屬性宣告包含`Iterator`關鍵字。  
  
```vb  
Sub Main()  
    Dim theStack As New Stack(Of Integer)  
  
    ' Add items to the stack.  
    For number As Integer = 0 To 9  
        theStack.Push(number)  
    Next  
  
    ' Retrieve items from the stack.  
    ' For Each is allowed because theStack implements  
    ' IEnumerable(Of Integer).  
    For Each number As Integer In theStack  
        Console.Write("{0} ", number)  
    Next  
    Console.WriteLine()  
    ' Output: 9 8 7 6 5 4 3 2 1 0  
  
    ' For Each is allowed, because theStack.TopToBottom  
    ' returns IEnumerable(Of Integer).  
    For Each number As Integer In theStack.TopToBottom  
        Console.Write("{0} ", number)  
    Next  
    Console.WriteLine()  
    ' Output: 9 8 7 6 5 4 3 2 1 0  
  
    For Each number As Integer In theStack.BottomToTop  
        Console.Write("{0} ", number)  
    Next  
    Console.WriteLine()  
    ' Output: 0 1 2 3 4 5 6 7 8 9   
  
    For Each number As Integer In theStack.TopN(7)  
        Console.Write("{0} ", number)  
    Next  
    Console.WriteLine()  
    ' Output: 9 8 7 6 5 4 3  
  
    Console.ReadKey()  
End Sub  
  
Public Class Stack(Of T)  
    Implements IEnumerable(Of T)  
  
    Private values As T() = New T(99) {}  
    Private top As Integer = 0  
  
    Public Sub Push(ByVal t As T)  
        values(top) = t  
        top = top + 1  
    End Sub  
  
    Public Function Pop() As T  
        top = top - 1  
        Return values(top)  
    End Function  
  
    ' This function implements the GetEnumerator method. It allows  
    ' an instance of the class to be used in a For Each statement.  
    Public Iterator Function GetEnumerator() As IEnumerator(Of T) _  
        Implements IEnumerable(Of T).GetEnumerator  
  
        For index As Integer = top - 1 To 0 Step -1  
            Yield values(index)  
        Next  
    End Function  
  
    Public Iterator Function GetEnumerator1() As IEnumerator _  
        Implements IEnumerable.GetEnumerator  
  
        Yield GetEnumerator()  
    End Function  
  
    Public ReadOnly Property TopToBottom() As IEnumerable(Of T)  
        Get  
            Return Me  
        End Get  
    End Property  
  
    Public ReadOnly Iterator Property BottomToTop As IEnumerable(Of T)  
        Get  
            For index As Integer = 0 To top - 1  
                Yield values(index)  
            Next  
        End Get  
    End Property  
  
    Public Iterator Function TopN(ByVal itemsFromTop As Integer) _  
        As IEnumerable(Of T)  
  
        ' Return less than itemsFromTop if necessary.  
        Dim startIndex As Integer =  
            If(itemsFromTop >= top, 0, top - itemsFromTop)  
  
        For index As Integer = top - 1 To startIndex Step -1  
            Yield values(index)  
        Next  
    End Function  
End Class  
  
```  
  
##  <a name="BKMK_SyntaxInformation"></a>語法資訊  
 可能是迭代器做為方法或`get`存取子。 迭代器不能出現在事件、 執行個體建構函式、 靜態建構函式或靜態的解構函式。  
  
 中的運算式型別必須有可隱含轉換`Yield`陳述式，以迭代器傳回的型別。  
  
 在 Visual Basic 中，迭代器方法不能有任何`ByRef`參數。  
  
 在 Visual Basic 中，「 產生 」 並不是保留的字，而且使用中時才具有特殊意義`Iterator`方法或`get`存取子。  
  
##  <a name="BKMK_Technical"></a>技術實作  
 雖然您撰寫迭代器做為方法時，編譯器將其轉譯成巢狀類別時，作用中狀態機器。 這個類別會追蹤的長度為迭代器位置`For Each...Next`用戶端程式碼中的迴圈會繼續執行。  
  
 若要查看的編譯器的執行，您可以使用 Ildasm.exe 工具來檢視迭代器方法會產生 Microsoft 中繼語言程式碼。  
  
 當您建立的迭代器[類別](../../../csharp/language-reference/keywords/class.md)或[結構](../../../csharp/language-reference/keywords/struct.md)，您就不必在實作整體<xref:System.Collections.IEnumerator>介面。</xref:System.Collections.IEnumerator> 當編譯器偵測到的迭代器時，它會自動產生`Current`， `MoveNext`，和`Dispose`方法<xref:System.Collections.IEnumerator>或<xref:System.Collections.Generic.IEnumerator%601>介面。</xref:System.Collections.Generic.IEnumerator%601> </xref:System.Collections.IEnumerator>  
  
 上的每個後續反覆項目的`For Each…Next`迴圈 (或直接呼叫`IEnumerator.MoveNext`)，繼續先前之後的下一個迭代器的程式碼主體`Yield`陳述式。 再繼續執行至下一個`Yield`陳述式，直到達到迭代器主體的結尾，或直到`Exit Function`或`Return`遇到陳述式。  
  
 不支援迭代器<xref:System.Collections.IEnumerator.Reset%2A?displayProperty=fullName>方法。</xref:System.Collections.IEnumerator.Reset%2A?displayProperty=fullName> 若要重新逐一查看從一開始，您必須取得新的迭代器。  
  
 如需詳細資訊，請參閱[Visual Basic 語言規格](../../../visual-basic/reference/language-specification.md)。  
  
##  <a name="BKMK_UseOfIterators"></a>迭代器的使用  
 迭代器可讓您維護的簡易性`For Each`循環播放，當您需要使用複雜的程式碼來填入清單順序。 當您想要這樣做，這非常有用︰  
  
-   在第一個之後修改清單順序`For Each`迴圈反覆項目。  
  
-   避免完全載入第一次反覆運算之前的大型清單`For Each`迴圈。 例如，分頁的 fetch 載入資料表的資料列的批次。 另一個範例是<xref:System.IO.DirectoryInfo.EnumerateFiles%2A>方法，它會實作在.NET Framework 中的迭代器。</xref:System.IO.DirectoryInfo.EnumerateFiles%2A>  
  
-   封裝建立重複的清單。 在 iterator 方法中，您可以建置清單中，然後產生在迴圈中的每個結果。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Collections.Generic></xref:System.Collections.Generic>   
 <xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>   
 [每個...下一個陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [Yield 陳述式](../../../visual-basic/language-reference/statements/yield-statement.md)   
 [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md)
