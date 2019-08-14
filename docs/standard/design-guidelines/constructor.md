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
author: KrzysztofCwalina
ms.openlocfilehash: a43ec815275e58f4bc6462fb4f5cb4733267de31
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972109"
---
# <a name="constructor-design"></a>建構函式設計

有兩種類型的「型別」 (type) 和「實例」 (instance) 函數。

類型的函式是靜態的, 而且會在使用類型之前由 CLR 執行。 建立類型的實例時, 會執行實例的函式。

類型的函式不能接受任何參數。 實例構造函式可以。 不接受任何參數的實例構造函式通常稱為無參數的函式。

建立型別的實例時, 這些是最自然的方式。 大部分的開發人員會先搜尋並嘗試使用「函式」, 然後再考慮建立實例的替代方式 (例如 factory 方法)。

**✓ CONSIDER** 提供簡單、 在理想情況下預設、 建構函式。

簡單的函式有非常少的參數數目, 而所有參數都是基本或列舉。 這類簡單的函式會提高架構的可用性。

**✓ CONSIDER** 而不建構函式使用的靜態 factory 方法，如果所需的作業語意是否未直接對應至建構的新執行個體，或建構函式設計指導方針並不適合。

**✓ DO** 以捷徑中使用建構函式參數，設定主要屬性。

使用空白的函式, 後面接著一些屬性集, 並使用具有多個引數的函式, 兩者之間的語義應該沒有任何差異。

**✓ DO** 如果建構函式參數用來只設定屬性，使用相同的名稱，建構函式參數和屬性。

這類參數和屬性之間的唯一差異應該是大小寫。

**✓ DO** 建構函式中的最少工作。

除了 capture 函式參數之外, 這些函式不應執行太多工。 任何其他處理的成本應延遲到需要的時間。

**✓ DO** 擲回例外狀況，從執行個體建構函式，如果適當的話。

如果需要這類的函式, **✓**會在類別中明確宣告公用無參數的函式。

如果您未在類型上明確宣告任何函式, 許多語言 (例如C#) 會自動加入公用無參數的函式。 (抽象類別會取得受保護的構造函式)。

將參數化的函式加入至類別, 可防止編譯器加入無參數的函式。 這通常會導致意外的中斷性變更。

**X 避免**在結構上明確定義無參數的構造函式。

這樣可以更快速地建立陣列, 因為如果未定義無參數的函式, 則不需要在陣列中的每個位置上執行。 請注意, 許多編譯器 ( C#包括) 都不允許結構因為此原因而擁有無參數的構造函式。

**X AVOID** 其建構函式內的物件上呼叫虛擬成員。

呼叫虛擬成員會導致呼叫最常衍生的覆寫, 即使最常衍生類型的函式尚未完全執行。

## <a name="type-constructor-guidelines"></a>型別函數方針

**✓ DO** 私人靜態建構函式。

靜態的函式 (也稱為類別的函式) 是用來初始化型別。 CLR 會在建立類型的第一個實例或呼叫該類型的任何靜態成員之前, 呼叫靜態的函式。 使用者無法控制呼叫靜態函式的時間。 如果靜態的函式不是私用, 則可由 CLR 以外的程式碼呼叫。 視在此函式中執行的作業而定, 這可能會造成非預期的行為。 C#編譯器會強制將靜態的構造函式設為私用。

**X DO NOT** 擲回例外狀況，從靜態建構函式。

如果從類型的函式擲回例外狀況, 類型在目前的應用程式域中無法使用。

**✓ CONSIDER** 初始化的靜態欄位內嵌，而不是使用明確靜態建構函式，因為執行階段能夠使效能最佳化的不需要明確定義的靜態建構函式的類型。

*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

*從[架構設計方針轉載已獲得皮耳森教育, inc. 的許可權:Krzysztof Cwalina 和 Brad Abrams 可重複使用的 .net 程式庫第](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 2 版的慣例、慣用語和模式, 已于2008年10月22日發行, 屬於 Microsoft Windows 開發系列的 Addison-Wesley Professional。*

## <a name="see-also"></a>另請參閱

- [成員設計方針](../../../docs/standard/design-guidelines/member.md)
- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
