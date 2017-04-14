---
title: "如何：顯示 Windows Form 的對話方塊 | Microsoft Docs"
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
  - "對話方塊, 針對 Windows Form 顯示"
  - "Windows Form 對話方塊, 顯示"
  - "Windows Form, 從另一表單呼叫表單"
  - "Windows Form, 顯示"
ms.assetid: aaac1b38-c651-495a-8d3d-5a9bfb32fee3
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：顯示 Windows Form 的對話方塊
您可使用在應用程式中顯示其他表單的方式，來顯示對話方塊。  應用程式執行時，啟動表單會自動載入。  若要在應用程式中做第二個表單或對話方塊，請撰寫程式碼載入並顯示。  同樣地，若要讓表單或對話方塊消失，請撰寫程式碼以卸載或隱藏。  
  
### 若要顯示對話方塊  
  
1.  巡覽到你要打開對話方塊的事件處理常式。  在選取某個功能表命令，按下按鈕或是任何其他事件發生時，可能會出現這種情形。  
  
2.  在事件處理常式內，加入程式碼以開啟對話方塊。  在這個範例中，button\-click 事件用來顯示對話方塊：  
  
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