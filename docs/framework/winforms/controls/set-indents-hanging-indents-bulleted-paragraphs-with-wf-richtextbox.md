---
title: 如何：使用 Windows Form RichTextBox 控制項設定縮排、首行縮排和分項段落
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
ms.openlocfilehash: 95ba276f3b2682d5b5bcaaa49916e856eb580632
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537683"
---
# <a name="how-to-set-indents-hanging-indents-and-bulleted-paragraphs-with-the-windows-forms-richtextbox-control"></a>如何：使用 Windows Form RichTextBox 控制項設定縮排、首行縮排和分項段落
Windows Form<xref:System.Windows.Forms.RichTextBox>控制項有許多選項可以格式化所顯示的文字。 您也可以設定為項目符號清單格式化選取的段落<xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A>屬性。 您也可以使用<xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>， <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>，和<xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A>屬性可用來設定段落相對於左和右邊緣的控制項，以及其他行文字的左邊的緣的縮排。  
  
### <a name="to-format-a-paragraph-as-a-bulleted-list"></a>將段落格式化為項目符號清單  
  
1.  將 <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> 屬性設定為 `true`。  
  
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
  
1.  設定<xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>屬性為整數，代表控制項左的緣與文字的左邊的緣之間的像素為單位的距離。  
  
2.  設定<xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A>屬性為整數，表示段落中文字的第一行的左邊的緣與位於相同的 paragraph 下來幾行的左邊的緣之間的像素為單位的距離。 值<xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A>屬性只適用於線條段落中的第一行下方換行。  
  
3.  設定<xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>屬性為整數，代表控制項右邊緣和文字的右邊緣之間的像素為單位的距離。  
  
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
    >  所有這些屬性都會影響任何包含所選取文字的段落，也會影響在目前插入點後面所輸入的文字。 例如，如果使用者選取段落中的文字，然後調整縮排，則新的設定會套用到包含該文字的整個段落，也會套用到任何在選取的段落之後後續輸入的段落。 如需以程式設計方式選取文字，請參閱<xref:System.Windows.Forms.TextBoxBase.Select%2A>。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.RichTextBox>  
 [RichTextBox 控制項](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [在 Windows Forms 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
