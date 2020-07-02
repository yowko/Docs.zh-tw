---
title: 事件和回呼
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
ms.openlocfilehash: 4000944c3b913f71bc18462cea9062e9237ae53f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619529"
---
# <a name="events-and-callbacks"></a>事件和回呼
回呼是擴充點，可讓架構透過委派回呼使用者程式碼。 這些委派通常會透過方法的參數傳遞至架構。

 事件是回呼的特殊案例，可支援方便且一致的語法來提供委派（事件處理常式）。 此外，Visual Studio 的語句完成和設計工具會提供使用以事件為基礎之 Api 的協助。 （請參閱[事件設計](event.md)）。

 ✔️考慮使用回呼，讓使用者提供可由架構執行的自訂程式碼。

 ✔️考慮使用事件，讓使用者自訂架構的行為，而不需要瞭解物件導向設計。

 ✔️偏好透過單純回呼的事件，因為它們較廣泛的開發人員更熟悉，並已與 Visual Studio 的語句完成整合。

 ❌避免在效能相關的 Api 中使用回呼。

 ✔️ `Func<...>` `Action<...>` `Expression<...>` 在定義具有回呼的 api 時，請使用新的、或類型，而不是自訂委派。

 `Func<...>`和 `Action<...>` 代表泛型委派。 `Expression<...>`表示函式定義，可以在執行時間編譯並接著叫用，但也可以序列化並傳遞至遠端進程。

 ✔️會測量並瞭解使用的效能含意 `Expression<...>` ，而不是使用 `Func<...>` 和 `Action<...>` 委派。

 `Expression<...>`在大部分的情況下，類型在邏輯上相當於 `Func<...>` 和 `Action<...>` 委派。 兩者之間的主要差異在於委派是要用於本機進程案例中。運算式適用于在遠端進程或電腦中評估運算式的好處。

 ✔️確實瞭解，藉由呼叫委派，您會執行任意程式碼，而且可能會有安全性、正確性和相容性的影響。

 *部分 &copy; 2005，2009 Microsoft Corporation。已保留擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。**

## <a name="see-also"></a>另請參閱

- [擴充性設計](designing-for-extensibility.md)
- [架構設計方針](index.md)
