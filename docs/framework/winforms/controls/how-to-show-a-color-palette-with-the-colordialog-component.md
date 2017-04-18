---
title: "如何：使用 ColorDialog 元件顯示色板 | Microsoft Docs"
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
  - "色彩對話方塊, 顯示色板"
  - "色板, 對話方塊"
  - "色板, 在 ColorDialog 元件中顯示"
  - "Color 屬性"
  - "ColorDialog 元件, 顯示色板"
  - "色彩, 允許使用者選取"
  - "色彩, 顯示調色盤"
  - "調色盤, 顯示色彩"
ms.assetid: ee050f61-dbc8-4436-ba22-51360981ab48
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：使用 ColorDialog 元件顯示色板
[ColorDialog](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md) 元件會顯示色板，並傳回包含使用者所選取的色彩屬性。  
  
### 若要使用 ColorDialog 元件選擇色彩  
  
1.  使用 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 方法顯示對話方塊。  
  
2.  使用 <xref:System.Windows.Forms.DialogResult> 屬性決定對話方塊關閉的方式。  
  
3.  使用 <xref:System.Windows.Forms.ColorDialog> 元件的 <xref:System.Windows.Forms.ColorDialog.Color%2A> 屬性設定選定的色彩。  
  
     在下列範例中，<xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Click> 事件處理常式會開啟 <xref:System.Windows.Forms.ColorDialog> 元件。  在色彩選定而且使用者按一下 \[**確定**\] 後，<xref:System.Windows.Forms.Button> 控制項的背景色彩會設成選定的色彩。  此範例假設您的表單具有 <xref:System.Windows.Forms.Button> 控制項和 <xref:System.Windows.Forms.ColorDialog> 元件。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button1.Click  
       If ColorDialog1.ShowDialog() = DialogResult.OK Then  
          Button1.BackColor = ColorDialog1.Color  
       End If  
    End Sub  
  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(colorDialog1.ShowDialog() == DialogResult.OK)  
       {  
          button1.BackColor = colorDialog1.Color;  
       }  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,   
          System::EventArgs ^ e)  
       {  
          if(colorDialog1->ShowDialog() == DialogResult::OK)  
          {  
             button1->BackColor = colorDialog1->Color;  
          }  
       }  
    ```  
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]、[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) 將下列程式碼加入表單的建構函式以註冊事件處理常式。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
  
    ```  
  
    ```cpp  
    this->button1->Click +=   
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.ColorDialog>   
 [ColorDialog 元件](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)