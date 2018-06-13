---
title: 如何：列印表單的工作區 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- client area [Visual Basic], printing
ms.assetid: c06c9c0e-bc07-48cd-9596-e29a2ff96236
ms.openlocfilehash: 361db89f0880a03273aac7fc36b5c5faa825486f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583987"
---
# <a name="how-to-print-the-client-area-of-a-form-visual-basic"></a>如何：列印表單的工作區 (Visual Basic)
<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件可讓您快速列印表單的影像，而不需要使用 <xref:System.Drawing.Printing.PrintDocument> 元件。 下列程序示範如何只列印表單的工作區，而不列印標題列、框線和捲軸。  
  
 Visual Studio 中已不再包含 PowerPack 控制項，但您可以從 [下載中心](http://www.microsoft.com/en-us/download/details.aspx?id=25169)下載這些控制項。  
  
### <a name="to-print-the-client-area-of-a-form"></a>列印表單的工作區  
  
1.  在 [工具箱] 中，按一下 [Visual Basic PowerPacks]  索引標籤，然後將 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件拖曳至表單上。  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件會加入元件匣中。  
  
2.  在 [屬性]  視窗中，將 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> 屬性設定為 <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>。  
  
3.  在適當的事件處理常式 (例如 [列印] `Click`**的**`Button`事件處理常式) 中加入下列程式碼。  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.ClientAreaOnly)  
    ```  
  
    > [!NOTE]
    >  在某些作業系統上，可能無法正確列印由 <xref:System.Drawing.Graphics> 方法所繪製的文字或圖形。 在這種情況下，請使用相容的列印方法： `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption CompatibleModeClientAreaOnly).`  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [PrintForm 元件](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [操作說明：列印表單的工作區和非工作區](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)  
 [操作說明：列印可捲動的表單](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
