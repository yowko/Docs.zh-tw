---
title: HOW TO：判斷按下的輔助按鍵
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboard input
- shift keys
- events [Windows Forms], mouse
- Keys.ControlKey enumeration member
- keys [Windows Forms], control keys
- user input [Windows Forms], checking for keyboard
- keys [Windows Forms], determining last pressed
- keys [Windows Forms], shift keys
- keys [Windows Forms], modifier keys
- control keys
- keys [Windows Forms], alt keys
- alt keys
- Keys.Shift enumeration member
- events [Windows Forms], keyboard
- keyboards [Windows Forms], keyboard input
- Keys.Alt enumeration member
- modifier keys
ms.assetid: 1e184048-0ae3-4067-a200-d4ba31dbc2cb
ms.openlocfilehash: 571af49cdf82b876cfb72a7c7636874c8d155fb7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803138"
---
# <a name="how-to-determine-which-modifier-key-was-pressed"></a>HOW TO：判斷按下的輔助按鍵
當您建立可接受使用者的按鍵輸入時，您也可以監視輔助按鍵，例如 SHIFT、 ALT 和 CTRL 鍵。 輔助按鍵按下時搭配其他索引鍵，或按下滑鼠，就可以適當地回應您的應用程式。 例如，如果按下以字母 S 時，這只會出現在畫面上，"s"，但如果按下按鍵 CTRL + S，可能會儲存目前的文件。 如果您處理<xref:System.Windows.Forms.Control.KeyDown>事件，<xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A>屬性<xref:System.Windows.Forms.KeyEventArgs>收到事件處理常式會指定哪一個輔助按鍵按下按鍵。 或者，<xref:System.Windows.Forms.KeyEventArgs.KeyData%2A>屬性<xref:System.Windows.Forms.KeyEventArgs>指定按鍵以及與位元 OR 運算結合任何輔助按鍵的字元。 不過，如果您處理<xref:System.Windows.Forms.Control.KeyPress>事件或滑鼠事件，事件處理常式不會收到這項資訊。 在此情況下，您必須使用<xref:System.Windows.Forms.Control.ModifierKeys%2A>屬性<xref:System.Windows.Forms.Control>類別。 在任一情況下，您必須執行適當的位元 AND<xref:System.Windows.Forms.Keys>值和您要測試的值。 <xref:System.Windows.Forms.Keys>列舉型別提供具有正確的值和每個修飾詞索引鍵，因此是很重要，您執行位元的變化。 比方說，SHIFT 鍵表示<xref:System.Windows.Forms.Keys.Shift>， <xref:System.Windows.Forms.Keys.ShiftKey>，<xref:System.Windows.Forms.Keys.RShiftKey>並<xref:System.Windows.Forms.Keys.LShiftKey>正確的值來測試 SHIFT 輔助按鍵是<xref:System.Windows.Forms.Keys.Shift>。 同樣地，若要測試 CTRL 和 ALT 修飾詞為您應該使用<xref:System.Windows.Forms.Keys.Control>和<xref:System.Windows.Forms.Keys.Alt>值，分別。  
  
> [!NOTE]
>  Visual Basic 程式設計人員也可以存取金鑰的資訊透過<xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A>屬性  
  
### <a name="to-determine-which-modifier-key-was-pressed"></a>若要判斷哪一個輔助按鍵  
  
-   使用位元`AND`運算子搭配<xref:System.Windows.Forms.Control.ModifierKeys%2A>屬性和值的<xref:System.Windows.Forms.Keys>列舉型別來判斷特定的修飾詞的索引鍵是否按下。 下列程式碼範例示範如何判斷是否在按下 SHIFT 鍵<xref:System.Windows.Forms.Control.KeyPress>事件處理常式。  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Keys>
- <xref:System.Windows.Forms.Control.ModifierKeys%2A>
- [Windows Forms 應用程式中的鍵盤輸入](keyboard-input-in-a-windows-forms-application.md)
- [如何：決定如果 CapsLock 是在 Visual Basic](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9c9d1fz9(v=vs.100))
