---
title: ".NET Framework Class Library 中的泛型 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], in .NET Framework class library
ms.assetid: afdd5477-6770-4686-8297-f58a4d749daf
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 35a6c53b089872076028e8ec82f55de2a90962a6
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="generics-in-the-net-framework-class-library-c-programming-guide"></a><span data-ttu-id="014e0-102">.NET Framework 類別庫中的泛型 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="014e0-102">Generics in the .NET Framework Class Library (C# Programming Guide)</span></span>
<span data-ttu-id="014e0-103">.NET Framework Class Library 2.0 版提供了新的命名空間 <xref:System.Collections.Generic>，其中包含數個立即可用的泛型集合類別和關聯介面。</span><span class="sxs-lookup"><span data-stu-id="014e0-103">Version 2.0 of the .NET Framework class library provides a new namespace, <xref:System.Collections.Generic>, which includes several ready-to-use generic collection classes and associated interfaces.</span></span> <span data-ttu-id="014e0-104">其他命名空間 (例如 <xref:System>) 也提供新的泛型介面 (例如 <xref:System.IComparable%601>)。</span><span class="sxs-lookup"><span data-stu-id="014e0-104">Other namespaces, such as <xref:System>, also provide new generic interfaces such as <xref:System.IComparable%601>.</span></span> <span data-ttu-id="014e0-105">與舊版 .NET Framework 中提供的非泛型集合類別相較，這些類別和介面更有效率且為型別安全。</span><span class="sxs-lookup"><span data-stu-id="014e0-105">These classes and interfaces are more efficient and type-safe than the non-generic collection classes provided in earlier releases of the .NET Framework.</span></span> <span data-ttu-id="014e0-106">在設計和實作您自己的自訂集合類別之前，請考慮是否可以使用 .NET Framework Class Library 所提供的其中一個類別，或從中衍生類別。</span><span class="sxs-lookup"><span data-stu-id="014e0-106">Before designing and implementing your own custom collection classes, consider whether you can use or derive a class from one of the classes provided in the .NET Framework class library.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="014e0-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="014e0-107">See Also</span></span>  
 <span data-ttu-id="014e0-108">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="014e0-108">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="014e0-109"> [何時使用泛型集合](../../../standard/collections/when-to-use-generic-collections.md) </span><span class="sxs-lookup"><span data-stu-id="014e0-109"> [When to Use Generic Collections](../../../standard/collections/when-to-use-generic-collections.md) </span></span>  
<span data-ttu-id="014e0-110"> [集合和資料結構](../../../standard/collections/index.md) </span><span class="sxs-lookup"><span data-stu-id="014e0-110"> [Collections and Data Structures](../../../standard/collections/index.md) </span></span>  
<span data-ttu-id="014e0-111"> [泛型簡介](../../../csharp/programming-guide/generics/introduction-to-generics.md)</span><span class="sxs-lookup"><span data-stu-id="014e0-111"> [Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md)</span></span>
