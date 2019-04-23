---
title: HOW TO：完成 Windows Forms 列印工作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print jobs [Windows Forms], completing in Windows Forms
- printing [Windows Forms], print jobs
ms.assetid: 23ec74f7-34c5-4710-82a0-ee2914518548
ms.openlocfilehash: 256b9a3d8842aaa4b032e67ebac9ca6a9e1ef34a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59293751"
---
# <a name="how-to-complete-windows-forms-print-jobs"></a>HOW TO：完成 Windows Forms 列印工作
通常，文書處理器和其他應用程式牽涉到列印會提供對列印工作已完成的使用者顯示一則訊息的選項。 您可以在 Windows Forms 中提供這項功能，藉由處理<xref:System.Drawing.Printing.PrintDocument.EndPrint>事件的<xref:System.Drawing.Printing.PrintDocument>元件。  
  
 下列程序需要您已建立的 Windows 應用程式與<xref:System.Drawing.Printing.PrintDocument>它，也就是標準的方式，啟用從以 Windows 為基礎的應用程式列印的元件。 如需有關從使用 Windows Form 列印<xref:System.Drawing.Printing.PrintDocument>元件，請參閱[How to:建立標準的 Windows Forms 列印工作](how-to-create-standard-windows-forms-print-jobs.md)。  
  
### <a name="to-complete-a-print-job"></a>若要完成列印工作  
  
1. 設定<xref:System.Drawing.Printing.PrintDocument.DocumentName%2A>屬性<xref:System.Drawing.Printing.PrintDocument>元件。  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2. 撰寫程式碼來處理 <xref:System.Drawing.Printing.PrintDocument.EndPrint> 事件。  
  
     在下列程式碼範例中，會顯示訊息方塊，表示文件已完成列印。  
  
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
  
     (Visual C# 和[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 下列程式碼置於表單的建構函式，以註冊事件處理常式。  
  
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

- <xref:System.Drawing.Printing.PrintDocument>
- [Windows Forms 列印支援](windows-forms-print-support.md)
