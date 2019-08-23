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
ms.openlocfilehash: 37fa897f5a2e1c65cbd5db9189f1500e3427c920
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964317"
---
# <a name="how-to-determine-which-modifier-key-was-pressed"></a>作法：判斷按下的輔助按鍵
當您建立接受使用者擊鍵的應用程式時, 您可能也會想要監視輔助按鍵, 例如 SHIFT、ALT 和 CTRL 鍵。 當輔助按鍵與其他按鍵組合, 或按一下滑鼠按鍵時, 您的應用程式就可以適當地回應。 例如, 如果按了字母 S, 這可能只會導致畫面出現 "s", 但是如果按下 CTRL + S 鍵, 則可能會儲存目前的檔。 如果您處理<xref:System.Windows.Forms.Control.KeyDown>事件<xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> , 事件處理常式所接收<xref:System.Windows.Forms.KeyEventArgs>之的屬性會指定要按下的輔助按鍵。 或者, 的<xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> <xref:System.Windows.Forms.KeyEventArgs>屬性會指定已按下的字元, 以及與位 or 結合的任何輔助按鍵。 不過, 如果您正在處理<xref:System.Windows.Forms.Control.KeyPress>事件或滑鼠事件, 事件處理常式就不會收到這則資訊。 在此情況下, 您必須使用<xref:System.Windows.Forms.Control.ModifierKeys%2A> <xref:System.Windows.Forms.Control>類別的屬性。 不論是哪一種情況, 您都必須執行適當<xref:System.Windows.Forms.Keys>值的位 and, 以及您要測試的值。 <xref:System.Windows.Forms.Keys>列舉會提供每個輔助按鍵的變化, 因此請務必以正確的值執行位 and。 例如, shift 鍵是以<xref:System.Windows.Forms.Keys.Shift> <xref:System.Windows.Forms.Keys.RShiftKey> 、 <xref:System.Windows.Forms.Keys.ShiftKey>和<xref:System.Windows.Forms.Keys.LShiftKey>表示, 做為輔助按鍵來測試移位<xref:System.Windows.Forms.Keys.Shift>的正確值。 同樣地, 若要測試 CTRL 和 ALT 做為修飾詞, <xref:System.Windows.Forms.Keys.Control>您<xref:System.Windows.Forms.Keys.Alt>應該分別使用和值。  
  
> [!NOTE]
> Visual Basic 程式設計人員也可以透過<xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A>屬性存取金鑰資訊  
  
### <a name="to-determine-which-modifier-key-was-pressed"></a>判斷按下的輔助按鍵  
  
- 使用位`AND`運算子<xref:System.Windows.Forms.Control.ModifierKeys%2A>搭配屬性<xref:System.Windows.Forms.Keys>和列舉的值, 以判斷是否按下特定的輔助按鍵。 下列程式碼範例示範如何判斷在<xref:System.Windows.Forms.Control.KeyPress>事件處理常式內是否按下 SHIFT 鍵。  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Keys>
- <xref:System.Windows.Forms.Control.ModifierKeys%2A>
- [Windows Forms 應用程式中的鍵盤輸入](keyboard-input-in-a-windows-forms-application.md)
- [如何：判斷 CapsLock 是否在 Visual Basic](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9c9d1fz9(v=vs.100))
