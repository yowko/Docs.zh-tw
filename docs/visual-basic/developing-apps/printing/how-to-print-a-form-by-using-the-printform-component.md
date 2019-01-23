---
title: HOW TO：列印表單使用 PrintForm 元件 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Form [Visual Basic], printing
ms.assetid: df963bf6-3ee1-49f4-8b2e-1d95d1beb0be
ms.openlocfilehash: 0a1a62627390c8839625862b9d43d61fc07ebf12
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521565"
---
# <a name="how-to-print-a-form-by-using-the-printform-component-visual-basic"></a>HOW TO：列印表單使用 PrintForm 元件 (Visual Basic)
<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件可讓您完全依照螢幕所示，快速列印表單的影像，而不需要使用 <xref:System.Drawing.Printing.PrintDocument> 元件。 下列程序示範如何將表單列印至印表機、[預覽列印] 視窗及封裝式 PostScript 檔案。  
  
 Visual Studio 中已不再包含 PowerPack 控制項，但您可以從 [下載中心](https://www.microsoft.com/en-us/download/details.aspx?id=25169)下載這些控制項。  
  
### <a name="to-print-a-form-to-the-default-printer"></a>將表單列印至預設印表機  
  
1.  在 [工具箱] 中，按一下 [Visual Basic PowerPacks]  索引標籤，然後將 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件拖曳至表單上。  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件會加入元件匣中。  
  
2.  在 [屬性]  視窗中，將 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> 屬性設定為 <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>。  
  
3.  在適當的事件處理常式 (例如 [列印] `Click`**的**`Button`事件處理常式) 中加入下列程式碼。  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### <a name="to-display-a-form-in-a-print-preview-window"></a>在 [預覽列印] 視窗中顯示表單  
  
1.  在 [工具箱] 中，按一下 [Visual Basic PowerPacks]  索引標籤，然後將 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件拖曳至表單上。  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件會加入元件匣中。  
  
2.  在 [屬性]  視窗中，將 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> 屬性設定為 <xref:System.Drawing.Printing.PrintAction.PrintToPreview>。  
  
3.  在適當的事件處理常式 (例如 [列印] `Click`**的**`Button`事件處理常式) 中加入下列程式碼。  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### <a name="to-print-a-form-to-a-file"></a>將表單列印至檔案  
  
1.  在 [工具箱] 中，按一下 [Visual Basic PowerPacks]  索引標籤，然後將 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件拖曳至表單上。  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件會加入元件匣中。  
  
2.  在 [屬性]  視窗中，將 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> 屬性設定為 <xref:System.Drawing.Printing.PrintAction.PrintToFile>。  
  
3.  (選擇性) 選取 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> 屬性，然後輸入目的檔案的完整路徑和檔案名稱。  
  
     如果您略過這個步驟，系統會在執行階段提示使用者輸入檔案名稱。  
  
4.  在適當的事件處理常式 (例如 [列印] `Click`**的**`Button`事件處理常式) 中加入下列程式碼。  
  
    ```  
    PrintForm1.Print()  
    ```  
  
## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>
- <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A>
- [如何：列印表單的工作區](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)
- [如何：列印表單的工作區和非工作區](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)
- [如何：列印可捲動的表單](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
- [PrintForm 元件](../../../visual-basic/developing-apps/printing/printform-component.md)
