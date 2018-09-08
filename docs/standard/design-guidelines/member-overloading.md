---
title: 成員多載
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2127497d294cbfd4e1bb24d033f432378627ff13
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44208227"
---
# <a name="member-overloading"></a><span data-ttu-id="fe725-102">成員多載</span><span class="sxs-lookup"><span data-stu-id="fe725-102">Member Overloading</span></span>
<span data-ttu-id="fe725-103">成員多載是指的差別只在於參數類型或數目，但具有相同名稱的相同型別上建立兩個或多個成員。</span><span class="sxs-lookup"><span data-stu-id="fe725-103">Member overloading means creating two or more members on the same type that differ only in the number or type of parameters but have the same name.</span></span> <span data-ttu-id="fe725-104">例如，在下列程式碼，`WriteLine`多載方法：</span><span class="sxs-lookup"><span data-stu-id="fe725-104">For example, in the following, the `WriteLine` method is overloaded:</span></span>  
  
```  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
```  
  
 <span data-ttu-id="fe725-105">只有方法、 建構函式和索引的屬性可以有參數，因為只有這些成員可以多載。</span><span class="sxs-lookup"><span data-stu-id="fe725-105">Because only methods, constructors, and indexed properties can have parameters, only those members can be overloaded.</span></span>  
  
 <span data-ttu-id="fe725-106">多載是其中一個最重要的技術改進使用性、 生產力及重複使用程式庫的可讀性。</span><span class="sxs-lookup"><span data-stu-id="fe725-106">Overloading is one of the most important techniques for improving usability, productivity, and readability of reusable libraries.</span></span> <span data-ttu-id="fe725-107">多載的參數數目，讓能夠提供簡單的建構函式和方法的版本。</span><span class="sxs-lookup"><span data-stu-id="fe725-107">Overloading on the number of parameters makes it possible to provide simpler versions of constructors and methods.</span></span> <span data-ttu-id="fe725-108">參數類型多載，讓能夠使用相同的成員名稱，執行相同的作業，在一組選取的不同類型的成員。</span><span class="sxs-lookup"><span data-stu-id="fe725-108">Overloading on the parameter type makes it possible to use the same member name for members performing identical operations on a selected set of different types.</span></span>  
  
 <span data-ttu-id="fe725-109">**✓ DO** 試著使用描述性的參數名稱，表示使用較短的多載的預設值。</span><span class="sxs-lookup"><span data-stu-id="fe725-109">**✓ DO** try to use descriptive parameter names to indicate the default used by shorter overloads.</span></span>  
  
 <span data-ttu-id="fe725-110">**X AVOID** 任意改變在多載的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="fe725-110">**X AVOID** arbitrarily varying parameter names in overloads.</span></span> <span data-ttu-id="fe725-111">如果其中一個多載中的參數代表相同的輸入參數，以在另一個多載，這些參數應該有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="fe725-111">If a parameter in one overload represents the same input as a parameter in another overload, the parameters should have the same name.</span></span>  
  
 <span data-ttu-id="fe725-112">**X AVOID** 不一致，在此順序中的參數中的多載成員。</span><span class="sxs-lookup"><span data-stu-id="fe725-112">**X AVOID** being inconsistent in the ordering of parameters in overloaded members.</span></span> <span data-ttu-id="fe725-113">具有相同名稱的參數應該會出現在所有多載中的相同位置。</span><span class="sxs-lookup"><span data-stu-id="fe725-113">Parameters with the same name should appear in the same position in all overloads.</span></span>  
  
 <span data-ttu-id="fe725-114">**✓ DO**（如果是必要的擴充性） 進行的最長多載虛擬。</span><span class="sxs-lookup"><span data-stu-id="fe725-114">**✓ DO** make only the longest overload virtual (if extensibility is required).</span></span> <span data-ttu-id="fe725-115">較短的多載應該只是透過呼叫較長的多載。</span><span class="sxs-lookup"><span data-stu-id="fe725-115">Shorter overloads should simply call through to a longer overload.</span></span>  
  
 <span data-ttu-id="fe725-116">**X DO NOT** 使用 `ref` 或 `out` 多載成員的修飾詞。</span><span class="sxs-lookup"><span data-stu-id="fe725-116">**X DO NOT** use `ref` or `out` modifiers to overload members.</span></span>  
  
 <span data-ttu-id="fe725-117">有些語言無法解析這類的多載的呼叫。</span><span class="sxs-lookup"><span data-stu-id="fe725-117">Some languages cannot resolve calls to overloads like this.</span></span> <span data-ttu-id="fe725-118">此外，這類多載通常有完全不同的語意，而且可能不應該多載，但兩個不同的方法而。</span><span class="sxs-lookup"><span data-stu-id="fe725-118">In addition, such overloads usually have completely different semantics and probably should not be overloads but two separate methods instead.</span></span>  
  
 <span data-ttu-id="fe725-119">**X DO NOT** 具有多載具有位於相同位置和類似的類型參數，但具有不同的語意。</span><span class="sxs-lookup"><span data-stu-id="fe725-119">**X DO NOT** have overloads with parameters at the same position and similar types yet with different semantics.</span></span>  
  
 <span data-ttu-id="fe725-120">**✓ DO** 允許 `null` 為選擇性引數傳遞。</span><span class="sxs-lookup"><span data-stu-id="fe725-120">**✓ DO**  allow `null` to be passed for optional arguments.</span></span>  
  
 <span data-ttu-id="fe725-121">**✓ DO** 使用成員多載，而不是定義具有預設引數的成員。</span><span class="sxs-lookup"><span data-stu-id="fe725-121">**✓ DO** use member overloading rather than defining members with default arguments.</span></span>  
  
 <span data-ttu-id="fe725-122">預設引數不符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="fe725-122">Default arguments are not CLS compliant.</span></span>  
  
 <span data-ttu-id="fe725-123">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="fe725-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="fe725-124">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="fe725-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe725-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe725-125">See also</span></span>

- [<span data-ttu-id="fe725-126">成員設計方針</span><span class="sxs-lookup"><span data-stu-id="fe725-126">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
- [<span data-ttu-id="fe725-127">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="fe725-127">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
