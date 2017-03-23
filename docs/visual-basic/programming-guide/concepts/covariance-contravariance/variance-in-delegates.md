---
title: "委派 (Visual Basic) 中的變異數 |Microsoft 文件"
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
ms.assetid: 38e9353f-74f8-4211-a8f0-7a495414df4a
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
ms.openlocfilehash: cbab7da8c97ca202f8a4d0a1a65b8fa240cca32d
ms.lasthandoff: 03/13/2017

---
# <a name="variance-in-delegates-visual-basic"></a>委派 (Visual Basic) 中的變異數
.NET framework 3.5 引入變異數支援使用所有的委派，在 C# 和 Visual Basic 中的委派型別比對方法簽章。 這表示您可以指派給委派不只具有相符簽章的方法，也會傳回更多衍生類型 （共變數），或接受具有較少衍生的型別 （反變數） 比指定的委派型別參數的方法。 這包括泛型和非泛型委派。  
  
 例如，請考慮下列程式碼，有兩個類別和兩個委派︰ 泛型和非泛型。  
  
```vb  
Public Class First  
End Class  
  
Public Class Second  
    Inherits First  
End Class  
  
Public Delegate Function SampleDelegate(ByVal a As Second) As First  
Public Delegate Function SampleGenericDelegate(Of A, R)(ByVal a As A) As R  
```  
  
 當您建立的委派`SampleDelegate`或`SampleDelegate(Of A, R)`型別，您可以指派下列方法其中給這些委派。  
  
```vb  
' Matching signature.  
Public Shared Function ASecondRFirst(  
    ByVal second As Second) As First  
    Return New First()  
End Function  
  
' The return type is more derived.  
Public Shared Function ASecondRSecond(  
    ByVal second As Second) As Second  
    Return New Second()  
End Function  
  
' The argument type is less derived.  
Public Shared Function AFirstRFirst(  
    ByVal first As First) As First  
    Return New First()  
End Function  
  
' The return type is more derived   
' and the argument type is less derived.  
Public Shared Function AFirstRSecond(  
    ByVal first As First) As Second  
    Return New Second()  
End Function  
```  
  
 下列程式碼範例說明的方法簽章與委派型別之間隱含轉換。  
  
```vb  
' Assigning a method with a matching signature   
' to a non-generic delegate. No conversion is necessary.  
Dim dNonGeneric As SampleDelegate = AddressOf ASecondRFirst  
' Assigning a method with a more derived return type   
' and less derived argument type to a non-generic delegate.  
' The implicit conversion is used.  
Dim dNonGenericConversion As SampleDelegate = AddressOf AFirstRSecond  
  
' Assigning a method with a matching signature to a generic delegate.  
' No conversion is necessary.  
Dim dGeneric As SampleGenericDelegate(Of Second, First) = AddressOf ASecondRFirst  
' Assigning a method with a more derived return type   
' and less derived argument type to a generic delegate.  
' The implicit conversion is used.  
Dim dGenericConversion As SampleGenericDelegate(Of Second, First) = AddressOf AFirstRSecond  
```  
  
 如需詳細資訊，請參閱[使用委派 (Visual Basic) 中的變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)和[Func 與 Action 委派 (Visual Basic) 使用變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)。  
  
## <a name="variance-in-generic-type-parameters"></a>泛型型別參數中的變異數  
 在.NET Framework 4 和更新版本可以啟用委派之間的隱含轉換，因此可以有不同類型的泛型型別參數所指定的泛型委派指派給彼此，如果型別繼承自其他所需的變異數。  
  
 若要啟用的隱含轉換，您必須明確宣告泛用參數中的委派做為 covariant 或 contravariant 使用`in`或`out`關鍵字。  
  
 下列程式碼範例示範如何建立具有共變性泛型型別參數的委派。  
  
```vb  
' Type T is declared covariant by using the out keyword.  
Public Delegate Function SampleGenericDelegate(Of Out T)() As T  
Sub Test()  
    Dim dString As SampleGenericDelegate(Of String) = Function() " "  
    ' You can assign delegates to each other,  
    ' because the type T is declared covariant.  
    Dim dObject As SampleGenericDelegate(Of Object) = dString  
End Sub  
```  
  
 如果您使用唯一的差異支援比對方法簽章與委派型別，並且不要使用`in`和`out`關鍵字，您可能會發現有時候執行個體化使用相同的 lambda 運算式或方法的委派，但您無法將一個委派指派給另一個。  
  
 在下列程式碼範例中，`SampleGenericDelegate(Of String)`無法明確地轉換成`SampleGenericDelegate(Of Object)`，不過`String`繼承`Object`。 您可以修正這個問題，是將泛型參數標記`T`與`out`關鍵字。  
  
