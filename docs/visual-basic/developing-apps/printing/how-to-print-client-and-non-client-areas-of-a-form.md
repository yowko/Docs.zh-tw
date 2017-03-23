---
title: "如何：列印表單的工作區和非工作區 (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "標題列, 列印"
  - "列印"
  - "框線, 列印"
  - "整個表單"
  - "非工作區, 列印"
ms.assetid: 856bb0e4-dbc3-47e2-81cd-4b376cf07757
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# 如何：列印表單的工作區和非工作區 (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件可讓您完全依照螢幕所示，快速列印表單的影像，而不需要使用 <xref:System.Drawing.Printing.PrintDocument> 元件。 下列程序示範如何列印表單，包括工作區和非工作區。 非工作區包含標題列、框線和捲軸。  
  
 Visual Studio 中已不再包含 PowerPack 控制項，但您可以從[下載中心](http://www.microsoft.com/en-us/download/details.aspx?id=25169)下載這些控制項。  
  
### 列印表單的工作區和非工作區  
  
1.  在 \[工具箱\] 中，按一下 \[Visual Basic PowerPacks\] 索引標籤，然後將 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件拖曳至表單上。  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件會加入元件匣中。  
  
2.  在 \[屬性\] 視窗中，將 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> 屬性設定為 <xref:System.Drawing.Printing.PrintAction>。  
  
3.  在適當的事件處理常式 \(例如 \[列印\] `Button`的 `Click` 事件處理常式\) 中加入下列程式碼。  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.FullWindow)  
    ```  
  
    > [!NOTE]
    >  在某些作業系統上，可能無法正確列印由 <xref:System.Drawing.Graphics> 方法所繪製的文字或圖形。 在這種情況下，請使用相容的列印方法：`PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.CompatibleModeFullWindow`\)。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>   
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>   
 [PrintForm Component](../../../visual-basic/developing-apps/printing/printform-component.md)   
 [如何：列印可捲動的表單](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)