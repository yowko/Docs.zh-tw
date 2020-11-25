---
title: 事件和回呼
ms.date: 10/22/2008
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
ms.openlocfilehash: c63a88cb4e500504f993352a03478f40cad58400
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734725"
---
# <a name="events-and-callbacks"></a>事件和回呼

回呼是延伸點，可讓架構透過委派回呼使用者程式碼。 這些委派通常會透過方法的參數傳遞至架構。

 事件是回呼的特殊案例，可支援方便且一致的語法，以 (事件處理常式) 提供委派。 此外，Visual Studio 的語句完成和設計工具會在使用事件型 Api 時提供協助。  (查看 [事件設計](event.md)。 ) 

 ✔️考慮使用回呼，讓使用者能夠提供要由架構執行的自訂程式碼。

 ✔️考慮使用事件，讓使用者自訂架構的行為，而不需要瞭解物件導向設計。

 ✔️會偏好透過一般回呼的事件，因為較廣泛的開發人員比較熟悉這些事件，並與 Visual Studio 的語句完成整合。

 ❌ 避免在效能相關的 Api 中使用回呼。

 使用 `Func<...>` `Action<...>` 回呼定義 api 時，✔️使用新的、或 `Expression<...>` 類型，而不是自訂委派。

 `Func<...>` 和 `Action<...>` 表示泛型委派。 `Expression<...>` 代表可在執行時間編譯並後續叫用，但也可以序列化並傳遞給遠端進程的函式定義。

 ✔️使用來測量和瞭解的效能含意 `Expression<...>` ，而不是使用 `Func<...>` 和 `Action<...>` 委派。

 `Expression<...>` 在大部分情況下，類型在邏輯上等同于 `Func<...>` 和 `Action<...>` 委派。 兩者之間的主要差異在於委派的用途是要用於本機進程案例;運算式適用于在遠端進程或電腦中評估運算式有説明的情況。

 ✔️確實知道，藉由呼叫委派，您會執行任意程式碼，而且可能會有安全性、正確性和相容性的影響。

 *部分 &copy; 2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>另請參閱

- [擴充性設計](designing-for-extensibility.md)
- [架構設計指導方針](index.md)
