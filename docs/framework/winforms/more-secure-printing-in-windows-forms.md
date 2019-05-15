---
title: Windows Form 中更安全的列印
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- PrintingPermission class [Windows Forms], Windows Forms security
- printing [Windows Forms], security
- security [Windows Forms], printing
ms.assetid: 48fd36ac-872f-4de0-902a-e52969cd4367
ms.openlocfilehash: b0387a82f142fb32912dad1370d6ac0c784e8894
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592649"
---
# <a name="more-secure-printing-in-windows-forms"></a><span data-ttu-id="897f5-102">Windows Form 中更安全的列印</span><span class="sxs-lookup"><span data-stu-id="897f5-102">More Secure Printing in Windows Forms</span></span>
<span data-ttu-id="897f5-103">Windows Forms 應用程式通常會包括列印功能。</span><span class="sxs-lookup"><span data-stu-id="897f5-103">Windows Forms applications frequently include printing abilities.</span></span> <span data-ttu-id="897f5-104">.NET Framework 會使用<xref:System.Drawing.Printing.PrintingPermission>類別來控制列印功能的存取和相關聯<xref:System.Drawing.Printing.PrintingPermissionLevel>列舉值，指出存取層級。</span><span class="sxs-lookup"><span data-stu-id="897f5-104">The .NET Framework uses the <xref:System.Drawing.Printing.PrintingPermission> class to control access to printing capabilities and the associated <xref:System.Drawing.Printing.PrintingPermissionLevel> enumeration value to indicate the level of access.</span></span> <span data-ttu-id="897f5-105">根據預設，近端內部網路和網際網路區域; 中預設啟用列印不過，存取層級受限於這兩個區域中。</span><span class="sxs-lookup"><span data-stu-id="897f5-105">By default, printing is enabled by default in the Local Intranet and Internet zones; however, the level of access is restricted in both zones.</span></span> <span data-ttu-id="897f5-106">是否可以列印您的應用程式，需要使用者互動，或無法列印值而定的權限授與應用程式。</span><span class="sxs-lookup"><span data-stu-id="897f5-106">Whether your application can print, requires user interaction, or cannot print depends upon the permission value granted to the application.</span></span> <span data-ttu-id="897f5-107">根據預設，近端內部網路區域會收到<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>存取，而且內部網路區域會收到<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>存取。</span><span class="sxs-lookup"><span data-stu-id="897f5-107">By default, the Local Intranet zone receives <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> access and the Intranet zone receives <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> access.</span></span>  
  
 <span data-ttu-id="897f5-108">下表顯示每個列印的權限層級所提供的功能。</span><span class="sxs-lookup"><span data-stu-id="897f5-108">The following table shows the functionality available at each printing permission level.</span></span>  
  
|<span data-ttu-id="897f5-109">PrintingPermissionLevel</span><span class="sxs-lookup"><span data-stu-id="897f5-109">PrintingPermissionLevel</span></span>|<span data-ttu-id="897f5-110">描述</span><span class="sxs-lookup"><span data-stu-id="897f5-110">Description</span></span>|  
|-----------------------------|-----------------|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>|<span data-ttu-id="897f5-111">提供所有已安裝印表機的完整存取。</span><span class="sxs-lookup"><span data-stu-id="897f5-111">Provides full access to all installed printers.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>|<span data-ttu-id="897f5-112">啟用以程式設計方式列印至預設印表機和更安全的列印功能，透過嚴格的列印對話方塊。</span><span class="sxs-lookup"><span data-stu-id="897f5-112">Enables programmatic printing to the default printer and safer printing through a restrictive printing dialog box.</span></span> <span data-ttu-id="897f5-113"><xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> 是 <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting> 的子集。</span><span class="sxs-lookup"><span data-stu-id="897f5-113"><xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>|<span data-ttu-id="897f5-114">提供列印只能從限制更嚴格的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="897f5-114">Provides printing only from a more-restricted dialog box.</span></span> <span data-ttu-id="897f5-115"><xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> 是 <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> 的子集。</span><span class="sxs-lookup"><span data-stu-id="897f5-115"><xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>|<span data-ttu-id="897f5-116">無法存取印表機。</span><span class="sxs-lookup"><span data-stu-id="897f5-116">Prevents access to printers.</span></span> <span data-ttu-id="897f5-117"><xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> 是 <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> 的子集。</span><span class="sxs-lookup"><span data-stu-id="897f5-117"><xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="897f5-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="897f5-118">See also</span></span>

- [<span data-ttu-id="897f5-119">Windows Forms 中更安全的檔案和資料存取</span><span class="sxs-lookup"><span data-stu-id="897f5-119">More Secure File and Data Access in Windows Forms</span></span>](more-secure-file-and-data-access-in-windows-forms.md)
- [<span data-ttu-id="897f5-120">Windows Forms 中的其他安全性考量</span><span class="sxs-lookup"><span data-stu-id="897f5-120">Additional Security Considerations in Windows Forms</span></span>](additional-security-considerations-in-windows-forms.md)
- [<span data-ttu-id="897f5-121">Windows Forms 中的安全性概觀</span><span class="sxs-lookup"><span data-stu-id="897f5-121">Security in Windows Forms Overview</span></span>](security-in-windows-forms-overview.md)
- [<span data-ttu-id="897f5-122">Windows Forms 安全性</span><span class="sxs-lookup"><span data-stu-id="897f5-122">Windows Forms Security</span></span>](windows-forms-security.md)
