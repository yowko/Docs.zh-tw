---
title: TextBox 控制項概觀 (Windows Form)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TextBox
helpviewer_keywords:
- TextBox control [Windows Forms], about TextBox controls
- text boxes [Windows Forms], adding
ms.assetid: d1a9c7f5-fa53-480a-a75c-158f8649ea2f
ms.openlocfilehash: a91b67df1071c79707bb20a68efb4d5e6f083ae0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162133"
---
# <a name="textbox-control-overview-windows-forms"></a>TextBox 控制項概觀 (Windows Form)
Windows Form 文字方塊用來從使用者取得輸入，或顯示的文字。 <xref:System.Windows.Forms.TextBox>控制項通常使用於可編輯的文字，雖然它可以也成為唯讀狀態。 文字方塊可以顯示多行、 文字換行到控制項的大小和加入基本的格式。 <xref:System.Windows.Forms.TextBox>控制項提供單一的格式樣式顯示，或輸入控制項的文字。 若要顯示多種類型的格式化文字，請使用<xref:System.Windows.Forms.RichTextBox>控制項。 如需詳細資訊，請參閱 < [RichTextBox 控制項概觀](richtextbox-control-overview-windows-forms.md)。  
  
## <a name="working-with-the-textbox-control"></a>使用 TextBox 控制項  
 控制項所顯示的文字包含在<xref:System.Windows.Forms.TextBox.Text%2A>屬性。 根據預設，您可以輸入最多 2048年個字元，在文字方塊中。 如果您設定<xref:System.Windows.Forms.TextBox.Multiline%2A>屬性設`true`，您可以輸入最多 32 KB 的文字。 <xref:System.Windows.Forms.TextBox.Text%2A>屬性可以在 [屬性] 視窗中，以在執行階段程式碼，或由使用者輸入，在執行階段的設計階段設定。 目前文字方塊的內容可以在執行階段擷取，請閱讀<xref:System.Windows.Forms.TextBox.Text%2A>屬性。  
  
 下列程式碼範例會設定在執行階段控制項中的文字。 `InitializeMyControl`程序將不會自動執行; 它必須先呼叫。  
  
```vb  
Private Sub InitializeMyControl()  
   ' Put some text into the control first.  
   TextBox1.Text = "This is a TextBox control."  
End Sub  
```  
  
```csharp  
private void InitializeMyControl() {  
   // Put some text into the control first.  
   textBox1.Text = "This is a TextBox control.";  
}  
```  
  
```cpp  
private:  
   void InitializeMyControl()  
   {  
      // Put some text into the control first.  
      textBox1->Text = "This is a TextBox control.";  
   }  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.TextBox>
- [HOW TO：控制 Windows Forms TextBox 控制項的插入點](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [HOW TO：使用 Windows Forms TextBox 控制項建立密碼文字方塊](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [HOW TO：建立唯讀文字方塊](how-to-create-a-read-only-text-box-windows-forms.md)
- [HOW TO：將引號放入字串中](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [HOW TO：選取 Windows Forms TextBox 控制項的文字](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [HOW TO：檢視 Windows Forms TextBox 控制項中的多行](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox 控制項](textbox-control-windows-forms.md)
