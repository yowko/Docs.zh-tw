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
ms.openlocfilehash: 7dab759ba48104530fc41e46f6f2bba18d6c4456
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741665"
---
# <a name="events-and-callbacks"></a><span data-ttu-id="cea8f-102">事件和回呼</span><span class="sxs-lookup"><span data-stu-id="cea8f-102">Events and Callbacks</span></span>
<span data-ttu-id="cea8f-103">回呼是擴充點，可讓架構透過委派回呼使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="cea8f-103">Callbacks are extensibility points that allow a framework to call back into user code through a delegate.</span></span> <span data-ttu-id="cea8f-104">這些委派通常會透過方法的參數傳遞至架構。</span><span class="sxs-lookup"><span data-stu-id="cea8f-104">These delegates are usually passed to the framework through a parameter of a method.</span></span>

 <span data-ttu-id="cea8f-105">事件是回呼的特殊案例，可支援方便且一致的語法來提供委派（事件處理常式）。</span><span class="sxs-lookup"><span data-stu-id="cea8f-105">Events are a special case of callbacks that supports convenient and consistent syntax for supplying the delegate (an event handler).</span></span> <span data-ttu-id="cea8f-106">此外，Visual Studio 的語句完成和設計工具會提供使用以事件為基礎之 Api 的協助。</span><span class="sxs-lookup"><span data-stu-id="cea8f-106">In addition, Visual Studio’s statement completion and designers provide help in using event-based APIs.</span></span> <span data-ttu-id="cea8f-107">（請參閱[事件設計](../../../docs/standard/design-guidelines/event.md)）。</span><span class="sxs-lookup"><span data-stu-id="cea8f-107">(See [Event Design](../../../docs/standard/design-guidelines/event.md).)</span></span>

 <span data-ttu-id="cea8f-108">✔️考慮使用回呼，讓使用者提供可由架構執行的自訂程式碼。</span><span class="sxs-lookup"><span data-stu-id="cea8f-108">✔️ CONSIDER using callbacks to allow users to provide custom code to be executed by the framework.</span></span>

 <span data-ttu-id="cea8f-109">✔️考慮使用事件，讓使用者自訂架構的行為，而不需要瞭解物件導向設計。</span><span class="sxs-lookup"><span data-stu-id="cea8f-109">✔️ CONSIDER using events to allow users to customize the behavior of a framework without the need for understanding object-oriented design.</span></span>

 <span data-ttu-id="cea8f-110">✔️偏好透過單純回呼的事件，因為它們較廣泛的開發人員更熟悉，並已與 Visual Studio 的語句完成整合。</span><span class="sxs-lookup"><span data-stu-id="cea8f-110">✔️ DO prefer events over plain callbacks, because they are more familiar to a broader range of developers and are integrated with Visual Studio statement completion.</span></span>

 <span data-ttu-id="cea8f-111">❌ 避免在效能相關的 Api 中使用回呼。</span><span class="sxs-lookup"><span data-stu-id="cea8f-111">❌ AVOID using callbacks in performance-sensitive APIs.</span></span>

 <span data-ttu-id="cea8f-112">✔️在定義具有回呼的 Api 時，請使用新的 `Func<...>`、`Action<...>`或 `Expression<...>` 類型，而不是自訂委派。</span><span class="sxs-lookup"><span data-stu-id="cea8f-112">✔️ DO use the new `Func<...>`, `Action<...>`, or `Expression<...>` types instead of custom delegates, when defining APIs with callbacks.</span></span>

 <span data-ttu-id="cea8f-113">`Func<...>` 和 `Action<...>` 代表泛型委派。</span><span class="sxs-lookup"><span data-stu-id="cea8f-113">`Func<...>` and `Action<...>` represent generic delegates.</span></span> <span data-ttu-id="cea8f-114">`Expression<...>` 代表可以在執行時間編譯並接著叫用，但也可以序列化並傳遞至遠端進程的函式定義。</span><span class="sxs-lookup"><span data-stu-id="cea8f-114">`Expression<...>` represents function definitions that can be compiled and subsequently invoked at runtime but can also be serialized and passed to remote processes.</span></span>

 <span data-ttu-id="cea8f-115">✔️確實測量和瞭解使用 `Expression<...>`的效能含意，而不是使用 `Func<...>` 和 `Action<...>` 委派。</span><span class="sxs-lookup"><span data-stu-id="cea8f-115">✔️ DO measure and understand performance implications of using `Expression<...>`, instead of using `Func<...>` and `Action<...>` delegates.</span></span>

 <span data-ttu-id="cea8f-116">在大部分的情況下，`Expression<...>` 類型會以邏輯方式等同于 `Func<...>` 和 `Action<...>` 委派。</span><span class="sxs-lookup"><span data-stu-id="cea8f-116">`Expression<...>` types are in most cases logically equivalent to `Func<...>` and `Action<...>` delegates.</span></span> <span data-ttu-id="cea8f-117">兩者之間的主要差異在於委派是要用於本機進程案例中。運算式適用于在遠端進程或電腦中評估運算式的好處。</span><span class="sxs-lookup"><span data-stu-id="cea8f-117">The main difference between them is that the delegates are intended to be used in local process scenarios; expressions are intended for cases where it’s beneficial and possible to evaluate the expression in a remote process or machine.</span></span>

 <span data-ttu-id="cea8f-118">✔️確實瞭解，藉由呼叫委派，您會執行任意程式碼，而且可能會有安全性、正確性和相容性的影響。</span><span class="sxs-lookup"><span data-stu-id="cea8f-118">✔️ DO understand that by calling a delegate, you are executing arbitrary code and that could have security, correctness, and compatibility repercussions.</span></span>

 <span data-ttu-id="cea8f-119">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="cea8f-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="cea8f-120">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="cea8f-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="cea8f-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="cea8f-121">See also</span></span>

- [<span data-ttu-id="cea8f-122">擴充性設計</span><span class="sxs-lookup"><span data-stu-id="cea8f-122">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [<span data-ttu-id="cea8f-123">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="cea8f-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
