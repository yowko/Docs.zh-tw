---
title: 命名方針
description: 在此總覽中，請參閱架構開發中使用的命名慣例。 移至涵蓋大小寫、一般命名和其他指導方針的文章。
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], about naming guidelines
- naming guidelines [.NET Framework]
- class library design guidelines [.NET Framework], names
- formatting [.NET Framework], names
- identifiers, class library element names
- names [.NET Framework]
- format naming guidelines [.NET Framework]
ms.assetid: fc076d66-9b5f-42d3-aa65-61d970c794a3
ms.openlocfilehash: de68eeb287b13bc9f55230243f23cd03508f2561
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706420"
---
# <a name="naming-guidelines"></a><span data-ttu-id="63f38-104">命名方針</span><span class="sxs-lookup"><span data-stu-id="63f38-104">Naming Guidelines</span></span>

<span data-ttu-id="63f38-105">在開發架構時遵循一組一致的命名慣例，可能會對架構的可用性有重大的貢獻。</span><span class="sxs-lookup"><span data-stu-id="63f38-105">Following a consistent set of naming conventions in the development of a framework can be a major contribution to the framework’s usability.</span></span> <span data-ttu-id="63f38-106">它可讓許多開發人員在廣泛分隔的專案上使用架構。</span><span class="sxs-lookup"><span data-stu-id="63f38-106">It allows the framework to be used by many developers on widely separated projects.</span></span> <span data-ttu-id="63f38-107">除了表單的一致性之外，架構元素的名稱也必須容易理解，而且必須傳達每個元素的函式。</span><span class="sxs-lookup"><span data-stu-id="63f38-107">Beyond consistency of form, names of framework elements must be easily understood and must convey the function of each element.</span></span>  
  
 <span data-ttu-id="63f38-108">本章的目的是要提供一組一致的命名慣例，以產生對開發人員而言可以立即理解的名稱。</span><span class="sxs-lookup"><span data-stu-id="63f38-108">The goal of this chapter is to provide a consistent set of naming conventions that results in names that make immediate sense to developers.</span></span>  
  
 <span data-ttu-id="63f38-109">雖然將這些命名慣例視為一般程式碼開發指導方針會導致在程式碼中有更一致的命名，但您只需要將它們套用至公開 (公用或受保護類型和成員的 Api，並) 明確執行的介面。</span><span class="sxs-lookup"><span data-stu-id="63f38-109">Although adopting these naming conventions as general code development guidelines would result in more consistent naming throughout your code, you are required only to apply them to APIs that are publicly exposed (public or protected types and members, and explicitly implemented interfaces).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="63f38-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="63f38-110">In This Section</span></span>  

 [<span data-ttu-id="63f38-111">大小寫慣例</span><span class="sxs-lookup"><span data-stu-id="63f38-111">Capitalization Conventions</span></span>](capitalization-conventions.md)  
 [<span data-ttu-id="63f38-112">一般命名慣例</span><span class="sxs-lookup"><span data-stu-id="63f38-112">General Naming Conventions</span></span>](general-naming-conventions.md)  
 [<span data-ttu-id="63f38-113">元件和 Dll 的名稱</span><span class="sxs-lookup"><span data-stu-id="63f38-113">Names of Assemblies and DLLs</span></span>](names-of-assemblies-and-dlls.md)  
 [<span data-ttu-id="63f38-114">命名空間的名稱</span><span class="sxs-lookup"><span data-stu-id="63f38-114">Names of Namespaces</span></span>](names-of-namespaces.md)  
 [<span data-ttu-id="63f38-115">類別、結構和介面的名稱</span><span class="sxs-lookup"><span data-stu-id="63f38-115">Names of Classes, Structs, and Interfaces</span></span>](names-of-classes-structs-and-interfaces.md)  
 [<span data-ttu-id="63f38-116">類型成員的名稱</span><span class="sxs-lookup"><span data-stu-id="63f38-116">Names of Type Members</span></span>](names-of-type-members.md)  
 [<span data-ttu-id="63f38-117">具名引數</span><span class="sxs-lookup"><span data-stu-id="63f38-117">Naming Parameters</span></span>](naming-parameters.md)  
 [<span data-ttu-id="63f38-118">命名資源</span><span class="sxs-lookup"><span data-stu-id="63f38-118">Naming Resources</span></span>](naming-resources.md)  
 <span data-ttu-id="63f38-119">*部分©2005、2009 Microsoft Corporation。保留的擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="63f38-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="63f38-120">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="63f38-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63f38-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63f38-121">See also</span></span>

- [<span data-ttu-id="63f38-122">架構設計指導方針</span><span class="sxs-lookup"><span data-stu-id="63f38-122">Framework Design Guidelines</span></span>](index.md)
