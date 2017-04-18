---
title: "如何：列印 Windows Form 中的圖形 | Microsoft Docs"
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
  - "圖形, 列印"
  - "列印 [Windows Form], 圖形"
ms.assetid: 32b891e6-52ff-4fea-a9ff-2ce5db20a4c6
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# 如何：列印 Windows Form 中的圖形
您會經常需要在 Windows 架構應用程式中列印圖形。  <xref:System.Drawing.Graphics> 類別提供將物件繪製至螢幕或印表機之類裝置的方法。  
  
### 若要列印圖形  
  
1.  將 <xref:System.Drawing.Printing.PrintDocument> 元件加入至表單。  
  
2.  在 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件處理常式中，使用 <xref:System.Drawing.Printing.PrintPageEventArgs> 類別的 <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> 屬性，以指示印表機所要列印的圖形類型。  
  
     下列程式碼範例示範了用來在週框 \(Bounding Rectangle\) 內建立藍色橢圓形的事件處理常式。  此週框具有下列位置和維度：從 100、150 開始算起，寬度是 250，高度也是 250。  
  
    ```vb  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillEllipse(Brushes.Blue, New Rectangle(100, 150, 250, 250))  
    End Sub  
  
    ```  
  
    ```csharp  
    private void printDocument1_PrintPage(object sender,   
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Blue,   
         new Rectangle(100, 150, 250, 250));  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Blue,  
             Rectangle(100, 150, 250, 250));  
       }  
    ```  
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 和 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) 將下列程式碼加入表單的建構函式以註冊事件處理常式。  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
  
    ```  
  
    ```cpp  
    this->printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    ```  
  
## 請參閱  
 <xref:System.Drawing.Graphics>   
 <xref:System.Drawing.Brush>   
 [Windows Form 列印支援](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)