---
title: 成員多載
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
ms.openlocfilehash: c9cb178e838aab99c22089b527a6bd2e86b325de
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76727835"
---
# <a name="member-overloading"></a><span data-ttu-id="28109-102">成員多載</span><span class="sxs-lookup"><span data-stu-id="28109-102">Member Overloading</span></span>
<span data-ttu-id="28109-103">Member overloading means creating two or more members on the same type that differ only in the number or type of parameters but have the same name.</span><span class="sxs-lookup"><span data-stu-id="28109-103">Member overloading means creating two or more members on the same type that differ only in the number or type of parameters but have the same name.</span></span> <span data-ttu-id="28109-104">For example, in the following, the `WriteLine` method is overloaded:</span><span class="sxs-lookup"><span data-stu-id="28109-104">For example, in the following, the `WriteLine` method is overloaded:</span></span>

```csharp
public static class Console {
    public void WriteLine();
    public void WriteLine(string value);
    public void WriteLine(bool value);
    ...
}
```

 <span data-ttu-id="28109-105">Because only methods, constructors, and indexed properties can have parameters, only those members can be overloaded.</span><span class="sxs-lookup"><span data-stu-id="28109-105">Because only methods, constructors, and indexed properties can have parameters, only those members can be overloaded.</span></span>

 <span data-ttu-id="28109-106">Overloading is one of the most important techniques for improving usability, productivity, and readability of reusable libraries.</span><span class="sxs-lookup"><span data-stu-id="28109-106">Overloading is one of the most important techniques for improving usability, productivity, and readability of reusable libraries.</span></span> <span data-ttu-id="28109-107">Overloading on the number of parameters makes it possible to provide simpler versions of constructors and methods.</span><span class="sxs-lookup"><span data-stu-id="28109-107">Overloading on the number of parameters makes it possible to provide simpler versions of constructors and methods.</span></span> <span data-ttu-id="28109-108">Overloading on the parameter type makes it possible to use the same member name for members performing identical operations on a selected set of different types.</span><span class="sxs-lookup"><span data-stu-id="28109-108">Overloading on the parameter type makes it possible to use the same member name for members performing identical operations on a selected set of different types.</span></span>

 <span data-ttu-id="28109-109">✔️ DO try to use descriptive parameter names to indicate the default used by shorter overloads.</span><span class="sxs-lookup"><span data-stu-id="28109-109">✔️ DO try to use descriptive parameter names to indicate the default used by shorter overloads.</span></span>

 <span data-ttu-id="28109-110">❌ AVOID arbitrarily varying parameter names in overloads.</span><span class="sxs-lookup"><span data-stu-id="28109-110">❌ AVOID arbitrarily varying parameter names in overloads.</span></span> <span data-ttu-id="28109-111">If a parameter in one overload represents the same input as a parameter in another overload, the parameters should have the same name.</span><span class="sxs-lookup"><span data-stu-id="28109-111">If a parameter in one overload represents the same input as a parameter in another overload, the parameters should have the same name.</span></span>

 <span data-ttu-id="28109-112">❌ AVOID being inconsistent in the ordering of parameters in overloaded members.</span><span class="sxs-lookup"><span data-stu-id="28109-112">❌ AVOID being inconsistent in the ordering of parameters in overloaded members.</span></span> <span data-ttu-id="28109-113">Parameters with the same name should appear in the same position in all overloads.</span><span class="sxs-lookup"><span data-stu-id="28109-113">Parameters with the same name should appear in the same position in all overloads.</span></span>

 <span data-ttu-id="28109-114">✔️ DO make only the longest overload virtual (if extensibility is required).</span><span class="sxs-lookup"><span data-stu-id="28109-114">✔️ DO make only the longest overload virtual (if extensibility is required).</span></span> <span data-ttu-id="28109-115">Shorter overloads should simply call through to a longer overload.</span><span class="sxs-lookup"><span data-stu-id="28109-115">Shorter overloads should simply call through to a longer overload.</span></span>

 <span data-ttu-id="28109-116">❌ DO NOT use `ref` or `out` modifiers to overload members.</span><span class="sxs-lookup"><span data-stu-id="28109-116">❌ DO NOT use `ref` or `out` modifiers to overload members.</span></span>

 <span data-ttu-id="28109-117">Some languages cannot resolve calls to overloads like this.</span><span class="sxs-lookup"><span data-stu-id="28109-117">Some languages cannot resolve calls to overloads like this.</span></span> <span data-ttu-id="28109-118">In addition, such overloads usually have completely different semantics and probably should not be overloads but two separate methods instead.</span><span class="sxs-lookup"><span data-stu-id="28109-118">In addition, such overloads usually have completely different semantics and probably should not be overloads but two separate methods instead.</span></span>

 <span data-ttu-id="28109-119">❌ DO NOT have overloads with parameters at the same position and similar types yet with different semantics.</span><span class="sxs-lookup"><span data-stu-id="28109-119">❌ DO NOT have overloads with parameters at the same position and similar types yet with different semantics.</span></span>

 <span data-ttu-id="28109-120">✔️ DO  allow `null` to be passed for optional arguments.</span><span class="sxs-lookup"><span data-stu-id="28109-120">✔️ DO  allow `null` to be passed for optional arguments.</span></span>

 <span data-ttu-id="28109-121">✔️ DO use member overloading rather than defining members with default arguments.</span><span class="sxs-lookup"><span data-stu-id="28109-121">✔️ DO use member overloading rather than defining members with default arguments.</span></span>

 <span data-ttu-id="28109-122">Default arguments are not CLS compliant.</span><span class="sxs-lookup"><span data-stu-id="28109-122">Default arguments are not CLS compliant.</span></span>

 <span data-ttu-id="28109-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="28109-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="28109-124">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="28109-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="28109-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="28109-125">See also</span></span>

- [<span data-ttu-id="28109-126">成員設計方針</span><span class="sxs-lookup"><span data-stu-id="28109-126">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="28109-127">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="28109-127">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
