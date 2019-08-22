---
title: 委派中的變異數 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 38e9353f-74f8-4211-a8f0-7a495414df4a
ms.openlocfilehash: 0c52fd3fb36162de16a91a85088018f4f579611c
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664347"
---
# <a name="variance-in-delegates-visual-basic"></a>委派中的變異數 (Visual Basic)

.NET Framework 3.5 引進了變異數支援, 以便在和 Visual Basic 中C#的所有委派中, 將方法簽章與委派類型相符。 這表示您可以指派給委派的不只是具有相符簽章的方法，也可以是會傳回更多衍生型別 (共變數) 的方法，或接受衍生型別 (反變數) 比委派型別指定少的參數的方法。 這包括泛型和非泛型委派。

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

如需更多範例, 請參閱[在委派中使用變異數 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)和[針對 Func 和 Action 泛型委派使用變異數 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)。

## <a name="variance-in-generic-type-parameters"></a>泛型型別參數中的差異

在 .NET Framework 4 和更新版本中, 您可以啟用委派之間的隱含轉換, 讓具有泛型型別參數所指定之不同類型的泛型委派可以指派給彼此, 如果類型是由所需的彼此繼承變化.

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

在下列程式碼範例中`SampleGenericDelegate(Of String)` , 不能明確地`SampleGenericDelegate(Of Object)`轉換為`String` , `Object`不過會繼承。 您可以使用 `out` 關鍵字標記泛型參數 `T`，修正這個問題。

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

- <xref:System> 命名空間中的 `Action` 委派，例如 <xref:System.Action%601> 和 <xref:System.Action%602>

- <xref:System> 命名空間中的 `Func` 委派，例如 <xref:System.Func%601> 和 <xref:System.Func%602>

- <xref:System.Predicate%601> 委派

- <xref:System.Comparison%601> 委派

- <xref:System.Converter%602> 委派

如需詳細資訊和範例, 請參閱針對[Func 和 Action 泛型委派使用變異數 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)。

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
> `ByRef`Visual Basic 中的參數不能標記為 variant。

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

您不應該組合 Variant 委派。 <xref:System.Delegate.Combine%2A> 方法不支援 Variant 委派轉換，且委派的類型必須完全一致。 當<xref:System.Delegate.Combine%2A>您使用方法 (在和 Visual Basic 中C# ), `+`或使用運算子 (在中C#) 結合委派時, 這可能會導致執行時間例外狀況, 如下列程式碼範例所示。

```vb
Dim actObj As Action(Of Object) = Sub(x) Console.WriteLine("object: {0}", x)
Dim actStr As Action(Of String) = Sub(x) Console.WriteLine("string: {0}", x)

' The following statement throws an exception at run time.
' Dim actCombine = [Delegate].Combine(actStr, actObj)
```

## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a>實值型別和參考型別的泛型型別參數中的差異

僅參考型別支援泛型型別參數的差異。 例如, `DVariant(Of Int)`無法以隱含方式轉換成`DVariant(Of Object)`或`DVariant(Of Long)`, 因為 integer 是實值型別。

下例示範實值型別不支援的泛型型別參數的差異。

```vb
' The type T is covariant.
Public Delegate Function DVariant(Of Out T)() As T
' The type T is invariant.
Public Delegate Function DInvariant(Of T)() As T
Sub Test()
    Dim i As Integer = 0
    Dim dInt As DInvariant(Of Integer) = Function() i
    Dim dVariantInt As DVariant(Of Integer) = Function() i

    ' All of the following statements generate a compiler error
    ' because type variance in generic parameters is not supported
    ' for value types, even if generic type parameters are declared variant.
    ' Dim dObject As DInvariant(Of Object) = dInt
    ' Dim dLong As DInvariant(Of Long) = dInt
    ' Dim dVariantObject As DInvariant(Of Object) = dInt
    ' Dim dVariantLong As DInvariant(Of Long) = dInt
End Sub
```

## <a name="relaxed-delegate-conversion-in-visual-basic"></a>Visual Basic 中的寬鬆委派轉換

寬鬆委派轉換可讓您更有彈性地比對方法簽章與委派類型。 例如, 當您將方法指派給委派時, 它可讓您省略參數規格並省略函數傳回值。 如需詳細資訊, 請參閱[寬鬆委派轉換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。

## <a name="see-also"></a>另請參閱

- [泛型](../../../../standard/generics/index.md)
- [針對 Func 與 Action 泛型委派使用變異數 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
