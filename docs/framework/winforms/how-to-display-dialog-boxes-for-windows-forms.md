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
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a><span data-ttu-id="30645-102">如何：顯示 Windows Form 的對話方塊</span><span class="sxs-lookup"><span data-stu-id="30645-102">How to: Display Dialog Boxes for Windows Forms</span></span>
<span data-ttu-id="30645-103">顯示對話方塊的方式與在應用程式中顯示任何其他表單的方式相同。</span><span class="sxs-lookup"><span data-stu-id="30645-103">You display a dialog box in the same way you display any other form in an application.</span></span> <span data-ttu-id="30645-104">當應用程式運行時，啟動表單會自動載入。</span><span class="sxs-lookup"><span data-stu-id="30645-104">The startup form loads automatically when the application is run.</span></span> <span data-ttu-id="30645-105">要使第二個表單或對話方塊顯示在應用程式中，請編寫代碼以載入並顯示它。</span><span class="sxs-lookup"><span data-stu-id="30645-105">To make a second form or dialog box appear in the application, write code to load and display it.</span></span> <span data-ttu-id="30645-106">同樣，要使表單或對話方塊消失，請編寫代碼以卸載或隱藏它。</span><span class="sxs-lookup"><span data-stu-id="30645-106">Similarly, to make the form or dialog box disappear, write code to unload or hide it.</span></span>  
  
### <a name="to-display-a-dialog-box"></a><span data-ttu-id="30645-107">顯示對話方塊</span><span class="sxs-lookup"><span data-stu-id="30645-107">To display a dialog box</span></span>  
  
1. <span data-ttu-id="30645-108">導航到要打開對話方塊的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="30645-108">Navigate to the event handler with which you want to open the dialog box.</span></span> <span data-ttu-id="30645-109">當選擇功能表命令、按一下按鈕時或發生任何其他事件時，可能會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="30645-109">This can happen when a menu command is selected, when a button is clicked, or when any other event occurs.</span></span>  
  
2. <span data-ttu-id="30645-110">在事件處理常式中，添加代碼以打開對話方塊。</span><span class="sxs-lookup"><span data-stu-id="30645-110">In the event handler, add code to open the dialog box.</span></span> <span data-ttu-id="30645-111">在此示例中，按鈕按一下事件用於顯示對話方塊：</span><span class="sxs-lookup"><span data-stu-id="30645-111">In this example, a button-click event is used to show the dialog box:</span></span>  
  
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
