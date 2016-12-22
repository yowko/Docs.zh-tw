---
title: "如何：使用 PrintForm 元件列印表單 (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "表單, 列印"
ms.assetid: df963bf6-3ee1-49f4-8b2e-1d95d1beb0be
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 如何：使用 PrintForm 元件列印表單 (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件可讓您完全依照螢幕所示，快速列印表單的影像，而不需要使用 <xref:System.Drawing.Printing.PrintDocument> 元件。 下列程序示範如何將表單列印至印表機、\[預覽列印\] 視窗及封裝式 PostScript 檔案。  
  
 Visual Studio 中已不再包含 PowerPack 控制項，但您可以從[下載中心](http://www.microsoft.com/en-us/download/details.aspx?id=25169)下載這些控制項。  
  
### 將表單列印至預設印表機  
  
1.  在 \[工具箱\] 中，按一下 \[Visual Basic PowerPacks\] 索引標籤，然後將 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件拖曳至表單上。  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件會加入元件匣中。  
  
2.  在 \[屬性\] 視窗中，將 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> 屬性設定為 <xref:System.Drawing.Printing.PrintAction>。  
  
3.  在適當的事件處理常式 \(例如 **Print**`Button` 的 `Click` 事件處理常式\) 中加入下列程式碼。  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### 在 \[預覽列印\] 視窗中顯示表單  
  
1.  在 \[工具箱\] 中，按一下 \[Visual Basic PowerPacks\] 索引標籤，然後將 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件拖曳至表單上。  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件會加入元件匣中。  
  
2.  在 \[屬性\] 視窗中，將 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> 屬性設定為 <xref:System.Drawing.Printing.PrintAction>。  
  
3.  在適當的事件處理常式 \(例如 **Print**`Button` 的 `Click` 事件處理常式\) 中加入下列程式碼。  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### 將表單列印至檔案  
  
1.  在 \[工具箱\] 中，按一下 \[Visual Basic PowerPacks\] 索引標籤，然後將 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件拖曳至表單上。  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件會加入元件匣中。  
  
2.  在 \[屬性\] 視窗中，將 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> 屬性設定為 <xref:System.Drawing.Printing.PrintAction>。  
  
3.  \(選擇性\) 選取 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> 屬性，然後輸入目的檔案的完整路徑和檔案名稱。  
  
     如果您略過這個步驟，系統會在執行階段提示使用者輸入檔案名稱。  
  
4.  在適當的事件處理常式 \(例如 **Print**`Button` 的 `Click` 事件處理常式\) 中加入下列程式碼。  
  
    ```  
    PrintForm1.Print()  
    ```  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>   
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A>   
 [如何：列印表單的工作區](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)   
 [如何：列印表單的工作區和非工作區](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)   
 [如何：列印可捲動的表單](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)   
 [PrintForm Component](../../../visual-basic/developing-apps/printing/printform-component.md)