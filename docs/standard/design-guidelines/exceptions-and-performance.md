---
title: 例外狀況和效能
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
ms.openlocfilehash: e3a7fa0f284ebf028a18cae37c050d7ceda9bb79
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709383"
---
# <a name="exceptions-and-performance"></a>例外狀況和效能
例外狀況的其中一個常見問題是，如果例外狀況是用於經常失敗的程式碼，則無法接受執行的效能。 這是有效的考慮。 當成員擲回例外狀況時，其效能可能是速度較慢的順序。 不過，您可以達成良好的效能，同時嚴格遵守不允許使用錯誤碼的例外狀況指導方針。 本節所述的兩種模式會建議執行這項操作的方式。

 **X**不會使用錯誤碼，因為例外狀況可能會對效能造成負面影響。

 若要改善效能，您可以使用惡人之手模式或 Try-Parse 模式，如下兩節所述。

## <a name="tester-doer-pattern"></a>測試人員-惡人之手模式
 有時候，例外狀況擲回成員的效能可以藉由將成員分成兩個來改善。 讓我們看看 <xref:System.Collections.Generic.ICollection%601> 介面的 <xref:System.Collections.Generic.ICollection%601.Add%2A> 方法。

```csharp
ICollection<int> numbers = ...
numbers.Add(1);
```

 如果集合是唯讀的，則方法 `Add` 擲回。 這可能會在方法呼叫預期經常失敗的情況下，發生效能問題。 解決此問題的其中一個方法，就是先測試集合是否為可寫入，再嘗試加入值。

```csharp
ICollection<int> numbers = ...
...
if (!numbers.IsReadOnly)
{
    numbers.Add(1);
}
```

 用來測試條件的成員（在我們的範例中是 `IsReadOnly`的屬性，稱為「測試者」）。 用來執行可能擲回作業的成員（在我們的範例中為 `Add` 方法）稱為惡人之手。

 **✓請考慮**在常見案例中可能會擲回例外狀況之成員的測試人員-惡人之手模式，以避免與例外狀況相關的效能問題。

## <a name="try-parse-pattern"></a>Try-剖析模式
 對於非常效能敏感的 Api，應使用比上一節中所述的測試人員惡人之手模式更快的模式。 模式會呼叫來調整成員名稱，讓定義完善的測試案例成為成員語義的一部分。 例如，如果字串的剖析失敗，<xref:System.DateTime> 會定義會擲回例外狀況的 <xref:System.DateTime.Parse%2A> 方法。 它也會定義嘗試剖析的對應 <xref:System.DateTime.TryParse%2A> 方法，但如果剖析不成功，則會傳回 false，並使用 `out` 參數傳回成功剖析的結果。

```csharp
public struct DateTime
{
    public static DateTime Parse(string dateTime)
    {
        ...
    }
    public static bool TryParse(string dateTime, out DateTime result)
    {
        ...
    }
}
```

 使用此模式時，請務必以嚴格的條款定義 try 功能。 如果成員因為任何不是妥善定義的嘗試而失敗，則成員仍然必須擲回對應的例外狀況。

 **✓請考慮**可能會在常見案例中擲回例外狀況的成員的 Try 剖析模式，以避免與例外狀況相關的效能問題。

 **✓ DO**會針對實作為此模式的方法，使用前置詞「Try」和布林傳回型別。

 **✓**會使用嘗試剖析模式，為每個成員提供例外狀況擲回的成員。

 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
- [例外狀況的設計方針](../../../docs/standard/design-guidelines/exceptions.md)
