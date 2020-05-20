---
title: 已被取代的 CLR 裝載介面和 Coclass
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 1
- .NET Framework 1.1, hosting interfaces
- hosting interfaces [.NET Framework], version 1
- .NET Framework 1.0, hosting interfaces
ms.assetid: 7b3d2755-cbab-4160-bc69-eb85791e38c7
ms.openlocfilehash: 814f148b39045ad5454a23dfce8e7f9441f69041
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616407"
---
# <a name="deprecated-clr-hosting-interfaces-and-coclasses"></a><span data-ttu-id="e99e0-102">已被取代的 CLR 裝載介面和 Coclass</span><span class="sxs-lookup"><span data-stu-id="e99e0-102">Deprecated CLR Hosting Interfaces and Coclasses</span></span>
<span data-ttu-id="e99e0-103">本節說明非受控主機可用來將 .NET Framework 版本1.0 和1.1 中的 common language runtime （CLR）整合到其應用程式的介面。</span><span class="sxs-lookup"><span data-stu-id="e99e0-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the .NET Framework versions 1.0 and 1.1 into their applications.</span></span> <span data-ttu-id="e99e0-104">這些介面會提供方法，讓主機設定並將執行時間載入進程中。</span><span class="sxs-lookup"><span data-stu-id="e99e0-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e99e0-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="e99e0-105">In This Section</span></span>  
 <span data-ttu-id="e99e0-106">IAppDomainSetup</span><span class="sxs-lookup"><span data-stu-id="e99e0-106">IAppDomainSetup</span></span>  
 <span data-ttu-id="e99e0-107">提供方法讓主機設定 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="e99e0-107">Provides methods for the host to configure an <xref:System.AppDomain>.</span></span>  
  
 [<span data-ttu-id="e99e0-108">ICeeFileGen 類別</span><span class="sxs-lookup"><span data-stu-id="e99e0-108">ICeeFileGen Class</span></span>](iceefilegen-class.md)  
 <span data-ttu-id="e99e0-109">不再提供建立原生可移植執行檔（PE）檔案的功能。</span><span class="sxs-lookup"><span data-stu-id="e99e0-109">(Deprecated) Provides functionality for creating a native portable executable (PE) file.</span></span>  
  
 [<span data-ttu-id="e99e0-110">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="e99e0-110">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)  
 <span data-ttu-id="e99e0-111">提供方法，讓主機設定 CLR 設定。</span><span class="sxs-lookup"><span data-stu-id="e99e0-111">Provides methods for the host to configure CLR settings.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e99e0-112">相關章節</span><span class="sxs-lookup"><span data-stu-id="e99e0-112">Related Sections</span></span>  
 [<span data-ttu-id="e99e0-113">CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="e99e0-113">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)  
 <span data-ttu-id="e99e0-114">包含描述 .NET Framework 版本2.0 和更新版本所提供之主控介面的主題。</span><span class="sxs-lookup"><span data-stu-id="e99e0-114">Contains topics that describe the hosting interfaces provided with the .NET Framework version 2.0 and later versions.</span></span>
