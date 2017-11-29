---
title: "裝載介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- interfaces [.NET Framework hosting]
- hosting interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], hosting
ms.assetid: cc64cb05-38da-418e-815a-daac8e8e26e5
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a3cad92c204fa10f72d7a9a61460f1234206cb39
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="hosting-interfaces"></a><span data-ttu-id="d7e9f-102">裝載介面</span><span class="sxs-lookup"><span data-stu-id="d7e9f-102">Hosting Interfaces</span></span>
<span data-ttu-id="d7e9f-103">本節描述 unmanaged 介面主機可用於將 common language runtime (CLR) 整合到他們的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d7e9f-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span>  
  
 <span data-ttu-id="d7e9f-104">.NET Framework 2.0 版裝載介面取代.NET Framework 1.0 和 1.1 版介面。</span><span class="sxs-lookup"><span data-stu-id="d7e9f-104">The .NET Framework version 2.0 hosting interfaces supersede the .NET Framework version 1.0 and 1.1 interfaces.</span></span> <span data-ttu-id="d7e9f-105">有兩個集合的介面之間的差異。</span><span class="sxs-lookup"><span data-stu-id="d7e9f-105">There are significant differences between the two sets of interfaces.</span></span> <span data-ttu-id="d7e9f-106">混用它們可能會造成非預期的行為，並不建議使用。</span><span class="sxs-lookup"><span data-stu-id="d7e9f-106">Mixing them could cause unexpected behavior and is not recommended.</span></span>  
  
 <span data-ttu-id="d7e9f-107">.NET Framework 3.0 和 3.5 版使用.NET Framework 2.0 版裝載介面，並不會產生任何裝載的功能。</span><span class="sxs-lookup"><span data-stu-id="d7e9f-107">The .NET Framework versions 3.0 and 3.5 use the .NET Framework version 2.0 hosting interfaces, and do not introduce any hosting features.</span></span>  
  
 <span data-ttu-id="d7e9f-108">[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]裝載介面取代.NET Framework 2.0 介面。</span><span class="sxs-lookup"><span data-stu-id="d7e9f-108">The [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] hosting interfaces supersede the .NET Framework 2.0 interfaces.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="d7e9f-109">本章節內容</span><span class="sxs-lookup"><span data-stu-id="d7e9f-109">In This Section</span></span>  
 [<span data-ttu-id="d7e9f-110">已被取代的 CLR 裝載介面和 Coclass</span><span class="sxs-lookup"><span data-stu-id="d7e9f-110">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="d7e9f-111">描述裝載.NET framework 1.0 和 1.1 版中導入的介面。</span><span class="sxs-lookup"><span data-stu-id="d7e9f-111">Describes the hosting interfaces introduced in the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="d7e9f-112">CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="d7e9f-112">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="d7e9f-113">描述裝載.NET Framework 2.0 版中導入的介面。</span><span class="sxs-lookup"><span data-stu-id="d7e9f-113">Describes the hosting interfaces introduced in the .NET Framework version 2.0.</span></span>  
  
 [<span data-ttu-id="d7e9f-114">在.NET Framework 4 和 4.5 加入的 CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="d7e9f-114">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="d7e9f-115">描述裝載中導入的介面[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d7e9f-115">Describes the hosting interfaces introduced in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d7e9f-116">相關章節</span><span class="sxs-lookup"><span data-stu-id="d7e9f-116">Related Sections</span></span>  
 [<span data-ttu-id="d7e9f-117">裝載 Coclass</span><span class="sxs-lookup"><span data-stu-id="d7e9f-117">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)  
  
 [<span data-ttu-id="d7e9f-118">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="d7e9f-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="d7e9f-119">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="d7e9f-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
  
 [<span data-ttu-id="d7e9f-120">裝載結構</span><span class="sxs-lookup"><span data-stu-id="d7e9f-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
  
 [<span data-ttu-id="d7e9f-121">裝載</span><span class="sxs-lookup"><span data-stu-id="d7e9f-121">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
  
 [<span data-ttu-id="d7e9f-122">執行階段主機</span><span class="sxs-lookup"><span data-stu-id="d7e9f-122">Runtime Hosts</span></span>](http://msdn.microsoft.com/en-us/99d9246a-b994-4fe5-985c-8588d1d59998)
