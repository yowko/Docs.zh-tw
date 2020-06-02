---
title: 屬性
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
ms.openlocfilehash: 12a67d75a5f9642408cca69b2e3764a67f101549
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280578"
---
# <a name="attributes"></a><span data-ttu-id="3f205-102">屬性</span><span class="sxs-lookup"><span data-stu-id="3f205-102">Attributes</span></span>

<span data-ttu-id="3f205-103"><xref:System.Attribute?displayProperty=nameWithType>是用來定義自訂屬性的基類。</span><span class="sxs-lookup"><span data-stu-id="3f205-103"><xref:System.Attribute?displayProperty=nameWithType> is a base class used to define custom attributes.</span></span>

 <span data-ttu-id="3f205-104">屬性（attribute）是可以新增至程式設計專案（例如元件、類型、成員和參數）的批註。</span><span class="sxs-lookup"><span data-stu-id="3f205-104">Attributes are annotations that can be added to programming elements such as assemblies, types, members, and parameters.</span></span> <span data-ttu-id="3f205-105">它們會儲存在元件的中繼資料中，而且可以在執行時間使用反映 Api 來存取。</span><span class="sxs-lookup"><span data-stu-id="3f205-105">They are stored in the metadata of the assembly and can be accessed at run time using the reflection APIs.</span></span> <span data-ttu-id="3f205-106">例如，.NET <xref:System.ObsoleteAttribute> 會定義屬性（attribute），它可以套用至類型或成員，以表示類型或成員已被取代。</span><span class="sxs-lookup"><span data-stu-id="3f205-106">For example, .NET defines the <xref:System.ObsoleteAttribute> attribute, which can be applied to a type or a member to indicate that the type or member has been deprecated.</span></span>

 <span data-ttu-id="3f205-107">屬性可以有一或多個屬性，其中包含與屬性相關的其他資料。</span><span class="sxs-lookup"><span data-stu-id="3f205-107">Attributes can have one or more properties that carry additional data related to the attribute.</span></span> <span data-ttu-id="3f205-108">例如， `ObsoleteAttribute` 可能會包含類型或成員已被取代之版本的其他相關資訊，以及取代過時 api 之新 api 的描述。</span><span class="sxs-lookup"><span data-stu-id="3f205-108">For example, `ObsoleteAttribute` could carry additional information about the release in which a type or a member got deprecated and a description of the new API that replaces the obsolete API.</span></span>

 <span data-ttu-id="3f205-109">套用屬性時，必須指定屬性的某些屬性。</span><span class="sxs-lookup"><span data-stu-id="3f205-109">Some properties of an attribute must be specified when the attribute is applied.</span></span> <span data-ttu-id="3f205-110">這些稱為必要的屬性或必要的引數，因為它們是以位置函式參數表示。</span><span class="sxs-lookup"><span data-stu-id="3f205-110">These are referred to as the required properties or required arguments, because they are represented as positional constructor parameters.</span></span> <span data-ttu-id="3f205-111">例如，的 <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> 屬性 <xref:System.Diagnostics.ConditionalAttribute> 是必要的屬性。</span><span class="sxs-lookup"><span data-stu-id="3f205-111">For example, the <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> property of the <xref:System.Diagnostics.ConditionalAttribute> is a required property.</span></span>

 <span data-ttu-id="3f205-112">套用屬性時，不一定要指定的屬性稱為選擇性屬性（或選擇性引數）。</span><span class="sxs-lookup"><span data-stu-id="3f205-112">Properties that don't necessarily have to be specified when the attribute is applied are called optional properties (or optional arguments).</span></span> <span data-ttu-id="3f205-113">它們是以可設定的屬性來表示。</span><span class="sxs-lookup"><span data-stu-id="3f205-113">They are represented by settable properties.</span></span> <span data-ttu-id="3f205-114">當套用屬性時，編譯器會提供特殊語法來設定這些屬性。</span><span class="sxs-lookup"><span data-stu-id="3f205-114">Compilers provide special syntax to set these properties when an attribute is applied.</span></span> <span data-ttu-id="3f205-115">例如， <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> 屬性代表一個選擇性引數。</span><span class="sxs-lookup"><span data-stu-id="3f205-115">For example, the <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property represents an optional argument.</span></span>

 <span data-ttu-id="3f205-116">✔️ DO 使用後置詞 "Attribute" 來命名自訂屬性類別。</span><span class="sxs-lookup"><span data-stu-id="3f205-116">✔️ DO name custom attribute classes with the suffix "Attribute."</span></span>

 <span data-ttu-id="3f205-117">✔️，請將套用 <xref:System.AttributeUsageAttribute> 至自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="3f205-117">✔️ DO apply the <xref:System.AttributeUsageAttribute> to custom attributes.</span></span>

 <span data-ttu-id="3f205-118">✔️提供選擇性引數的可設定屬性。</span><span class="sxs-lookup"><span data-stu-id="3f205-118">✔️ DO provide settable properties for optional arguments.</span></span>

 <span data-ttu-id="3f205-119">✔️提供必要引數的僅限取得屬性。</span><span class="sxs-lookup"><span data-stu-id="3f205-119">✔️ DO provide get-only properties for required arguments.</span></span>

 <span data-ttu-id="3f205-120">✔️確實提供了用來初始化對應于必要引數之屬性的參數化參數。</span><span class="sxs-lookup"><span data-stu-id="3f205-120">✔️ DO provide constructor parameters to initialize properties corresponding to required arguments.</span></span> <span data-ttu-id="3f205-121">每個參數都應該具有相同的名稱（但大小寫不同）做為對應的屬性。</span><span class="sxs-lookup"><span data-stu-id="3f205-121">Each parameter should have the same name (although with different casing) as the corresponding property.</span></span>

 <span data-ttu-id="3f205-122">❌請避免提供函數參數來初始化對應于選擇性引數的屬性。</span><span class="sxs-lookup"><span data-stu-id="3f205-122">❌ AVOID providing constructor parameters to initialize properties corresponding to the optional arguments.</span></span>

 <span data-ttu-id="3f205-123">換句話說，沒有可同時使用「函式」和「setter」設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="3f205-123">In other words, do not have properties that can be set with both a constructor and a setter.</span></span> <span data-ttu-id="3f205-124">這項指導方針非常明確地說，哪些引數是選擇性的，而且是必要的，而且可以避免有兩種方式來執行相同的動作。</span><span class="sxs-lookup"><span data-stu-id="3f205-124">This guideline makes very explicit which arguments are optional and which are required, and avoids having two ways of doing the same thing.</span></span>

 <span data-ttu-id="3f205-125">❌避免多載自訂屬性的函式。</span><span class="sxs-lookup"><span data-stu-id="3f205-125">❌ AVOID overloading custom attribute constructors.</span></span>

 <span data-ttu-id="3f205-126">只有一個函式會清楚地與使用者通訊，而這些引數是必要的，哪些是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="3f205-126">Having only one constructor clearly communicates to the user which arguments are required and which are optional.</span></span>

 <span data-ttu-id="3f205-127">✔️在可能的情況下密封自訂屬性類別。</span><span class="sxs-lookup"><span data-stu-id="3f205-127">✔️ DO seal custom attribute classes, if possible.</span></span> <span data-ttu-id="3f205-128">這會讓屬性的查詢速度更快。</span><span class="sxs-lookup"><span data-stu-id="3f205-128">This makes the look-up for the attribute faster.</span></span>

 <span data-ttu-id="3f205-129">*部分 &copy; 2005，2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="3f205-129">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="3f205-130">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。\*\*</span><span class="sxs-lookup"><span data-stu-id="3f205-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="3f205-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f205-131">See also</span></span>

- [<span data-ttu-id="3f205-132">架構設計方針</span><span class="sxs-lookup"><span data-stu-id="3f205-132">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="3f205-133">使用指導方針</span><span class="sxs-lookup"><span data-stu-id="3f205-133">Usage Guidelines</span></span>](usage-guidelines.md)
