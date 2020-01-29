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
# <a name="more-secure-printing-in-windows-forms"></a>Windows Form 中更安全的列印
Windows Forms 的應用程式經常會包含列印能力。 .NET Framework 使用 <xref:System.Drawing.Printing.PrintingPermission> 類別來控制列印功能的存取權，以及相關聯的 <xref:System.Drawing.Printing.PrintingPermissionLevel> 列舉值，以指出存取層級。 根據預設，預設會在近端內部網路和網際網路區域中啟用列印;不過，這兩個區域中的存取層級會受到限制。 您的應用程式可以列印、需要使用者互動，還是無法列印，取決於授與應用程式的許可權值。 根據預設，近端內部網路區域會收到 <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> 存取權，而內部網路區域會收到 <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> 存取權。  
  
 下表顯示每個列印許可權層級可用的功能。  
  
|介於|描述|  
|-----------------------------|-----------------|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>|提供所有已安裝印表機的完整存取權。|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>|可讓您以程式設計方式列印到預設印表機，並透過 [限制列印] 對話方塊，更安全地列印。 <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> 是 <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting> 的子集。|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>|只會從更受限制的對話方塊中提供列印。 <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> 是 <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> 的子集。|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>|防止存取印表機。 <xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> 是 <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> 的子集。|  
  
## <a name="see-also"></a>請參閱

- [Windows Forms 中更安全的檔案和資料存取](more-secure-file-and-data-access-in-windows-forms.md)
- [Windows Forms 中的其他安全性考量](additional-security-considerations-in-windows-forms.md)
- [Windows Forms 中的安全性概觀](security-in-windows-forms-overview.md)
- [Windows Forms 安全性](windows-forms-security.md)
