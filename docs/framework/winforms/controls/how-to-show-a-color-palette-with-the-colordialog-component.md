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
ms.openlocfilehash: 0406ef7a32678bd149c0024348a7adf1f0b72926
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141779"
---
# <a name="how-to-show-a-color-palette-with-the-colordialog-component"></a>如何：使用 ColorDialog 元件顯示色板
[ColorDialog](colordialog-component-windows-forms.md)元件顯示顏色調色板，並返回包含使用者選擇的顏色的屬性。  
  
### <a name="to-choose-a-color-using-the-colordialog-component"></a>使用 ColorDialog 元件選擇顏色  
  
1. 使用<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法顯示對話方塊。  
  
2. 使用<xref:System.Windows.Forms.DialogResult>屬性確定對話方塊的關閉方式。  
  
3. <xref:System.Windows.Forms.ColorDialog.Color%2A>使用元件的屬性<xref:System.Windows.Forms.ColorDialog>設置所選顏色。  
  
     在下面的示例中，<xref:System.Windows.Forms.Button>控制項<xref:System.Windows.Forms.Control.Click>的事件處理常式將打開一個<xref:System.Windows.Forms.ColorDialog>元件。 當選擇顏色並且使用者按一下 **"確定"** 時，<xref:System.Windows.Forms.Button>控制項的背景顏色將設置為所選顏色。 該示例假定表單具有控制項<xref:System.Windows.Forms.Button>和<xref:System.Windows.Forms.ColorDialog>元件。  
  
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
  
     （視覺 C#，視覺C++）將以下代碼放在表單的建構函式中以註冊事件處理常式。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ColorDialog>
- [ColorDialog 元件](colordialog-component-windows-forms.md)
