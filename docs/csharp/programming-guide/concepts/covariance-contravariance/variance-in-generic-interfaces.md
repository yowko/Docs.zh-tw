---
title: 泛型介面中的差異 (C#)
ms.date: 06/06/2019
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: 71225814a11074f52e4937dec88ca5e27114d6c7
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179053"
---
# <a name="variance-in-generic-interfaces-c"></a>泛型介面中的差異 (C#)

.NET Framework 4 針對數個現有泛型介面推出了差異支援。 差異支援可讓實作這些介面的類別以隱含方式轉換。 

從 .NET Framework 4 開始，下列介面是 variant：

- <xref:System.Collections.Generic.IEnumerable%601> (T 是 Covariant)

- <xref:System.Collections.Generic.IEnumerator%601> (T 是 Covariant)

- <xref:System.Linq.IQueryable%601> (T 是 Covariant)

- <xref:System.Linq.IGrouping%602> (`TKey` 和 `TElement` 都是 Covariant)

- <xref:System.Collections.Generic.IComparer%601> (T 是 Contravariant)

- <xref:System.Collections.Generic.IEqualityComparer%601> (T 是 Contravariant)

- <xref:System.IComparable%601> (T 是 Contravariant)

開始使用 .NET Framework 4.5，下列介面是變數：

- <xref:System.Collections.Generic.IReadOnlyList%601> (T 是 Covariant)

- <xref:System.Collections.Generic.IReadOnlyCollection%601> (T 是 Covariant)

共變數允許方法具有比介面泛型型別參數所定義之衍生程度更大的傳回型別。 若要示範共變數功能，請考慮這些泛型介面︰`IEnumerable<Object>` 和 `IEnumerable<String>`。 `IEnumerable<String>` 介面不會繼承 `IEnumerable<Object>` 介面。 不過，`String` 型別確實會繼承`Object` 型別，而且在某些情況下，您可能希望將這些介面的物件指派給彼此。 這會顯示在以下程式碼範例中。

```csharp
IEnumerable<String> strings = new List<String>();
IEnumerable<Object> objects = strings;
```

在舊版的 .NET Framework 中，此程式碼會造成 C# 和 Visual Basic (如果開啟 `Option Strict`) 中的編譯錯誤。 但現在您可以使用 `strings`，而不使用 `objects`，如上例所示，因為 <xref:System.Collections.Generic.IEnumerable%601> 介面是 Covariant。

反變數允許方法具有比介面泛型參數所指定之衍生程度更小的引數型別。 為示範反變數，我們假設您已建立 `BaseComparer` 類別來比較 `BaseClass` 類別的執行個體。 `BaseComparer` 類別會實作 `IEqualityComparer<BaseClass>` 介面。 因為 <xref:System.Collections.Generic.IEqualityComparer%601> 介面現在是 Contravariant，所以您可以使用 `BaseComparer` 比較繼承了 `BaseClass` 類別的類別執行個體。 這會顯示在以下程式碼範例中。

```csharp
// Simple hierarchy of classes.
class BaseClass { }
class DerivedClass : BaseClass { }

// Comparer class.
class BaseComparer : IEqualityComparer<BaseClass>
{
    public int GetHashCode(BaseClass baseInstance)
    {
        return baseInstance.GetHashCode();
    }
    public bool Equals(BaseClass x, BaseClass y)
    {
        return x == y;
    }
}
class Program
{
    static void Test()
    {
        IEqualityComparer<BaseClass> baseComparer = new BaseComparer();

        // Implicit conversion of IEqualityComparer<BaseClass> to
        // IEqualityComparer<DerivedClass>.
        IEqualityComparer<DerivedClass> childComparer = baseComparer;
    }
}
```

如需更多範例，請參閱[針對泛型集合使用介面中的差異 (C#)](./using-variance-in-interfaces-for-generic-collections.md)。

僅參考型別支援泛型介面的差異。 實值型別不支援差異。 例如，`IEnumerable<int>` 無法以隱含方式轉換成 `IEnumerable<object>`，因為整數是以實值型別表示。

```csharp
IEnumerable<int> integers = new List<int>();
// The following statement generates a compiler error,
// because int is a value type.
// IEnumerable<Object> objects = integers;
```

請務必牢記，實作 Variant 介面的類別仍然是非變異的。 例如，雖然 <xref:System.Collections.Generic.List%601> 實作了 Covariant 介面 <xref:System.Collections.Generic.IEnumerable%601>，但您不能以隱含方式將 `List<String>` 轉換成 `List<Object>`。 下列程式碼範例說明此情形。

```csharp
// The following line generates a compiler error
// because classes are invariant.
// List<Object> list = new List<String>();

// You can use the interface object instead.
IEnumerable<Object> listObjects = new List<String>();
```

## <a name="see-also"></a>另請參閱

- [針對泛型集合使用介面中的差異 (C#)](./using-variance-in-interfaces-for-generic-collections.md)
- [建立 Variant 泛型介面 (C#)](./creating-variant-generic-interfaces.md)
- [泛型介面](../../../../standard/generics/interfaces.md)
- [委派中的差異 (C#)](./variance-in-delegates.md)
