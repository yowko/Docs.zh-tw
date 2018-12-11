---
title: Framework 設計方針
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
author: KrzysztofCwalina
ms.openlocfilehash: 736069926a2a3fdc4856a51c5226f725b22c1d5f
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147602"
---
# <a name="framework-design-guidelines"></a><span data-ttu-id="b45ec-102">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="b45ec-102">Framework Design Guidelines</span></span>
<span data-ttu-id="b45ec-103">本章節提供指導方針來設計擴充並與其互動 .NET Framework 的程式庫。</span><span class="sxs-lookup"><span data-stu-id="b45ec-103">This section provides guidelines for designing libraries that extend and interact with the .NET Framework.</span></span> <span data-ttu-id="b45ec-104">目標是要協助確保 API 一致性和易用性，藉由提供統一的程式設計模型，用於開發的程式設計語言無關的程式庫設計人員。</span><span class="sxs-lookup"><span data-stu-id="b45ec-104">The goal is to help library designers ensure API consistency and ease of use by providing a unified programming model that is independent of the programming language used for development.</span></span> <span data-ttu-id="b45ec-105">我們建議您遵循這些設計指導方針，開發可擴充.NET Framework 的類別和元件時。</span><span class="sxs-lookup"><span data-stu-id="b45ec-105">We recommend that you follow these design guidelines when developing classes and components that extend the .NET Framework.</span></span> <span data-ttu-id="b45ec-106">不一致的程式庫設計造成不良影響開發人員的生產力，並防止採用。</span><span class="sxs-lookup"><span data-stu-id="b45ec-106">Inconsistent library design adversely affects developer productivity and discourages adoption.</span></span>  
  
 <span data-ttu-id="b45ec-107">指導方針會編排成簡單的建議前置詞條款`Do`， `Consider`， `Avoid`，和`Do not`。</span><span class="sxs-lookup"><span data-stu-id="b45ec-107">The guidelines are organized as simple recommendations prefixed with the terms `Do`, `Consider`, `Avoid`, and `Do not`.</span></span> <span data-ttu-id="b45ec-108">這些指導方針旨在協助類別庫設計人員了解不同方案之間的取捨。</span><span class="sxs-lookup"><span data-stu-id="b45ec-108">These guidelines are intended to help class library designers understand the trade-offs between different solutions.</span></span> <span data-ttu-id="b45ec-109">可能會有一些情況良好的程式庫設計需要您違反這些設計指導方針。</span><span class="sxs-lookup"><span data-stu-id="b45ec-109">There might be situations where good library design requires that you violate these design guidelines.</span></span> <span data-ttu-id="b45ec-110">這種情況下應該很少見，而且您必須清除且吸引人的原因，對您的決策。</span><span class="sxs-lookup"><span data-stu-id="b45ec-110">Such cases should be rare, and it is important that you have a clear and compelling reason for your decision.</span></span>  
  
 <span data-ttu-id="b45ec-111">這些指導方針摘錄自*Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式*，Krzysztof Cwalina 與 Brad Abrams。</span><span class="sxs-lookup"><span data-stu-id="b45ec-111">These guidelines are excerpted from the book *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition*, by Krzysztof Cwalina and Brad Abrams.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b45ec-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="b45ec-112">In This Section</span></span>  
 [<span data-ttu-id="b45ec-113">命名方針</span><span class="sxs-lookup"><span data-stu-id="b45ec-113">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 <span data-ttu-id="b45ec-114">提供的指導方針命名組件、 命名空間、 類型和類別庫中的成員。</span><span class="sxs-lookup"><span data-stu-id="b45ec-114">Provides guidelines for naming assemblies, namespaces, types, and members in class libraries.</span></span>  
  
 [<span data-ttu-id="b45ec-115">類型設計方針</span><span class="sxs-lookup"><span data-stu-id="b45ec-115">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 <span data-ttu-id="b45ec-116">提供使用靜態和抽象類別、 介面、 列舉、 結構與其他類型的指導方針。</span><span class="sxs-lookup"><span data-stu-id="b45ec-116">Provides guidelines for using static and abstract classes, interfaces, enumerations, structures, and other types.</span></span>  
  
 [<span data-ttu-id="b45ec-117">成員設計方針</span><span class="sxs-lookup"><span data-stu-id="b45ec-117">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 <span data-ttu-id="b45ec-118">提供設計和使用屬性、 方法、 建構函式、 欄位、 事件、 運算子和參數的指導方針。</span><span class="sxs-lookup"><span data-stu-id="b45ec-118">Provides guidelines for designing and using properties, methods, constructors, fields, events, operators, and parameters.</span></span>  
  
 [<span data-ttu-id="b45ec-119">擴充性設計</span><span class="sxs-lookup"><span data-stu-id="b45ec-119">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 <span data-ttu-id="b45ec-120">討論擴充性機制，例如子類別化，使用事件、 虛擬成員和回呼，並說明如何選擇最符合您的架構需求的機制。</span><span class="sxs-lookup"><span data-stu-id="b45ec-120">Discusses extensibility mechanisms such as subclassing, using events, virtual members, and callbacks, and explains how to choose the mechanisms that best meet your framework's requirements.</span></span>  
  
 [<span data-ttu-id="b45ec-121">例外狀況的設計方針</span><span class="sxs-lookup"><span data-stu-id="b45ec-121">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)  
 <span data-ttu-id="b45ec-122">說明設計、 擲回和攔截例外狀況的設計方針。</span><span class="sxs-lookup"><span data-stu-id="b45ec-122">Describes design guidelines for designing, throwing, and catching exceptions.</span></span>  
  
 [<span data-ttu-id="b45ec-123">用法方針</span><span class="sxs-lookup"><span data-stu-id="b45ec-123">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 <span data-ttu-id="b45ec-124">描述使用常見的類型，例如陣列、 屬性和集合、 支援序列化，以及多載等號比較運算子的指導方針。</span><span class="sxs-lookup"><span data-stu-id="b45ec-124">Describes guidelines for using common types such as arrays, attributes, and collections, supporting serialization, and overloading equality operators.</span></span>  
  
 [<span data-ttu-id="b45ec-125">一般設計模式</span><span class="sxs-lookup"><span data-stu-id="b45ec-125">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 <span data-ttu-id="b45ec-126">提供指導方針選擇並實作相依性屬性和處置模式。</span><span class="sxs-lookup"><span data-stu-id="b45ec-126">Provides guidelines for choosing and implementing dependency properties and the dispose pattern.</span></span>  
  
 <span data-ttu-id="b45ec-127">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="b45ec-127">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="b45ec-128">*皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*</span><span class="sxs-lookup"><span data-stu-id="b45ec-128">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b45ec-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b45ec-129">See also</span></span>

- [<span data-ttu-id="b45ec-130">概觀</span><span class="sxs-lookup"><span data-stu-id="b45ec-130">Overview</span></span>](../../../docs/framework/get-started/overview.md)  
- [<span data-ttu-id="b45ec-131">.NET Framework 藍圖</span><span class="sxs-lookup"><span data-stu-id="b45ec-131">Roadmap for the .NET Framework</span></span>](https://msdn.microsoft.com/library/0b46b7c6-9163-4f99-8e58-0d1ee7da8c67)  
- [<span data-ttu-id="b45ec-132">開發指南</span><span class="sxs-lookup"><span data-stu-id="b45ec-132">Development Guide</span></span>](../../../docs/framework/development-guide.md)
