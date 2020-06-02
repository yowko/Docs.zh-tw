---
title: 擴充方法
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
ms.openlocfilehash: 77c012d7838ae2fa1f62163bc58520db67c64ce5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289755"
---
# <a name="extension-methods"></a><span data-ttu-id="249cc-102">擴充方法</span><span class="sxs-lookup"><span data-stu-id="249cc-102">Extension methods</span></span>

<span data-ttu-id="249cc-103">擴充方法是一種語言功能，可使用實例方法呼叫語法來呼叫靜態方法。</span><span class="sxs-lookup"><span data-stu-id="249cc-103">Extension methods are a language feature that allows static methods to be called using instance-method call syntax.</span></span> <span data-ttu-id="249cc-104">這些方法必須採用至少一個參數，其代表方法要運作的實例。</span><span class="sxs-lookup"><span data-stu-id="249cc-104">These methods must take at least one parameter, which represents the instance the method is to operate on.</span></span>

 <span data-ttu-id="249cc-105">定義擴充方法的類別稱為「贊助商」類別，而且必須宣告為 `static` 。</span><span class="sxs-lookup"><span data-stu-id="249cc-105">The class that defines an extension method is referred to as the "sponsor" class, and it must be declared as `static`.</span></span> <span data-ttu-id="249cc-106">若要使用擴充方法，您必須匯入定義贊助程式類別的命名空間。</span><span class="sxs-lookup"><span data-stu-id="249cc-106">To use extension methods, you must import the namespace that defines the sponsor class.</span></span>

 <span data-ttu-id="249cc-107">❌避免過度利用擴充方法，特別是在您不擁有的類型上。</span><span class="sxs-lookup"><span data-stu-id="249cc-107">❌ AVOID overuse of extension methods, especially on types you don't own.</span></span>

 <span data-ttu-id="249cc-108">如果您擁有類型的原始程式碼，請考慮改為使用一般實例方法。</span><span class="sxs-lookup"><span data-stu-id="249cc-108">If you do own source code of a type, consider using regular instance methods instead.</span></span> <span data-ttu-id="249cc-109">如果您沒有原始碼，而且想要新增方法，請務必小心。</span><span class="sxs-lookup"><span data-stu-id="249cc-109">If you don't own the source code and you want to add a method, be very careful.</span></span> <span data-ttu-id="249cc-110">使用擴充方法時，可能會有雜亂的型別 Api，而這些型別並未設計成具有這些方法。</span><span class="sxs-lookup"><span data-stu-id="249cc-110">Liberal use of extension methods has the potential of cluttering APIs of types that were not designed to have these methods.</span></span>

 <span data-ttu-id="249cc-111">✔️在下列任何情況下，請考慮使用擴充方法：</span><span class="sxs-lookup"><span data-stu-id="249cc-111">✔️ CONSIDER using extension methods in any of the following scenarios:</span></span>

- <span data-ttu-id="249cc-112">若要提供與每個介面執行相關的協助程式功能，也可以根據核心介面來撰寫功能。</span><span class="sxs-lookup"><span data-stu-id="249cc-112">To provide helper functionality relevant to every implementation of an interface, if said functionality can be written in terms of the core interface.</span></span> <span data-ttu-id="249cc-113">這是因為實體的執行無法以其他方式指派給介面。</span><span class="sxs-lookup"><span data-stu-id="249cc-113">This is because concrete implementations cannot otherwise be assigned to interfaces.</span></span> <span data-ttu-id="249cc-114">例如，LINQ to Objects 運算子會實作為所有類型的擴充方法 <xref:System.Collections.Generic.IEnumerable%601> 。</span><span class="sxs-lookup"><span data-stu-id="249cc-114">For example, the LINQ to Objects operators are implemented as extension methods for all <xref:System.Collections.Generic.IEnumerable%601> types.</span></span> <span data-ttu-id="249cc-115">因此，任何 `IEnumerable<>` 實現都會自動啟用 LINQ。</span><span class="sxs-lookup"><span data-stu-id="249cc-115">Thus, any `IEnumerable<>` implementation is automatically LINQ-enabled.</span></span>

