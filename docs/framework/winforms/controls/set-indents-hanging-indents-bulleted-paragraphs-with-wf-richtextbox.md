---
title: HOW TO：使用 Windows Forms RichTextBox 控制項設定縮排、首行縮排和分項段落
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], setting indents
- .rtf files [Windows Forms], formatting in RichTextBox control
- examples [Windows Forms], text boxes
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting indents and bullets
- text boxes [Windows Forms], bullets
ms.assetid: abfb40e6-5642-4691-8ec1-9d9ae91688dc
ms.openlocfilehash: ef579923ac2b9ea9905a60000d93f6bfc90ed5b8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59342670"
---
# <a name="how-to-set-indents-hanging-indents-and-bulleted-paragraphs-with-the-windows-forms-richtextbox-control"></a>HOW TO：使用 Windows Forms RichTextBox 控制項設定縮排、首行縮排和分項段落
Windows Form<xref:System.Windows.Forms.RichTextBox>控制項有許多選項可以格式化所顯示的文字。 您可以選取的段落格式化為項目符號清單設定<xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A>屬性。 您也可以使用<xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>， <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>，和<xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A>屬性來設定左和右邊緣的控制項和其他文字行的左邊的緣相對的段落的縮排。  
  
### <a name="to-format-a-paragraph-as-a-bulleted-list"></a>將段落格式化為項目符號清單  
  
1. 將 <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> 屬性設定為 `true`。  
  
    ```vb  
    RichTextBox1.SelectionBullet = True  
    ```  
  
    ```csharp  
    richTextBox1.SelectionBullet = true;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionBullet = true;  
    ```  
  
### <a name="to-indent-a-paragraph"></a>縮排段落  
  
1. 設定<xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>屬性設為整數，代表控制項左的緣與文字左邊的緣之間的像素的距離。  
  
2. 設定<xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A>屬性設為整數，代表像素為單位的段落文字的第一行的左邊的緣和同段落中的接下來幾行的左邊的緣之間的距離。 值<xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A>屬性只適用於在段落中第一行下方的已包裝的幾行。  
  
3. 設定<xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>屬性設為整數，代表控制項右緣與文字右邊緣之間的像素的距離。  
  
    ```vb  
    RichTextBox1.SelectionIndent = 8  
    RichTextBox1.SelectionHangingIndent = 3  
    RichTextBox1.SelectionRightIndent = 12  
    ```  
  
    ```csharp  
    richTextBox1.SelectionIndent = 8;  
    richTextBox1.SelectionHangingIndent = 3;  
    richTextBox1.SelectionRightIndent = 12;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionIndent = 8;  
    richTextBox1->SelectionHangingIndent = 3;  
    richTextBox1->SelectionRightIndent = 12;  
    ```  
  
    > [!NOTE]
    >  所有這些屬性都會影響任何包含所選取文字的段落，也會影響在目前插入點後面所輸入的文字。 例如，如果使用者選取段落中的文字，然後調整縮排，則新的設定會套用到包含該文字的整個段落，也會套用到任何在選取的段落之後後續輸入的段落。 如需以程式設計方式選取文字的資訊，請參閱<xref:System.Windows.Forms.TextBoxBase.Select%2A>。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox 控制項](richtextbox-control-windows-forms.md)
- [在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)
