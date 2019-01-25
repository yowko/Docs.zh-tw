---
title: HOW TO：Windows Form RichTextBox 控制項設定字型屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- .rtf files [Windows Forms], formatting in RichTextBox control
- fonts [Windows Forms], changing attributes in RichTextBox control
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting font attributes
- text [Windows Forms]
- text boxes [Windows Forms], formatting text
- formatting [Windows Forms]
ms.assetid: 2bc23ddb-0529-4489-a1a2-ad253cb43f9a
ms.openlocfilehash: 3793c33d378ee242656889434c7b29c415e9ec9a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496201"
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a>HOW TO：Windows Form RichTextBox 控制項設定字型屬性
Windows Form<xref:System.Windows.Forms.RichTextBox>控制項有許多選項可以格式化所顯示的文字。 您得於所選取的字元粗體、 底線或斜體使用<xref:System.Windows.Forms.RichTextBox.SelectionFont%2A>屬性。 您也可以使用這個屬性來變更所選取字元的大小和字體。 <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A>屬性可讓您變更所選取的字元的色彩。  
  
### <a name="to-change-the-appearance-of-characters"></a>變更字元的外觀  
  
1.  設定<xref:System.Windows.Forms.RichTextBox.SelectionFont%2A>屬性設為適當字型。  
  
     若要讓使用者能夠設定應用程式中的字型家族、 大小和字體，您通常會使用<xref:System.Windows.Forms.FontDialog>元件。 如需概觀，請參閱 [FontDialog 元件概觀](../../../../docs/framework/winforms/controls/fontdialog-component-overview-windows-forms.md)。  
  
2.  設定<xref:System.Windows.Forms.RichTextBox.SelectionColor%2A>屬性設為適當的色彩。  
  
     若要讓使用者能夠設定應用程式中的色彩，您通常會使用<xref:System.Windows.Forms.ColorDialog>元件。 如需概觀，請參閱 [ColorDialog 元件概觀](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md)。  
  
    ```vb  
    RichTextBox1.SelectionFont = New Font("Tahoma", 12, FontStyle.Bold)  
    RichTextBox1.SelectionColor = System.Drawing.Color.Red  
    ```  
  
    ```csharp  
    richTextBox1.SelectionFont = new Font("Tahoma", 12, FontStyle.Bold);  
    richTextBox1.SelectionColor = System.Drawing.Color.Red;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionFont =  
       gcnew System::Drawing::Font("Tahoma", 12, FontStyle::Bold);  
    richTextBox1->SelectionColor = System::Drawing::Color::Red;  
    ```  
  
    > [!NOTE]
    >  這些屬性只會影響選取的文字；或者，如果未選取文字，則是在目前插入點位置中輸入的文字。 如需以程式設計方式選取文字的資訊，請參閱<xref:System.Windows.Forms.TextBoxBase.Select%2A>。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox 控制項](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)
- [在 Windows Forms 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
