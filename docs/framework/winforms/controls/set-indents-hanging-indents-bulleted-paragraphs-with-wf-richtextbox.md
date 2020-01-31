---
title: 使用 RichTextBox 控制項設定縮排、懸掛縮排和點符段落
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
ms.openlocfilehash: 4dcd5691f328eac6d94675c50ed41a7d7cc36596
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743012"
---
# <a name="how-to-set-indents-hanging-indents-and-bulleted-paragraphs-with-the-windows-forms-richtextbox-control"></a>如何：使用 Windows Form RichTextBox 控制項設定縮排、首行縮排和分項段落
Windows Forms <xref:System.Windows.Forms.RichTextBox> 控制項有許多選項可讓您格式化所顯示的文字。 您可以藉由設定 [<xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A>] 屬性，將選取的段落格式化為項目符號清單。 您也可以使用 [<xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>]、[<xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>] 和 [<xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> 屬性]，將段落的縮排設定為相對於控制項的左右邊緣，以及其他行文字的左邊緣。  
  
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
  
1. 將 <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> 屬性設定為整數，代表控制項左邊緣與文字左邊緣之間的距離（以圖元為單位）。  
  
2. 將 [<xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A>] 屬性設定為一個整數，代表段落中第一行文字的左邊緣與同一段落中後續行的左邊緣之間的距離（以圖元為單位）。 [<xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A>] 屬性的值僅適用于在第一行下方換行的段落中的線條。  
  
3. 將 <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> 屬性設定為整數，代表控制項右邊緣和文字右邊緣之間的距離（以圖元為單位）。  
  
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
    > 所有這些屬性都會影響任何包含所選取文字的段落，也會影響在目前插入點後面所輸入的文字。 例如，如果使用者選取段落中的文字，然後調整縮排，則新的設定會套用到包含該文字的整個段落，也會套用到任何在選取的段落之後後續輸入的段落。 如需以程式設計方式選取文字的相關資訊，請參閱 <xref:System.Windows.Forms.TextBoxBase.Select%2A>。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox 控制項](richtextbox-control-windows-forms.md)
- [在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)
