---
title: 建構函式設計
ms.date: 10/22/2008
helpviewer_keywords:
- member design guidelines, constructors
- constructors, design guidelines
- instance constructors
- type constructors
- virtual members
- constructors, types
- parameterless constructors
- static constructors
ms.assetid: b4496afe-5fa7-4bb0-85ca-70b0ef21e6fc
ms.openlocfilehash: 27fb73aa01adf31117d1b82724873db3a03fd269
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821394"
---
# <a name="constructor-design"></a>建構函式設計

有兩種類型的函數：類型的函式和實例的函式。

型別函式是靜態的，而且是在使用型別之前由 CLR 執行。 建立型別的實例時，會執行實例的函式。

型別函式不能採用任何參數。 實例的函式可以。 未採用任何參數的實例函式通常稱為無參數的函式。

使用函式是建立型別實例的最自然方式。 大部分的開發人員會先搜尋並嘗試使用函式，再考慮建立實例的替代方式 (例如) 的 factory 方法。

✔️考慮提供簡單且理想的預設值。

簡單的函式具有極少的參數數目，而所有參數都是基本或列舉。 這類簡單的函式會增加架構的可用性。

如果所需作業的語法不會直接對應至新實例的結構，或遵循函式設計指導方針的非自然，則✔️考慮使用靜態 factory 方法，而不是函式。

✔️請使用函式參數做為設定主要屬性的快捷方式。

在使用空白的函式後接某些屬性集，以及使用具有多個引數的函式時，兩者之間的語法應該沒有任何差異。

如果使用函式參數來直接設定屬性，則✔️會針對函式參數使用相同的名稱，並使用屬性。

這類參數和屬性之間的唯一差異應該是大小寫。

✔️在函式中執行最少量的工作。

除了捕捉函式參數之外，這些函式不應該執行太多工作。 任何其他處理的成本都應該延遲到需要的時間。

✔️確實會從實例的函式擲回例外狀況（如果有的話）。

如果需要這類的函式，✔️確實在類別中宣告公用無參數的函式。

如果您未在類型上明確宣告任何的函式，則許多語言 (例如 c # ) 會自動加入公用無參數的函式。  (抽象類別會取得受保護的函式。 ) 

將參數化的函式加入至類別，可防止編譯器新增無參數的函式。 這通常會導致意外的中斷性變更。

❌ 避免在結構上明確定義無參數的函式。

這使得陣列的建立速度更快，因為如果未定義無參數的函式，則不需要在陣列中的每個位置執行。 請注意，許多編譯器（包括 c #）都不允許結構因為這個原因而有無參數的函式。

❌ 避免在其函式內的物件上呼叫虛擬成員。

呼叫虛擬成員會導致呼叫最常衍生的覆寫，即使大部分衍生類型的函式尚未完全執行也一樣。

## <a name="type-constructor-guidelines"></a>型別函式指導方針

✔️將靜態的函式設為私用。

靜態的函式（也稱為類別的函式）是用來初始化型別。 CLR 會在建立類型的第一個實例或呼叫該類型上的任何靜態成員之前，呼叫靜態的函式。 使用者無法控制呼叫靜態函式的時機。 如果靜態的函式不是私用的，則可由 CLR 以外的程式碼呼叫。 根據在函式中執行的作業而定，這可能會導致非預期的行為。 C # 編譯器會強制將靜態的函式設為私用。

❌ 請勿從靜態的函式擲回例外狀況。

如果從類型的函式擲回例外狀況，則類型在目前的應用程式域中無法使用。

✔️考慮將靜態欄位初始化，而不是明確地使用靜態的函式，因為執行時間可以將沒有明確定義之靜態函式的類型效能優化。

*部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>請參閱

- [成員設計方針](member.md)
- [架構設計指導方針](index.md)
