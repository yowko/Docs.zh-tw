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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400600"
---
# <a name="constructor-design"></a>建構函式設計

有兩種建構函式：類型建構函式和實例建構函式。

類型建構函式是靜態的，在使用類型之前由 CLR 運行。 實例建構函式在創建類型的實例時運行。

類型建構函式不能採用任何參數。 實例建構函式可以。 不採用任何參數的實例建構函式通常稱為無參數建構函式。

建構函式是創建類型實例的最自然方法。 大多數開發人員在考慮創建實例（如工廠方法）的替代方法之前，將搜索並嘗試使用建構函式。

✔️ 考慮提供簡單、理想的預設建構函式。

簡單的建構函式具有非常少量的參數，並且所有參數都是基元或枚舉。 這種簡單的建構函式提高了框架的可用性。

✔️如果所需操作的語義不直接映射到新實例的構造，或者遵循建構函式設計準則感覺不自然，則考慮使用靜態工廠方法而不是建構函式。

✔️ DO 使用建構函式參數作為設置主屬性的快捷方式。

在語義上，使用空建構函式後跟某些屬性集和使用具有多個參數的建構函式之間應該沒有區別。

如果建構函式參數用於簡單地設置屬性，則✔️ DO 對建構函式參數使用相同的名稱和屬性。

此類參數和屬性之間的唯一區別應該是套管。

✔️在建構函式中執行最小工作。

除了捕獲建構函式參數之外，建構函式不應執行太多工作。 任何其他處理的成本應延遲到需要。

✔️如果適用，從實例建構函式引發異常。

✔️如果需要這樣的建構函式，則在類中顯式聲明公共無參數建構函式。

如果不顯式聲明類型上的任何建構函式，則許多語言（如 C#）將自動添加公共無參數建構函式。 （抽象類別獲取受保護的建構函式。

向類添加參數化建構函式可防止編譯器添加無參數建構函式。 這通常會導致意外的中斷更改。

❌AVOID 在結構上顯式定義無參數建構函式。

這使得陣列創建速度更快，因為如果未定義無參數建構函式，則不必在陣列中的每個插槽上運行。 請注意，許多編譯器（包括 C#）不允許結構具有無參數建構函式。因此。

❌AVOID 在其建構函式內的物件上調用虛擬成員。

調用虛擬成員將導致調用最派生的重寫，即使最派生類型的建構函式尚未完全運行。

## <a name="type-constructor-guidelines"></a>類型建構函式指南

✔️將靜態建構函式作為私有。

靜態建構函式（也稱為類建構函式）用於初始化類型。 CLR 在創建類型的第一個實例或調用該類型上的任何靜態成員之前調用靜態建構函式。 使用者無法控制何時調用靜態建構函式。 如果靜態建構函式不是私有的，則可以由 CLR 以外的代碼調用它。 根據建構函式中執行的操作，這可能導致意外行為。 C# 編譯器強制靜態建構函式為私有。

❌不要從靜態建構函式引發異常。

如果從類型建構函式引發異常，則該類型在當前應用程式域中不可用。

✔️考慮內聯初始化靜態欄位，而不是顯式使用靜態建構函式，因為運行時能夠優化沒有顯式定義的靜態建構函式的類型的性能。

*部分© 2005， 2009 微軟公司.保留擁有權利。*

獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。**

## <a name="see-also"></a>另請參閱

- [成員設計方針](../../../docs/standard/design-guidelines/member.md)
- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
