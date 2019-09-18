---
title: 適用於 Windows 市集應用程式的 .NET 的 MEF
ms.date: 03/30/2017
ms.assetid: 7667770e-d163-4ad6-a303-085cf73db2f2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 255892e4dd3938028f488f80d8fba367590976f7
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051623"
---
# <a name="mef-for-net-for-windows-store-apps"></a><span data-ttu-id="f79a1-102">適用於 Windows 市集應用程式的 .NET 的 MEF</span><span class="sxs-lookup"><span data-stu-id="f79a1-102">MEF for .NET for Windows Store Apps</span></span>
<span data-ttu-id="f79a1-103"><xref:System.Composition?displayProperty=nameWithType> 及其子命名空間包含適用於使用 Managed Extensibility Framework (MEF) 開發可擴充 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式的類型。</span><span class="sxs-lookup"><span data-stu-id="f79a1-103"><xref:System.Composition?displayProperty=nameWithType> and its child namespaces contain types for developing extensible [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps with Managed Extensibility Framework (MEF).</span></span> <span data-ttu-id="f79a1-104">這些命名空間為 [!INCLUDE[win8](../../../includes/win8-md.md)] 作業系統 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] 子集的一部分。</span><span class="sxs-lookup"><span data-stu-id="f79a1-104">These namespaces are part of the [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] subset for the [!INCLUDE[win8](../../../includes/win8-md.md)] operating system.</span></span>  
  
 <span data-ttu-id="f79a1-105">這些命名空間不是隨 .NET Framework 所散發核心類別庫的一部分。</span><span class="sxs-lookup"><span data-stu-id="f79a1-105">These namespaces are not part of the core class library distributed with the .NET Framework.</span></span> <span data-ttu-id="f79a1-106">若要安裝這些命名空間，請在 Visual Studio 中開啟專案，從 [專案] 功能表中選擇 [管理 NuGet 套件]，然後在線上搜尋 Microsoft.Composition 套件。</span><span class="sxs-lookup"><span data-stu-id="f79a1-106">To install these namespaces, open your project in Visual Studio, choose **Manage NuGet Packages** from the **Project** menu, and search online for the Microsoft.Composition package.</span></span>  
  
- <span data-ttu-id="f79a1-107"><xref:System.Composition?displayProperty=nameWithType> 提供的類別會構成 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式的核心 MEF。</span><span class="sxs-lookup"><span data-stu-id="f79a1-107"><xref:System.Composition?displayProperty=nameWithType> provides classes that constitute the core MEF for [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span>  
  
- <span data-ttu-id="f79a1-108"><xref:System.Composition.Convention?displayProperty=nameWithType> 提供的類型可支援將 MEF 與以慣例為基礎的設定模型搭配使用。</span><span class="sxs-lookup"><span data-stu-id="f79a1-108"><xref:System.Composition.Convention?displayProperty=nameWithType> provides types that support using MEF with a convention-based configuration model.</span></span>  
  
- <span data-ttu-id="f79a1-109"><xref:System.Composition.Hosting?displayProperty=nameWithType> 提供的 MEF 類型對主應用程式的開發人員而言非常有用。</span><span class="sxs-lookup"><span data-stu-id="f79a1-109"><xref:System.Composition.Hosting?displayProperty=nameWithType> provides MEF types that are useful to developers of host applications.</span></span>  
  
- <span data-ttu-id="f79a1-110"><xref:System.Composition.Hosting.Core?displayProperty=nameWithType> 提供組合引擎內部使用的 MEF 類型。</span><span class="sxs-lookup"><span data-stu-id="f79a1-110"><xref:System.Composition.Hosting.Core?displayProperty=nameWithType> provides MEF types used internally by the composition engine.</span></span>  
  
 <span data-ttu-id="f79a1-111">如需 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] 及其所包含命名空間與類型清單的詳細資訊，請參閱 Windows 開發人員中心的[適用於 Windows 市集應用程式的 .NET 概觀](https://go.microsoft.com/fwlink/p/?LinkID=238312)。</span><span class="sxs-lookup"><span data-stu-id="f79a1-111">For more information about [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] and a list of namespaces and types that it contains, see [.NET for Windows Store apps overview](https://go.microsoft.com/fwlink/p/?LinkID=238312) in the Windows Dev Center.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f79a1-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f79a1-112">See also</span></span>

- [<span data-ttu-id="f79a1-113">適用於 Windows 市集應用程式的 .NET 概觀</span><span class="sxs-lookup"><span data-stu-id="f79a1-113">.NET for Windows Store apps overview</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=238312)
- [<span data-ttu-id="f79a1-114">適用於 Windows 市集應用程式的 .NET - 所支援的應用程式開發介面</span><span class="sxs-lookup"><span data-stu-id="f79a1-114">.NET for Windows Store apps – supported APIs</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=247912)
- [<span data-ttu-id="f79a1-115">Managed Extensibility Framework (MEF)</span><span class="sxs-lookup"><span data-stu-id="f79a1-115">Managed Extensibility Framework (MEF)</span></span>](index.md)
