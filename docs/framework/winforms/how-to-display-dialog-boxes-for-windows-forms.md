---
title: 操作方式：顯示對話方塊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, displaying
- Windows Forms dialog boxes [Windows Forms], displaying
- Windows Forms, calling one form from another
- dialog boxes [Windows Forms], displaying for Windows Forms
ms.assetid: aaac1b38-c651-495a-8d3d-5a9bfb32fee3
ms.openlocfilehash: 3625080c7c322e297a9de92e4f95a40c0caf3e72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181979"
---
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a>如何：顯示 Windows Form 的對話方塊
顯示對話方塊的方式與在應用程式中顯示任何其他表單的方式相同。 當應用程式運行時，啟動表單會自動載入。 要使第二個表單或對話方塊顯示在應用程式中，請編寫代碼以載入並顯示它。 同樣，要使表單或對話方塊消失，請編寫代碼以卸載或隱藏它。  
  
### <a name="to-display-a-dialog-box"></a>顯示對話方塊  
  
1. 導航到要打開對話方塊的事件處理常式。 當選擇功能表命令、按一下按鈕時或發生任何其他事件時，可能會發生這種情況。  
  
2. 在事件處理常式中，添加代碼以打開對話方塊。 在此示例中，按鈕按一下事件用於顯示對話方塊：  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim dlg1 as new Form()  
       dlg1.ShowDialog()  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)
    {  
       Form dlg1 = new Form();  
       dlg1.ShowDialog();  
    }  
    ```  
  
    ```cpp  
    private:
      void button1_Click(System::Object ^ sender,  
        System::EventArgs ^ e)  
      {  
        Form ^ dlg1 = gcnew Form();  
        dlg1->ShowDialog();  
      }  
    ```