```vb  
Public Delegate Function SampleGenericDelegate(Of T)() As T  
Sub Test()  
    Dim dString As SampleGenericDelegate(Of String) = Function() " "  
  
    ' You can assign the dObject delegate  
    ' to the same lambda expression as dString delegate  
    ' because of the variance support for   
    ' matching method signatures with delegate types.  
    Dim dObject As SampleGenericDelegate(Of Object) = Function() " "  
  
    ' The following statement generates a compiler error  
    ' because the generic type T is not marked as covariant.  
    ' Dim dObject As SampleGenericDelegate(Of Object) = dString  
  
End Sub  
```  
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a>在具有變異的泛型委派在.NET Framework 型別參數  
 .NET framework 4 引入變異數支援數個現有的泛型委派中的泛型型別參數︰  
  
-   `Action`從委派<xref:System>命名空間，例如<xref:System.Action%601>和<xref:System.Action%602></xref:System.Action%602></xref:System.Action%601></xref:System>  
  
-   `Func`從委派<xref:System>命名空間，例如<xref:System.Func%601>和<xref:System.Func%602></xref:System.Func%602></xref:System.Func%601></xref:System>  
  
-   <xref:System.Predicate%601>委派</xref:System.Predicate%601>  
  
-   <xref:System.Comparison%601>委派</xref:System.Comparison%601>  
  
-   <xref:System.Converter%602>委派</xref:System.Converter%602>  
  
 如需詳細資訊和範例，請參閱[Func 與 Action 委派 (Visual Basic) 使用變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)。  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a>宣告泛型委派中的 Variant 類型參數  
 如果泛型委派具有 covariant 或 contravariant 的泛型型別參數，它可以稱為*variant 泛型委派*。  
  
 您可以宣告泛型型別參數中的泛型委派的共變數使用`out`關鍵字。 可以使用 covariant 類型，只要方法的傳回型別，而不是一種方法引數。 下列程式碼範例示範如何宣告共變性泛型委派。  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
 您可以使用宣告中的泛型委派的泛型型別參數 contravariant`in`關鍵字。 可以使用 contravariant 類型，只為方法引數的型別，而不是方法的傳回型別。 下列程式碼範例示範如何宣告 contravariant 的泛型委派。  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
> [!IMPORTANT]
>  `ByRef`在 Visual Basic 中的參數不能標示為 variant。  
  
 此外，也可以在相同的委派，但不同的型別參數支援共變數和變異數。 這在下列範例中顯示。  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a>具現化，並叫用 Variant 泛型委派  
 您可以具現化，並叫用 variant 的委派，就像您具現化，並叫用委派而異。 在下列範例中，委派是 lambda 運算式所具現化。  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
### <a name="combining-variant-generic-delegates"></a>結合 Variant 泛型委派  
 您不應該結合 variant 的委派。 <xref:System.Delegate.Combine%2A>方法不支援 variant 委派轉換，而且必須是相同類型的委派。</xref:System.Delegate.Combine%2A> 這可能會導致執行階段例外狀況時結合使用委派<xref:System.Delegate.Combine%2A>方法 （在 C# 和 Visual Basic） 或使用`+`運算子 （C# 中），如下列程式碼範例所示。</xref:System.Delegate.Combine%2A>  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a>泛型型別參數的值和參考類型的變異數  
 參考型別只支援泛型型別參數的變異數。 例如，`DVariant(Of Int)`無法隱含地轉換成`DVariant(Of Object)`或`DVariant(Of Long)`，因為整數是實值型別。  
  
 下列範例示範的變異數的泛型型別參數不支援實值型別。  
  
```vb  
' The type T is covariant.  
Public Delegate Function DVariant(Of Out T)() As T  
' The type T is invariant.  
Public Delegate Function DInvariant(Of T)() As T  
Sub Test()  
    Dim i As Integer = 0  
    Dim dInt As DInvariant(Of Integer) = Function() i  
    Dim dVaraintInt As DVariant(Of Integer) = Function() i  
  
    ' All of the following statements generate a compiler error  
    ' because type variance in generic parameters is not supported  
    ' for value types, even if generic type parameters are declared variant.  
    ' Dim dObject As DInvariant(Of Object) = dInt  
    ' Dim dLong As DInvariant(Of Long) = dInt  
    ' Dim dVaraintObject As DInvariant(Of Object) = dInt  
    ' Dim dVaraintLong As DInvariant(Of Long) = dInt  
End Sub  
```  
  
## <a name="relaxed-delegate-conversion-in-visual-basic"></a>在 Visual Basic 中寬鬆的委派轉換  
 寬鬆的委派轉換可讓您更靈活地使用委派型別比對方法簽章。 比方說，它可讓您省略參數規格，並省略函式傳回值，當您指派給委派的方法。 如需詳細資訊，請參閱[寬鬆委派轉換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。  
  
## <a name="see-also"></a>另請參閱  
 [泛型](https://msdn.microsoft.com/library/ms172192)   
 [針對 Func 與 Action 委派 (Visual Basic) 中使用變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
