---
title: 命名方針
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
ms.openlocfilehash: ad98c0f3b02bdc81e6348493b4e0a02f9cb20ed4
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709188"
---
# <a name="naming-guidelines"></a><span data-ttu-id="70900-102">命名方針</span><span class="sxs-lookup"><span data-stu-id="70900-102">Naming Guidelines</span></span>
<span data-ttu-id="70900-103">在開發架構時遵循一組一致的命名慣例，可能是架構可用性的主要貢獻。</span><span class="sxs-lookup"><span data-stu-id="70900-103">Following a consistent set of naming conventions in the development of a framework can be a major contribution to the framework’s usability.</span></span> <span data-ttu-id="70900-104">它可讓許多開發人員在廣為分隔的專案上使用架構。</span><span class="sxs-lookup"><span data-stu-id="70900-104">It allows the framework to be used by many developers on widely separated projects.</span></span> <span data-ttu-id="70900-105">除了表單的一致性之外，架構專案的名稱也必須容易理解，而且必須傳達每個元素的函式。</span><span class="sxs-lookup"><span data-stu-id="70900-105">Beyond consistency of form, names of framework elements must be easily understood and must convey the function of each element.</span></span>  
  
 <span data-ttu-id="70900-106">本章的目標是要提供一組一致的命名慣例，讓開發人員能夠立即瞭解其名稱。</span><span class="sxs-lookup"><span data-stu-id="70900-106">The goal of this chapter is to provide a consistent set of naming conventions that results in names that make immediate sense to developers.</span></span>  
  
 <span data-ttu-id="70900-107">雖然將這些命名慣例當做一般程式碼開發指導方針，會在整個程式碼中產生更一致的命名，但您只需要將它們套用至公開公開的 Api （公用或受保護的類型和成員，以及明確實作為介面）。</span><span class="sxs-lookup"><span data-stu-id="70900-107">Although adopting these naming conventions as general code development guidelines would result in more consistent naming throughout your code, you are required only to apply them to APIs that are publicly exposed (public or protected types and members, and explicitly implemented interfaces).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="70900-108">本章節內容</span><span class="sxs-lookup"><span data-stu-id="70900-108">In This Section</span></span>  
 [<span data-ttu-id="70900-109">大小寫慣例</span><span class="sxs-lookup"><span data-stu-id="70900-109">Capitalization Conventions</span></span>](../../../docs/standard/design-guidelines/capitalization-conventions.md)  
 [<span data-ttu-id="70900-110">一般命名慣例</span><span class="sxs-lookup"><span data-stu-id="70900-110">General Naming Conventions</span></span>](../../../docs/standard/design-guidelines/general-naming-conventions.md)  
 [<span data-ttu-id="70900-111">組件和 DLL 的名稱</span><span class="sxs-lookup"><span data-stu-id="70900-111">Names of Assemblies and DLLs</span></span>](../../../docs/standard/design-guidelines/names-of-assemblies-and-dlls.md)  
 [<span data-ttu-id="70900-112">命名空間的名稱</span><span class="sxs-lookup"><span data-stu-id="70900-112">Names of Namespaces</span></span>](../../../docs/standard/design-guidelines/names-of-namespaces.md)  
 [<span data-ttu-id="70900-113">類別、結構和介面的名稱</span><span class="sxs-lookup"><span data-stu-id="70900-113">Names of Classes, Structs, and Interfaces</span></span>](../../../docs/standard/design-guidelines/names-of-classes-structs-and-interfaces.md)  
 [<span data-ttu-id="70900-114">類型成員名稱</span><span class="sxs-lookup"><span data-stu-id="70900-114">Names of Type Members</span></span>](../../../docs/standard/design-guidelines/names-of-type-members.md)  
 [<span data-ttu-id="70900-115">命名參數</span><span class="sxs-lookup"><span data-stu-id="70900-115">Naming Parameters</span></span>](../../../docs/standard/design-guidelines/naming-parameters.md)  
 [<span data-ttu-id="70900-116">命名資源</span><span class="sxs-lookup"><span data-stu-id="70900-116">Naming Resources</span></span>](../../../docs/standard/design-guidelines/naming-resources.md)  
 <span data-ttu-id="70900-117">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="70900-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="70900-118">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="70900-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70900-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="70900-119">See also</span></span>

- [<span data-ttu-id="70900-120">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="70900-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
