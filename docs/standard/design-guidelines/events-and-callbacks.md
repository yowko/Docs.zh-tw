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
author: KrzysztofCwalina
ms.openlocfilehash: 3609d6ac4847cb081740fd698869df4976f83f8f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54525478"
---
# <a name="events-and-callbacks"></a><span data-ttu-id="3c86d-102">事件和回呼</span><span class="sxs-lookup"><span data-stu-id="3c86d-102">Events and Callbacks</span></span>
<span data-ttu-id="3c86d-103">回呼是擴充點，讓回呼透過委派的使用者程式碼的架構。</span><span class="sxs-lookup"><span data-stu-id="3c86d-103">Callbacks are extensibility points that allow a framework to call back into user code through a delegate.</span></span> <span data-ttu-id="3c86d-104">這些委派通常會透過方法的參數傳遞給架構。</span><span class="sxs-lookup"><span data-stu-id="3c86d-104">These delegates are usually passed to the framework through a parameter of a method.</span></span>  
  
 <span data-ttu-id="3c86d-105">事件是回呼中的特殊案例，用來提供委派 （事件處理常式） 支援方便且一致的語法。</span><span class="sxs-lookup"><span data-stu-id="3c86d-105">Events are a special case of callbacks that supports convenient and consistent syntax for supplying the delegate (an event handler).</span></span> <span data-ttu-id="3c86d-106">此外，Visual Studio 的陳述式完成和設計工具提供在使用事件為基礎的 Api 說明。</span><span class="sxs-lookup"><span data-stu-id="3c86d-106">In addition, Visual Studio’s statement completion and designers provide help in using event-based APIs.</span></span> <span data-ttu-id="3c86d-107">(請參閱[事件設計](../../../docs/standard/design-guidelines/event.md)。)</span><span class="sxs-lookup"><span data-stu-id="3c86d-107">(See [Event Design](../../../docs/standard/design-guidelines/event.md).)</span></span>  
  
 <span data-ttu-id="3c86d-108">**✓ CONSIDER** 使用回呼，以允許使用者提供架構所執行的自訂程式碼。</span><span class="sxs-lookup"><span data-stu-id="3c86d-108">**✓ CONSIDER** using callbacks to allow users to provide custom code to be executed by the framework.</span></span>  
  
 <span data-ttu-id="3c86d-109">**✓ CONSIDER** 使用事件可讓使用者自訂的架構，而不需要了解物件導向設計的行為。</span><span class="sxs-lookup"><span data-stu-id="3c86d-109">**✓ CONSIDER** using events to allow users to customize the behavior of a framework without the need for understanding object-oriented design.</span></span>  
  
 <span data-ttu-id="3c86d-110">**✓ DO** 而不用事件純文字的回呼，因為它們是更廣泛的開發人員熟悉，而且會與 Visual Studio 陳述式完成整合。</span><span class="sxs-lookup"><span data-stu-id="3c86d-110">**✓ DO** prefer events over plain callbacks, because they are more familiar to a broader range of developers and are integrated with Visual Studio statement completion.</span></span>  
  
 <span data-ttu-id="3c86d-111">**X AVOID** 重視效能的 Api 中使用回呼。</span><span class="sxs-lookup"><span data-stu-id="3c86d-111">**X AVOID** using callbacks in performance-sensitive APIs.</span></span>  
  
 <span data-ttu-id="3c86d-112">**✓ DO** 使用新 `Func<...>`， `Action<...>`，或 `Expression<...>` 類型而不是自訂委派，定義應用程式開發介面，以回撥時。</span><span class="sxs-lookup"><span data-stu-id="3c86d-112">**✓ DO** use the new `Func<...>`, `Action<...>`, or `Expression<...>` types instead of custom delegates, when defining APIs with callbacks.</span></span>  
  
 <span data-ttu-id="3c86d-113">`Func<...>` 和`Action<...>`代表泛型委派。</span><span class="sxs-lookup"><span data-stu-id="3c86d-113">`Func<...>` and `Action<...>` represent generic delegates.</span></span> <span data-ttu-id="3c86d-114">`Expression<...>` 代表函式定義可編譯和接著也會在執行階段，但可以叫用可序列化，並傳遞給遠端處理程序。</span><span class="sxs-lookup"><span data-stu-id="3c86d-114">`Expression<...>` represents function definitions that can be compiled and subsequently invoked at runtime but can also be serialized and passed to remote processes.</span></span>  
  
 <span data-ttu-id="3c86d-115">**✓ DO** 衡量並且了解使用的效能含意 `Expression<...>`，而不是使用`Func<...>` 和 `Action<...>` 委派。</span><span class="sxs-lookup"><span data-stu-id="3c86d-115">**✓ DO** measure and understand performance implications of using `Expression<...>`, instead of using `Func<...>` and `Action<...>` delegates.</span></span>  
  
 <span data-ttu-id="3c86d-116">`Expression<...>` 型別是在大部分的情況下，邏輯上等同於`Func<...>`和`Action<...>`委派。</span><span class="sxs-lookup"><span data-stu-id="3c86d-116">`Expression<...>` types are in most cases logically equivalent to `Func<...>` and `Action<...>` delegates.</span></span> <span data-ttu-id="3c86d-117">它們之間的主要差異是委派要用於本機處理程序的案例;運算式適用的情況下，很有幫助和評估的運算式中的遠端程序或機器。</span><span class="sxs-lookup"><span data-stu-id="3c86d-117">The main difference between them is that the delegates are intended to be used in local process scenarios; expressions are intended for cases where it’s beneficial and possible to evaluate the expression in a remote process or machine.</span></span>  
  
 <span data-ttu-id="3c86d-118">**✓ DO** 了解呼叫委派時，您會執行任意程式碼，並可能會有安全性、 正確性，以及相容性的影響。</span><span class="sxs-lookup"><span data-stu-id="3c86d-118">**✓ DO** understand that by calling a delegate, you are executing arbitrary code and that could have security, correctness, and compatibility repercussions.</span></span>  
  
 <span data-ttu-id="3c86d-119">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="3c86d-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="3c86d-120">*皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*</span><span class="sxs-lookup"><span data-stu-id="3c86d-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c86d-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c86d-121">See also</span></span>

- [<span data-ttu-id="3c86d-122">擴充性設計</span><span class="sxs-lookup"><span data-stu-id="3c86d-122">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [<span data-ttu-id="3c86d-123">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="3c86d-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
