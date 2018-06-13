---
title: 裝載介面
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting]
- hosting interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], hosting
ms.assetid: cc64cb05-38da-418e-815a-daac8e8e26e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c2bef9e1671b8487a6702cce71106c84a2984317
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436156"
---
# <a name="hosting-interfaces"></a><span data-ttu-id="9d6a8-102">裝載介面</span><span class="sxs-lookup"><span data-stu-id="9d6a8-102">Hosting Interfaces</span></span>
<span data-ttu-id="9d6a8-103">本節描述 unmanaged 介面主機可用於將 common language runtime (CLR) 整合到他們的應用程式。</span><span class="sxs-lookup"><span data-stu-id="9d6a8-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span>  
  
 <span data-ttu-id="9d6a8-104">.NET Framework 2.0 版裝載介面取代.NET Framework 1.0 和 1.1 版介面。</span><span class="sxs-lookup"><span data-stu-id="9d6a8-104">The .NET Framework version 2.0 hosting interfaces supersede the .NET Framework version 1.0 and 1.1 interfaces.</span></span> <span data-ttu-id="9d6a8-105">有兩個集合的介面之間的差異。</span><span class="sxs-lookup"><span data-stu-id="9d6a8-105">There are significant differences between the two sets of interfaces.</span></span> <span data-ttu-id="9d6a8-106">混用它們可能會造成非預期的行為，並不建議使用。</span><span class="sxs-lookup"><span data-stu-id="9d6a8-106">Mixing them could cause unexpected behavior and is not recommended.</span></span>  
  
 <span data-ttu-id="9d6a8-107">.NET Framework 3.0 和 3.5 版使用.NET Framework 2.0 版裝載介面，並不會產生任何裝載的功能。</span><span class="sxs-lookup"><span data-stu-id="9d6a8-107">The .NET Framework versions 3.0 and 3.5 use the .NET Framework version 2.0 hosting interfaces, and do not introduce any hosting features.</span></span>  
  
 <span data-ttu-id="9d6a8-108">[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]裝載介面取代.NET Framework 2.0 介面。</span><span class="sxs-lookup"><span data-stu-id="9d6a8-108">The [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] hosting interfaces supersede the .NET Framework 2.0 interfaces.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="9d6a8-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="9d6a8-109">In This Section</span></span>  
 [<span data-ttu-id="9d6a8-110">已被取代的 CLR 裝載介面和 Coclass</span><span class="sxs-lookup"><span data-stu-id="9d6a8-110">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="9d6a8-111">描述裝載.NET framework 1.0 和 1.1 版中導入的介面。</span><span class="sxs-lookup"><span data-stu-id="9d6a8-111">Describes the hosting interfaces introduced in the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="9d6a8-112">CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="9d6a8-112">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="9d6a8-113">描述裝載.NET Framework 2.0 版中導入的介面。</span><span class="sxs-lookup"><span data-stu-id="9d6a8-113">Describes the hosting interfaces introduced in the .NET Framework version 2.0.</span></span>  
  
 [<span data-ttu-id="9d6a8-114">.NET Framework 4 和 4.5 中新增的 CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="9d6a8-114">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="9d6a8-115">描述裝載中導入的介面[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9d6a8-115">Describes the hosting interfaces introduced in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9d6a8-116">相關章節</span><span class="sxs-lookup"><span data-stu-id="9d6a8-116">Related Sections</span></span>  
 [<span data-ttu-id="9d6a8-117">裝載 Coclass</span><span class="sxs-lookup"><span data-stu-id="9d6a8-117">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)  
  
 [<span data-ttu-id="9d6a8-118">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="9d6a8-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="9d6a8-119">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="9d6a8-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
  
 [<span data-ttu-id="9d6a8-120">裝載結構</span><span class="sxs-lookup"><span data-stu-id="9d6a8-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
  
 [<span data-ttu-id="9d6a8-121">裝載</span><span class="sxs-lookup"><span data-stu-id="9d6a8-121">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
  
 [<span data-ttu-id="9d6a8-122">執行階段主機</span><span class="sxs-lookup"><span data-stu-id="9d6a8-122">Runtime Hosts</span></span>](http://msdn.microsoft.com/library/99d9246a-b994-4fe5-985c-8588d1d59998)
