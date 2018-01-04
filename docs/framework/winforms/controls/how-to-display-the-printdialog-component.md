---
title: "如何：顯示 PrintDialog 元件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], displaying
- printing [Windows Forms], displaying print dialog box
ms.assetid: 745a8db7-0526-4b21-b09d-18e13ed32014
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d955febe528add4b774766a3b204f96eef5a119d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-the-printdialog-component"></a>如何：顯示 PrintDialog 元件
<xref:System.Windows.Forms.PrintDialog>元件是標準 Windows 列印對話方塊，您的使用者都很熟悉。 因為您的使用者會立即熟悉，很有幫助您使用<xref:System.Windows.Forms.PrintDialog>元件。  
  
### <a name="to-display-the-printdialog-component"></a>顯示 PrintDialog 元件  
  
-   呼叫<xref:System.Windows.Forms.Form.ShowDialog%2A>從您的應用程式的程式碼中的方法。  
  
     顯示此元件之後，使用者將會透過設定列印工作的屬性來與其互動。 這些會儲存在<!--zz <xref:System.Drawing.Printing.PrinterSetting>-->`PrinterSetting`類別 (和<xref:System.Drawing.Printing.PageSettings>類別，如果使用者存取[PageSetupDialog 元件](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)透過<xref:System.Windows.Forms.PrintDialog>元件) 與該列印工作相關聯。 您接著可以呼叫它們所設定的屬性來決定列印工作的詳細資訊。  
  
## <a name="see-also"></a>請參閱  
 [操作說明：建立標準的 Windows Forms 列印工作](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 [操作說明：在執行階段從 PrintDialog 擷取使用者輸入](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 [PrintPreviewDialog 控制項](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [PrintDialog 元件](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)  
 [Windows Forms 列印支援](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [Windows Forms 控制項](../../../../docs/framework/winforms/controls/index.md)