- <span data-ttu-id="249cc-116">當實例方法會引進某種類型的相依性，但這類相依性會中斷相依性管理規則。</span><span class="sxs-lookup"><span data-stu-id="249cc-116">When an instance method would introduce a dependency on some type, but such a dependency would break dependency management rules.</span></span> <span data-ttu-id="249cc-117">例如，從到的相依 <xref:System.String> 性 <xref:System.Uri?displayProperty=nameWithType> 可能不是理想的做法，因此從相依性管理的觀點來看，傳回 `String.ToUri()` 的實例方法會 `System.Uri` 是錯誤的設計。</span><span class="sxs-lookup"><span data-stu-id="249cc-117">For example, a dependency from <xref:System.String> to <xref:System.Uri?displayProperty=nameWithType> is probably not desirable, and so `String.ToUri()` instance method returning `System.Uri` would be the wrong design from a dependency management perspective.</span></span> <span data-ttu-id="249cc-118">傳回的靜態擴充方法會 `Uri.ToUri(this string str)` `System.Uri` 是更好的設計。</span><span class="sxs-lookup"><span data-stu-id="249cc-118">A static extension method `Uri.ToUri(this string str)` returning `System.Uri` would be a much better design.</span></span>

 <span data-ttu-id="249cc-119">❌避免在上定義擴充方法 <xref:System.Object?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="249cc-119">❌ AVOID defining extension methods on <xref:System.Object?displayProperty=nameWithType>.</span></span>

 <span data-ttu-id="249cc-120">Visual Basic 使用者將無法在使用擴充方法語法的物件參考上呼叫這類方法。</span><span class="sxs-lookup"><span data-stu-id="249cc-120">Visual Basic users will not be able to call such methods on object references using the extension method syntax.</span></span> <span data-ttu-id="249cc-121">在 Visual Basic 中，將參考宣告為 `Object` 會強制將其上的所有方法調用都設為晚期繫結（這表示呼叫的實際成員會在執行時間決定）。</span><span class="sxs-lookup"><span data-stu-id="249cc-121">In Visual Basic, declaring a reference as `Object` forces all method invocations on it to be late bound (which means the actual member called is determined at run time).</span></span> <span data-ttu-id="249cc-122">擴充方法的系結是在編譯時期決定（早期繫結）。</span><span class="sxs-lookup"><span data-stu-id="249cc-122">Bindings to extension methods are determined at compile time (early bound).</span></span>

 <span data-ttu-id="249cc-123">此指導方針適用于有相同系結行為或不支援擴充方法的其他語言。</span><span class="sxs-lookup"><span data-stu-id="249cc-123">This guideline applies to other languages where the same binding behavior is present or where extension methods are not supported.</span></span>

 <span data-ttu-id="249cc-124">❌請勿將擴充方法放在與延伸類型相同的命名空間中，除非它是用來將方法加入介面或用於相依性管理。</span><span class="sxs-lookup"><span data-stu-id="249cc-124">❌ DO NOT put extension methods in the same namespace as the extended type unless it is for adding methods to interfaces or for dependency management.</span></span>

 <span data-ttu-id="249cc-125">❌請避免定義兩個或多個具有相同簽章的擴充方法，即使它們位於不同的命名空間也一樣。</span><span class="sxs-lookup"><span data-stu-id="249cc-125">❌ AVOID defining two or more extension methods with the same signature, even if they reside in different namespaces.</span></span>

 <span data-ttu-id="249cc-126">✔️如果類型為介面，則請考慮在與延伸類型相同的命名空間中定義擴充方法，而且如果延伸方法要用於大部分或所有案例中，則為。</span><span class="sxs-lookup"><span data-stu-id="249cc-126">✔️ CONSIDER defining extension methods in the same namespace as the extended type if the type is an interface and if the extension methods are meant to be used in most or all cases.</span></span>

 <span data-ttu-id="249cc-127">❌請勿定義擴充方法，以在通常與其他功能相關聯的命名空間中執行功能。</span><span class="sxs-lookup"><span data-stu-id="249cc-127">❌ DO NOT define extension methods implementing a feature in namespaces normally associated with other features.</span></span> <span data-ttu-id="249cc-128">相反地，請在與它們所屬的功能相關聯的命名空間中定義它們。</span><span class="sxs-lookup"><span data-stu-id="249cc-128">Instead, define them in the namespace associated with the feature they belong to.</span></span>

 <span data-ttu-id="249cc-129">❌避免針對擴充方法專用的命名空間進行一般命名（例如 "Extension"）。</span><span class="sxs-lookup"><span data-stu-id="249cc-129">❌ AVOID generic naming of namespaces dedicated to extension methods (e.g., "Extensions").</span></span> <span data-ttu-id="249cc-130">請改用描述性名稱（例如「路由」）。</span><span class="sxs-lookup"><span data-stu-id="249cc-130">Use a descriptive name (e.g., "Routing") instead.</span></span>

 <span data-ttu-id="249cc-131">*部分 &copy; 2005，2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="249cc-131">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="249cc-132">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。\*\*</span><span class="sxs-lookup"><span data-stu-id="249cc-132">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="249cc-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="249cc-133">See also</span></span>

- [<span data-ttu-id="249cc-134">成員設計方針</span><span class="sxs-lookup"><span data-stu-id="249cc-134">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="249cc-135">架構設計方針</span><span class="sxs-lookup"><span data-stu-id="249cc-135">Framework Design Guidelines</span></span>](index.md)
