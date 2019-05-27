---
title: HOW TO：使用 FontDialog 元件顯示字型清單
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- fonts [Windows Forms], showing list
- FontDialog component [Windows Forms]
- fonts [Windows Forms], attributes
- Font property [Windows Forms], setting with FontDialog component
- Font dialog box [Windows Forms], displaying
- fonts [Windows Forms], selecting
ms.assetid: 35692c1b-0937-4b7a-9207-1ae6bdc244a0
ms.openlocfilehash: 05e9b5e1280d0318354b0d47f4d78f7ec1c5f4e7
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053454"
---
# <a name="how-to-show-a-font-list-with-the-fontdialog-component"></a>作法：使用 FontDialog 元件顯示字型清單
[FontDialog](fontdialog-component-windows-forms.md)元件可讓使用者選取的字型，以及變更其顯示的層面，例如其加權和大小。  
  
 在對話方塊中選取的字型會傳入<xref:System.Windows.Forms.FontDialog.Font%2A>屬性。 因此，利用使用者所選取是字型的簡單，只要讀取屬性。  
  
### <a name="to-select-font-properties-using-the-fontdialog-component"></a>若要選取的字型屬性使用 FontDialog 元件  
  
1. 顯示對話方塊方塊中，使用<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法。  
  
2. 使用<xref:System.Windows.Forms.DialogResult>屬性來決定對話方塊關閉的方式。  
  
3. 使用<xref:System.Windows.Forms.FontDialog.Font%2A>屬性來設定所需的字型。  
  
     在下列範例中，<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Click>事件處理常式會開啟<xref:System.Windows.Forms.FontDialog>元件。 如果字型是選擇且使用者按下 **[確定]**，則<xref:System.Windows.Forms.FontDialog.Font%2A>屬性<xref:System.Windows.Forms.TextBox>表單上的控制項設為所選的字型。 此範例假設您的表單具有<xref:System.Windows.Forms.Button>控制項中，<xref:System.Windows.Forms.TextBox>控制項，並有<xref:System.Windows.Forms.FontDialog>元件。  
  
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
  
     (VisualC#和 Visual C++)下列程式碼置於表單的建構函式，以註冊事件處理常式。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.FontDialog>
- [FontDialog 元件](fontdialog-component-windows-forms.md)
