---
title: "建立 Variant 泛型介面 (Visual Basic) |Microsoft 文件"
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
ms.assetid: d4037dd2-dfe9-4811-9150-93d4e8b20113
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
ms.openlocfilehash: 324e2a906e84950aa9019bbf68a524458492646e
ms.lasthandoff: 03/13/2017

---
# <a name="creating-variant-generic-interfaces-visual-basic"></a>建立 Variant 泛型介面 (Visual Basic)
您可以宣告泛型型別參數，在介面做為 covariant 或 contravariant。 *共變數*允許具有衍生程度較大的傳回型別比泛型型別參數所定義的介面方法。 *反變數*允許其較少衍生的泛型參數所指定的引數型別介面方法。 泛型介面具有 covariant 或 contravariant 的泛型型別參數呼叫*變異*。  
  
> [!NOTE]
>  .NET framework 4 引入變異數支援數個現有的泛型介面。 .NET Framework 中的 variant 介面清單，請參閱[泛型介面 (Visual Basic) 中的變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)。  
  
## <a name="declaring-variant-generic-interfaces"></a>宣告的 Variant 泛型介面  
 您可以使用宣告 variant 泛型介面`in`和`out`泛型型別參數的關鍵字。  
  
> [!IMPORTANT]
>  `ByRef`在 Visual Basic 中的參數不能變體。 實值型別也不支援變異數。  
  
 您可以宣告泛型型別參數 covariant 使用`out`關鍵字。 共變數的型別必須滿足下列條件︰  
  
-   型別是只用來做為介面方法的傳回型別，而不使用為方法引數的型別。 下列範例中，在其中所示的型別`R`宣告共變性。  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        Function GetSomething() As R  
        ' The following statement generates a compiler error.  
        ' Sub SetSomething(ByVal sampleArg As R)  
    End Interface  
    ```  
  
     這個規則只有一個例外。 如果您有 contravariant 泛型委派做為方法參數，您可以使用泛型型別參數類型的委派。 說明這種型別所`R`在下列範例中。 如需詳細資訊，請參閱[委派 (Visual Basic) 中的變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)和[Func 與 Action 委派 (Visual Basic) 使用變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)。  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        Sub DoSomething(ByVal callback As Action(Of R))  
    End Interface  
    ```  
  
-   型別不是做為泛型條件約束的介面方法。 下列程式碼所示。  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        ' The following statement generates a compiler error  
        ' because you can use only contravariant or invariant types  
        ' in generic contstraints.  
        ' Sub DoSomething(Of T As R)()  
    End Interface  
    ```  
  
 您可以使用宣告泛型型別參數 contravariant`in`關鍵字。 可以使用 contravariant 類型，只為方法引數的型別，而不是介面方法的傳回型別。 Contravariant 類型也用於泛型條件約束。 下列程式碼示範如何宣告逆變性介面，並使用其中一個方法的泛型條件約束。  
  
```vb  
Interface IContravariant(Of In A)  
    Sub SetSomething(ByVal sampleArg As A)  
    Sub DoSomething(Of T As A)()  
    ' The following statement generates a compiler error.  
    ' Function GetSomething() As A  
End Interface  
```  
  
 它也可支援共變數和反變數相同的介面，但在不同的型別參數，如下列程式碼範例所示。  
  
```vb  
Interface IVariant(Of Out R, In A)  
    Function GetSomething() As R  
    Sub SetSomething(ByVal sampleArg As A)  
    Function GetSetSomething(ByVal sampleArg As A) As R  
End Interface  
```  
  
 在 Visual Basic 中，您無法宣告 variant 介面中的事件，但未指定的委派型別。 此外，類別、 列舉或結構，變異數介面不能有巢狀，但它可以有巢狀介面。 下列程式碼所示。  
  
```vb  
Interface ICovariant(Of Out R)  
    ' The following statement generates a compiler error.  
    ' Event SampleEvent()  
    ' The following statement specifies the delegate type and   
    ' does not generate an error.  
    Event AnotherEvent As EventHandler  
  
    ' The following statements generate compiler errors,  
    ' because a variant interface cannot have  
    ' nested enums, classes, or structures.  
  
    'Enum SampleEnum : test : End Enum  
    'Class SampleClass : End Class  
    'Structure SampleStructure : Dim value As Integer : End Structure  
  
    ' Variant interfaces can have nested interfaces.  
    Interface INested : End Interface  
End Interface  
```  
  
## <a name="implementing-variant-generic-interfaces"></a>實作 Variant 泛型介面  
 您可以使用相同語法不變的介面是用於類別中實作 variant 泛型介面。 下列程式碼範例示範如何實作泛型類別中的共變數的介面。  
  
```vb  
Interface ICovariant(Of Out R)  
    Function GetSomething() As R  
