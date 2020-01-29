---
title: 更安全的列印
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- PrintingPermission class [Windows Forms], Windows Forms security
- printing [Windows Forms], security
- security [Windows Forms], printing
ms.assetid: 48fd36ac-872f-4de0-902a-e52969cd4367
ms.openlocfilehash: 6285b76d01660bfa761ea606421f264bdc0c0af5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734888"
---
# <a name="more-secure-printing-in-windows-forms"></a><span data-ttu-id="1cb2a-102">Windows Form 中更安全的列印</span><span class="sxs-lookup"><span data-stu-id="1cb2a-102">More Secure Printing in Windows Forms</span></span>
<span data-ttu-id="1cb2a-103">Windows Forms 的應用程式經常會包含列印能力。</span><span class="sxs-lookup"><span data-stu-id="1cb2a-103">Windows Forms applications frequently include printing abilities.</span></span> <span data-ttu-id="1cb2a-104">.NET Framework 使用 <xref:System.Drawing.Printing.PrintingPermission> 類別來控制列印功能的存取權，以及相關聯的 <xref:System.Drawing.Printing.PrintingPermissionLevel> 列舉值，以指出存取層級。</span><span class="sxs-lookup"><span data-stu-id="1cb2a-104">The .NET Framework uses the <xref:System.Drawing.Printing.PrintingPermission> class to control access to printing capabilities and the associated <xref:System.Drawing.Printing.PrintingPermissionLevel> enumeration value to indicate the level of access.</span></span> <span data-ttu-id="1cb2a-105">根據預設，預設會在近端內部網路和網際網路區域中啟用列印;不過，這兩個區域中的存取層級會受到限制。</span><span class="sxs-lookup"><span data-stu-id="1cb2a-105">By default, printing is enabled by default in the Local Intranet and Internet zones; however, the level of access is restricted in both zones.</span></span> <span data-ttu-id="1cb2a-106">您的應用程式可以列印、需要使用者互動，還是無法列印，取決於授與應用程式的許可權值。</span><span class="sxs-lookup"><span data-stu-id="1cb2a-106">Whether your application can print, requires user interaction, or cannot print depends upon the permission value granted to the application.</span></span> <span data-ttu-id="1cb2a-107">根據預設，近端內部網路區域會收到 <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> 存取權，而內部網路區域會收到 <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> 存取權。</span><span class="sxs-lookup"><span data-stu-id="1cb2a-107">By default, the Local Intranet zone receives <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> access and the Intranet zone receives <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> access.</span></span>  
  
 <span data-ttu-id="1cb2a-108">下表顯示每個列印許可權層級可用的功能。</span><span class="sxs-lookup"><span data-stu-id="1cb2a-108">The following table shows the functionality available at each printing permission level.</span></span>  
  
|<span data-ttu-id="1cb2a-109">介於</span><span class="sxs-lookup"><span data-stu-id="1cb2a-109">PrintingPermissionLevel</span></span>|<span data-ttu-id="1cb2a-110">描述</span><span class="sxs-lookup"><span data-stu-id="1cb2a-110">Description</span></span>|  
|-----------------------------|-----------------|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>|<span data-ttu-id="1cb2a-111">提供所有已安裝印表機的完整存取權。</span><span class="sxs-lookup"><span data-stu-id="1cb2a-111">Provides full access to all installed printers.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>|<span data-ttu-id="1cb2a-112">可讓您以程式設計方式列印到預設印表機，並透過 [限制列印] 對話方塊，更安全地列印。</span><span class="sxs-lookup"><span data-stu-id="1cb2a-112">Enables programmatic printing to the default printer and safer printing through a restrictive printing dialog box.</span></span> <span data-ttu-id="1cb2a-113"><xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> 是 <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting> 的子集。</span><span class="sxs-lookup"><span data-stu-id="1cb2a-113"><xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>|<span data-ttu-id="1cb2a-114">只會從更受限制的對話方塊中提供列印。</span><span class="sxs-lookup"><span data-stu-id="1cb2a-114">Provides printing only from a more-restricted dialog box.</span></span> <span data-ttu-id="1cb2a-115"><xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> 是 <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> 的子集。</span><span class="sxs-lookup"><span data-stu-id="1cb2a-115"><xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>|<span data-ttu-id="1cb2a-116">防止存取印表機。</span><span class="sxs-lookup"><span data-stu-id="1cb2a-116">Prevents access to printers.</span></span> <span data-ttu-id="1cb2a-117"><xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> 是 <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> 的子集。</span><span class="sxs-lookup"><span data-stu-id="1cb2a-117"><xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1cb2a-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="1cb2a-118">See also</span></span>

- [<span data-ttu-id="1cb2a-119">Windows Forms 中更安全的檔案和資料存取</span><span class="sxs-lookup"><span data-stu-id="1cb2a-119">More Secure File and Data Access in Windows Forms</span></span>](more-secure-file-and-data-access-in-windows-forms.md)
- [<span data-ttu-id="1cb2a-120">Windows Forms 中的其他安全性考量</span><span class="sxs-lookup"><span data-stu-id="1cb2a-120">Additional Security Considerations in Windows Forms</span></span>](additional-security-considerations-in-windows-forms.md)
- [<span data-ttu-id="1cb2a-121">Windows Forms 中的安全性概觀</span><span class="sxs-lookup"><span data-stu-id="1cb2a-121">Security in Windows Forms Overview</span></span>](security-in-windows-forms-overview.md)
- [<span data-ttu-id="1cb2a-122">Windows Forms 安全性</span><span class="sxs-lookup"><span data-stu-id="1cb2a-122">Windows Forms Security</span></span>](windows-forms-security.md)
