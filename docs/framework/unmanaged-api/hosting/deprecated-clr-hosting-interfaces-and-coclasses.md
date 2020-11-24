---
title: 已被取代的 CLR 裝載介面和 Coclass
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 1
- .NET Framework 1.1, hosting interfaces
- hosting interfaces [.NET Framework], version 1
- .NET Framework 1.0, hosting interfaces
ms.assetid: 7b3d2755-cbab-4160-bc69-eb85791e38c7
ms.openlocfilehash: 8b90a33e2a0e6780a2ce908ff7ab251e94fbce90
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673094"
---
# <a name="deprecated-clr-hosting-interfaces-and-coclasses"></a><span data-ttu-id="2451b-102">已被取代的 CLR 裝載介面和 Coclass</span><span class="sxs-lookup"><span data-stu-id="2451b-102">Deprecated CLR Hosting Interfaces and Coclasses</span></span>

<span data-ttu-id="2451b-103">本節說明非受控主機可用來將 .NET Framework 1.0 版和1.1 版中的 common language runtime (CLR) 整合至其應用程式的介面。</span><span class="sxs-lookup"><span data-stu-id="2451b-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the .NET Framework versions 1.0 and 1.1 into their applications.</span></span> <span data-ttu-id="2451b-104">這些介面會提供方法，讓主機在進程中設定和載入執行時間。</span><span class="sxs-lookup"><span data-stu-id="2451b-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2451b-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="2451b-105">In This Section</span></span>  

 <span data-ttu-id="2451b-106">IAppDomainSetup</span><span class="sxs-lookup"><span data-stu-id="2451b-106">IAppDomainSetup</span></span>  
 <span data-ttu-id="2451b-107">提供可供主機設定的方法 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="2451b-107">Provides methods for the host to configure an <xref:System.AppDomain>.</span></span>  
  
 [<span data-ttu-id="2451b-108">ICeeFileGen 類別</span><span class="sxs-lookup"><span data-stu-id="2451b-108">ICeeFileGen Class</span></span>](iceefilegen-class.md)  
 <span data-ttu-id="2451b-109"> (已淘汰的) 會提供功能，以 (PE) 檔建立原生可攜式可執行檔。</span><span class="sxs-lookup"><span data-stu-id="2451b-109">(Deprecated) Provides functionality for creating a native portable executable (PE) file.</span></span>  
  
 [<span data-ttu-id="2451b-110">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="2451b-110">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)  
 <span data-ttu-id="2451b-111">提供用來設定 CLR 設定的主機方法。</span><span class="sxs-lookup"><span data-stu-id="2451b-111">Provides methods for the host to configure CLR settings.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2451b-112">相關章節</span><span class="sxs-lookup"><span data-stu-id="2451b-112">Related Sections</span></span>  

 [<span data-ttu-id="2451b-113">CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="2451b-113">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)  
 <span data-ttu-id="2451b-114">包含描述 .NET Framework 2.0 版和更新版本所提供之裝載介面的主題。</span><span class="sxs-lookup"><span data-stu-id="2451b-114">Contains topics that describe the hosting interfaces provided with the .NET Framework version 2.0 and later versions.</span></span>
