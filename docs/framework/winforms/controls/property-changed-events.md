---
title: 屬性變更事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- properties [Windows Forms], changes
ms.assetid: 268039ec-5aaa-4d76-b902-acccb036c850
ms.openlocfilehash: cabfd9e799288a332a0b2f96140f5f1cc328508b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755424"
---
# <a name="property-changed-events"></a>屬性變更事件
如果您想傳送通知時屬性，名為控制項*PropertyName*的變更，定義名為事件*PropertyName* `Changed`和名為`On` *PropertyName* `Changed`引發事件。 在 Windows Form 中的命名慣例是將文字附加*Changed*屬性的名稱。 屬性變更事件的相關聯的事件委派類型是<xref:System.EventHandler>，且事件的資料類型為<xref:System.EventArgs>。 基底類別<xref:System.Windows.Forms.Control>定義許多屬性變更事件，例如<xref:System.Windows.Forms.Control.BackColorChanged>， <xref:System.Windows.Forms.Control.BackgroundImageChanged>， <xref:System.Windows.Forms.Control.FontChanged>， <xref:System.Windows.Forms.Control.LocationChanged>，和其他人。 如需事件的背景資訊，請參閱 <<c0> [ 事件](../../../standard/events/index.md)並[Windows Forms 控制項中的事件](events-in-windows-forms-controls.md)。  
  
 屬性變更事件會很有用，因為它們可讓控制項的取用者，將回應變更的事件處理常式附加。 如果您的控制項需要回應，便會產生屬性變更事件，請覆寫對應`On` *PropertyName* `Changed`方法，而非附加事件的委派。 更新其他屬性，或重新繪製部分或所有其繪圖介面，控制項通常會回應屬性變更事件。  
  
 下列範例示範如何`FlashTrackBar`自訂控制項的回應它所繼承的屬性變更事件的一些<xref:System.Windows.Forms.Control>。 如需完整的範例，請參閱[How to:建立顯示進度的 Windows Form 控制項](how-to-create-a-windows-forms-control-that-shows-progress.md)。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#2)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#2)]  
  
## <a name="see-also"></a>另請參閱

- [事件](../../../standard/events/index.md)
- [Windows Forms 控制項中的事件](events-in-windows-forms-controls.md)
- [Windows Forms 控制項中的屬性](properties-in-windows-forms-controls.md)
