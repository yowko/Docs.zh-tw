---
title: 已被取代的 CLR 裝載介面和 Coclass
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 1
- .NET Framework 1.1, hosting interfaces
- hosting interfaces [.NET Framework], version 1
- .NET Framework 1.0, hosting interfaces
ms.assetid: 7b3d2755-cbab-4160-bc69-eb85791e38c7
ms.openlocfilehash: 08e193ed40c6538b62d8b1af0a8c41b4225f136b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138254"
---
# <a name="deprecated-clr-hosting-interfaces-and-coclasses"></a><span data-ttu-id="9f933-102">已被取代的 CLR 裝載介面和 Coclass</span><span class="sxs-lookup"><span data-stu-id="9f933-102">Deprecated CLR Hosting Interfaces and Coclasses</span></span>
<span data-ttu-id="9f933-103">本節說明非受控主機可用來將 .NET Framework 版本1.0 和1.1 中的 common language runtime （CLR）整合到其應用程式的介面。</span><span class="sxs-lookup"><span data-stu-id="9f933-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the .NET Framework versions 1.0 and 1.1 into their applications.</span></span> <span data-ttu-id="9f933-104">這些介面會提供方法，讓主機設定並將執行時間載入進程中。</span><span class="sxs-lookup"><span data-stu-id="9f933-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9f933-105">本章節內容</span><span class="sxs-lookup"><span data-stu-id="9f933-105">In This Section</span></span>  
 <span data-ttu-id="9f933-106">IAppDomainSetup</span><span class="sxs-lookup"><span data-stu-id="9f933-106">IAppDomainSetup</span></span>  
 <span data-ttu-id="9f933-107">提供可讓主機設定 <xref:System.AppDomain>的方法。</span><span class="sxs-lookup"><span data-stu-id="9f933-107">Provides methods for the host to configure an <xref:System.AppDomain>.</span></span>  
  
 [<span data-ttu-id="9f933-108">ICeeFileGen 類別</span><span class="sxs-lookup"><span data-stu-id="9f933-108">ICeeFileGen Class</span></span>](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md)  
 <span data-ttu-id="9f933-109">不再提供建立原生可移植執行檔（PE）檔案的功能。</span><span class="sxs-lookup"><span data-stu-id="9f933-109">(Deprecated) Provides functionality for creating a native portable executable (PE) file.</span></span>  
  
 [<span data-ttu-id="9f933-110">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="9f933-110">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 <span data-ttu-id="9f933-111">提供方法，讓主機設定 CLR 設定。</span><span class="sxs-lookup"><span data-stu-id="9f933-111">Provides methods for the host to configure CLR settings.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9f933-112">相關章節</span><span class="sxs-lookup"><span data-stu-id="9f933-112">Related Sections</span></span>  
 [<span data-ttu-id="9f933-113">CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="9f933-113">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="9f933-114">包含描述 .NET Framework 版本2.0 和更新版本所提供之主控介面的主題。</span><span class="sxs-lookup"><span data-stu-id="9f933-114">Contains topics that describe the hosting interfaces provided with the .NET Framework version 2.0 and later versions.</span></span>
