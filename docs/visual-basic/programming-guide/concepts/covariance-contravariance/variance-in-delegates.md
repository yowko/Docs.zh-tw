---
title: "委派 (Visual Basic) 中的變異數"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 38e9353f-74f8-4211-a8f0-7a495414df4a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9fe76a32f76f760497021289ec1c6ce673cec1b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="variance-in-delegates-visual-basic"></a>委派 (Visual Basic) 中的變異數
.NET framework 3.5 引入了使用所有的委派，在 C# 和 Visual Basic 中的委派型別比對方法簽章的支援變異數。 這表示您可以指派給委派的不只是具有相符簽章的方法，也可以是會傳回更多衍生型別 (共變數) 的方法，或接受衍生型別 (反變數) 比委派型別指定少的參數的方法。 這包括泛型和非泛型委派。  
  
 例如，請考慮下列程式碼，有兩個類別和兩個委派︰泛型和非泛型。  
  
```vb  
Public Class First  
End Class  
  
Public Class Second  
    Inherits First  
End Class  
  
Public Delegate Function SampleDelegate(ByVal a As Second) As First  
Public Delegate Function SampleGenericDelegate(Of A, R)(ByVal a As A) As R  
```  
  
 當您建立 `SampleDelegate` 或 `SampleDelegate(Of A, R)` 型別的委派時，您可以指派下列任一方法給這些委派。  
  
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
  
 下列程式碼範例會示範方法簽章與委派型別之間的隱含轉換。  
  
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
  
 如需其他範例，請參閱[使用委派 (Visual Basic) 中的變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)和[Func 與 Action 委派 (Visual Basic) 使用變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)。  
  
## <a name="variance-in-generic-type-parameters"></a>泛型型別參數中的差異  
 在.NET Framework 4 和更新版本，以便有泛型型別參數所指定的不同類型的泛型委派可以指派給彼此，如果所需的型別繼承自彼此，您可以啟用委派之間的隱含轉換變異數。  
  
 若要啟用隱含轉換，您必須使用 `in` 或 `out` 關鍵字，明確宣告委派中的泛型參數為 Covariant 或 Contravariant。  
  
 下列程式碼範例示範如何建立具有 Covariant 泛型型別參數的委派。  
  
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
  
 如果您使用唯一的差異支援來比對方法簽章與委派型別，請不要使用 `in` 和 `out` 關鍵字，因為您會發現，有時候您會使用相同的 lambda 運算式或方法具現化委派，但無法將一個委派指派給另一個。  
  
 在下列程式碼範例中，`SampleGenericDelegate(Of String)`無法明確地轉換成`SampleGenericDelegate(Of Object)`，不過`String`繼承`Object`。 您可以使用 `out` 關鍵字標記泛型參數 `T`，修正這個問題。  
  
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
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a>.NET Framework 中具有 Variant 型別參數的泛型委派  
 .NET Framework 4 推出差異支援，適用於數個現有泛型委派中的泛型型別參數：  
  
-   <xref:System> 命名空間中的 `Action` 委派，例如 <xref:System.Action%601> 和 <xref:System.Action%602>  
  
-   <xref:System> 命名空間中的 `Func` 委派，例如 <xref:System.Func%601> 和 <xref:System.Func%602>  
  
-   <xref:System.Predicate%601> 委派  
  
-   <xref:System.Comparison%601> 委派  
  
-   <xref:System.Converter%602> 委派  
  
 如需詳細資訊和範例，請參閱[Func 與 Action 委派 (Visual Basic) 使用變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)。  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a>宣告泛型委派中的 Variant 型別參數  
 如果泛型委派具有 Covariant 或 Contravariant 泛型型別參數，它可以稱之為「Variant 泛型委派」。  
  
 您可以使用 `out` 關鍵字將泛型委派中的泛型型別參數宣告為 Covariant。 Covariant 型別僅可用為方法傳回型別，不能用為方法引數的型別。 以下程式碼範例會示範如何宣告 Covariant 泛型委派。  
  
```vb  
Public Delegate Function DCovariant(Of Out R)() As R  
```  
  
 您可以使用 `in` 關鍵字將泛型委派中的泛型型別參數宣告為 Contravariant。 Contravariant 型別僅可用為方法引數的型別，不能用為方法傳回型別。 以下程式碼範例會示範如何宣告 Contravariant 泛型委派。  
  
```vb  
Public Delegate Sub DContravariant(Of In A)(ByVal a As A)  
```  
  
> [!IMPORTANT]
>  `ByRef`在 Visual Basic 中的參數不能標示為 variant。  
  
 您也可以支援相同委派中不同型別參數的差異和共變數。 這在下列範例中顯示。  
  
```vb  
Public Delegate Function DVariant(Of In A, Out R)(ByVal a As A) As R  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a>具現化及叫用 Variant 泛型委派  
 您可以具現化及叫用 Variant 委派，一如您具現化及叫用非變異委派。 在下例中，委派是由 lambda 運算式具現化。  
  
```vb  
Dim dvariant As DVariant(Of String, String) = Function(str) str + " "  
dvariant("test")  
```  
  
### <a name="combining-variant-generic-delegates"></a>結合 Variant 泛型委派  
 您不應該組合 Variant 委派。 <xref:System.Delegate.Combine%2A> 方法不支援 Variant 委派轉換，且委派的類型必須完全一致。 這可能會導致執行階段例外狀況時結合使用委派<xref:System.Delegate.Combine%2A>方法 （在 C# 和 Visual Basic） 或使用`+`運算子 （C# 中），如下列程式碼範例所示。  
  
```vb  
Dim actObj As Action(Of Object) = Sub(x) Console.WriteLine("object: {0}", x)  
Dim actStr As Action(Of String) = Sub(x) Console.WriteLine("string: {0}", x)  
  
' The following statement throws an exception at run time.  
' Dim actCombine = [Delegate].Combine(actStr, actObj)  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a>實值型別和參考型別的泛型型別參數中的差異  
 僅參考型別支援泛型型別參數的差異。 例如，`DVariant(Of Int)`無法隱含地轉換成`DVariant(Of Object)`或`DVariant(Of Long)`，因為整數是實值類型。  
  
 下例示範實值型別不支援的泛型型別參數的差異。  
  
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
  
## <a name="relaxed-delegate-conversion-in-visual-basic"></a>在 Visual Basic 中的寬鬆的委派轉換  
 寬鬆的委派轉換可讓您更有彈性地使用委派型別比對方法簽章。 例如，它可讓您可以省略參數規格，並省略函式傳回值，當您指派給委派的方法。 如需詳細資訊，請參閱[寬鬆委派轉換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。  
  
## <a name="see-also"></a>另請參閱  
 [泛型](~/docs/standard/generics/index.md)  
 [針對 Func 與 Action 泛型委派使用變異數 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
