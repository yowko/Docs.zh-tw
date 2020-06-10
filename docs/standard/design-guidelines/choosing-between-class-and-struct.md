---
title: 在類別和結構之間選擇
description: 瞭解如何決定是否要將類型設計為類別，或將類型設計為結構。 瞭解 .NET 中的參考型別和實數值型別有何不同。
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- class library design guidelines [.NET Framework], classes
- structures [.NET Framework], vs. classes
- classes [.NET Framework], design guidelines
- type design guidelines, structures
- structures [.NET Framework], design guidelines
- classes [.NET Framework], vs. structures
- type design guidelines, classes
ms.assetid: f8b8ec9b-0ba7-4dea-aadf-a93395cd804f
ms.openlocfilehash: 9d757e77292c1226fbe2328cce082033ae8f7003
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662598"
---
# <a name="choosing-between-class-and-struct"></a>在類別和結構之間選擇
每個架構設計工具所面臨的基本設計決策之一，是要將型別設計為類別（參考型別）還是結構（實值型別）。 瞭解參考型別和實值型別的行為差異，對於進行這項選擇十分重要。

 我們將考慮的參考型別和實值型別之間的第一個差異在於，參考型別會在堆積上配置並進行垃圾收集，而實值型別則會在堆疊中或內嵌于包含型別中進行配置，或在堆疊回溯或其包含類型解除配置時解除配置。 因此，實數值型別的配置和取消配置，通常比參考類型的配置和取消配置來得便宜。

 接下來，參考型別的陣列是配置的，這表示陣列元素只是在堆積上之參考型別實例的參考。 實值型別陣列是以內嵌方式配置，這表示陣列元素是實值型別的實際實例。 因此，實數值型別陣列的配置和取消配置，比參考類型陣列的配置和取消配置更便宜。 此外，在大部分的情況下，實數值型別陣列表現出更好的參考位置。

 下一個差異與記憶體使用量有關。 轉換成參考型別或其所實的其中一個介面時，實數值型別會得到裝箱。 當轉換回實值型別時，它們會被取消裝箱。 因為 box 是在堆積上配置的物件，而且會進行垃圾收集，所乙太多的裝箱和取消裝箱可能會對堆積、垃圾收集行程和最終應用程式效能產生負面影響。  相反地，在參考型別轉換時，不會發生這類的裝箱。 （如需詳細資訊，請參閱[裝箱和取消裝箱](../../csharp/programming-guide/types/boxing-and-unboxing.md)）。

 接下來，參考型別指派會複製參考，而實值型別指派則會複製整個值。 因此，大型參考型別的指派比大型實值型別的指派便宜。

 最後，參考型別會以傳址方式傳遞，而實值型別則會以傳值方式傳遞。 對參考型別的實例所做的變更會影響指向該實例的所有參考。 數值型別實例會在以傳值方式傳遞時複製。 當實值型別的實例變更時，當然不會影響它的任何複本。 由於複本不是由使用者明確建立，而是在傳遞引數或傳回值時以隱含方式建立，因此可以變更的實數值型別可能會讓許多使用者感到困惑。 因此，實數值型別應該是不可變的。

 根據經驗法則，架構中的大部分類型都應該是類別。 不過，在某些情況下，實數值型別的特性會使其更適合使用結構。

 ✔️請考慮定義結構，而不是在類別的實例很小，而且通常很短，或通常內嵌于其他物件中。

 ❌除非類型具有下列所有特性，否則請避免定義結構：

- 它會以邏輯方式表示單一值，類似于基本類型（ `int` 、 `double` 等）。

- 其實例大小低於16個位元組。

- 它是不可變的。

- 不需要經常進行裝箱。

 在所有其他情況下，您應該將類型定義為類別。

 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。**

## <a name="see-also"></a>另請參閱

- [類型設計方針](type.md)
- [架構設計方針](index.md)
