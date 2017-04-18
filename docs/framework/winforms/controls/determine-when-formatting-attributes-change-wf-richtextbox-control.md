---
title: "如何：判斷 Windows Form RichTextBox 控制項中的格式屬性何時變更 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "範例 [Windows Form], 文字方塊"
  - "RichTextBox 控制項 [Windows Form], 決定字型的變更"
  - "SelBold 屬性"
  - "SelChange 事件"
  - "文字方塊, 決定字型的變更"
ms.assetid: bdfed015-f77a-41e5-b38f-f8629b2fa166
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：判斷 Windows Form RichTextBox 控制項中的格式屬性何時變更
Windows Form <xref:System.Windows.Forms.RichTextBox> 控制項的常見用法之一是使用屬性格式化文字，例如字型選項或段落樣式。  您的應用程式可能需要記錄文字格式的任何變更以便顯示工具列，就像許多文書處理應用程式的做法一樣。  
  
### 若要回應格式屬性 \(Attribute\) 中的變更  
  
1.  在 <xref:System.Windows.Forms.RichTextBox.SelectionChanged> 事件處理常式中寫入程式碼，以便根據屬性的值執行適當的動作。  下列範例會根據 <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> 屬性的值變更工具列按鈕的外觀。  工具列按鈕只會在插入點移入控制項時更新。  
  
     以下範例假設含有 <xref:System.Windows.Forms.RichTextBox> 控制項和含有工具列按鈕的 <xref:System.Windows.Forms.ToolBar> 控制項之表單。  如需工具列和工具列按鈕的詳細資料，請參閱 [如何：將按鈕加入至 ToolBar 控制項](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)。  
  
    ```vb  
    ' The following code assumes the existence of a toolbar control  
    ' with at least one toolbar button.  
    Private Sub RichTextBox1_SelectionChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles RichTextBox1.SelectionChanged  
       If RichTextBox1.SelectionBullet = True Then  
          ' Bullet button on toolbar should appear pressed  
          ToolBarButton1.Pushed = True  
       Else  
           ' Bullet button on toolbar should appear unpressed  
           ToolBarButton1.Pushed = False  
       End If  
    End Sub  
  
    ```  
  
    ```csharp  
    // The following code assumes the existence of a toolbar control  
    // with at least one toolbar button.  
    private void richTextBox1_SelectionChanged(object sender,  
    System.EventArgs e)  
    {  
       if (richTextBox1.SelectionBullet == true)   
       {  
          // Bullet button on toolbar should appear pressed  
          toolBarButton1.Pushed = true;  
       }  
       else   
       {  
          // Bullet button on toolbar should appear unpressed  
          toolBarButton1.Pushed = false;  
       }  
    }  
  
    ```  
  
    ```cpp  
    // The following code assumes the existence of a toolbar control  
    // with at least one toolbar button.  
    private:  
       System::Void richTextBox1_SelectionChanged(  
          System::Object ^  sender, System::EventArgs ^  e)  
       {  
          if (richTextBox1->SelectionBullet == true)  
          {  
             // Bullet button on toolbar should appear pressed  
             toolBarButton1->Pushed = true;  
          }  
          else  
          {  
             // Bullet button on toolbar should appear unpressed  
             toolBarButton1->Pushed = false;  
          }  
       }  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.RichTextBox.SelectionChanged>   
 <xref:System.Windows.Forms.RichTextBox>   
 [RichTextBox 控制項](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)   
 [在 Windows Form 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)