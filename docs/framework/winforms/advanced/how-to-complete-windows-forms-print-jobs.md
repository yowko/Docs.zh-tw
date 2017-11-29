---
title: "如何：完成 Windows Form 列印工作"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print jobs [Windows Forms], completing in Windows Forms
- printing [Windows Forms], print jobs
ms.assetid: 23ec74f7-34c5-4710-82a0-ee2914518548
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9decba052589bfcc3ecd7b2861dad51e9c51378a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-complete-windows-forms-print-jobs"></a>如何：完成 Windows Form 列印工作
通常，文書處理器和其他應用程式牽涉到列印會提供選項，以顯示訊息給使用者，列印工作已完成。 您可以在 Windows Form 提供這項功能，藉由處理<xref:System.Drawing.Printing.PrintDocument.EndPrint>事件<xref:System.Drawing.Printing.PrintDocument>元件。  
  
 下列程序需要您已建立的 Windows 應用程式與<xref:System.Drawing.Printing.PrintDocument>元件上，也就是啟用列印從 windows 應用程式的標準方式。 如需有關從使用 Windows Form 列印<xref:System.Drawing.Printing.PrintDocument>元件，請參閱[How to： 建立標準 Windows Form 列印工作](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)。  
  
### <a name="to-complete-a-print-job"></a>若要完成列印工作  
  
1.  設定<xref:System.Drawing.Printing.PrintDocument.DocumentName%2A>屬性<xref:System.Drawing.Printing.PrintDocument>元件。  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2.  撰寫程式碼來處理 <xref:System.Drawing.Printing.PrintDocument.EndPrint> 事件。  
  
     下列程式碼範例中，會顯示訊息方塊，表示已完成列印的文件。  
  
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
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 和 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 請將下列程式碼置於表單的建構函式中，以註冊事件處理常式。  
  
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
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Drawing.Printing.PrintDocument>  
 [Windows Forms 列印支援](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
