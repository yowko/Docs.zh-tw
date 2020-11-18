---
title: 結構設計
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
ms.openlocfilehash: da831d1477b451131bb27372d65ad7229fcf3f77
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828617"
---
# <a name="struct-design"></a>結構設計
一般用途的實值型別通常稱為結構，也就是它的 c # 關鍵字。 本節提供一般結構設計的指導方針。

 ❌ 請勿為結構提供無參數的函式。

 遵循此指導方針可建立結構陣列，而不需要在陣列的每個專案上執行此函式。 請注意，c # 不允許結構具有無參數的函式。

 ❌ 請勿定義可變實數值型別。

 可變實值型別有幾個問題。 例如，當屬性 getter 傳回實值型別時，呼叫端會收到一份複本。 由於複本是以隱含方式建立的，因此開發人員可能不知道它們會改變複本，而不是原始值。 此外，某些語言 (動態語言，特別是) 在使用可變實值型別時遇到問題，因為即使是本機變數，當取值時，也會產生複製。

 ✔️確定所有實例資料都設定為零、false 或 null (適當的) 有效的狀態。

 這可防止在建立結構陣列時，意外建立不正確實例。

 ✔️在實 <xref:System.IEquatable%601> 值型別上執行。

 <xref:System.Object.Equals%2A?displayProperty=nameWithType>實值型別上的方法會造成裝箱，而其預設實並不太有效率，因為它會使用反映。 <xref:System.IEquatable%601.Equals%2A> 可以有更好的效能，並可進行實作為，使其不會導致裝箱。

 ❌ 請勿明確擴充 <xref:System.ValueType> 。 事實上，大部分的語言都能防止這種情況。

 一般而言，結構可能很有用，但僅適用于不會經常被裝箱的小型、單一且不可變的值。

 *部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>請參閱

- [型別設計方針](type.md)
- [架構設計指導方針](index.md)
- [在類別和結構之間選擇](choosing-between-class-and-struct.md)
