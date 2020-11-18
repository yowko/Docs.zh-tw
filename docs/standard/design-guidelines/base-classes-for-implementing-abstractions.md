---
title: 實作抽象的基底類別
ms.date: 10/22/2008
helpviewer_keywords:
- abstractions [.NET Framework]
- base classes, abstractions
ms.assetid: 37a2d9a4-9721-482a-a40f-eee2c1d97875
ms.openlocfilehash: 314fcd0e1e91d1fc869453dd442ecaa72f91955d
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821589"
---
# <a name="base-classes-for-implementing-abstractions"></a>實作抽象的基底類別
嚴格來說，當另一個類別衍生自類別時，類別會變成基類。 但基於本節的目的，基類是設計來提供通用抽象概念的類別，或讓其他類別透過繼承重複使用一些預設的執行。 基類通常位於繼承階層的中間，在階層根目錄的抽象概念和底部的數個自訂實體系之間。

 它們是做為執行抽象概念的實作為協助程式。 例如，其中一個已排序之專案集合的架構抽象概念是 <xref:System.Collections.Generic.IList%601> 介面。 其實 <xref:System.Collections.Generic.IList%601> 作並不簡單，因此架構會提供數個基類，例如 <xref:System.Collections.ObjectModel.Collection%601> 和 <xref:System.Collections.ObjectModel.KeyedCollection%602> ，作為協助程式來執行自訂集合。

 基類通常不適合做為抽象概念，因為它們通常會包含太多執行。 例如， `Collection<T>` 基類包含許多與其實作為泛型介面相關的實 `IList` (，使其與非泛型) 集合的整合更好，並使其成為儲存在其中一個欄位之記憶體中的專案集合。

 如先前所討論，基類可以為需要執行抽象概念的使用者提供寶貴的協助，但同時也會造成重大的責任。 他們加入介面區並提高繼承階層的深度，因此在概念上會使架構變得複雜。 因此，只有當基類為架構的使用者提供顯著的價值時，才應該使用這些類別。 如果它們只將值提供給架構的實作者，則應避免使用這些值，在此情況下，應該強烈考慮對內部實值的委派，而不是從基類繼承。

 ✔️考慮將基類設為抽象，即使它們不包含任何抽象成員也一樣。 這會清楚地傳達類別設計的使用者，而此類別是專門用來繼承的。

 ✔️考慮將基類從主線案例類型放在不同的命名空間中。 根據定義，基類適用于先進的擴充性案例，因此對大部分的使用者而言並不感興趣。

 ❌ 如果類別是要在公用 Api 中使用，請避免以 "Base" 尾碼命名基類。

 *部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>請參閱

- [架構設計指導方針](index.md)
- [擴充性設計](designing-for-extensibility.md)