End Interface  
  
Class SampleImplementation(Of R)  
    Implements ICovariant(Of R)  
    Public Function GetSomething() As R _  
    Implements ICovariant(Of R).GetSomething  
        ' Some code.  
    End Function  
End Class  
```  
  
 類別可實作 variant 介面都是不變。 例如，試想下列程式碼。  
  
```vb  
 The interface is covariant.  
Dim ibutton As ICovariant(Of Button) =  
    New SampleImplementation(Of Button)  
Dim iobj As ICovariant(Of Object) = ibutton  
  
' The class is invariant.  
Dim button As SampleImplementation(Of Button) =  
    New SampleImplementation(Of Button)  
' The following statement generates a compiler error  
' because classes are invariant.  
' Dim obj As SampleImplementation(Of Object) = button  
```  
  
## <a name="extending-variant-generic-interfaces"></a>擴充的 Variant 泛型介面  
 當您擴充 variant 泛型介面時，您必須使用`in`和`out`關鍵字明確指定衍生的介面是否支援變異數。 編譯器不會推斷要擴充的介面中的變異數。 例如，請考慮下列介面。  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
Interface IInvariant(Of T)  
    Inherits ICovariant(Of T)  
End Interface  
  
Interface IExtCovariant(Of Out T)  
    Inherits ICovariant(Of T)  
End Interface  
```  
  
 在`Invariant(Of T)`介面，泛型型別參數`T`不變，而在`IExtCovariant (Of Out T)`型別參數是共變數，雖然這兩個介面擴充相同的介面。 相同的規則會套用至 contravariant 泛型類型參數。  
  
 您可以擴充泛型型別參數的兩個介面的介面建立`T`是 covariant 和介面反變數中的擴充介面的泛型型別參數`T`不變。 下列程式碼範例所示。  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
Interface IContravariant(Of In T)  
End Interface  
  
Interface IInvariant(Of T)  
    Inherits ICovariant(Of T), IContravariant(Of T)  
End Interface  
```  
  
 不過，如果泛型型別參數`T`是共變數的宣告一個介面，您無法將其宣告逆變性在擴充的介面，反之亦然。 下列程式碼範例所示。  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
' The following statements generate a compiler error.  
' Interface ICoContraVariant(Of In T)  
'     Inherits ICovariant(Of T)  
' End Interface  
```  
  
### <a name="avoiding-ambiguity"></a>避免模稜兩可  
 當您實作 variant 泛型介面時，變異數有時會導致模稜兩可。 對此應該要設法避免。  
  
 例如，如果您明確地實作相同 variant 泛型介面具有不同的泛型型別參數，一個類別中，它可以建立模稜兩可。 編譯器不會在此情況下，產生錯誤，但未指定的介面實作，則會選擇在執行階段。 這可能會導致您的程式碼中的細微錯誤。 請考慮下列程式碼範例。  
  
> [!NOTE]
>  使用`Option Strict Off`，Visual Basic 會產生編譯器警告，當模稜兩可的介面實作。 使用`Option Strict On`，Visual Basic 會產生編譯器錯誤。  
  
```vb  
' Simple class hierarchy.  
Class Animal  
End Class  
  
Class Cat  
    Inherits Animal  
End Class  
  
Class Dog  
    Inherits Animal  
End Class  
  
' This class introduces ambiguity  
' because IEnumerable(Of Out T) is covariant.  
Class Pets  
    Implements IEnumerable(Of Cat), IEnumerable(Of Dog)  
  
    Public Function GetEnumerator() As IEnumerator(Of Cat) _  
        Implements IEnumerable(Of Cat).GetEnumerator  
        Console.WriteLine("Cat")  
        ' Some code.  
    End Function  
  
    Public Function GetEnumerator1() As IEnumerator(Of Dog) _  
        Implements IEnumerable(Of Dog).GetEnumerator  
        Console.WriteLine("Dog")  
        ' Some code.  
    End Function  
  
    Public Function GetEnumerator2() As IEnumerator _  
        Implements IEnumerable.GetEnumerator  
        ' Some code.  
    End Function  
End Class  
  
Sub Main()  
    Dim pets As IEnumerable(Of Animal) = New Pets()  
    pets.GetEnumerator()  
End Sub  
```  
  
 在此範例中，並未指定如何`pets.GetEnumerator`方法之間選擇`Cat`和`Dog`。 在程式碼中，這可能會造成問題。  
  
## <a name="see-also"></a>另請參閱  
 [泛型介面 (Visual Basic) 中的變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)   
 [針對 Func 與 Action 委派 (Visual Basic) 中使用變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
