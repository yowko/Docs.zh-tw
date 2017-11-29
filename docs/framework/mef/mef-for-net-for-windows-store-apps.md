---
title: "適用於 Windows 市集應用程式的.NET 的 MEF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7667770e-d163-4ad6-a303-085cf73db2f2
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7f427656f9b385214db5b3bd26c4addb1122b35a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="mef-for-net-for-windows-store-apps"></a><span data-ttu-id="399e6-102">適用於 Windows 市集應用程式的.NET 的 MEF</span><span class="sxs-lookup"><span data-stu-id="399e6-102">MEF for .NET for Windows Store Apps</span></span>
<span data-ttu-id="399e6-103"><xref:System.Composition?displayProperty=nameWithType>及其子命名空間包含的類型，用於開發可擴充和[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式使用 Managed Extensibility Framework (MEF)。</span><span class="sxs-lookup"><span data-stu-id="399e6-103"><xref:System.Composition?displayProperty=nameWithType> and its child namespaces contain types for developing extensible [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps with Managed Extensibility Framework (MEF).</span></span> <span data-ttu-id="399e6-104">這些命名空間屬於[!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]子集的[!INCLUDE[win8](../../../includes/win8-md.md)]作業系統。</span><span class="sxs-lookup"><span data-stu-id="399e6-104">These namespaces are part of the [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] subset for the [!INCLUDE[win8](../../../includes/win8-md.md)] operating system.</span></span>  
  
 <span data-ttu-id="399e6-105">這些命名空間不是.NET Framework 一起散發的核心類別庫的一部分。</span><span class="sxs-lookup"><span data-stu-id="399e6-105">These namespaces are not part of the core class library distributed with the .NET Framework.</span></span> <span data-ttu-id="399e6-106">若要安裝這些命名空間，開啟您的專案中[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]，選擇**管理 NuGet 封裝**從**專案**，並在線上搜尋 Microsoft.Composition 封裝。</span><span class="sxs-lookup"><span data-stu-id="399e6-106">To install these namespaces, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the **Project** menu, and search online for the Microsoft.Composition package.</span></span>  
  
-   <span data-ttu-id="399e6-107"><xref:System.Composition?displayProperty=nameWithType>提供類別會構成核心 MEF 的[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="399e6-107"><xref:System.Composition?displayProperty=nameWithType> provides classes that constitute the core MEF for [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span>  
  
-   <span data-ttu-id="399e6-108"><xref:System.Composition.Convention?displayProperty=nameWithType>提供類型，可支援以慣例為基礎的組態模型使用 MEF。</span><span class="sxs-lookup"><span data-stu-id="399e6-108"><xref:System.Composition.Convention?displayProperty=nameWithType> provides types that support using MEF with a convention-based configuration model.</span></span>  
  
-   <span data-ttu-id="399e6-109"><xref:System.Composition.Hosting?displayProperty=nameWithType>提供的主應用程式的開發人員很有用的 MEF 類型。</span><span class="sxs-lookup"><span data-stu-id="399e6-109"><xref:System.Composition.Hosting?displayProperty=nameWithType> provides MEF types that are useful to developers of host applications.</span></span>  
  
-   <span data-ttu-id="399e6-110"><xref:System.Composition.Hosting.Core?displayProperty=nameWithType>提供由組合引擎內部使用的 MEF 類型。</span><span class="sxs-lookup"><span data-stu-id="399e6-110"><xref:System.Composition.Hosting.Core?displayProperty=nameWithType> provides MEF types used internally by the composition engine.</span></span>  
  
 <span data-ttu-id="399e6-111">如需有關[!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]和命名空間和它所包含的類型的清單請參閱[適用於 Windows 市集應用程式的概觀](http://go.microsoft.com/fwlink/p/?LinkID=238312)Windows 開發人員中心。</span><span class="sxs-lookup"><span data-stu-id="399e6-111">For more information about [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] and a list of namespaces and types that it contains, see [.NET for Windows Store apps overview](http://go.microsoft.com/fwlink/p/?LinkID=238312) in the Windows Dev Center.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="399e6-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="399e6-112">See Also</span></span>  
 [<span data-ttu-id="399e6-113">適用於 Windows 市集應用程式的概觀</span><span class="sxs-lookup"><span data-stu-id="399e6-113">.NET for Windows Store apps overview</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=238312)  
 [<span data-ttu-id="399e6-114">適用於 Windows 市集應用程式的 .NET - 所支援的應用程式開發介面</span><span class="sxs-lookup"><span data-stu-id="399e6-114">.NET for Windows Store apps – supported APIs</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=247912)  
 [<span data-ttu-id="399e6-115">Managed Extensibility Framework (MEF)</span><span class="sxs-lookup"><span data-stu-id="399e6-115">Managed Extensibility Framework (MEF)</span></span>](../../../docs/framework/mef/index.md)
