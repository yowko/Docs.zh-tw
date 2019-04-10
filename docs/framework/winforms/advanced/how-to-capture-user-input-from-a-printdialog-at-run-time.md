---
title: HOW TO：在執行階段從 PrintDialog 擷取使用者輸入
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print options [Windows Forms], changing at run time
- printing [Windows Forms], options
- print options
- run time [Windows Forms], changing print options
ms.assetid: 438501d8-9a70-4fb3-aae6-e46579aba0c6
ms.openlocfilehash: 2aaf988f362baf9cd80eb16e4a08f7f65a5077bb
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59311418"
---
# <a name="how-to-capture-user-input-from-a-printdialog-at-run-time"></a>HOW TO：在執行階段從 PrintDialog 擷取使用者輸入
雖然您可以設定在設計階段的列印相關的選項，您有時要變更這些選項在執行階段，最有可能因為使用者所做的選擇。 您可以擷取列印文件使用的使用者輸入<xref:System.Windows.Forms.PrintDialog>而<xref:System.Drawing.Printing.PrintDocument>元件。  
  
### <a name="to-change-print-options-programmatically"></a>若要以程式設計方式變更列印選項  
  
1. 新增<xref:System.Windows.Forms.PrintDialog>和<xref:System.Drawing.Printing.PrintDocument>元件至您的表單。  
  
2. 設定<xref:System.Windows.Forms.PrintDialog.Document%2A>的屬性<xref:System.Windows.Forms.PrintDialog>到<xref:System.Drawing.Printing.PrintDocument>加入至表單。  
  
    ```vb  
    PrintDialog1.Document = PrintDocument1  
    ```  
  
    ```csharp  
    printDialog1.Document = PrintDocument1;  
    ```  
  
    ```cpp  
    printDialog1->Document = PrintDocument1;  
    ```  
  
3. 顯示<xref:System.Windows.Forms.PrintDialog>元件使用<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法。  
  
    ```vb  
    PrintDialog1.ShowDialog()  
    ```  
  
    ```csharp  
    printDialog1.ShowDialog();  
    ```  
  
    ```cpp  
    printDialog1->ShowDialog();  
    ```  
  
4. 使用者的列印選項，從對話方塊將會複製到<xref:System.Drawing.Printing.PrinterSettings>屬性<xref:System.Drawing.Printing.PrintDocument>元件。  
  
## <a name="see-also"></a>另請參閱

- [HOW TO：在 Windows Forms 中列印多頁文字檔](how-to-print-a-multi-page-text-file-in-windows-forms.md)
- [Windows Form 列印支援](windows-forms-print-support.md)
