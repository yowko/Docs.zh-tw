---
title: 介面設計
ms.date: 10/22/2008
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
ms.openlocfilehash: 6f8cbb757ffb42f63903b212fee33cdcbba7ecb2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727675"
---
# <a name="interface-design"></a>介面設計

雖然大部分的 Api 最適合使用類別和結構來建立模型，但在某些情況下，介面較適合或為唯一的選項。

 CLR 不支援多重繼承 (亦即，CLR 類別無法繼承自一個以上的基類) ，但是除了繼承自基類之外，它也允許型別執行一或多個介面。 因此，介面通常用來達成多重繼承的效果。 例如， <xref:System.IDisposable> 是允許類型支援 disposability 的介面，而不受其想要參與的任何其他繼承階層。

 定義介面的另一種情況是建立可由數種類型支援的通用介面，包括一些實數值型別。 實值型別無法繼承自以外的型別 <xref:System.ValueType> ，但是它們可以實作為介面，因此使用介面是唯一的選項，以便提供通用基底型別。

 如果您需要一組包含實值型別的型別，✔️會定義介面。

 如果您需要在已繼承自其他類型的類型上支援其功能，✔️考慮定義介面。

 ❌ 避免使用標記介面 (沒有成員) 的介面。

 如果您需要將類別標示為具有特定特性 (標記) ，一般而言，請使用自訂屬性，而不是介面。

 ✔️請至少提供一個實作為介面的型別。

 這樣做有助於驗證介面的設計。 例如， <xref:System.Collections.Generic.List%601> 是介面的實 <xref:System.Collections.Generic.IList%601> 。

 ✔️請提供至少一個 API 來取用您所定義的每個介面， (使用介面做為參數的方法，或輸入為介面) 的屬性。

 這樣做有助於驗證介面設計。 例如， <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> 使用 <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> 介面。

 ❌ 請勿將成員新增至先前已發行的介面。

 這麼做會中斷介面的實作為。 您應該建立新的介面，以避免版本控制問題。

 除了這些指導方針中所述的情況之外，一般而言，您應該在設計 managed 程式碼可重複使用的程式庫中選擇類別，而不是介面。

 *部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>另請參閱

- [型別設計方針](type.md)
- [架構設計指導方針](index.md)
