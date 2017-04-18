---
title: "如何：設定由 Windows Form 控制項所顯示的文字 | Microsoft Docs"
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
  - "Button 控制項 [Windows Form], 按鈕文字"
  - "Button 控制項 [Windows Form], 文字顯示"
  - "按鈕, 文字"
  - "標題, 設定"
  - "標題, Windows Form 控制項"
  - "控制項 [Windows Form], 標題"
  - "範例 [Windows Form], 控制項"
  - "表單, 標題"
  - "標籤, 加入至 CommandButton 控制項"
  - "StdFont 物件與 CommandButton 標題"
  - "文字"
  - "Text 屬性, Windows Form 控制項"
  - "文字, Windows Form 控制項"
  - "Windows Form, 標題"
ms.assetid: 36b95bff-8780-479d-b86a-f1a0673653aa
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 如何：設定由 Windows Form 控制項所顯示的文字
Windows Form 控制項通常會顯示與控制項主要功能相關的一些文字。  例如，<xref:System.Windows.Forms.Button> 控制項通常會顯示一個標題，指出當按下按鈕時，就會執行什麼動作。  針對所有控制項，您都可以使用 <xref:System.Windows.Forms.Control.Text%2A> 屬性來設定或傳回該文字。  您可以使用 <xref:System.Windows.Forms.Control.Font%2A> 屬性來變更字型。  您也可以使用設計工具來設定文字。  另請參閱[如何：使用設計工具來建立 Windows Form 控制項的便捷鍵](http://msdn.microsoft.com/library/ms233673\(v=vs.110\))、[如何：使用設計工具來設定 Windows Form 控制項所顯示的文字](http://msdn.microsoft.com/library/ms233665\(v=vs.110\))、[如何：使用設計工具來設定 Windows Form 控制項所顯示的影像](http://msdn.microsoft.com/library/ms233656\(v=vs.110\))。  
  
### 以程式設計方式來設定控制項所顯示的文字  
  
1.  將 <xref:System.Windows.Forms.Control.Text%2A> 屬性設為字串。  
  
     若要建立加上底線的便捷鍵，請在要成為便捷鍵的字母前面加上連字號 \(&\) 字元。  
  
2.  將 <xref:System.Windows.Forms.Control.Font%2A> 屬性設為 <xref:System.Drawing.Font> 類型的物件。  
  
    ```vb  
    Button1.Text = "Click here to save changes"  
    Button1.Font = New Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point)  
    ```  
  
    ```csharp  
    button1.Text = "Click here to save changes";  
    button1.Font = new Font("Arial", 10, FontStyle.Bold,  
       GraphicsUnit.Point);  
    ```  
  
    ```cpp#  
    button1->Text = "Click here to save changes";  
    button1->Font = new System::Drawing::Font("Arial",  
       10, FontStyle::Bold, GraphicsUnit::Point);  
    ```  
  
    > [!NOTE]
    >  您可以在使用者介面項目中使用逸出字元來顯示特殊字元，這些使用者介面項目 \(例如功能表項目\) 通常會以不同方式來解譯該字元。  例如，下列程式碼字行會設定功能表項目的文字來讀取 "& Now For Something Completely Different"：  
  
    ```vb  
    MPMenuItem.Text = "&& Now For Something Completely Different"  
    ```  
  
    ```csharp  
    mpMenuItem.Text = "&& Now For Something Completely Different";  
    ```  
  
    ```cpp#  
    mpMenuItem->Text = "&& Now For Something Completely Different";  
  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.Control.Text%2A?displayProperty=fullName>   
 [如何：建立 Windows Form 控制項的便捷鍵](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)   
 [如何：回應 Windows Form Button 按一下動作](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)