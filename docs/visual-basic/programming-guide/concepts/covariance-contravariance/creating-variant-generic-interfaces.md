---
title: 建立 Variant 泛型介面 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d4037dd2-dfe9-4811-9150-93d4e8b20113
ms.openlocfilehash: d6afddf018b4608418f82fa851d018f2c3e1d0fb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663254"
---
# <a name="creating-variant-generic-interfaces-visual-basic"></a>建立 Variant 泛型介面 (Visual Basic)
您可以在介面中將泛型型別參數宣告為 Covariant 或 Contravariant。 「共變數」允許介面方法具有比泛型型別參數衍生程度更大的傳回型別。 「反變數」允許介面具有比泛型參數所指定引數型別衍生程度更小的引數類型。 具有 Covariant 或 Contravariant 泛型型別參數的泛型介面稱為「變異」。  
  
> [!NOTE]
>  .NET Framework 4 引入了對於數個現有泛型介面的變異數支援。 如需.NET Framework 中的 variant 介面清單，請參閱[泛型介面 (Visual Basic) 中的變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)。  
  
## <a name="declaring-variant-generic-interfaces"></a>宣告 Variant 泛型介面  
 您可以使用泛型型別參數的 `in` 和 `out` 關鍵字宣告 Variant 泛型介面。  
  
> [!IMPORTANT]
>  `ByRef` 在 Visual Basic 中的參數不可變動。 實值型別也不支援變異數。  
  
 您可以使用 `out` 關鍵字將泛型型別參數宣告為 Covariant 。 Covariant 類型必須滿足下列條件︰  
  
-   類型僅用為介面方法的傳回型別，不用為方法引數的類型。 這說明於下列範例中，其中 `R` 類型已宣告為 Covariant。  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        Function GetSomething() As R  
        ' The following statement generates a compiler error.  
        ' Sub SetSomething(ByVal sampleArg As R)  
    End Interface  
    ```  
  
     這個規則只有一個例外。 如果您以 Contravariant 泛型委派作為方法參數，則可將類型用作委派的泛型型別參數。 以下範例的 `R` 類型說明這種情況： 如需詳細資訊，請參閱 <<c0> [ 委派 (Visual Basic) 中的變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)並[針對 Func 與 Action 泛型委派 (Visual Basic) 使用差異](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)。  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        Sub DoSomething(ByVal callback As Action(Of R))  
    End Interface  
    ```  
  
-   類型不會用作介面方法的泛型條件約束。 下列程式碼說明此情形。  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        ' The following statement generates a compiler error  
        ' because you can use only contravariant or invariant types  
        ' in generic contstraints.  
        ' Sub DoSomething(Of T As R)()  
    End Interface  
    ```  
  
 您可以使用 `in` 關鍵字將泛型型別參數宣告為 Contravariant 。 Contravariant 類型僅可用作方法引數的類型，而不能用作介面方法的傳回型別。 Contravariant 類型也用於泛型條件約束。 下列程式碼示範如何宣告 Contravariant 介面，並針對其中一個方法使用泛型條件約束。  
  
```vb  
Interface IContravariant(Of In A)  
    Sub SetSomething(ByVal sampleArg As A)  
    Sub DoSomething(Of T As A)()  
    ' The following statement generates a compiler error.  
    ' Function GetSomething() As A  
End Interface  
```  
  
 也可以在相同介面中同時支援共變數和反變數，但是對於不同的型別參數，如下列程式碼範例所示。  
  
```vb  
Interface IVariant(Of Out R, In A)  
    Function GetSomething() As R  
    Sub SetSomething(ByVal sampleArg As A)  
    Function GetSetSomething(ByVal sampleArg As A) As R  
End Interface  
```  
  
 在 Visual Basic 中，您無法宣告 variant 介面中的事件，但未指定的委派型別。 此外，類別、 列舉或結構，變異數介面不能有巢狀，但它可以有巢狀介面。 下列程式碼說明此情形。  
  
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
 您可以使用用於非變異介面的相同語法，在類別中實作 Variant 泛型介面。 下列程式碼範例示範如何在泛型類別中實作 Covariant 介面。  
  
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
  
 實作 Variant 介面的類別為非變異。 例如，試想下列程式碼。  
  
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
  
## <a name="extending-variant-generic-interfaces"></a>擴充 Variant 泛型介面  
 當您擴充 Variant 泛型介面時，必須使用 `in` 和 `out` 關鍵字明確指定衍生的介面是否支援變異數。 編譯器不會從要擴充的介面推斷變異數。 例如，請參考下列介面。  
  
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
  
 在 `Invariant(Of T)`介面，泛型類型參數`T`為非變異，而在`IExtCovariant (Of Out T)`型別參數是 covariant，雖然這兩個介面都擴充相同的介面。 相同的規則也套用至 Contravariant 泛型型別參數。  
  
 您可以建立介面，以便擴充 `T` 泛型型別參數為 Covariant 的介面，以及如果在擴充介面中， `T` 泛型型別參數為非變異的情況下，擴充其為 Contravariant 的介面。 下列程式碼範例說明此情形。  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
Interface IContravariant(Of In T)  
End Interface  
  
Interface IInvariant(Of T)  
    Inherits ICovariant(Of T), IContravariant(Of T)  
End Interface  
```  
  
 不過，如果 `T` 泛型型別參數在一個介面中宣告為 Covariant，則無法在擴充的介面中將它宣告為 Contravariant，反之亦然。 下列程式碼範例說明此情形。  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
' The following statements generate a compiler error.  
' Interface ICoContraVariant(Of In T)  
'     Inherits ICovariant(Of T)  
' End Interface  
```  
  
### <a name="avoiding-ambiguity"></a>避免語意模糊  
 當您實作 Variant 泛型介面時，變異數有時會導致語意模糊。 對此應該要設法避免。  
  
 例如，如果您在一個類別中，明確地實作相同 Variant 泛型介面與不同泛型型別參數，它可能會造成語意模糊。 在此情況下，編譯器不會產生錯誤，但未指定在執行階段將選擇哪個介面實作。 這可能會導致您的程式碼中有細微錯誤。 請參考下列程式碼範例。  
  
> [!NOTE]
>  使用`Option Strict Off`，Visual Basic 會產生編譯器警告，模稜兩可的介面實作時。 使用`Option Strict On`，Visual Basic 會產生編譯器錯誤。  
  
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
  
 在此範例中，並未指定 `pets.GetEnumerator` 方法如何在 `Cat` 和 `Dog` 之間選擇。 這可能會在程式碼中造成問題。  
  
## <a name="see-also"></a>另請參閱
- [泛型介面中的變異數 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [針對 Func 與 Action 泛型委派使用變異數 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
