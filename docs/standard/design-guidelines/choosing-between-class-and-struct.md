---
title: 在類別和結構之間選擇
description: 瞭解如何決定是否要將類型設計為類別，或將型別設計為結構。 瞭解 .NET 中的參考型別和實數值型別有何不同。
ms.date: 10/22/2008
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
ms.openlocfilehash: 05ba9abbc9495d927b7f58ebb06f152c0c15772f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701246"
---
# <a name="choosing-between-class-and-struct"></a>在類別和結構之間選擇

每個 framework 設計工具都有臉部的其中一個基本設計決策，就是要將類型設計為類別 (參考型別) 或作為結構 () 數值型別。 若要對參考型別和實值型別行為的差異有很大的瞭解，對進行這項選擇是很重要的。

 參考型別和實值型別之間的第一個差異是，參考型別是在堆積上配置和垃圾收集，而實值型別則是在堆疊上配置，或是在堆疊回溯或其包含型別解除配置時解除配置。 因此，實值型別的配置和取消配置，通常比參考型別的配置和取消配置還便宜。

 接下來，參考型別的陣列是在外配置的，這表示陣列元素只是參考型別（位於堆積上）的實例參考。 實值型別陣列是以內嵌方式配置，表示陣列元素是實值型別的實際實例。 因此，實值型別陣列的配置和取消配置比參考型別陣列的配置和取消配置更便宜。 此外，在大部分的情況下，實值型別陣列也展現了更好的參考位置。

 下一項差異與記憶體使用量有關。 當轉換成參考型別或它們所執行的其中一個介面時，實值型別會被裝箱。 當轉換回實值型別時，它們會被取消裝箱。 因為 box 是在堆積上配置的物件，而且會進行垃圾收集，所乙太多的裝箱和取消取消項對堆積、垃圾收集行程，以及最終的應用程式效能可能會有負面影響。  相反地，在轉換參考型別時，不會發生這類的裝箱。  (需詳細資訊，請參閱) 的 [裝箱和取消](../../csharp/programming-guide/types/boxing-and-unboxing.md) 。

 接下來，參考型別指派會複製參考，而實值型別指派則會複製整個值。 因此，大型參考型別的指派比大型實值型別的指派更便宜。

 最後，參考型別會以傳址方式傳遞，而實值型別會以傳值方式傳遞。 對參考型別的實例所做的變更會影響所有指向該實例的參考。 數值型別實例會在以傳值方式傳遞時複製。 當實值型別的實例變更時，當然不會影響它的任何複本。 由於系統不會明確地建立複本，而是在傳遞引數或傳回值時，隱含地建立複本，因此可以變更的實數值型別可能會讓許多使用者混淆。 因此，實數值型別應該是不可變的。

 根據經驗法則，架構中的大部分類型都應該是類別。 不過，在某些情況下，實值型別的特性讓它更適合使用結構。

 如果類型的實例很小且通常是存留期，或通常內嵌于其他物件中，✔️可考慮定義結構，而不是類別。

 ❌ 除非類型具有下列所有特性，否則請避免定義結構：

- 它會以邏輯方式表示單一值，類似于基本類型 (`int` 、等 `double` ) 。

- 它的實例大小低於16位元組。

- 它是不可變的。

- 不需要經常進行封裝。

 在所有其他情況下，您應該將類型定義為類別。

 *部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>另請參閱

- [型別設計方針](type.md)
- [架構設計指導方針](index.md)
