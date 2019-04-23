---
title: Windows Form 中更安全的列印
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- PrintingPermission class [Windows Forms], Windows Forms security
- printing [Windows Forms], security
- security [Windows Forms], printing
ms.assetid: 48fd36ac-872f-4de0-902a-e52969cd4367
ms.openlocfilehash: 5ee170980ed02d90606c774e2a7055f047292e33
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197356"
---
# <a name="more-secure-printing-in-windows-forms"></a>Windows Form 中更安全的列印
Windows Forms 應用程式通常會包括列印功能。 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]會使用<xref:System.Drawing.Printing.PrintingPermission>類別，以控制列印功能的存取和相關聯<xref:System.Drawing.Printing.PrintingPermissionLevel>列舉值，指出存取層級。 根據預設，近端內部網路和網際網路區域; 中預設啟用列印不過，存取層級受限於這兩個區域中。 是否可以列印您的應用程式，需要使用者互動，或無法列印值而定的權限授與應用程式。 根據預設，近端內部網路區域會收到<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>存取，而且內部網路區域會收到<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>存取。  
  
 下表顯示每個列印的權限層級所提供的功能。  
  
|PrintingPermissionLevel|描述|  
|-----------------------------|-----------------|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>|提供所有已安裝印表機的完整存取。|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>|啟用以程式設計方式列印至預設印表機和更安全的列印功能，透過嚴格的列印對話方塊。 <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> 是 <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting> 的子集。|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>|提供列印只能從限制更嚴格的對話方塊。 <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> 是 <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> 的子集。|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>|無法存取印表機。 <xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> 是 <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> 的子集。|  
  
## <a name="see-also"></a>另請參閱

- [Windows Forms 中更安全的檔案和資料存取](more-secure-file-and-data-access-in-windows-forms.md)
- [Windows Forms 中的其他安全性考量](additional-security-considerations-in-windows-forms.md)
- [Windows Forms 中的安全性概觀](security-in-windows-forms-overview.md)
- [Windows Forms 安全性](windows-forms-security.md)
