---
title: 泛型介面 (Visual Basic) 中的變異數
ms.date: 07/20/2015
ms.assetid: cf4096d0-4bb3-45a9-9a6b-f01e29a60333
ms.openlocfilehash: 50a1aeb5c17a0f193b9e90ca2167ef298f7ed237
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828104"
---
# <a name="variance-in-generic-interfaces-visual-basic"></a>泛型介面 (Visual Basic) 中的變異數
.NET Framework 4 引入了對於數個現有泛型介面的變異數支援。 差異支援可讓實作這些介面的類別以隱含方式轉換。 下列介面現在都是 Variant︰  
  
-   <xref:System.Collections.Generic.IEnumerable%601> (T 是 Covariant)  
  
-   <xref:System.Collections.Generic.IEnumerator%601> (T 是 Covariant)  
  
-   <xref:System.Linq.IQueryable%601> (T 是 Covariant)  
  
-   <xref:System.Linq.IGrouping%602> (`TKey` 和 `TElement` 都是 Covariant)  
  
-   <xref:System.Collections.Generic.IComparer%601> (T 是 Contravariant)  
  
-   <xref:System.Collections.Generic.IEqualityComparer%601> (T 是 Contravariant)  
  
-   <xref:System.IComparable%601> (T 是 Contravariant)  
  
 共變數允許方法具有比介面泛型型別參數所定義之衍生程度更大的傳回型別。 若要示範共變數功能，請考慮這些泛型介面︰`IEnumerable(Of Object)` 和 `IEnumerable(Of String)`。 `IEnumerable(Of String)` 介面不會繼承 `IEnumerable(Of Object)` 介面。 不過，`String` 型別確實會繼承`Object` 型別，而且在某些情況下，您可能希望將這些介面的物件指派給彼此。 這會顯示在以下程式碼範例中。  
  
```vb  
Dim strings As IEnumerable(Of String) = New List(Of String)  
Dim objects As IEnumerable(Of Object) = strings  
```  
  
 在舊版的.NET Framework 中，此程式碼會造成編譯錯誤，在 Visual Basic 搭配`Option Strict On`。 但現在您可以使用 `strings`，而不使用 `objects`，如上例所示，因為 <xref:System.Collections.Generic.IEnumerable%601> 介面是 Covariant。  
  
 反變數允許方法具有比介面泛型參數所指定之衍生程度更小的引數型別。 為示範反變數，我們假設您已建立 `BaseComparer` 類別來比較 `BaseClass` 類別的執行個體。 `BaseComparer` 類別會實作 `IEqualityComparer(Of BaseClass)` 介面。 因為 <xref:System.Collections.Generic.IEqualityComparer%601> 介面現在是 Contravariant，所以您可以使用 `BaseComparer` 比較繼承了 `BaseClass` 類別的類別執行個體。 這會顯示在以下程式碼範例中。  
  
```vb  
' Simple hierarchy of classes.  
Class BaseClass  
End Class  
  
Class DerivedClass  
    Inherits BaseClass  
End Class  
  
' Comparer class.  
Class BaseComparer  
    Implements IEqualityComparer(Of BaseClass)  
  
    Public Function Equals1(ByVal x As BaseClass,  
                            ByVal y As BaseClass) As Boolean _  
                            Implements IEqualityComparer(Of BaseClass).Equals  
        Return (x.Equals(y))  
    End Function  
  
    Public Function GetHashCode1(ByVal obj As BaseClass) As Integer _  
        Implements IEqualityComparer(Of BaseClass).GetHashCode  
        Return obj.GetHashCode  
    End Function  
End Class  
Sub Test()  
    Dim baseComparer As IEqualityComparer(Of BaseClass) = New BaseComparer  
    ' Implicit conversion of IEqualityComparer(Of BaseClass) to   
    ' IEqualityComparer(Of DerivedClass).  
    Dim childComparer As IEqualityComparer(Of DerivedClass) = baseComparer  
End Sub  
```  
  
 如需其他範例，請參閱 <<c0> [ 針對泛型集合 (Visual Basic) 的介面中的 使用差異](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)。  
  
 僅參考型別支援泛型介面的差異。 實值型別不支援差異。 例如，`IEnumerable(Of Integer)` 無法以隱含方式轉換成 `IEnumerable(Of Object)`，因為整數是以實值型別表示。  
  
```vb  
Dim integers As IEnumerable(Of Integer) = New List(Of Integer)  
' The following statement generates a compiler error  
' with Option Strict On, because Integer is a value type.  
' Dim objects As IEnumerable(Of Object) = integers  
```  
  
 請務必牢記，實作 Variant 介面的類別仍然是非變異的。 例如，雖然 <xref:System.Collections.Generic.List%601> 實作了 Covariant 介面 <xref:System.Collections.Generic.IEnumerable%601>，但您不能以隱含方式將 `List(Of Object)` 轉換成 `List(Of String)`。 下列程式碼範例說明此情形。  
  
```vb  
' The following statement generates a compiler error  
' because classes are invariant.  
' Dim list As List(Of Object) = New List(Of String)  
  
' You can use the interface object instead.  
Dim listObjects As IEnumerable(Of Object) = New List(Of String)  
```  
  
## <a name="see-also"></a>另請參閱

- [使用泛型集合介面中的變異數 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)
- [建立 Variant 泛型介面 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)
- [泛型介面](../../../../standard/generics/interfaces.md)
- [委派中的變異數 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
