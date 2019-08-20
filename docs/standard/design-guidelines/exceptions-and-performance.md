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
author: KrzysztofCwalina
ms.openlocfilehash: 967692092186b81802a7ab635ea8fe4dbacd49ed
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69611512"
---
# <a name="exceptions-and-performance"></a>例外狀況和效能
例外狀況的其中一個常見問題是, 如果例外狀況是用於經常失敗的程式碼, 則無法接受執行的效能。 這是有效的考慮。 當成員擲回例外狀況時, 其效能可能是速度較慢的順序。 不過, 您可以達成良好的效能, 同時嚴格遵守不允許使用錯誤碼的例外狀況指導方針。 本節所述的兩種模式會建議執行這項操作的方式。

 **X DO NOT** 使用錯誤碼，例外狀況可能會造成負面影響效能的考量。

 若要改善效能, 您可以使用惡人之手模式或 Try-Parse 模式, 如下兩節所述。

## <a name="tester-doer-pattern"></a>測試人員-惡人之手模式
 有時候, 例外狀況擲回成員的效能可以藉由將成員分成兩個來改善。 讓我們看看<xref:System.Collections.Generic.ICollection%601.Add%2A> <xref:System.Collections.Generic.ICollection%601>介面的方法。

```csharp
ICollection<int> numbers = ...
numbers.Add(1);
```

 如果集合`Add`是唯讀的, 方法會擲回。 這可能會在方法呼叫預期經常失敗的情況下, 發生效能問題。 解決此問題的其中一個方法, 就是先測試集合是否為可寫入, 再嘗試加入值。

```csharp
ICollection<int> numbers = ...
...
if (!numbers.IsReadOnly)
{
    numbers.Add(1);
}
```

 用來測試條件的成員 (在我們的範例中為屬性`IsReadOnly`) 稱為「測試者」。 用來執行可能擲回作業的成員 (在`Add`我們的範例中為方法) 稱為惡人之手。

 **✓ CONSIDER** Tester-doer 模式，可能會擲回例外狀況的成員在一般案例，以避免發生效能問題相關的例外狀況。

## <a name="try-parse-pattern"></a>Try-剖析模式
 對於非常效能敏感的 Api, 應使用比上一節中所述的測試人員惡人之手模式更快的模式。 模式會呼叫來調整成員名稱, 讓定義完善的測試案例成為成員語義的一部分。 例如, <xref:System.DateTime>會<xref:System.DateTime.Parse%2A>定義方法, 如果字串剖析失敗, 則會擲回例外狀況。 它也會定義嘗試<xref:System.DateTime.TryParse%2A>剖析的對應方法, 但如果剖析不成功, 則會傳回 false, 並`out`使用參數傳回成功剖析的結果。

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

 使用此模式時, 請務必以嚴格的條款定義 try 功能。 如果成員因為任何不是妥善定義的嘗試而失敗, 則成員仍然必須擲回對應的例外狀況。

 **✓ CONSIDER** 再試一次剖析模式，可能會擲回例外狀況的成員在一般案例，以避免發生效能問題相關的例外狀況。

 **✓ DO** 方法實作這個模式使用的前置詞"Try"和布林值傳回型別。

 **✓ DO** 擲回例外狀況的成員提供使用 Try 剖析模式，每個成員。

 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

 *從[架構設計方針轉載已獲得皮耳森教育, inc. 的許可權:Krzysztof Cwalina 和 Brad Abrams 可重複使用的 .net 程式庫第](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 2 版的慣例、慣用語和模式, 已于2008年10月22日發行, 屬於 Microsoft Windows 開發系列的 Addison-Wesley Professional。*

## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
- [例外狀況的設計方針](../../../docs/standard/design-guidelines/exceptions.md)
