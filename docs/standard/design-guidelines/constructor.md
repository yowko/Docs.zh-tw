---
title: 建構函式設計
ms.date: 10/22/2008
ms.technology: dotnet-standard
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
ms.openlocfilehash: 7ab795cd4c6e0ff5e1451c05987848c41bd69577
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741731"
---
# <a name="constructor-design"></a>建構函式設計

有兩種類型的「型別」（type）和「實例」（instance）函數。

類型的函式是靜態的，而且會在使用類型之前由 CLR 執行。 建立類型的實例時，會執行實例的函式。

類型的函式不能接受任何參數。 實例構造函式可以。 不接受任何參數的實例構造函式通常稱為無參數的函式。

建立型別的實例時，這些是最自然的方式。 大部分的開發人員會先搜尋並嘗試使用「函式」，然後再考慮建立實例的替代方式（例如 factory 方法）。

✔️考慮提供簡單、理想的預設函式。

簡單的函式有非常少的參數數目，而所有參數都是基本或列舉。 這類簡單的函式會提高架構的可用性。

如果所需作業的語義不會直接對應至新實例的結構，或如果遵循非自然的設計方針，則請考慮使用靜態處理站方法來取代函式。✔️

✔️確實要使用此函式參數作為設定主要屬性的快捷方式。

使用空白的函式，後面接著一些屬性集，並使用具有多個引數的函式，兩者之間的語義應該沒有任何差異。

如果使用了函數參數來直接設定屬性，✔️就會使用相同的名稱來處理函式參數和屬性。

這類參數和屬性之間的唯一差異應該是大小寫。

✔️在此函式中執行最少的工作。

除了 capture 函式參數之外，這些函式不應執行太多工。 任何其他處理的成本應延遲到需要的時間。

✔️確實會從實例的函式擲回例外狀況（如果適用的話）。

如果需要這類的函式，✔️會在類別中明確宣告公用無參數的函數。

如果您未在類型上明確宣告任何函式，許多語言（例如C#）會自動加入公用無參數的函式。 （抽象類別會取得受保護的構造函式）。

將參數化的函式加入至類別，可防止編譯器加入無參數的函式。 這通常會導致意外的中斷性變更。

❌ 避免在結構上明確定義無參數的構造函式。

這樣可以更快速地建立陣列，因為如果未定義無參數的函式，則不需要在陣列中的每個位置上執行。 請注意，許多編譯器（ C#包括）都不允許結構因為此原因而擁有無參數的構造函式。

❌ 避免在其函式內的物件上呼叫虛擬成員。

呼叫虛擬成員會導致呼叫最常衍生的覆寫，即使最常衍生類型的函式尚未完全執行。

## <a name="type-constructor-guidelines"></a>型別函數方針

✔️將靜態的函式設為私用。

靜態的函式（也稱為類別的函式）是用來初始化型別。 CLR 會在建立類型的第一個實例或呼叫該類型的任何靜態成員之前，呼叫靜態的函式。 使用者無法控制呼叫靜態函式的時間。 如果靜態的函式不是私用，則可由 CLR 以外的程式碼呼叫。 視在此函式中執行的作業而定，這可能會造成非預期的行為。 C#編譯器會強制將靜態的構造函式設為私用。

❌ 不會從靜態的函式擲回例外狀況。

如果從類型的函式擲回例外狀況，類型在目前的應用程式域中無法使用。

✔️考慮將靜態欄位內嵌，而不是明確地使用靜態的函式，因為執行時間可以將沒有明確定義之靜態函式的類型效能優化。

*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*

獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>請參閱

- [成員設計方針](../../../docs/standard/design-guidelines/member.md)
- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
