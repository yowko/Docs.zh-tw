---
title: 處理使用者輸入
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], user input using code
- custom controls [Windows Forms], keyboard events using code
- custom controls [Windows Forms], mouse events using code
ms.assetid: d9b12787-86f6-4022-8e0f-e12d312c4af2
ms.openlocfilehash: f92b742c3f6feec72e5b3150204d7d984636281d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934085"
---
# <a name="handling-user-input"></a>處理使用者輸入
本主題描述所提供<xref:System.Windows.Forms.Control?displayProperty=nameWithType>的主要鍵盤和滑鼠事件。 處理事件時，控制項作者應覆寫受保護的 `On`*EventName* 方法，而不是將委派附加至事件。 如需檢閱事件，請參閱[從元件引發事件](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120))。  
  
> [!NOTE]
> 如果沒有與事件相關聯的資料, 則<xref:System.EventArgs>會將基類的實例當做引數傳遞`On`給事件*名稱*方法。  
  
## <a name="keyboard-events"></a>鍵盤事件  
 控制項可以處理的常用鍵盤事件為<xref:System.Windows.Forms.Control.KeyDown>、 <xref:System.Windows.Forms.Control.KeyPress>和<xref:System.Windows.Forms.Control.KeyUp>。  
  
|事件名稱|要覆寫的方法|事件的描述|  
|----------------|------------------------|--------------------------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|只在最初按下按鍵時引發。|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|每次按下按鍵時引發。 如果保留索引鍵, <xref:System.Windows.Forms.Control.KeyPress>則會以作業系統定義的重複速度來引發事件。|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|在放開按鍵時引發。|  
  
> [!NOTE]
> 相較於覆寫上表中的事件，處理鍵盤輸入更為複雜，而且已超出本主題的範圍。 如需詳細資訊，請參閱 [Windows Forms 中的使用者輸入](../user-input-in-windows-forms.md)。  
  
## <a name="mouse-events"></a>滑鼠事件  
 控制項可以處理的滑鼠事件為<xref:System.Windows.Forms.Control.MouseDown>、 <xref:System.Windows.Forms.Control.MouseEnter>、 <xref:System.Windows.Forms.Control.MouseHover>、 <xref:System.Windows.Forms.Control.MouseLeave>、 <xref:System.Windows.Forms.Control.MouseMove>和<xref:System.Windows.Forms.Control.MouseUp>。  
  
|事件名稱|要覆寫的方法|事件的描述|  
|----------------|------------------------|--------------------------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|當滑鼠指標位於控制項上並按下滑鼠按鈕時引發。|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|當滑鼠指標第一次進入控制項的區域時引發。|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|當滑鼠指標停留在控制項上時引發。|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|當滑鼠指標離開控制項的區域時引發。|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|當滑鼠指標移入控制項的區域時引發。|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|當滑鼠指標位於控制項上並放開滑鼠按鈕時或當滑鼠指標離開控制項的區域時引發。|  
  
 下列程式碼片段顯示覆寫<xref:System.Windows.Forms.Control.MouseDown>事件的範例。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 下列程式碼片段顯示覆寫<xref:System.Windows.Forms.Control.MouseMove>事件的範例。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 下列程式碼片段顯示覆寫<xref:System.Windows.Forms.Control.MouseUp>事件的範例。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 如需`FlashTrackBar`範例的完整原始程式碼, 請參閱[如何:建立顯示進度](how-to-create-a-windows-forms-control-that-shows-progress.md)的 Windows Forms 控制項。  
  
## <a name="see-also"></a>另請參閱

- [Windows Forms 控制項中的事件](events-in-windows-forms-controls.md)
- [定義事件](defining-an-event-in-windows-forms-controls.md)
- [事件](../../../standard/events/index.md)
- [Windows Forms 中的使用者輸入](../user-input-in-windows-forms.md)
