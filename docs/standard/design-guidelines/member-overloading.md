---
title: 成員多載
ms.date: 10/22/2008
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
ms.openlocfilehash: fe8bf23a04e6684564d3d7e287c2a009e0817732
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706628"
---
# <a name="member-overloading"></a><span data-ttu-id="20e91-102">成員多載</span><span class="sxs-lookup"><span data-stu-id="20e91-102">Member Overloading</span></span>

<span data-ttu-id="20e91-103">成員多載表示在相同類型上建立兩個或多個成員，而這些成員只在參數的數目或類型不同，但具有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="20e91-103">Member overloading means creating two or more members on the same type that differ only in the number or type of parameters but have the same name.</span></span> <span data-ttu-id="20e91-104">例如，在下列範例中， `WriteLine` 方法會超載：</span><span class="sxs-lookup"><span data-stu-id="20e91-104">For example, in the following, the `WriteLine` method is overloaded:</span></span>

```csharp
public static class Console {
    public void WriteLine();
    public void WriteLine(string value);
    public void WriteLine(bool value);
    ...
}
```

 <span data-ttu-id="20e91-105">因為只有方法、函式和索引屬性可以有參數，所以只有這些成員可以多載。</span><span class="sxs-lookup"><span data-stu-id="20e91-105">Because only methods, constructors, and indexed properties can have parameters, only those members can be overloaded.</span></span>

 <span data-ttu-id="20e91-106">多載是改善可重複使用之程式庫的可用性、生產力和可讀性的最重要技術之一。</span><span class="sxs-lookup"><span data-stu-id="20e91-106">Overloading is one of the most important techniques for improving usability, productivity, and readability of reusable libraries.</span></span> <span data-ttu-id="20e91-107">參數數目的多載可讓您提供更簡單版本的函式和方法。</span><span class="sxs-lookup"><span data-stu-id="20e91-107">Overloading on the number of parameters makes it possible to provide simpler versions of constructors and methods.</span></span> <span data-ttu-id="20e91-108">參數類型上的多載可讓成員在一組選取的不同類型上執行相同的作業時，可以使用相同的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="20e91-108">Overloading on the parameter type makes it possible to use the same member name for members performing identical operations on a selected set of different types.</span></span>

 <span data-ttu-id="20e91-109">✔️請嘗試使用描述性參數名稱來表示較短的多載所使用的預設值。</span><span class="sxs-lookup"><span data-stu-id="20e91-109">✔️ DO try to use descriptive parameter names to indicate the default used by shorter overloads.</span></span>

 <span data-ttu-id="20e91-110">❌ 避免在多載中任意改變參數名稱。</span><span class="sxs-lookup"><span data-stu-id="20e91-110">❌ AVOID arbitrarily varying parameter names in overloads.</span></span> <span data-ttu-id="20e91-111">如果某個多載中的參數表示與另一個多載中的參數相同的輸入，則參數應具有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="20e91-111">If a parameter in one overload represents the same input as a parameter in another overload, the parameters should have the same name.</span></span>

 <span data-ttu-id="20e91-112">❌ 避免在多載成員的參數順序中出現不一致的情況。</span><span class="sxs-lookup"><span data-stu-id="20e91-112">❌ AVOID being inconsistent in the ordering of parameters in overloaded members.</span></span> <span data-ttu-id="20e91-113">具有相同名稱的參數應該會出現在所有多載中的相同位置。</span><span class="sxs-lookup"><span data-stu-id="20e91-113">Parameters with the same name should appear in the same position in all overloads.</span></span>

 <span data-ttu-id="20e91-114">如果) 需要擴充性，✔️只會進行最長的多載虛擬 (。</span><span class="sxs-lookup"><span data-stu-id="20e91-114">✔️ DO make only the longest overload virtual (if extensibility is required).</span></span> <span data-ttu-id="20e91-115">較短的多載應該只是呼叫較長的多載。</span><span class="sxs-lookup"><span data-stu-id="20e91-115">Shorter overloads should simply call through to a longer overload.</span></span>

 <span data-ttu-id="20e91-116">❌ 請勿使用或修飾詞來多載 `ref` `out` 成員。</span><span class="sxs-lookup"><span data-stu-id="20e91-116">❌ DO NOT use `ref` or `out` modifiers to overload members.</span></span>

 <span data-ttu-id="20e91-117">某些語言無法解析多載的呼叫，如下所示。</span><span class="sxs-lookup"><span data-stu-id="20e91-117">Some languages cannot resolve calls to overloads like this.</span></span> <span data-ttu-id="20e91-118">此外，這類多載通常會有完全不同的語法，但可能不應該是多載，而是兩個不同的方法。</span><span class="sxs-lookup"><span data-stu-id="20e91-118">In addition, such overloads usually have completely different semantics and probably should not be overloads but two separate methods instead.</span></span>

 <span data-ttu-id="20e91-119">❌ 沒有具有相同位置之參數的多載，以及具有不同語義的類似類型。</span><span class="sxs-lookup"><span data-stu-id="20e91-119">❌ DO NOT have overloads with parameters at the same position and similar types yet with different semantics.</span></span>

 <span data-ttu-id="20e91-120">✔️允許 `null` 傳遞選擇性引數。</span><span class="sxs-lookup"><span data-stu-id="20e91-120">✔️ DO  allow `null` to be passed for optional arguments.</span></span>

 <span data-ttu-id="20e91-121">✔️確實使用成員多載，而不是使用預設引數來定義成員。</span><span class="sxs-lookup"><span data-stu-id="20e91-121">✔️ DO use member overloading rather than defining members with default arguments.</span></span>

 <span data-ttu-id="20e91-122">預設引數不符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="20e91-122">Default arguments are not CLS compliant.</span></span>

 <span data-ttu-id="20e91-123">*部分©2005、2009 Microsoft Corporation。保留的擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="20e91-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="20e91-124">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="20e91-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="20e91-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20e91-125">See also</span></span>

- [<span data-ttu-id="20e91-126">成員設計方針</span><span class="sxs-lookup"><span data-stu-id="20e91-126">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="20e91-127">架構設計指導方針</span><span class="sxs-lookup"><span data-stu-id="20e91-127">Framework Design Guidelines</span></span>](index.md)
