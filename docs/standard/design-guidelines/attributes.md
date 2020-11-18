---
title: 屬性
ms.date: 10/22/2008
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
ms.openlocfilehash: cc4752066124a0ea8081390bfb5f3791d21ec96d
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821615"
---
# <a name="attributes"></a><span data-ttu-id="396f8-102">屬性</span><span class="sxs-lookup"><span data-stu-id="396f8-102">Attributes</span></span>
<span data-ttu-id="396f8-103"><xref:System.Attribute?displayProperty=nameWithType> 是用來定義自訂屬性的基類。</span><span class="sxs-lookup"><span data-stu-id="396f8-103"><xref:System.Attribute?displayProperty=nameWithType> is a base class used to define custom attributes.</span></span>

 <span data-ttu-id="396f8-104">屬性是可以加入至程式設計專案（例如元件、類型、成員和參數）的附注。</span><span class="sxs-lookup"><span data-stu-id="396f8-104">Attributes are annotations that can be added to programming elements such as assemblies, types, members, and parameters.</span></span> <span data-ttu-id="396f8-105">它們會儲存在元件的中繼資料中，並可在執行時間使用反映 Api 來存取。</span><span class="sxs-lookup"><span data-stu-id="396f8-105">They are stored in the metadata of the assembly and can be accessed at runtime using the reflection APIs.</span></span> <span data-ttu-id="396f8-106">例如，架構會定義可套用 <xref:System.ObsoleteAttribute> 至類型或成員的，以表示類型或成員已被取代。</span><span class="sxs-lookup"><span data-stu-id="396f8-106">For example, the Framework defines the <xref:System.ObsoleteAttribute>, which can be applied to a type or a member to indicate that the type or member has been deprecated.</span></span>

 <span data-ttu-id="396f8-107">屬性可以有一或多個屬性包含與屬性相關的其他資料。</span><span class="sxs-lookup"><span data-stu-id="396f8-107">Attributes can have one or more properties that carry additional data related to the attribute.</span></span> <span data-ttu-id="396f8-108">例如， `ObsoleteAttribute` 可能會包含類型或成員已被取代之版本的其他相關資訊，以及取代淘汰的 api 之新 api 的描述。</span><span class="sxs-lookup"><span data-stu-id="396f8-108">For example, `ObsoleteAttribute` could carry additional information about the release in which a type or a member got deprecated and the description of the new APIs replacing the obsolete API.</span></span>

 <span data-ttu-id="396f8-109">套用屬性時，必須指定屬性的某些屬性。</span><span class="sxs-lookup"><span data-stu-id="396f8-109">Some properties of an attribute must be specified when the attribute is applied.</span></span> <span data-ttu-id="396f8-110">這些是必要的屬性或必要的引數，因為它們是以位置的函式參數來表示。</span><span class="sxs-lookup"><span data-stu-id="396f8-110">These are referred to as the required properties or required arguments, because they are represented as positional constructor parameters.</span></span> <span data-ttu-id="396f8-111">例如，的 <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> 屬性 <xref:System.Diagnostics.ConditionalAttribute> 是必要屬性。</span><span class="sxs-lookup"><span data-stu-id="396f8-111">For example, the <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> property of the <xref:System.Diagnostics.ConditionalAttribute> is a required property.</span></span>

 <span data-ttu-id="396f8-112">套用屬性時，不一定要指定的屬性稱為選用屬性 (或) 選擇性引數。</span><span class="sxs-lookup"><span data-stu-id="396f8-112">Properties that do not necessarily have to be specified when the attribute is applied are called optional properties (or optional arguments).</span></span> <span data-ttu-id="396f8-113">它們是由可設定的屬性工作表示。</span><span class="sxs-lookup"><span data-stu-id="396f8-113">They are represented by settable properties.</span></span> <span data-ttu-id="396f8-114">當套用屬性時，編譯器會提供特殊的語法來設定這些屬性。</span><span class="sxs-lookup"><span data-stu-id="396f8-114">Compilers provide special syntax to set these properties when an attribute is applied.</span></span> <span data-ttu-id="396f8-115">例如， <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> 屬性代表選擇性引數。</span><span class="sxs-lookup"><span data-stu-id="396f8-115">For example, the <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property represents an optional argument.</span></span>

 <span data-ttu-id="396f8-116">✔️使用尾碼 "Attribute" 來命名自訂屬性類別。</span><span class="sxs-lookup"><span data-stu-id="396f8-116">✔️ DO name custom attribute classes with the suffix "Attribute."</span></span>

 <span data-ttu-id="396f8-117">✔️請將套用 <xref:System.AttributeUsageAttribute> 至自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="396f8-117">✔️ DO apply the <xref:System.AttributeUsageAttribute> to custom attributes.</span></span>

 <span data-ttu-id="396f8-118">✔️確實提供選擇性引數的可設定屬性。</span><span class="sxs-lookup"><span data-stu-id="396f8-118">✔️ DO provide settable properties for optional arguments.</span></span>

 <span data-ttu-id="396f8-119">✔️確實提供必要引數的 get 屬性。</span><span class="sxs-lookup"><span data-stu-id="396f8-119">✔️ DO provide get-only properties for required arguments.</span></span>

 <span data-ttu-id="396f8-120">✔️確實提供了函式參數，以初始化對應到必要引數的屬性。</span><span class="sxs-lookup"><span data-stu-id="396f8-120">✔️ DO provide constructor parameters to initialize properties corresponding to required arguments.</span></span> <span data-ttu-id="396f8-121">每個參數都應該有相同的名稱 (但使用不同的大小寫) 作為對應的屬性。</span><span class="sxs-lookup"><span data-stu-id="396f8-121">Each parameter should have the same name (although with different casing) as the corresponding property.</span></span>

 <span data-ttu-id="396f8-122">❌ 避免提供函式參數來初始化對應至選擇性引數的屬性。</span><span class="sxs-lookup"><span data-stu-id="396f8-122">❌ AVOID providing constructor parameters to initialize properties corresponding to the optional arguments.</span></span>

 <span data-ttu-id="396f8-123">換句話說，沒有可同時以函式和 setter 設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="396f8-123">In other words, do not have properties that can be set with both a constructor and a setter.</span></span> <span data-ttu-id="396f8-124">這項指導方針很明確地明確指出哪些引數是選擇性的，哪些是必要的，而且可以避免有兩種方法來執行相同的工作。</span><span class="sxs-lookup"><span data-stu-id="396f8-124">This guideline makes very explicit which arguments are optional and which are required, and avoids having two ways of doing the same thing.</span></span>

 <span data-ttu-id="396f8-125">❌ 避免多載自訂屬性的函式。</span><span class="sxs-lookup"><span data-stu-id="396f8-125">❌ AVOID overloading custom attribute constructors.</span></span>

 <span data-ttu-id="396f8-126">只有一個函式會清楚地與使用者傳達需要哪些引數，哪些是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="396f8-126">Having only one constructor clearly communicates to the user which arguments are required and which are optional.</span></span>

 <span data-ttu-id="396f8-127">✔️盡可能密封自訂屬性類別。</span><span class="sxs-lookup"><span data-stu-id="396f8-127">✔️ DO seal custom attribute classes, if possible.</span></span> <span data-ttu-id="396f8-128">這樣就能更快地查閱屬性。</span><span class="sxs-lookup"><span data-stu-id="396f8-128">This makes the look-up for the attribute faster.</span></span>

 <span data-ttu-id="396f8-129">*部分 &copy; 2005、2009 Microsoft Corporation。保留的擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="396f8-129">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="396f8-130">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="396f8-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="396f8-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="396f8-131">See also</span></span>

- [<span data-ttu-id="396f8-132">架構設計指導方針</span><span class="sxs-lookup"><span data-stu-id="396f8-132">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="396f8-133">使用指導方針</span><span class="sxs-lookup"><span data-stu-id="396f8-133">Usage Guidelines</span></span>](usage-guidelines.md)
