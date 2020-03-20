---
title: 完成列印工作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print jobs [Windows Forms], completing in Windows Forms
- printing [Windows Forms], print jobs
ms.assetid: 23ec74f7-34c5-4710-82a0-ee2914518548
ms.openlocfilehash: 62f67002bfbaf46e73bae06fdaff26efde865c06
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182603"
---
# <a name="how-to-complete-windows-forms-print-jobs"></a>如何：完成 Windows Form 列印工作
通常，文字處理器和其他涉及列印的應用程式將提供向使用者顯示列印工作已完成的消息的選項。 您可以通過處理<xref:System.Drawing.Printing.PrintDocument.EndPrint><xref:System.Drawing.Printing.PrintDocument>元件的事件在 Windows 表單中提供此功能。  
  
 以下過程要求您創建了一個帶有<xref:System.Drawing.Printing.PrintDocument>元件的基於 Windows 的應用程式，這是啟用從基於 Windows 的應用程式進行列印的標準方法。 有關使用<xref:System.Drawing.Printing.PrintDocument>該元件從 Windows 表單列印的詳細資訊，請參閱[：創建標準 Windows 表單列印工作](how-to-create-standard-windows-forms-print-jobs.md)。  
  
### <a name="to-complete-a-print-job"></a>完成列印工作  
  
1. 設置<xref:System.Drawing.Printing.PrintDocument.DocumentName%2A>元件的屬性<xref:System.Drawing.Printing.PrintDocument>。  
  
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
  
     在下面的代碼示例中，將顯示一個訊息方塊，指示文檔已完成列印。  
  
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
  
     （視覺 C# 和視覺C++）將以下代碼放在表單的建構函式中以註冊事件處理常式。  
  
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
