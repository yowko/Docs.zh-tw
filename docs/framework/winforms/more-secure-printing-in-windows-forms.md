---
title: "Windows Form 中更安全的列印"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, printing
- PrintingPermission class [Windows Forms], Windows Forms security
- printing [Windows Forms], security
- security [Windows Forms], printing
ms.assetid: 48fd36ac-872f-4de0-902a-e52969cd4367
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b89a94fd0223d817b0dee37f7a3ed84dcbacbbec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="more-secure-printing-in-windows-forms"></a>Windows Form 中更安全的列印
Windows Form 應用程式經常會包括列印的能力。 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]使用<xref:System.Drawing.Printing.PrintingPermission>類別來控制存取列印功能，並關聯<xref:System.Drawing.Printing.PrintingPermissionLevel>列舉值，指出的存取層級。 根據預設，預設會在 近端內部網路和網際網路區域; 啟用列印不過，這兩個區域中限制的存取層級。 是否可以列印您的應用程式，需要使用者互動，或無法列印取決於應用程式授與的權限值。 根據預設，近端內部網路區域會接收<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>存取和內部網路區域接收<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>存取。  
  
 下表顯示每個列印權限層級中可用的功能。  
  
|PrintingPermissionLevel|說明|  
|-----------------------------|-----------------|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>|提供完整存取所有已安裝的印表機。|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>|啟用以程式設計方式列印到預設印表機和更安全的列印功能透過限制列印對話方塊。 <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> 是 <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting> 的子集。|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>|提供列印只能從限制更嚴格的對話方塊。 <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> 是 <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> 的子集。|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>|無法存取印表機。 <xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> 是 <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> 的子集。|  
  
## <a name="see-also"></a>另請參閱  
 [Windows Forms 中更安全的檔案和資料存取](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 [Windows Forms 中的其他安全性考量](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 [Windows Forms 中的安全性概觀](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 [Windows Forms 安全性](../../../docs/framework/winforms/windows-forms-security.md)
