---
title: 屬性
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
ms.openlocfilehash: c7bbbda88bd2fddb235b9ae639848e08a452c913
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741794"
---
# <a name="attributes"></a><span data-ttu-id="4208e-102">屬性</span><span class="sxs-lookup"><span data-stu-id="4208e-102">Attributes</span></span>
<span data-ttu-id="4208e-103"><xref:System.Attribute?displayProperty=nameWithType> 是用來定義自訂屬性的基類。</span><span class="sxs-lookup"><span data-stu-id="4208e-103"><xref:System.Attribute?displayProperty=nameWithType> is a base class used to define custom attributes.</span></span>

 <span data-ttu-id="4208e-104">屬性（attribute）是可以新增至程式設計專案（例如元件、類型、成員和參數）的批註。</span><span class="sxs-lookup"><span data-stu-id="4208e-104">Attributes are annotations that can be added to programming elements such as assemblies, types, members, and parameters.</span></span> <span data-ttu-id="4208e-105">它們會儲存在元件的中繼資料中，而且可以在執行時間使用反映 Api 來存取。</span><span class="sxs-lookup"><span data-stu-id="4208e-105">They are stored in the metadata of the assembly and can be accessed at runtime using the reflection APIs.</span></span> <span data-ttu-id="4208e-106">例如，架構會定義可以套用至類型或成員的 <xref:System.ObsoleteAttribute>，以指出類型或成員已被取代。</span><span class="sxs-lookup"><span data-stu-id="4208e-106">For example, the Framework defines the <xref:System.ObsoleteAttribute>, which can be applied to a type or a member to indicate that the type or member has been deprecated.</span></span>

 <span data-ttu-id="4208e-107">屬性可以有一或多個屬性，其中包含與屬性相關的其他資料。</span><span class="sxs-lookup"><span data-stu-id="4208e-107">Attributes can have one or more properties that carry additional data related to the attribute.</span></span> <span data-ttu-id="4208e-108">例如，`ObsoleteAttribute` 可能會包含有關發行的其他資訊，其中的類型或成員已被取代，而新 Api 的描述則取代過時的 API。</span><span class="sxs-lookup"><span data-stu-id="4208e-108">For example, `ObsoleteAttribute` could carry additional information about the release in which a type or a member got deprecated and the description of the new APIs replacing the obsolete API.</span></span>

 <span data-ttu-id="4208e-109">套用屬性時，必須指定屬性的某些屬性。</span><span class="sxs-lookup"><span data-stu-id="4208e-109">Some properties of an attribute must be specified when the attribute is applied.</span></span> <span data-ttu-id="4208e-110">這些稱為必要的屬性或必要的引數，因為它們是以位置函式參數表示。</span><span class="sxs-lookup"><span data-stu-id="4208e-110">These are referred to as the required properties or required arguments, because they are represented as positional constructor parameters.</span></span> <span data-ttu-id="4208e-111">例如，<xref:System.Diagnostics.ConditionalAttribute> 的 <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> 屬性是必要的屬性。</span><span class="sxs-lookup"><span data-stu-id="4208e-111">For example, the <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> property of the <xref:System.Diagnostics.ConditionalAttribute> is a required property.</span></span>

 <span data-ttu-id="4208e-112">套用屬性時，不一定要指定的屬性稱為選擇性屬性（或選擇性引數）。</span><span class="sxs-lookup"><span data-stu-id="4208e-112">Properties that do not necessarily have to be specified when the attribute is applied are called optional properties (or optional arguments).</span></span> <span data-ttu-id="4208e-113">它們是以可設定的屬性來表示。</span><span class="sxs-lookup"><span data-stu-id="4208e-113">They are represented by settable properties.</span></span> <span data-ttu-id="4208e-114">當套用屬性時，編譯器會提供特殊語法來設定這些屬性。</span><span class="sxs-lookup"><span data-stu-id="4208e-114">Compilers provide special syntax to set these properties when an attribute is applied.</span></span> <span data-ttu-id="4208e-115">例如，<xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> 屬性代表一個選擇性引數。</span><span class="sxs-lookup"><span data-stu-id="4208e-115">For example, the <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property represents an optional argument.</span></span>

 <span data-ttu-id="4208e-116">✔️ DO 使用後置詞 "Attribute" 來命名自訂屬性類別。</span><span class="sxs-lookup"><span data-stu-id="4208e-116">✔️ DO name custom attribute classes with the suffix "Attribute."</span></span>

 <span data-ttu-id="4208e-117">✔️請將 <xref:System.AttributeUsageAttribute> 套用至自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="4208e-117">✔️ DO apply the <xref:System.AttributeUsageAttribute> to custom attributes.</span></span>

 <span data-ttu-id="4208e-118">✔️提供選擇性引數的可設定屬性。</span><span class="sxs-lookup"><span data-stu-id="4208e-118">✔️ DO provide settable properties for optional arguments.</span></span>

 <span data-ttu-id="4208e-119">✔️提供必要引數的僅限取得屬性。</span><span class="sxs-lookup"><span data-stu-id="4208e-119">✔️ DO provide get-only properties for required arguments.</span></span>

 <span data-ttu-id="4208e-120">✔️確實提供了用來初始化對應于必要引數之屬性的參數化參數。</span><span class="sxs-lookup"><span data-stu-id="4208e-120">✔️ DO provide constructor parameters to initialize properties corresponding to required arguments.</span></span> <span data-ttu-id="4208e-121">每個參數都應該具有相同的名稱（但大小寫不同）做為對應的屬性。</span><span class="sxs-lookup"><span data-stu-id="4208e-121">Each parameter should have the same name (although with different casing) as the corresponding property.</span></span>

 <span data-ttu-id="4208e-122">❌ 避免提供函數化參數來初始化對應于選擇性引數的屬性。</span><span class="sxs-lookup"><span data-stu-id="4208e-122">❌ AVOID providing constructor parameters to initialize properties corresponding to the optional arguments.</span></span>

 <span data-ttu-id="4208e-123">換句話說，沒有可同時使用「函式」和「setter」設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="4208e-123">In other words, do not have properties that can be set with both a constructor and a setter.</span></span> <span data-ttu-id="4208e-124">這項指導方針非常明確地說，哪些引數是選擇性的，而且是必要的，而且可以避免有兩種方式來執行相同的動作。</span><span class="sxs-lookup"><span data-stu-id="4208e-124">This guideline makes very explicit which arguments are optional and which are required, and avoids having two ways of doing the same thing.</span></span>

 <span data-ttu-id="4208e-125">❌ 避免多載自訂屬性的函式。</span><span class="sxs-lookup"><span data-stu-id="4208e-125">❌ AVOID overloading custom attribute constructors.</span></span>

 <span data-ttu-id="4208e-126">只有一個函式會清楚地與使用者通訊，而這些引數是必要的，哪些是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="4208e-126">Having only one constructor clearly communicates to the user which arguments are required and which are optional.</span></span>

 <span data-ttu-id="4208e-127">✔️在可能的情況下密封自訂屬性類別。</span><span class="sxs-lookup"><span data-stu-id="4208e-127">✔️ DO seal custom attribute classes, if possible.</span></span> <span data-ttu-id="4208e-128">這會讓屬性的查詢速度更快。</span><span class="sxs-lookup"><span data-stu-id="4208e-128">This makes the look-up for the attribute faster.</span></span>

 <span data-ttu-id="4208e-129">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="4208e-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="4208e-130">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="4208e-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="4208e-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="4208e-131">See also</span></span>

- [<span data-ttu-id="4208e-132">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="4208e-132">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="4208e-133">用法方針</span><span class="sxs-lookup"><span data-stu-id="4208e-133">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
