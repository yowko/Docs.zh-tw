---
title: "成員多載"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2c84d70fb8c05dc295fc807c9a59085c47d0f455
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="member-overloading"></a><span data-ttu-id="9c463-102">成員多載</span><span class="sxs-lookup"><span data-stu-id="9c463-102">Member Overloading</span></span>
<span data-ttu-id="9c463-103">成員多載是指只有不同數目或類型的參數，但具有相同名稱的相同型別上建立兩個或多個成員。</span><span class="sxs-lookup"><span data-stu-id="9c463-103">Member overloading means creating two or more members on the same type that differ only in the number or type of parameters but have the same name.</span></span> <span data-ttu-id="9c463-104">例如，在下列程式碼，`WriteLine`方法多載：</span><span class="sxs-lookup"><span data-stu-id="9c463-104">For example, in the following, the `WriteLine` method is overloaded:</span></span>  
  
```  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
```  
  
 <span data-ttu-id="9c463-105">因為只有方法、 建構函式和索引的屬性可以有參數，只有那些成員可能會超載。</span><span class="sxs-lookup"><span data-stu-id="9c463-105">Because only methods, constructors, and indexed properties can have parameters, only those members can be overloaded.</span></span>  
  
 <span data-ttu-id="9c463-106">多載是其中一個最重要的技術，用於改善可用性、 產能和可重複使用程式庫的可讀性。</span><span class="sxs-lookup"><span data-stu-id="9c463-106">Overloading is one of the most important techniques for improving usability, productivity, and readability of reusable libraries.</span></span> <span data-ttu-id="9c463-107">多載的參數數目，讓能夠提供更簡單的建構函式和方法的版本。</span><span class="sxs-lookup"><span data-stu-id="9c463-107">Overloading on the number of parameters makes it possible to provide simpler versions of constructors and methods.</span></span> <span data-ttu-id="9c463-108">參數類型多載，可讓使用相同的成員執行相同作業上將選取的不同類型的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="9c463-108">Overloading on the parameter type makes it possible to use the same member name for members performing identical operations on a selected set of different types.</span></span>  
  
 <span data-ttu-id="9c463-109">**✓ 不要**試著使用描述性的參數名稱，表示使用較短的多載的預設值。</span><span class="sxs-lookup"><span data-stu-id="9c463-109">**✓ DO** try to use descriptive parameter names to indicate the default used by shorter overloads.</span></span>  
  
 <span data-ttu-id="9c463-110">**請避免 x**任意改變在多載的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="9c463-110">**X AVOID** arbitrarily varying parameter names in overloads.</span></span> <span data-ttu-id="9c463-111">如果一個多載中的參數表示相同的輸入中另一個多載的參數，參數應該是相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="9c463-111">If a parameter in one overload represents the same input as a parameter in another overload, the parameters should have the same name.</span></span>  
  
 <span data-ttu-id="9c463-112">**請避免 x**不一致，在此順序中的參數中的多載成員。</span><span class="sxs-lookup"><span data-stu-id="9c463-112">**X AVOID** being inconsistent in the ordering of parameters in overloaded members.</span></span> <span data-ttu-id="9c463-113">具有相同名稱的參數應該會出現在所有多載中的相同位置。</span><span class="sxs-lookup"><span data-stu-id="9c463-113">Parameters with the same name should appear in the same position in all overloads.</span></span>  
  
 <span data-ttu-id="9c463-114">**✓ 不要**（如果是必要的擴充性） 進行的最長多載虛擬。</span><span class="sxs-lookup"><span data-stu-id="9c463-114">**✓ DO** make only the longest overload virtual (if extensibility is required).</span></span> <span data-ttu-id="9c463-115">較短的多載應該只是透過呼叫長的多載。</span><span class="sxs-lookup"><span data-stu-id="9c463-115">Shorter overloads should simply call through to a longer overload.</span></span>  
  
 <span data-ttu-id="9c463-116">**X 不**使用`ref`或`out`多載成員的修飾詞。</span><span class="sxs-lookup"><span data-stu-id="9c463-116">**X DO NOT** use `ref` or `out` modifiers to overload members.</span></span>  
  
 <span data-ttu-id="9c463-117">某些語言無法將呼叫解析為多載，就像這樣。</span><span class="sxs-lookup"><span data-stu-id="9c463-117">Some languages cannot resolve calls to overloads like this.</span></span> <span data-ttu-id="9c463-118">此外，這種多載通常有完全不同的語意，而且可能不能多載，但兩個各自方法改為。</span><span class="sxs-lookup"><span data-stu-id="9c463-118">In addition, such overloads usually have completely different semantics and probably should not be overloads but two separate methods instead.</span></span>  
  
 <span data-ttu-id="9c463-119">**X 不**具有多載具有位於相同位置和類似的類型參數，但具有不同的語意。</span><span class="sxs-lookup"><span data-stu-id="9c463-119">**X DO NOT** have overloads with parameters at the same position and similar types yet with different semantics.</span></span>  
  
 <span data-ttu-id="9c463-120">**✓ 不要**允許`null`為選擇性引數傳遞。</span><span class="sxs-lookup"><span data-stu-id="9c463-120">**✓ DO**  allow `null` to be passed for optional arguments.</span></span>  
  
 <span data-ttu-id="9c463-121">**✓ 不要**使用成員多載，而不是定義具有預設引數的成員。</span><span class="sxs-lookup"><span data-stu-id="9c463-121">**✓ DO** use member overloading rather than defining members with default arguments.</span></span>  
  
 <span data-ttu-id="9c463-122">預設引數不符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="9c463-122">Default arguments are not CLS compliant.</span></span>  
  
 <span data-ttu-id="9c463-123">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="9c463-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="9c463-124">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="9c463-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c463-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="9c463-125">See Also</span></span>  
 [<span data-ttu-id="9c463-126">成員設計方針</span><span class="sxs-lookup"><span data-stu-id="9c463-126">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="9c463-127">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="9c463-127">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
