---
title: "TextBox 控制項概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4d7312246c43157ca9cd6c7b41d2b110586721c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="textbox-control-overview-windows-forms"></a>TextBox 控制項概觀 (Windows Form)
Windows Form 的文字方塊會用來從使用者取得輸入或顯示的文字。 <xref:System.Windows.Forms.TextBox>控制項通常用於編輯的文字，不過它也可以設定為唯讀。 文字方塊可以顯示多行、 文字換行到控制項的大小和加入基本的格式。 <xref:System.Windows.Forms.TextBox>控制項提供單一的格式樣式的文字顯示，或輸入控制項。 若要顯示多種類型的格式化的文字，請使用<xref:System.Windows.Forms.RichTextBox>控制項。 如需詳細資訊，請參閱[RichTextBox 控制項概觀](../../../../docs/framework/winforms/controls/richtextbox-control-overview-windows-forms.md)。  
  
## <a name="working-with-the-textbox-control"></a>使用 TextBox 控制項  
 控制項所顯示的文字包含於<xref:System.Windows.Forms.TextBox.Text%2A>屬性。 根據預設，您可以輸入最多 2048年個字元，在文字方塊中。 如果您設定<xref:System.Windows.Forms.TextBox.Multiline%2A>屬性`true`，您可以輸入最多 32 KB 的文字。 <xref:System.Windows.Forms.TextBox.Text%2A>屬性可以在 [屬性] 視窗中，以在執行階段的執行階段程式碼，或由使用者輸入的設計階段設定。 可以在執行階段擷取的文字方塊中目前的內容，藉由讀取<xref:System.Windows.Forms.TextBox.Text%2A>屬性。  
  
 下列程式碼範例會設定在執行階段控制項中的文字。 `InitializeMyControl`程序將不會自動執行，它必須進行呼叫。  
  
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
 <xref:System.Windows.Forms.TextBox>  
 [操作說明：控制 Windows Forms TextBox 控制項中的插入點](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [操作說明：使用 Windows Forms TextBox 控制項建立密碼文字方塊](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [操作說明：建立唯讀文字方塊](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [操作說明：將引號放入字串中](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [操作說明：在 Windows Forms TextBox 控制項中選取文字](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [操作說明：在 Windows Forms TextBox 控制項中檢視多行](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [TextBox 控制項](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
