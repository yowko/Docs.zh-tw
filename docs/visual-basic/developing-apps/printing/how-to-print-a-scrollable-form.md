---
title: "如何：列印可捲動的表單 (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "整個表單, 列印"
  - "可捲動的表單, 列印"
ms.assetid: 1196e1cf-b77f-4928-a3e4-85b51ba3787d
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# 如何：列印可捲動的表單 (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件可讓您快速列印表單的影像，而不需要使用 <xref:System.Drawing.Printing.PrintDocument> 元件。 根據預設，只會列印表單的目前可見部分；如果使用者已在執行階段調整表單的大小，影像可能無法如預期般列印。 下列程序示範如何列印可捲動表單的完整工作區，而不論表單是否已調整大小。  
  
 Visual Studio 中已不再包含 PowerPack 控制項，但您可以從[下載中心](http://www.microsoft.com/en-us/download/details.aspx?id=25169)下載這些控制項。  
  
### 列印可捲動表單的完整工作區  
  
1.  在 \[工具箱\] 中，按一下 \[Visual Basic PowerPacks\] 索引標籤，然後將 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件拖曳至表單上。  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件會加入元件匣中。  
  
2.  在 \[屬性\] 視窗中，將 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> 屬性設定為 <xref:System.Drawing.Printing.PrintAction>。  
  
3.  在適當的事件處理常式 \(例如 \[列印\]`Button` 的 `Click` 事件處理常式\) 中加入下列程式碼。  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.Scrollable)  
    ```  
  
    > [!NOTE]
    >  在某些作業系統上，可能無法正確列印由 <xref:System.Drawing.Graphics> 方法所繪製的文字或圖形。 在這種情況下，您將無法使用 `Scrollable` 參數進行列印。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>   
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>   
 [PrintForm Component](../../../visual-basic/developing-apps/printing/printform-component.md)   
 [如何：列印表單的工作區](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)   
 [如何：列印表單的工作區和非工作區](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)