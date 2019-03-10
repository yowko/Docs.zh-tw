---
title: Windows Form 中更安全的列印
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- PrintingPermission class [Windows Forms], Windows Forms security
- printing [Windows Forms], security
- security [Windows Forms], printing
ms.assetid: 48fd36ac-872f-4de0-902a-e52969cd4367
ms.openlocfilehash: 2fd61ea1c56ee2dbe7ff725d9f9f79df6b6cdfd8
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723029"
---
# <a name="more-secure-printing-in-windows-forms"></a><span data-ttu-id="c2bd3-102">Windows Form 中更安全的列印</span><span class="sxs-lookup"><span data-stu-id="c2bd3-102">More Secure Printing in Windows Forms</span></span>
<span data-ttu-id="c2bd3-103">Windows Forms 應用程式通常會包括列印功能。</span><span class="sxs-lookup"><span data-stu-id="c2bd3-103">Windows Forms applications frequently include printing abilities.</span></span> <span data-ttu-id="c2bd3-104">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]會使用<xref:System.Drawing.Printing.PrintingPermission>類別，以控制列印功能的存取和相關聯<xref:System.Drawing.Printing.PrintingPermissionLevel>列舉值，指出存取層級。</span><span class="sxs-lookup"><span data-stu-id="c2bd3-104">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] uses the <xref:System.Drawing.Printing.PrintingPermission> class to control access to printing capabilities and the associated <xref:System.Drawing.Printing.PrintingPermissionLevel> enumeration value to indicate the level of access.</span></span> <span data-ttu-id="c2bd3-105">根據預設，近端內部網路和網際網路區域; 中預設啟用列印不過，存取層級受限於這兩個區域中。</span><span class="sxs-lookup"><span data-stu-id="c2bd3-105">By default, printing is enabled by default in the Local Intranet and Internet zones; however, the level of access is restricted in both zones.</span></span> <span data-ttu-id="c2bd3-106">是否可以列印您的應用程式，需要使用者互動，或無法列印值而定的權限授與應用程式。</span><span class="sxs-lookup"><span data-stu-id="c2bd3-106">Whether your application can print, requires user interaction, or cannot print depends upon the permission value granted to the application.</span></span> <span data-ttu-id="c2bd3-107">根據預設，近端內部網路區域會收到<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>存取，而且內部網路區域會收到<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>存取。</span><span class="sxs-lookup"><span data-stu-id="c2bd3-107">By default, the Local Intranet zone receives <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> access and the Intranet zone receives <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> access.</span></span>  
  
 <span data-ttu-id="c2bd3-108">下表顯示每個列印的權限層級所提供的功能。</span><span class="sxs-lookup"><span data-stu-id="c2bd3-108">The following table shows the functionality available at each printing permission level.</span></span>  
  
|<span data-ttu-id="c2bd3-109">PrintingPermissionLevel</span><span class="sxs-lookup"><span data-stu-id="c2bd3-109">PrintingPermissionLevel</span></span>|<span data-ttu-id="c2bd3-110">描述</span><span class="sxs-lookup"><span data-stu-id="c2bd3-110">Description</span></span>|  
|-----------------------------|-----------------|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>|<span data-ttu-id="c2bd3-111">提供所有已安裝印表機的完整存取。</span><span class="sxs-lookup"><span data-stu-id="c2bd3-111">Provides full access to all installed printers.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>|<span data-ttu-id="c2bd3-112">啟用以程式設計方式列印至預設印表機和更安全的列印功能，透過嚴格的列印對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c2bd3-112">Enables programmatic printing to the default printer and safer printing through a restrictive printing dialog box.</span></span> <span data-ttu-id="c2bd3-113"><xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> 是 <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting> 的子集。</span><span class="sxs-lookup"><span data-stu-id="c2bd3-113"><xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>|<span data-ttu-id="c2bd3-114">提供列印只能從限制更嚴格的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c2bd3-114">Provides printing only from a more-restricted dialog box.</span></span> <span data-ttu-id="c2bd3-115"><xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> 是 <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> 的子集。</span><span class="sxs-lookup"><span data-stu-id="c2bd3-115"><xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>|<span data-ttu-id="c2bd3-116">無法存取印表機。</span><span class="sxs-lookup"><span data-stu-id="c2bd3-116">Prevents access to printers.</span></span> <span data-ttu-id="c2bd3-117"><xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> 是 <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> 的子集。</span><span class="sxs-lookup"><span data-stu-id="c2bd3-117"><xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c2bd3-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2bd3-118">See also</span></span>
- [<span data-ttu-id="c2bd3-119">Windows Forms 中更安全的檔案和資料存取</span><span class="sxs-lookup"><span data-stu-id="c2bd3-119">More Secure File and Data Access in Windows Forms</span></span>](more-secure-file-and-data-access-in-windows-forms.md)
- [<span data-ttu-id="c2bd3-120">Windows Forms 中的其他安全性考量</span><span class="sxs-lookup"><span data-stu-id="c2bd3-120">Additional Security Considerations in Windows Forms</span></span>](additional-security-considerations-in-windows-forms.md)
- [<span data-ttu-id="c2bd3-121">Windows Forms 中的安全性概觀</span><span class="sxs-lookup"><span data-stu-id="c2bd3-121">Security in Windows Forms Overview</span></span>](security-in-windows-forms-overview.md)
- [<span data-ttu-id="c2bd3-122">Windows Forms 安全性</span><span class="sxs-lookup"><span data-stu-id="c2bd3-122">Windows Forms Security</span></span>](windows-forms-security.md)
