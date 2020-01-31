---
title: 如何：顯示對話方塊
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
ms.openlocfilehash: dd04a06eaa0dd7583ef2f72edb4cffa99aaaa60c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739456"
---
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a>如何：顯示 Windows Form 的對話方塊
您可以使用與在應用程式中顯示任何其他表單相同的方式來顯示對話方塊。 當應用程式執行時，會自動載入啟動表單。 若要讓第二個表單或對話方塊出現在應用程式中，請撰寫程式碼來載入並顯示。 同樣地，若要讓表單或對話方塊消失，請撰寫程式碼來卸載或隱藏它。  
  
### <a name="to-display-a-dialog-box"></a>若要顯示對話方塊  
  
1. 導覽至您要開啟對話方塊的事件處理常式。 當選取了功能表命令、按一下按鈕時，或發生其他任何事件時，就會發生這種情況。  
  
2. 在事件處理常式中，加入程式碼以開啟對話方塊。 在此範例中，會使用按鈕按下事件來顯示對話方塊：  
  
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
