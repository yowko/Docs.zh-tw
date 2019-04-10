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
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59311080"
---
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a><span data-ttu-id="46d4a-102">HOW TO：顯示 Windows Forms 的對話方塊</span><span class="sxs-lookup"><span data-stu-id="46d4a-102">How to: Display Dialog Boxes for Windows Forms</span></span>
<span data-ttu-id="46d4a-103">您可以顯示對話方塊中您的應用程式中顯示任何其他形式的方式相同。</span><span class="sxs-lookup"><span data-stu-id="46d4a-103">You display a dialog box in the same way you display any other form in an application.</span></span> <span data-ttu-id="46d4a-104">執行應用程式時，會自動載入啟動表單。</span><span class="sxs-lookup"><span data-stu-id="46d4a-104">The startup form loads automatically when the application is run.</span></span> <span data-ttu-id="46d4a-105">若要讓第二種形式或應用程式中出現的對話方塊中，撰寫程式碼來載入和顯示它。</span><span class="sxs-lookup"><span data-stu-id="46d4a-105">To make a second form or dialog box appear in the application, write code to load and display it.</span></span> <span data-ttu-id="46d4a-106">同樣地，若要讓表單或對話方塊消失，請撰寫程式碼來卸載或隱藏它。</span><span class="sxs-lookup"><span data-stu-id="46d4a-106">Similarly, to make the form or dialog box disappear, write code to unload or hide it.</span></span>  
  
### <a name="to-display-a-dialog-box"></a><span data-ttu-id="46d4a-107">若要顯示的對話方塊</span><span class="sxs-lookup"><span data-stu-id="46d4a-107">To display a dialog box</span></span>  
  
1. <span data-ttu-id="46d4a-108">瀏覽至您要開啟的對話方塊中的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="46d4a-108">Navigate to the event handler with which you want to open the dialog box.</span></span> <span data-ttu-id="46d4a-109">選取功能表命令時，按一下按鈕時，或任何其他事件發生時，也可能會發生。</span><span class="sxs-lookup"><span data-stu-id="46d4a-109">This can happen when a menu command is selected, when a button is clicked, or when any other event occurs.</span></span>  
  
2. <span data-ttu-id="46d4a-110">在事件處理常式中，加入程式碼，以開啟對話方塊。</span><span class="sxs-lookup"><span data-stu-id="46d4a-110">In the event handler, add code to open the dialog box.</span></span> <span data-ttu-id="46d4a-111">在此範例中，按鈕 click 事件用來顯示此對話方塊：</span><span class="sxs-lookup"><span data-stu-id="46d4a-111">In this example, a button-click event is used to show the dialog box:</span></span>  
  
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
