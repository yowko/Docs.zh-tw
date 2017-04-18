---
title: "Windows Form 中更安全的列印 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "列印 [Windows Form], 安全性"
  - "PrintingPermission 類別, Windows Form 安全性"
  - "安全性 [Windows Form], 列印"
  - "Windows Form, 列印"
ms.assetid: 48fd36ac-872f-4de0-902a-e52969cd4367
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Windows Form 中更安全的列印
Windows Form 應用程式通常都會包含列印功能。  [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 會使用 <xref:System.Drawing.Printing.PrintingPermission> 類別來控制對列印功能的存取，並使用相關的 <xref:System.Drawing.Printing.PrintingPermissionLevel> 列舉值來指示存取層級。  根據預設，近端內部網路區域和網際網路區域中的列印功能已啟用，但是這兩個區域的存取層級都會受到限制。  至於應用程式究竟為可列印、需要使用者互動或無法列印，則需根據應用程式所取得的使用權限值而定。  根據預設，近端內部網路區域會取得 <xref:System.Drawing.Printing.PrintingPermissionLevel> 存取權限，而內部網路區域則會取得 <xref:System.Drawing.Printing.PrintingPermissionLevel> 存取權限。  
  
 下表說明每個列印使用權限等級可以使用的功能：  
  
|PrintingPermissionLevel|描述|  
|-----------------------------|--------|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel>|對所有安裝的印表機提供完整的存取權。|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel>|以程式設計方式啟用預設印表機的列印功能，並且透過限制列印的對話方塊提供更安全的列印。  <xref:System.Drawing.Printing.PrintingPermissionLevel> 是 <xref:System.Drawing.Printing.PrintingPermissionLevel> 的子集。|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel>|只能透過限制更嚴格的對話方塊提供列印。  <xref:System.Drawing.Printing.PrintingPermissionLevel> 是 <xref:System.Drawing.Printing.PrintingPermissionLevel> 的子集。|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel>|防止印表機的存取。  <xref:System.Drawing.Printing.PrintingPermissionLevel> 是 <xref:System.Drawing.Printing.PrintingPermissionLevel> 的子集。|  
  
## 請參閱  
 [Windows Form 中更安全的檔案和資料存取](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)   
 [Windows Form 中的其他安全性考量](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)   
 [Windows Form 中的安全性概觀](../../../docs/framework/winforms/security-in-windows-forms-overview.md)   
 [Windows Form 安全性](../../../docs/framework/winforms/windows-forms-security.md)