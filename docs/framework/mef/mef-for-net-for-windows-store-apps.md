---
title: 適用於 Windows 市集應用程式的 .NET 的 MEF
ms.date: 03/30/2017
ms.assetid: 7667770e-d163-4ad6-a303-085cf73db2f2
ms.openlocfilehash: a9c6e757cebc5dd1ad501c1cf1e2c2b666f385a1
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204698"
---
# <a name="mef-for-net-for-windows-store-apps"></a><span data-ttu-id="a1e6a-102">適用於 Windows 市集應用程式的 .NET 的 MEF</span><span class="sxs-lookup"><span data-stu-id="a1e6a-102">MEF for .NET for Windows Store Apps</span></span>
<span data-ttu-id="a1e6a-103"><xref:System.Composition?displayProperty=nameWithType> 及其子命名空間包含的類型，可讓您使用 Managed Extensibility Framework （MEF）開發可擴充的 Windows 8.x 儲存應用程式。</span><span class="sxs-lookup"><span data-stu-id="a1e6a-103"><xref:System.Composition?displayProperty=nameWithType> and its child namespaces contain types for developing extensible Windows 8.x Store apps with Managed Extensibility Framework (MEF).</span></span> <span data-ttu-id="a1e6a-104">這些命名空間為 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] 作業系統 [!INCLUDE[win8](../../../includes/win8-md.md)] 子集的一部分。</span><span class="sxs-lookup"><span data-stu-id="a1e6a-104">These namespaces are part of the [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] subset for the [!INCLUDE[win8](../../../includes/win8-md.md)] operating system.</span></span>  
  
 <span data-ttu-id="a1e6a-105">這些命名空間不是隨 .NET Framework 所散發核心類別庫的一部分。</span><span class="sxs-lookup"><span data-stu-id="a1e6a-105">These namespaces are not part of the core class library distributed with the .NET Framework.</span></span> <span data-ttu-id="a1e6a-106">若要安裝這些命名空間，請在 Visual Studio 中開啟專案，從 [專案] 功能表中選擇 [管理 NuGet 套件]，然後在線上搜尋 Microsoft.Composition 套件。</span><span class="sxs-lookup"><span data-stu-id="a1e6a-106">To install these namespaces, open your project in Visual Studio, choose **Manage NuGet Packages** from the **Project** menu, and search online for the Microsoft.Composition package.</span></span>  
  
- <span data-ttu-id="a1e6a-107"><xref:System.Composition?displayProperty=nameWithType> 提供的類別構成 Windows 8.x 存放區應用程式的核心 MEF。</span><span class="sxs-lookup"><span data-stu-id="a1e6a-107"><xref:System.Composition?displayProperty=nameWithType> provides classes that constitute the core MEF for Windows 8.x Store apps.</span></span>  
  
- <span data-ttu-id="a1e6a-108"><xref:System.Composition.Convention?displayProperty=nameWithType> 提供的類型可支援將 MEF 與以慣例為基礎的設定模型搭配使用。</span><span class="sxs-lookup"><span data-stu-id="a1e6a-108"><xref:System.Composition.Convention?displayProperty=nameWithType> provides types that support using MEF with a convention-based configuration model.</span></span>  
  
- <span data-ttu-id="a1e6a-109"><xref:System.Composition.Hosting?displayProperty=nameWithType> 提供的 MEF 類型對主應用程式的開發人員而言非常有用。</span><span class="sxs-lookup"><span data-stu-id="a1e6a-109"><xref:System.Composition.Hosting?displayProperty=nameWithType> provides MEF types that are useful to developers of host applications.</span></span>  
  
- <span data-ttu-id="a1e6a-110"><xref:System.Composition.Hosting.Core?displayProperty=nameWithType> 提供組合引擎內部使用的 MEF 類型。</span><span class="sxs-lookup"><span data-stu-id="a1e6a-110"><xref:System.Composition.Hosting.Core?displayProperty=nameWithType> provides MEF types used internally by the composition engine.</span></span>  
  
 <span data-ttu-id="a1e6a-111">如需 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] 的詳細資訊，以及它所包含的命名空間和類型清單，請參閱[適用于 Windows Store 應用程式的 .net 總覽](https://docs.microsoft.com/previous-versions/br230302(v=vs.110))。</span><span class="sxs-lookup"><span data-stu-id="a1e6a-111">For more information about [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] and a list of namespaces and types that it contains, see [.NET for Windows Store apps overview](https://docs.microsoft.com/previous-versions/br230302(v=vs.110)).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a1e6a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1e6a-112">See also</span></span>

- <span data-ttu-id="a1e6a-113">[適用於 Windows 市集應用程式的 .NET 概觀](https://docs.microsoft.com/previous-versions/br230302(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="a1e6a-113">[.NET for Windows Store apps overview](https://docs.microsoft.com/previous-versions/br230302(v=vs.110))</span></span>
- <span data-ttu-id="a1e6a-114">[適用於 Windows 市集應用程式的 .NET - 所支援的應用程式開發介面](https://docs.microsoft.com/previous-versions/br230232(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="a1e6a-114">[.NET for Windows Store apps – supported APIs](https://docs.microsoft.com/previous-versions/br230232(v=vs.110))</span></span>
- [<span data-ttu-id="a1e6a-115">Managed Extensibility Framework (MEF)</span><span class="sxs-lookup"><span data-stu-id="a1e6a-115">Managed Extensibility Framework (MEF)</span></span>](index.md)
