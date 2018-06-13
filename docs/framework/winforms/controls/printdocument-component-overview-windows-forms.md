---
title: PrintDocument 元件概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: b02133321624d27b9c1e8faae9cac1b4fe8f76c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538261"
---
# <a name="printdocument-component-overview-windows-forms"></a>PrintDocument 元件概觀 (Windows Form)
Windows Forms [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) 元件可用來設定描述列印項目的屬性，以及在 Windows 應用程式中列印文件的能力。 它可以與 [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) 元件一起使用，以控制文件列印的各個方面。  
  
## <a name="working-with-the-printdocument-component"></a>使用 PrintDocument 元件  
 兩個有關的主要案例<xref:System.Drawing.Printing.PrintDocument>元件是：  
  
-   簡單列印工作，例如列印個別的文字檔。 在此情況下您會將<xref:System.Drawing.Printing.PrintDocument>元件至 Windows 表單，然後新增列印的檔案中的程式設計邏輯<xref:System.Drawing.Printing.PrintDocument.PrintPage>事件處理常式。 與應該做為目標的程式設計邏輯<xref:System.Drawing.Printing.PrintDocument.Print%2A>列印文件的方法。 這個方法會傳送<xref:System.Drawing.Graphics>中包含的物件<xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A>屬性<xref:System.Drawing.Printing.PrintPageEventArgs>類別，以印表機。 如需範例，示範如何使用文字文件列印<xref:System.Drawing.Printing.PrintDocument>元件，請參閱[如何： 列印 Windows Form 中的多頁文字檔](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)。  
  
-   更複雜的列印工作，例如，您想要重複使用您所撰寫之列印邏輯的情況。 在這種情況下，您會衍生新的元件，從<xref:System.Drawing.Printing.PrintDocument>元件，然後覆寫 (請參閱[會覆寫](~/docs/visual-basic/language-reference/modifiers/overrides.md)適用於 Visual Basic 或[覆寫](~/docs/csharp/language-reference/keywords/override.md)C#)<xref:System.Drawing.Printing.PrintDocument.PrintPage>事件。  
  
 當加入至表單，<xref:System.Drawing.Printing.PrintDocument>元件會出現在 Windows Form 設計工具底部的紙匣。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Drawing.Graphics>  
 <xref:System.Drawing.Printing.PrintDocument>  
 [Windows Forms 列印支援](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [PrintDocument 元件](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)
