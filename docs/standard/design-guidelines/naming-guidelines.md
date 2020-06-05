---
title: 命名方針
description: 在此總覽中，請閱讀在架構開發中使用的命名慣例。 前往涵蓋大小寫、一般命名和其他指導方針的文章。
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], about naming guidelines
- naming guidelines [.NET Framework]
- class library design guidelines [.NET Framework], names
- formatting [.NET Framework], names
- identifiers, class library element names
- names [.NET Framework]
- format naming guidelines [.NET Framework]
ms.assetid: fc076d66-9b5f-42d3-aa65-61d970c794a3
ms.openlocfilehash: fbcf5ef5eb02a5e45b5c981b4247ffe1c9c2631b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447143"
---
# <a name="naming-guidelines"></a><span data-ttu-id="9506c-104">命名方針</span><span class="sxs-lookup"><span data-stu-id="9506c-104">Naming Guidelines</span></span>
<span data-ttu-id="9506c-105">在開發架構時遵循一組一致的命名慣例，可能是架構可用性的主要貢獻。</span><span class="sxs-lookup"><span data-stu-id="9506c-105">Following a consistent set of naming conventions in the development of a framework can be a major contribution to the framework’s usability.</span></span> <span data-ttu-id="9506c-106">它可讓許多開發人員在廣為分隔的專案上使用架構。</span><span class="sxs-lookup"><span data-stu-id="9506c-106">It allows the framework to be used by many developers on widely separated projects.</span></span> <span data-ttu-id="9506c-107">除了表單的一致性之外，架構專案的名稱也必須容易理解，而且必須傳達每個元素的函式。</span><span class="sxs-lookup"><span data-stu-id="9506c-107">Beyond consistency of form, names of framework elements must be easily understood and must convey the function of each element.</span></span>  
  
 <span data-ttu-id="9506c-108">本章的目標是要提供一組一致的命名慣例，讓開發人員能夠立即瞭解其名稱。</span><span class="sxs-lookup"><span data-stu-id="9506c-108">The goal of this chapter is to provide a consistent set of naming conventions that results in names that make immediate sense to developers.</span></span>  
  
 <span data-ttu-id="9506c-109">雖然將這些命名慣例當做一般程式碼開發指導方針，會在整個程式碼中產生更一致的命名，但您只需要將它們套用至公開公開的 Api （公用或受保護的類型和成員，以及明確實作為介面）。</span><span class="sxs-lookup"><span data-stu-id="9506c-109">Although adopting these naming conventions as general code development guidelines would result in more consistent naming throughout your code, you are required only to apply them to APIs that are publicly exposed (public or protected types and members, and explicitly implemented interfaces).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9506c-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="9506c-110">In This Section</span></span>  
 [<span data-ttu-id="9506c-111">大小寫慣例</span><span class="sxs-lookup"><span data-stu-id="9506c-111">Capitalization Conventions</span></span>](capitalization-conventions.md)  
 [<span data-ttu-id="9506c-112">一般命名慣例</span><span class="sxs-lookup"><span data-stu-id="9506c-112">General Naming Conventions</span></span>](general-naming-conventions.md)  
 [<span data-ttu-id="9506c-113">元件和 Dll 的名稱</span><span class="sxs-lookup"><span data-stu-id="9506c-113">Names of Assemblies and DLLs</span></span>](names-of-assemblies-and-dlls.md)  
 [<span data-ttu-id="9506c-114">命名空間的名稱</span><span class="sxs-lookup"><span data-stu-id="9506c-114">Names of Namespaces</span></span>](names-of-namespaces.md)  
 [<span data-ttu-id="9506c-115">類別、結構和介面的名稱</span><span class="sxs-lookup"><span data-stu-id="9506c-115">Names of Classes, Structs, and Interfaces</span></span>](names-of-classes-structs-and-interfaces.md)  
 [<span data-ttu-id="9506c-116">成員類型的名稱</span><span class="sxs-lookup"><span data-stu-id="9506c-116">Names of Type Members</span></span>](names-of-type-members.md)  
 [<span data-ttu-id="9506c-117">具名引數</span><span class="sxs-lookup"><span data-stu-id="9506c-117">Naming Parameters</span></span>](naming-parameters.md)  
 [<span data-ttu-id="9506c-118">命名資源</span><span class="sxs-lookup"><span data-stu-id="9506c-118">Naming Resources</span></span>](naming-resources.md)  
 <span data-ttu-id="9506c-119">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="9506c-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="9506c-120">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。\*\*</span><span class="sxs-lookup"><span data-stu-id="9506c-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9506c-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="9506c-121">See also</span></span>

- [<span data-ttu-id="9506c-122">架構設計方針</span><span class="sxs-lookup"><span data-stu-id="9506c-122">Framework Design Guidelines</span></span>](index.md)
