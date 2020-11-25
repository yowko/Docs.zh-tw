---
title: 例外狀況和效能
ms.date: 10/22/2008
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
ms.openlocfilehash: babe378e0d61357709006e08f71ff578492f116c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734747"
---
# <a name="exceptions-and-performance"></a>例外狀況和效能

與例外狀況相關的其中一個常見考慮是，如果例外狀況是用於經常失敗的程式碼，就無法接受執行的效能。 此顧慮是有效的。 當成員擲回例外狀況時，其效能可能會以較慢的順序排列。 不過，您可以達到良好的效能，同時嚴格遵守不允許使用錯誤碼的例外狀況指導方針。 本章節所述的兩種模式會建議您這樣做。

 ❌ 由於例外狀況可能會對效能造成負面影響，因此請勿使用錯誤碼。

 若要改善效能，您可以使用 Tester-Doer 模式或 Try-Parse 模式，如接下來的兩節所述。

## <a name="tester-doer-pattern"></a>Tester-Doer 模式

 有時候例外狀況擲回成員的效能，可以藉由將成員分成兩個來改善。 讓我們看看 <xref:System.Collections.Generic.ICollection%601.Add%2A> 介面的方法 <xref:System.Collections.Generic.ICollection%601> 。

```csharp
ICollection<int> numbers = ...
numbers.Add(1);
```

 `Add`如果集合是唯讀的，方法會擲回。 如果預期方法呼叫通常會失敗，這可能會造成效能問題。 解決問題的其中一種方法，是在嘗試加入值之前測試是否可寫入集合。

```csharp
ICollection<int> numbers = ...
...
if (!numbers.IsReadOnly)
{
    numbers.Add(1);
}
```

 用來測試條件的成員（在我們的範例中為屬性）稱為「測試人員」（test） `IsReadOnly` 。 用來執行可能擲回作業的成員（ `Add` 在我們的範例中為方法）稱為惡人之手。

 ✔️針對可能會在常見案例中擲回例外狀況的成員考慮 Tester-Doer 模式，以避免與例外狀況相關的效能問題。

## <a name="try-parse-pattern"></a>Try-Parse 模式

 針對極具效能效益的 Api，您應該使用比上一節所述的 Tester-Doer 模式更快的模式。 模式會呼叫以調整成員名稱，使定義完善的測試案例成為成員語義的一部分。 例如， <xref:System.DateTime> 定義 <xref:System.DateTime.Parse%2A> 當字串剖析失敗時擲回例外狀況的方法。 它也會定義 <xref:System.DateTime.TryParse%2A> 嘗試剖析的對應方法，但如果剖析失敗，則會傳回 false，並傳回使用參數成功剖析的結果 `out` 。

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

 使用此模式時，請務必以嚴格的條款來定義 try 功能。 如果成員因為明確定義的 try 以外的任何原因而失敗，則成員仍然必須擲回對應的例外狀況。

 ✔️針對可能會在常見案例中擲回例外狀況的成員考慮 Try-Parse 模式，以避免與例外狀況相關的效能問題。

 ✔️針對實作為此模式的方法，請使用前置詞 "Try" 和布林傳回型別。

 ✔️使用 Try-Parse 模式，為每個成員提供例外狀況擲回成員。

 *部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>另請參閱

- [架構設計指導方針](index.md)
- [例外狀況的設計方針](exceptions.md)
