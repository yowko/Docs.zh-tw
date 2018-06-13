---
title: Windows Form 中更安全的列印
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- PrintingPermission class [Windows Forms], Windows Forms security
- printing [Windows Forms], security
- security [Windows Forms], printing
ms.assetid: 48fd36ac-872f-4de0-902a-e52969cd4367
ms.openlocfilehash: 976079f39e13186014b77e85c092c37be11238b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538935"
---
# <a name="more-secure-printing-in-windows-forms"></a><span data-ttu-id="89e94-102">Windows Form 中更安全的列印</span><span class="sxs-lookup"><span data-stu-id="89e94-102">More Secure Printing in Windows Forms</span></span>
<span data-ttu-id="89e94-103">Windows Form 應用程式經常會包括列印的能力。</span><span class="sxs-lookup"><span data-stu-id="89e94-103">Windows Forms applications frequently include printing abilities.</span></span> <span data-ttu-id="89e94-104">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]使用<xref:System.Drawing.Printing.PrintingPermission>類別來控制存取列印功能，並關聯<xref:System.Drawing.Printing.PrintingPermissionLevel>列舉值，指出的存取層級。</span><span class="sxs-lookup"><span data-stu-id="89e94-104">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] uses the <xref:System.Drawing.Printing.PrintingPermission> class to control access to printing capabilities and the associated <xref:System.Drawing.Printing.PrintingPermissionLevel> enumeration value to indicate the level of access.</span></span> <span data-ttu-id="89e94-105">根據預設，預設會在 近端內部網路和網際網路區域; 啟用列印不過，這兩個區域中限制的存取層級。</span><span class="sxs-lookup"><span data-stu-id="89e94-105">By default, printing is enabled by default in the Local Intranet and Internet zones; however, the level of access is restricted in both zones.</span></span> <span data-ttu-id="89e94-106">是否可以列印您的應用程式，需要使用者互動，或無法列印取決於應用程式授與的權限值。</span><span class="sxs-lookup"><span data-stu-id="89e94-106">Whether your application can print, requires user interaction, or cannot print depends upon the permission value granted to the application.</span></span> <span data-ttu-id="89e94-107">根據預設，近端內部網路區域會接收<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>存取和內部網路區域接收<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>存取。</span><span class="sxs-lookup"><span data-stu-id="89e94-107">By default, the Local Intranet zone receives <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> access and the Intranet zone receives <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> access.</span></span>  
  
 <span data-ttu-id="89e94-108">下表顯示每個列印權限層級中可用的功能。</span><span class="sxs-lookup"><span data-stu-id="89e94-108">The following table shows the functionality available at each printing permission level.</span></span>  
  
|<span data-ttu-id="89e94-109">PrintingPermissionLevel</span><span class="sxs-lookup"><span data-stu-id="89e94-109">PrintingPermissionLevel</span></span>|<span data-ttu-id="89e94-110">描述</span><span class="sxs-lookup"><span data-stu-id="89e94-110">Description</span></span>|  
|-----------------------------|-----------------|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>|<span data-ttu-id="89e94-111">提供完整存取所有已安裝的印表機。</span><span class="sxs-lookup"><span data-stu-id="89e94-111">Provides full access to all installed printers.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>|<span data-ttu-id="89e94-112">啟用以程式設計方式列印到預設印表機和更安全的列印功能透過限制列印對話方塊。</span><span class="sxs-lookup"><span data-stu-id="89e94-112">Enables programmatic printing to the default printer and safer printing through a restrictive printing dialog box.</span></span> <span data-ttu-id="89e94-113"><xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> 是 <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting> 的子集。</span><span class="sxs-lookup"><span data-stu-id="89e94-113"><xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>|<span data-ttu-id="89e94-114">提供列印只能從限制更嚴格的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="89e94-114">Provides printing only from a more-restricted dialog box.</span></span> <span data-ttu-id="89e94-115"><xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> 是 <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> 的子集。</span><span class="sxs-lookup"><span data-stu-id="89e94-115"><xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>|<span data-ttu-id="89e94-116">無法存取印表機。</span><span class="sxs-lookup"><span data-stu-id="89e94-116">Prevents access to printers.</span></span> <span data-ttu-id="89e94-117"><xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> 是 <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> 的子集。</span><span class="sxs-lookup"><span data-stu-id="89e94-117"><xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="89e94-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89e94-118">See Also</span></span>  
 [<span data-ttu-id="89e94-119">Windows Forms 中更安全的檔案和資料存取</span><span class="sxs-lookup"><span data-stu-id="89e94-119">More Secure File and Data Access in Windows Forms</span></span>](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 [<span data-ttu-id="89e94-120">Windows Forms 中的其他安全性考量</span><span class="sxs-lookup"><span data-stu-id="89e94-120">Additional Security Considerations in Windows Forms</span></span>](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 [<span data-ttu-id="89e94-121">Windows Forms 中的安全性概觀</span><span class="sxs-lookup"><span data-stu-id="89e94-121">Security in Windows Forms Overview</span></span>](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 [<span data-ttu-id="89e94-122">Windows Forms 安全性</span><span class="sxs-lookup"><span data-stu-id="89e94-122">Windows Forms Security</span></span>](../../../docs/framework/winforms/windows-forms-security.md)
