---
title: TextBox 控制項概觀
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
ms.openlocfilehash: 06ab460d720d17331881b5ba653263160eaf3cb3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742801"
---
# <a name="textbox-control-overview-windows-forms"></a>TextBox 控制項概觀 (Windows Form)
Windows Forms 文字方塊可用來取得使用者的輸入或顯示文字。 <xref:System.Windows.Forms.TextBox> 控制項通常用於可編輯的文字，不過它也可以設為唯讀。 文字方塊可以顯示多行、將文字換成控制項的大小，以及新增基本格式。 <xref:System.Windows.Forms.TextBox> 控制項會針對顯示或輸入控制項的文字提供單一格式樣式。 若要顯示多種類型的格式化文字，請使用 <xref:System.Windows.Forms.RichTextBox> 控制項。 如需詳細資訊，請參閱[RichTextBox 控制項總覽](richtextbox-control-overview-windows-forms.md)。  
  
## <a name="working-with-the-textbox-control"></a>使用 TextBox 控制項  
 控制項所顯示的文字會包含在 <xref:System.Windows.Forms.TextBox.Text%2A> 屬性中。 根據預設，您最多可以在文字方塊中輸入2048個字元。 如果您將 [<xref:System.Windows.Forms.TextBox.Multiline%2A>] 屬性設定為 [`true`]，則最多可以輸入 32 KB 的文字。 <xref:System.Windows.Forms.TextBox.Text%2A> 屬性可以在設計階段使用 [屬性] 視窗、在程式碼中的執行時間，或在執行時間由使用者輸入設定。 您可以藉由讀取 <xref:System.Windows.Forms.TextBox.Text%2A> 屬性，在執行時間抓取文字方塊的目前內容。  
  
 下列程式碼範例會在執行時間設定控制項中的文字。 `InitializeMyControl` 程式不會自動執行;必須呼叫它。  
  
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
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.TextBox>
- [操作說明：控制 Windows Forms TextBox 控制項中的插入點](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [操作說明：使用 Windows Forms TextBox 控制項建立密碼文字方塊](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [操作說明：建立唯讀文字方塊](how-to-create-a-read-only-text-box-windows-forms.md)
- [操作說明：將引號放入字串中](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [操作說明：在 Windows Forms TextBox 控制項中選取文字](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [操作說明：在 Windows Forms TextBox 控制項中檢視多行](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox 控制項](textbox-control-windows-forms.md)
