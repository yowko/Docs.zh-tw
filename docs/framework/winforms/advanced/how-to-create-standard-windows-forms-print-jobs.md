---
title: "如何：建立標準的 Windows Form 列印工作 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "列印 [Visual Basic], 在 Windows 應用程式中"
  - "列印 [Windows Form]"
  - "列印 [Windows Form], 建立列印工作"
ms.assetid: 03342b90-9cfe-40b2-838b-b479a13c5dea
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 如何：建立標準的 Windows Form 列印工作
Windows Form 中的列印基礎是 <xref:System.Drawing.Printing.PrintDocument> 元件，特別是 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件。  藉由撰寫處理 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件的程式碼，您可指定列印項目和如何列印。  
  
### 若要建立列印工作  
  
1.  將 <xref:System.Drawing.Printing.PrintDocument> 元件加入至表單。  
  
2.  撰寫用來處理 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件的程式碼。  
  
     您必須編寫自己的列印邏輯。  此外，您必須指定所要列印的材料。  
  
     在下列程式碼範例中，會在 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件處理常式中建立一個紅色矩形的樣本圖形，以做為要列印的材料。  
  
    ```vb  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillRectangle(Brushes.Red, New Rectangle(500, 500, 500, 500))  
    End Sub  
  
    ```  
  
    ```csharp  
    private void printDocument1_PrintPage(object sender,   
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Red,   
         new Rectangle(500, 500, 500, 500));  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Red,  
             Rectangle(500, 500, 500, 500));  
       }  
    ```  
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 和 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) 將下列程式碼加入表單的建構函式以註冊事件處理常式。  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
  
    ```  
  
    ```cpp  
    printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    ```  
  
     您可能還需要撰寫 <xref:System.Drawing.Printing.PrintDocument.BeginPrint> 和 <xref:System.Drawing.Printing.PrintDocument.EndPrint> 事件的程式碼，或許還包括代表總列印頁數的整數 \(會在每一頁列印時遞減\)。  
  
    > [!NOTE]
    >  您可以將 <xref:System.Windows.Forms.PrintDialog> 元件加入至表單，為使用者提供清楚且高效率的使用者介面 \(UI\)。  藉由設定 <xref:System.Windows.Forms.PrintDialog> 元件的 <xref:System.Windows.Forms.PrintDialog.Document%2A> 屬性，可讓您設定與表單上正在使用的列印文件有關的屬性。  如需 <xref:System.Windows.Forms.PrintDialog> 元件的詳細資訊，請參閱 [PrintDialog 元件](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)。  
  
     如需 Windows Form 列印工作細節 \(包括如何以程式設計的方式來建立列印工作\) 的詳細資訊，請參閱 <xref:System.Drawing.Printing.PrintPageEventArgs>。  
  
## 請參閱  
 <xref:System.Drawing.Printing.PrintDocument>   
 [Windows Form 列印支援](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)