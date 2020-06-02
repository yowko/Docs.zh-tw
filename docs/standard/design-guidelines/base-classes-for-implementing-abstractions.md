---
title: 實作抽象的基底類別
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- abstractions [.NET Framework]
- base classes, abstractions
ms.assetid: 37a2d9a4-9721-482a-a40f-eee2c1d97875
ms.openlocfilehash: 6af63373b7cbb571265f14ac36028953525fcc7f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280565"
---
# <a name="base-classes-for-implementing-abstractions"></a>實作抽象的基底類別
嚴格來說，當另一個類別衍生自它時，類別會變成基類。 不過，就本節的目的而言，基類是主要設計來提供通用抽象概念或其他類別的類別，以便在繼承時重複使用一些預設的執行。 基類通常位於繼承階層的中間，在階層根目錄的抽象概念和底部的數個自訂實體系之間。

 它們做為執行抽象概念的執行協助程式。 例如，已排序專案集合的其中一個架構抽象概念是 <xref:System.Collections.Generic.IList%601> 介面。 執行並 <xref:System.Collections.Generic.IList%601> 不簡單，因此架構會提供數種基類，例如 <xref:System.Collections.ObjectModel.Collection%601> 和 <xref:System.Collections.ObjectModel.KeyedCollection%602> ，做為協助程式來執行自訂集合。

 基類通常不適合做為抽象概念，因為它們可能包含太多的執行。 例如， `Collection<T>` 基類包含許多與執行非泛型介面的事實相關的實做 `IList` （以更好的方式與非泛型集合整合），以及它是儲存在其中一個欄位之記憶體中的專案集合。

 如先前所討論，基類可以為需要執行抽象概念的使用者提供寶貴的協助，但同時也可能會造成嚴重的責任。 他們會加入介面區並增加繼承階層的深度，因此概念上會使架構複雜化。 因此，只有當基類為架構的使用者提供顯著的價值時，才應該使用這些類別。 如果它們只提供值給架構的實作者，就應該避免這些情況，在此情況下，委派到內部執行，而不是從基類繼承。

 ✔️請考慮將基類設為抽象，即使它們未包含任何抽象成員也一樣。 這會清楚地傳達類別設計為繼承自的使用者。

 ✔️考慮將基類放在主線案例類型的個別命名空間中。 根據定義，基類適用于先進的擴充性案例，因此不會對大多數的使用者感興趣。

 ❌如果類別是要在公用 Api 中使用，請避免以「基底」尾碼命名基類。

 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。**

## <a name="see-also"></a>另請參閱

- [架構設計方針](index.md)
- [擴充性設計](designing-for-extensibility.md)
