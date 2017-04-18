---
title: "如何：使用 FontDialog 元件顯示字型清單 | Microsoft Docs"
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
  - "字型對話方塊, 顯示"
  - "Font 屬性, 使用 FontDialog 元件設定"
  - "FontDialog 元件 [Windows Form]"
  - "字型, 屬性"
  - "字型, 選取"
  - "字型, 顯示清單"
ms.assetid: 35692c1b-0937-4b7a-9207-1ae6bdc244a0
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：使用 FontDialog 元件顯示字型清單
[FontDialog](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md) 元件可讓使用者選取字型，以及變更字型的顯示外觀，例如其粗細和大小。  
  
 在對話方塊中選取的字型會傳回至 <xref:System.Windows.Forms.FontDialog.Font%2A> 屬性。  因此，利用使用者選取的字型就和讀取屬性一樣容易。  
  
### 若要使用 FontDialog 元件選取字型屬性  
  
1.  使用 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 方法顯示對話方塊。  
  
2.  使用 <xref:System.Windows.Forms.DialogResult> 屬性決定對話方塊關閉的方式。  
  
3.  使用 <xref:System.Windows.Forms.FontDialog.Font%2A> 屬性設定想要的字型。  
  
     在下列範例中，<xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Click> 事件處理常式會開啟 <xref:System.Windows.Forms.FontDialog> 元件。  在字型選定而且使用者按一下 \[**確定**\] 後，表單上 <xref:System.Windows.Forms.TextBox> 控制項的 <xref:System.Windows.Forms.FontDialog.Font%2A> 屬性會設定成選定的字型。  此範例假設您的表單具有 <xref:System.Windows.Forms.Button> 控制項、<xref:System.Windows.Forms.TextBox> 控制項和 <xref:System.Windows.Forms.FontDialog> 元件。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       If FontDialog1.ShowDialog() = DialogResult.OK Then  
          TextBox1.Font = FontDialog1.Font  
       End If  
    End Sub  
  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(fontDialog1.ShowDialog() == DialogResult.OK)  
       {  
          textBox1.Font = fontDialog1.Font;  
       }  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if(fontDialog1->ShowDialog() == DialogResult::OK)  
          {  
             textBox1->Font = fontDialog1->Font;  
          }  
       }  
    ```  
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 和 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) 將下列程式碼加入表單的建構函式以註冊事件處理常式。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
  
    ```  
  
    ```cpp  
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.FontDialog>   
 [FontDialog 元件](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md)