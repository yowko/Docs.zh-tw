---
title: 結構設計
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
ms.openlocfilehash: b6d06bc8a1e8535f1452af0726138abaebfd4951
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743609"
---
# <a name="struct-design"></a>結構設計
一般用途的實值型別通常稱為結構，也就是它C#的關鍵字。 本節提供一般結構設計的指導方針。

 ❌ 不提供結構的無參數的函式。

 遵循此指導方針，可讓您建立結構陣列，而不需要在陣列的每個專案上執行此函式。 請注意C# ，不允許結構具有無參數的函數。

 ❌ 不會定義可變的實值型別。

 可變的實值型別有幾個問題。 例如，當屬性 getter 傳回實數值型別時，呼叫端會收到複本。 因為複本是以隱含方式建立的，所以開發人員可能不知道它們會改變複本，而不是原始值。 此外，某些語言（尤其是動態語言）在使用可變值型別時遇到問題，因為在取值時，即使是區域變數，也會造成複製的執行。

 ✔️確實確定所有實例資料設定為零、false 或 null （適當）的狀態都是有效的。

 這可避免在建立結構的陣列時，意外建立不正確實例。

 ✔️在實數值型別上執行 <xref:System.IEquatable%601>。

 實值型別上的 <xref:System.Object.Equals%2A?displayProperty=nameWithType> 方法會造成「裝箱」，而且它的預設執行不會非常有效率，因為它會使用反映。 <xref:System.IEquatable%601.Equals%2A> 可以有更好的效能，而且可以實作為不會造成裝箱的問題。

 ❌ 不會明確地延伸 <xref:System.ValueType>。 事實上，大部分的語言都會阻止這種情況。

 一般來說，結構可能非常有用，但僅適用于不會頻繁地裝箱的小型、單一、不可變的值。

 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>請參閱

- [類型設計方針](../../../docs/standard/design-guidelines/type.md)
- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
- [在類別和結構之間選擇](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
