---
title: 如何：使用 ColorDialog 元件顯示色板
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- palettes [Windows Forms], showing color
- color dialog box [Windows Forms], showing color palettes
- colors [Windows Forms], allowing users to select
- color palettes [Windows Forms], dialog box
- ColorDialog component [Windows Forms], showing color palettes
- color palettes [Windows Forms], showing in ColorDialog component
- colors [Windows Forms], showing palettes
ms.assetid: ee050f61-dbc8-4436-ba22-51360981ab48
ms.openlocfilehash: ea12fe19b6c8c7464f0820267face8a1d66de784
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-show-a-color-palette-with-the-colordialog-component"></a>如何：使用 ColorDialog 元件顯示色板
[ColorDialog](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)元件會顯示色的調色盤，並傳回包含使用者所選取的色彩屬性。  
  
### <a name="to-choose-a-color-using-the-colordialog-component"></a>選擇色彩，其使用 ColorDialog 元件  
  
1.  顯示對話方塊方塊使用<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法。  
  
2.  使用<xref:System.Windows.Forms.DialogResult>屬性來決定對話方塊關閉的方式。  
  
3.  使用<xref:System.Windows.Forms.ColorDialog.Color%2A>屬性<xref:System.Windows.Forms.ColorDialog>設定所選的色彩的元件。  
  
     在下列範例中，<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Click>事件處理常式會開啟<xref:System.Windows.Forms.ColorDialog>元件。 色彩選擇和使用者時按下**確定**、<xref:System.Windows.Forms.Button>控制項的背景色彩會設為選擇的色彩。 這個範例假設您的表單具有<xref:System.Windows.Forms.Button>控制項和<xref:System.Windows.Forms.ColorDialog>元件。  
  
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
  
     (Visual C# [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 下列程式碼置於表單的建構函式，以註冊事件處理常式。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=   
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.ColorDialog>  
 [ColorDialog 元件](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)
