---
title: "如何：在執行階段從 PrintDialog 擷取使用者輸入 | Microsoft Docs"
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
  - "列印選項"
  - "列印選項, 於執行階段時變更"
  - "列印 [Windows Form], 選項"
  - "執行階段, 變更列印選項"
ms.assetid: 438501d8-9a70-4fb3-aae6-e46579aba0c6
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 如何：在執行階段從 PrintDialog 擷取使用者輸入
當您可以在設計階段設定和列印有關的選項時，有時候很可能因為使用者所做的選擇，而需要在執行階段變更這些選項。  您可以使用 <xref:System.Windows.Forms.PrintDialog> 和 <xref:System.Drawing.Printing.PrintDocument> 元件來捕捉列印文件的使用者輸入。  
  
### 若要以程式設計方式變更列印選項  
  
1.  將 <xref:System.Windows.Forms.PrintDialog> 和 <xref:System.Drawing.Printing.PrintDocument> 元件加入您的表單。  
  
2.  將 <xref:System.Windows.Forms.PrintDialog> 的 <xref:System.Windows.Forms.PrintDialog.Document%2A> 屬性設定為加入至表單的 <xref:System.Drawing.Printing.PrintDocument>。  
  
    ```vb  
    PrintDialog1.Document = PrintDocument1  
  
    ```  
  
    ```csharp  
    printDialog1.Document = PrintDocument1;  
  
    ```  
  
    ```cpp  
    printDialog1->Document = PrintDocument1;  
    ```  
  
3.  經由使用 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 方法來顯示 <xref:System.Windows.Forms.PrintDialog> 元件。  
  
    ```vb  
    PrintDialog1.ShowDialog()  
  
    ```  
  
    ```csharp  
    printDialog1.ShowDialog();  
  
    ```  
  
    ```cpp  
    printDialog1->ShowDialog();  
    ```  
  
4.  使用者在對話方塊中的列印選擇，將會複製到 <xref:System.Drawing.Printing.PrintDocument> 元件的 <xref:System.Drawing.Printing.PrinterSettings> 屬性。  
  
## 請參閱  
 [如何：在 Windows Form 中列印多頁文字檔](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)   
 [Windows Form 列印支援](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)