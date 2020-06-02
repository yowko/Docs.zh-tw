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
ms.openlocfilehash: ad7774fd197db80ce84b3b8a5baa4e9ee06b6cef
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289794"
---
# <a name="events-and-callbacks"></a><span data-ttu-id="ce848-102">事件和回呼</span><span class="sxs-lookup"><span data-stu-id="ce848-102">Events and Callbacks</span></span>
<span data-ttu-id="ce848-103">回呼是擴充點，可讓架構透過委派回呼使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="ce848-103">Callbacks are extensibility points that allow a framework to call back into user code through a delegate.</span></span> <span data-ttu-id="ce848-104">這些委派通常會透過方法的參數傳遞至架構。</span><span class="sxs-lookup"><span data-stu-id="ce848-104">These delegates are usually passed to the framework through a parameter of a method.</span></span>

 <span data-ttu-id="ce848-105">事件是回呼的特殊案例，可支援方便且一致的語法來提供委派（事件處理常式）。</span><span class="sxs-lookup"><span data-stu-id="ce848-105">Events are a special case of callbacks that supports convenient and consistent syntax for supplying the delegate (an event handler).</span></span> <span data-ttu-id="ce848-106">此外，Visual Studio 的語句完成和設計工具會提供使用以事件為基礎之 Api 的協助。</span><span class="sxs-lookup"><span data-stu-id="ce848-106">In addition, Visual Studio’s statement completion and designers provide help in using event-based APIs.</span></span> <span data-ttu-id="ce848-107">（請參閱[事件設計](event.md)）。</span><span class="sxs-lookup"><span data-stu-id="ce848-107">(See [Event Design](event.md).)</span></span>

 <span data-ttu-id="ce848-108">✔️考慮使用回呼，讓使用者提供可由架構執行的自訂程式碼。</span><span class="sxs-lookup"><span data-stu-id="ce848-108">✔️ CONSIDER using callbacks to allow users to provide custom code to be executed by the framework.</span></span>

 <span data-ttu-id="ce848-109">✔️考慮使用事件，讓使用者自訂架構的行為，而不需要瞭解物件導向設計。</span><span class="sxs-lookup"><span data-stu-id="ce848-109">✔️ CONSIDER using events to allow users to customize the behavior of a framework without the need for understanding object-oriented design.</span></span>

 <span data-ttu-id="ce848-110">✔️偏好透過單純回呼的事件，因為它們較廣泛的開發人員更熟悉，並已與 Visual Studio 的語句完成整合。</span><span class="sxs-lookup"><span data-stu-id="ce848-110">✔️ DO prefer events over plain callbacks, because they are more familiar to a broader range of developers and are integrated with Visual Studio statement completion.</span></span>

 <span data-ttu-id="ce848-111">❌避免在效能相關的 Api 中使用回呼。</span><span class="sxs-lookup"><span data-stu-id="ce848-111">❌ AVOID using callbacks in performance-sensitive APIs.</span></span>

 <span data-ttu-id="ce848-112">✔️ `Func<...>` `Action<...>` `Expression<...>` 在定義具有回呼的 api 時，請使用新的、或類型，而不是自訂委派。</span><span class="sxs-lookup"><span data-stu-id="ce848-112">✔️ DO use the new `Func<...>`, `Action<...>`, or `Expression<...>` types instead of custom delegates, when defining APIs with callbacks.</span></span>

 <span data-ttu-id="ce848-113">`Func<...>`和 `Action<...>` 代表泛型委派。</span><span class="sxs-lookup"><span data-stu-id="ce848-113">`Func<...>` and `Action<...>` represent generic delegates.</span></span> <span data-ttu-id="ce848-114">`Expression<...>`表示函式定義，可以在執行時間進行編譯並接著叫用，但也可以序列化並傳遞至遠端進程。</span><span class="sxs-lookup"><span data-stu-id="ce848-114">`Expression<...>` represents function definitions that can be compiled and subsequently invoked at run time but can also be serialized and passed to remote processes.</span></span>

 <span data-ttu-id="ce848-115">✔️會測量並瞭解使用的效能含意 `Expression<...>` ，而不是使用 `Func<...>` 和 `Action<...>` 委派。</span><span class="sxs-lookup"><span data-stu-id="ce848-115">✔️ DO measure and understand performance implications of using `Expression<...>`, instead of using `Func<...>` and `Action<...>` delegates.</span></span>

 <span data-ttu-id="ce848-116">`Expression<...>`在大部分的情況下，類型在邏輯上相當於 `Func<...>` 和 `Action<...>` 委派。</span><span class="sxs-lookup"><span data-stu-id="ce848-116">`Expression<...>` types are in most cases logically equivalent to `Func<...>` and `Action<...>` delegates.</span></span> <span data-ttu-id="ce848-117">兩者之間的主要差異在於委派是要用於本機進程案例中。運算式適用于在遠端進程或電腦中評估運算式的好處。</span><span class="sxs-lookup"><span data-stu-id="ce848-117">The main difference between them is that the delegates are intended to be used in local process scenarios; expressions are intended for cases where it’s beneficial and possible to evaluate the expression in a remote process or machine.</span></span>

 <span data-ttu-id="ce848-118">✔️確實瞭解，藉由呼叫委派，您會執行任意程式碼，而且可能會有安全性、正確性和相容性的影響。</span><span class="sxs-lookup"><span data-stu-id="ce848-118">✔️ DO understand that by calling a delegate, you are executing arbitrary code and that could have security, correctness, and compatibility repercussions.</span></span>

 <span data-ttu-id="ce848-119">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="ce848-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="ce848-120">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。\*\*</span><span class="sxs-lookup"><span data-stu-id="ce848-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="ce848-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce848-121">See also</span></span>

- [<span data-ttu-id="ce848-122">擴充性設計</span><span class="sxs-lookup"><span data-stu-id="ce848-122">Designing for Extensibility</span></span>](designing-for-extensibility.md)
- [<span data-ttu-id="ce848-123">架構設計方針</span><span class="sxs-lookup"><span data-stu-id="ce848-123">Framework Design Guidelines</span></span>](index.md)
