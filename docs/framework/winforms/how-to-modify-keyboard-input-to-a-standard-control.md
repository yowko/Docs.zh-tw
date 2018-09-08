---
title: 如何：將鍵盤輸入修改為標準控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyboard input [Windows Forms], modifying
- modifying keyboard input
- Windows Forms, modifying keyboard input
- keyboards [Windows Forms], keyboard input
ms.assetid: 626d3712-d866-4988-bcda-a2d5b36ec0ba
ms.openlocfilehash: c109615b9a0eb61d18f7f44e3248d2b24934ee5f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44184950"
---
# <a name="how-to-modify-keyboard-input-to-a-standard-control"></a>如何：將鍵盤輸入修改為標準控制項
Windows Form 提供使用和修改鍵盤輸入的功能。 使用按鍵表示在方法或事件處理常式中處理按鍵，讓訊息佇列較後面的其他方法和事件不會收到按鍵值。 修改按鍵表示修改按鍵的值，讓訊息佇列較後面的方法和事件處理常式會收到不同的按鍵值。 本主題將示範如何完成這些工作。  
  
### <a name="to-consume-a-key"></a>使用按鍵  
  
-   在 <xref:System.Windows.Forms.Control.KeyPress> 事件處理常式中，將 <xref:System.Windows.Forms.KeyPressEventArgs> 類別的 <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> 屬性設定為 `true`。  
  
     -或-  
  
     在 <xref:System.Windows.Forms.Control.KeyDown> 事件處理常式中，將 <xref:System.Windows.Forms.KeyEventArgs> 類別的 <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> 屬性設定為 `true`。  
  
    > [!NOTE]
    >  在 <xref:System.Windows.Forms.Control.KeyDown> 事件處理常式中設定 <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> 屬性，並不會防止引發目前按鍵的 <xref:System.Windows.Forms.Control.KeyPress> 和 <xref:System.Windows.Forms.Control.KeyUp> 事件。 為了這個目的，請使用 <xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> 屬性。  
  
     下列範例摘錄自 `switch` 陳述式，它會檢查 <xref:System.Windows.Forms.Control.KeyPress> 事件處理常式所收到之 <xref:System.Windows.Forms.KeyPressEventArgs> 的 <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> 屬性。 這個程式碼使用 'A' 和 'a' 字元按鍵。  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#6)]  
  
### <a name="to-modify-a-standard-character-key"></a>修改標準的字元按鍵  
  
-   在 <xref:System.Windows.Forms.Control.KeyPress> 事件處理常式中，將 <xref:System.Windows.Forms.KeyPressEventArgs> 類別的 <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> 屬性設定為新的字元按鍵值。  
  
     下列範例摘錄自 `switch` 陳述式，它會將 'B' 修改為 'A' 並將 'b' 修改為 'a'。 請注意，<xref:System.Windows.Forms.KeyPressEventArgs> 參數的 <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> 屬性會設定為 `false`，因此新按鍵值會傳播給訊息佇列中的其他方法和事件。  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#7)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#7)]  
  
### <a name="to-modify-a-noncharacter-key"></a>修改非字元按鍵  
  
-   覆寫處理 Windows 訊息的 <xref:System.Windows.Forms.Control> 方法，偵測 WM_KEYDOWN 或 WM_SYSKEYDOWN 訊息，並將 <xref:System.Windows.Forms.Message> 參數的 <xref:System.Windows.Forms.Message.WParam%2A> 屬性設定為代表新非字元按鍵的 <xref:System.Windows.Forms.Keys> 值。  
  
     下列程式碼範例示範如何覆寫控制項的 <xref:System.Windows.Forms.Control.PreProcessMessage%2A> 方法，以偵測按鍵 F1 至 F9，並將任何 F3 按鍵修改為 F1。 如需詳細資訊<xref:System.Windows.Forms.Control>方法，您可以覆寫以攔截鍵盤訊息，請參閱[在 Windows Forms 應用程式中的使用者輸入](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md)並[鍵盤輸入的運作方式](../../../docs/framework/winforms/how-keyboard-input-works.md)。  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#12](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#12](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#12)]  
  
## <a name="example"></a>範例  
 下列程式碼範例是前面幾節中程式碼範例的完整應用程式。 這個應用程式使用衍生自 <xref:System.Windows.Forms.TextBox> 類別的自訂控制項來使用和修改鍵盤輸入。  
  
 [!code-csharp[System.Windows.Forms.KeyBoardInput#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInput#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   System、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
 Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。  另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Forms 程式碼範例](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## <a name="see-also"></a>另請參閱  
 [Windows Forms 應用程式中的鍵盤輸入](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [Windows Forms 應用程式中的使用者輸入](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md)  
 [鍵盤輸入的運作方式](../../../docs/framework/winforms/how-keyboard-input-works.md)
