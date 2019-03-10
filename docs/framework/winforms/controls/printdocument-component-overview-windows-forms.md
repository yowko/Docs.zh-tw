---
title: PrintDocument 元件概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: c35c60b651dd3becfeca0f07788efab9d1619117
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715859"
---
# <a name="printdocument-component-overview-windows-forms"></a>PrintDocument 元件概觀 (Windows Form)
Windows Forms [PrintDocument](printdocument-component-windows-forms.md) 元件可用來設定描述列印項目的屬性，以及在 Windows 應用程式中列印文件的能力。 它可以與 [PrintDialog](printdialog-component-windows-forms.md) 元件一起使用，以控制文件列印的各個方面。  
  
## <a name="working-with-the-printdocument-component"></a>使用 PrintDocument 元件  
 兩個主要案例牽涉到<xref:System.Drawing.Printing.PrintDocument>元件：  
  
-   簡單列印工作，例如列印個別的文字檔。 在此情況下，您可以加入<xref:System.Drawing.Printing.PrintDocument>元件至 Windows 表單，然後新增會列印的檔案中的程式設計邏輯<xref:System.Drawing.Printing.PrintDocument.PrintPage>事件處理常式。 程式設計邏輯應做為目標<xref:System.Drawing.Printing.PrintDocument.Print%2A>列印文件的方法。 這個方法會傳送<xref:System.Drawing.Graphics>中所含的物件<xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A>屬性<xref:System.Drawing.Printing.PrintPageEventArgs>到印表機的類別。 如需範例，示範如何使用文字文件列印<xref:System.Drawing.Printing.PrintDocument>元件，請參閱[How to:列印 Windows Form 中的多頁文字檔](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)。  
  
-   更複雜的列印工作，例如，您想要重複使用您所撰寫之列印邏輯的情況。 這種情況中，您會衍生新的元件，從<xref:System.Drawing.Printing.PrintDocument>元件，並覆寫 (請參閱 <<c2> [ 覆寫](~/docs/visual-basic/language-reference/modifiers/overrides.md)適用於 Visual Basic 或[覆寫](~/docs/csharp/language-reference/keywords/override.md)的C#)<xref:System.Drawing.Printing.PrintDocument.PrintPage>事件。</c2>  
  
 當加入至表單，<xref:System.Drawing.Printing.PrintDocument>元件會出現在底部的 Windows Form 設計工具的紙匣。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Printing.PrintDocument>
- [Windows Forms 列印支援](../advanced/windows-forms-print-support.md)
- [PrintDocument 元件](printdocument-component-windows-forms.md)
