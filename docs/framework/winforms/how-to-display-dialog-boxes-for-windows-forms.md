---
title: HOW TO：顯示 Windows Forms 的對話方塊
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
ms.openlocfilehash: b99f2273dae88faf86448da6e1d2986a83803abf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802579"
---
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a>HOW TO：顯示 Windows Forms 的對話方塊
您可以顯示對話方塊中您的應用程式中顯示任何其他形式的方式相同。 執行應用程式時，會自動載入啟動表單。 若要讓第二種形式或應用程式中出現的對話方塊中，撰寫程式碼來載入和顯示它。 同樣地，若要讓表單或對話方塊消失，請撰寫程式碼來卸載或隱藏它。  
  
### <a name="to-display-a-dialog-box"></a>若要顯示的對話方塊  
  
1. 瀏覽至您要開啟的對話方塊中的事件處理常式。 選取功能表命令時，按一下按鈕時，或任何其他事件發生時，也可能會發生。  
  
2. 在事件處理常式中，加入程式碼，以開啟對話方塊。 在此範例中，按鈕 click 事件用來顯示此對話方塊：  
  
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
