---
title: 命名方針
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 70888e068782add5ebe5ae1c7da3bdee842faea8
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44267004"
---
# <a name="naming-guidelines"></a><span data-ttu-id="86318-102">命名方針</span><span class="sxs-lookup"><span data-stu-id="86318-102">Naming Guidelines</span></span>
<span data-ttu-id="86318-103">遵循一組一致的開發架構的命名慣例，可以是主要的投稿內容架構的可用性。</span><span class="sxs-lookup"><span data-stu-id="86318-103">Following a consistent set of naming conventions in the development of a framework can be a major contribution to the framework’s usability.</span></span> <span data-ttu-id="86318-104">它可讓廣泛分隔的專案上的許多開發人員所使用的架構。</span><span class="sxs-lookup"><span data-stu-id="86318-104">It allows the framework to be used by many developers on widely separated projects.</span></span> <span data-ttu-id="86318-105">超過表單的一致性，必須容易了解架構元素的名稱，並必須傳達每個項目的函式。</span><span class="sxs-lookup"><span data-stu-id="86318-105">Beyond consistency of form, names of framework elements must be easily understood and must convey the function of each element.</span></span>  
  
 <span data-ttu-id="86318-106">本指南的目標是提供一組一致的命名慣例，產生對開發人員的即時運算的有意義的名稱。</span><span class="sxs-lookup"><span data-stu-id="86318-106">The goal of this chapter is to provide a consistent set of naming conventions that results in names that make immediate sense to developers.</span></span>  
  
 <span data-ttu-id="86318-107">雖然因為一般開發指導方針會導致更一致的命名，在整個程式碼，請採用下列命名慣例，您僅需要將它們套用到對外公開的 Api (公用或受保護的類型和成員，以及明確實作介面）。</span><span class="sxs-lookup"><span data-stu-id="86318-107">Although adopting these naming conventions as general code development guidelines would result in more consistent naming throughout your code, you are required only to apply them to APIs that are publicly exposed (public or protected types and members, and explicitly implemented interfaces).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="86318-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="86318-108">In This Section</span></span>  
 [<span data-ttu-id="86318-109">大小寫慣例</span><span class="sxs-lookup"><span data-stu-id="86318-109">Capitalization Conventions</span></span>](../../../docs/standard/design-guidelines/capitalization-conventions.md)  
 [<span data-ttu-id="86318-110">一般命名慣例</span><span class="sxs-lookup"><span data-stu-id="86318-110">General Naming Conventions</span></span>](../../../docs/standard/design-guidelines/general-naming-conventions.md)  
 [<span data-ttu-id="86318-111">組件和 DLL 的名稱</span><span class="sxs-lookup"><span data-stu-id="86318-111">Names of Assemblies and DLLs</span></span>](../../../docs/standard/design-guidelines/names-of-assemblies-and-dlls.md)  
 [<span data-ttu-id="86318-112">命名空間的名稱</span><span class="sxs-lookup"><span data-stu-id="86318-112">Names of Namespaces</span></span>](../../../docs/standard/design-guidelines/names-of-namespaces.md)  
 [<span data-ttu-id="86318-113">類別、結構和介面的名稱</span><span class="sxs-lookup"><span data-stu-id="86318-113">Names of Classes, Structs, and Interfaces</span></span>](../../../docs/standard/design-guidelines/names-of-classes-structs-and-interfaces.md)  
 [<span data-ttu-id="86318-114">類型成員名稱</span><span class="sxs-lookup"><span data-stu-id="86318-114">Names of Type Members</span></span>](../../../docs/standard/design-guidelines/names-of-type-members.md)  
 [<span data-ttu-id="86318-115">命名參數</span><span class="sxs-lookup"><span data-stu-id="86318-115">Naming Parameters</span></span>](../../../docs/standard/design-guidelines/naming-parameters.md)  
 [<span data-ttu-id="86318-116">命名資源</span><span class="sxs-lookup"><span data-stu-id="86318-116">Naming Resources</span></span>](../../../docs/standard/design-guidelines/naming-resources.md)  
 <span data-ttu-id="86318-117">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="86318-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="86318-118">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="86318-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86318-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86318-119">See also</span></span>

- [<span data-ttu-id="86318-120">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="86318-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
