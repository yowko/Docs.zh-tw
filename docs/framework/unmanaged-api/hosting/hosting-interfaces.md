---
title: 裝載介面
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting]
- hosting interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], hosting
ms.assetid: cc64cb05-38da-418e-815a-daac8e8e26e5
ms.openlocfilehash: f82301da1813b8d50deebf4452d8c07809c186c5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721799"
---
# <a name="hosting-interfaces"></a><span data-ttu-id="91181-102">裝載介面</span><span class="sxs-lookup"><span data-stu-id="91181-102">Hosting Interfaces</span></span>

<span data-ttu-id="91181-103">本節說明非受控主機可用來將 common language runtime (CLR) 整合至其應用程式的介面。</span><span class="sxs-lookup"><span data-stu-id="91181-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span>  
  
 <span data-ttu-id="91181-104">.NET Framework 2.0 版裝載介面會取代 .NET Framework 1.0 版和1.1 介面。</span><span class="sxs-lookup"><span data-stu-id="91181-104">The .NET Framework version 2.0 hosting interfaces supersede the .NET Framework version 1.0 and 1.1 interfaces.</span></span> <span data-ttu-id="91181-105">這兩組介面之間有顯著的差異。</span><span class="sxs-lookup"><span data-stu-id="91181-105">There are significant differences between the two sets of interfaces.</span></span> <span data-ttu-id="91181-106">混合它們可能會導致非預期的行為，因此不建議使用。</span><span class="sxs-lookup"><span data-stu-id="91181-106">Mixing them could cause unexpected behavior and is not recommended.</span></span>  
  
 <span data-ttu-id="91181-107">.NET Framework 版本3.0 和3.5 使用 .NET Framework 版本2.0 裝載介面，不會引進任何裝載功能。</span><span class="sxs-lookup"><span data-stu-id="91181-107">The .NET Framework versions 3.0 and 3.5 use the .NET Framework version 2.0 hosting interfaces, and do not introduce any hosting features.</span></span>  
  
 <span data-ttu-id="91181-108">.NET Framework 4 裝載介面會取代 .NET Framework 2.0 介面。</span><span class="sxs-lookup"><span data-stu-id="91181-108">The .NET Framework 4 hosting interfaces supersede the .NET Framework 2.0 interfaces.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="91181-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="91181-109">In This Section</span></span>  

 [<span data-ttu-id="91181-110">已被取代的 CLR 裝載介面和 Coclass</span><span class="sxs-lookup"><span data-stu-id="91181-110">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="91181-111">描述 .NET Framework 1.0 和1.1 版中引進的裝載介面。</span><span class="sxs-lookup"><span data-stu-id="91181-111">Describes the hosting interfaces introduced in the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="91181-112">CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="91181-112">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)  
 <span data-ttu-id="91181-113">描述 .NET Framework 版本2.0 中引進的裝載介面。</span><span class="sxs-lookup"><span data-stu-id="91181-113">Describes the hosting interfaces introduced in the .NET Framework version 2.0.</span></span>  
  
 [<span data-ttu-id="91181-114">.NET Framework 4 和 4.5 中新增的 CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="91181-114">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="91181-115">描述 .NET Framework 4 中引進的裝載介面。</span><span class="sxs-lookup"><span data-stu-id="91181-115">Describes the hosting interfaces introduced in the .NET Framework 4.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="91181-116">相關章節</span><span class="sxs-lookup"><span data-stu-id="91181-116">Related Sections</span></span>  

 [<span data-ttu-id="91181-117">裝載 Coclass</span><span class="sxs-lookup"><span data-stu-id="91181-117">Hosting Coclasses</span></span>](hosting-coclasses.md)  
  
 [<span data-ttu-id="91181-118">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="91181-118">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="91181-119">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="91181-119">Hosting Enumerations</span></span>](hosting-enumerations.md)  
  
 [<span data-ttu-id="91181-120">裝載結構</span><span class="sxs-lookup"><span data-stu-id="91181-120">Hosting Structures</span></span>](hosting-structures.md)  
  
 [<span data-ttu-id="91181-121">裝載</span><span class="sxs-lookup"><span data-stu-id="91181-121">Hosting</span></span>](index.md)  
  
 <span data-ttu-id="91181-122">[執行階段主應用程式](/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="91181-122">[Runtime Hosts](/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span></span>
