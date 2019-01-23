---
title: HOW TO：顯示 PrintDialog 元件
ms.date: 03/30/2017
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], displaying
- printing [Windows Forms], displaying print dialog box
ms.assetid: 745a8db7-0526-4b21-b09d-18e13ed32014
ms.openlocfilehash: 5315dc8b47c8ca846376ac6d1da5a0bf46fd6241
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543993"
---
# <a name="how-to-display-the-printdialog-component"></a>HOW TO：顯示 PrintDialog 元件
<xref:System.Windows.Forms.PrintDialog>元件是標準 Windows 列印對話方塊，您的許多使用者不會感到陌生。 因為您的使用者可以立即熟悉它，它會有幫助您使用<xref:System.Windows.Forms.PrintDialog>元件。  
  
### <a name="to-display-the-printdialog-component"></a>顯示 PrintDialog 元件  
  
-   呼叫<xref:System.Windows.Forms.Form.ShowDialog%2A>從您的應用程式的程式碼的方法。  
  
     顯示此元件之後，使用者將會透過設定列印工作的屬性來與其互動。 這些會儲存在<!--zz <xref:System.Drawing.Printing.PrinterSetting>-->`PrinterSetting`類別 (而<xref:System.Drawing.Printing.PageSettings>類別，如果使用者存取[PageSetupDialog 元件](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)透過<xref:System.Windows.Forms.PrintDialog>元件) 與該列印工作相關聯。 您接著可以呼叫它們所設定的屬性來決定列印工作的詳細資訊。  
  
## <a name="see-also"></a>另請參閱
- [如何：建立標準的 Windows Forms 列印工作](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)
- [如何：在執行階段擷取使用者輸入從 PrintDialog](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)
- [PrintPreviewDialog 控制項](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)
- [PrintDialog 元件](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)
- [Windows Forms 列印支援](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
- [Windows Forms 控制項](../../../../docs/framework/winforms/controls/index.md)
