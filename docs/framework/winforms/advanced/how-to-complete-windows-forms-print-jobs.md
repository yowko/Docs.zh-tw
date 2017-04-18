---
title: "如何：完成 Windows Form 列印工作 | Microsoft Docs"
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
  - "列印工作, 在 Windows Form 中完成"
  - "列印 [Windows Form], 列印工作"
ms.assetid: 23ec74f7-34c5-4710-82a0-ee2914518548
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 23
---
# 如何：完成 Windows Form 列印工作
通常，會涉及列印作業的文書處理器和其他應用程式都會提供顯示訊息的選項，以告訴使用者列印工作已經完成。  您可以經由處理 <xref:System.Drawing.Printing.PrintDocument> 元件的 <xref:System.Drawing.Printing.PrintDocument.EndPrint> 事件，在 Windows Form 中提供這項功能。  
  
 下列程序需要您準備一個含有 <xref:System.Drawing.Printing.PrintDocument> 元件的 Windows 架構應用程式，這個元件是從 Windows 架構應用程式中啟用列印作業的標準方法。  如需使用 <xref:System.Drawing.Printing.PrintDocument> 元件從 Windows Form 中進行列印的詳細資訊，請參閱 [如何：建立標準的 Windows Form 列印工作](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)。  
  
### 若要完成列印工作  
  
1.  設定 <xref:System.Drawing.Printing.PrintDocument> 元件的 <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> 屬性。  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2.  撰寫用來處理 <xref:System.Drawing.Printing.PrintDocument.EndPrint> 事件的程式碼。  
  
     下列程式碼範例會顯示訊息方塊，以表示文件已印列完成。  
  
    ```vb  
    Private Sub PrintDocument1_EndPrint(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintEventArgs) Handles PrintDocument1.EndPrint  
       MessageBox.Show(PrintDocument1.DocumentName + " has finished printing.")  
    End Sub  
  
    ```  
  
    ```csharp  
    private void printDocument1_EndPrint(object sender,   
    System.Drawing.Printing.PrintEventArgs e)  
    {  
       MessageBox.Show(printDocument1.DocumentName +   
          " has finished printing.");  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_EndPrint(System::Object ^ sender,  
          System::Drawing::Printing::PrintEventArgs ^ e)  
       {  
          MessageBox::Show(String::Concat(printDocument1->DocumentName,  
             " has finished printing."));  
       }  
    ```  
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 和 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) 將下列程式碼加入表單的建構函式以註冊事件處理常式。  
  
    ```csharp  
    this.printDocument1.EndPrint += new  
       System.Drawing.Printing.PrintEventHandler  
       (this.printDocument1_EndPrint);  
  
    ```  
  
    ```cpp  
    this->printDocument1->EndPrint += gcnew  
       System::Drawing::Printing::PrintEventHandler  
       (this, &Form1::printDocument1_EndPrint);  
    ```  
  
## 請參閱  
 <xref:System.Drawing.Printing.PrintDocument>   
 [Windows Form 列印支援](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)