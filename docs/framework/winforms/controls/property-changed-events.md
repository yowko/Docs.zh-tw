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
ms.openlocfilehash: d02c6f6f3b5a3add7d78f6c3813a36d08b2b9cb3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54584853"
---
# <a name="property-changed-events"></a>屬性變更事件
如果您想傳送通知時屬性，名為控制項*PropertyName*的變更，定義名為事件*PropertyName* `Changed`和名為`On` *PropertyName* `Changed`引發事件。 在 Windows Form 中的命名慣例是將文字附加*Changed*屬性的名稱。 屬性變更事件的相關聯的事件委派類型是<xref:System.EventHandler>，且事件的資料類型為<xref:System.EventArgs>。 基底類別<xref:System.Windows.Forms.Control>定義許多屬性變更事件，例如<xref:System.Windows.Forms.Control.BackColorChanged>， <xref:System.Windows.Forms.Control.BackgroundImageChanged>， <xref:System.Windows.Forms.Control.FontChanged>， <xref:System.Windows.Forms.Control.LocationChanged>，和其他人。 如需事件的背景資訊，請參閱 <<c0> [ 事件](../../../../docs/standard/events/index.md)並[Windows Forms 控制項中的事件](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)。  
  
 屬性變更事件會很有用，因為它們可讓控制項的取用者，將回應變更的事件處理常式附加。 如果您的控制項需要回應，便會產生屬性變更事件，請覆寫對應`On` *PropertyName* `Changed`方法，而非附加事件的委派。 更新其他屬性，或重新繪製部分或所有其繪圖介面，控制項通常會回應屬性變更事件。  
  
 下列範例示範如何`FlashTrackBar`自訂控制項的回應它所繼承的屬性變更事件的一些<xref:System.Windows.Forms.Control>。 如需完整的範例，請參閱[How to:建立顯示進度的 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#2)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#2)]  
  
## <a name="see-also"></a>另請參閱
- [事件](../../../../docs/standard/events/index.md)
- [Windows Forms 控制項中的事件](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)
- [Windows Forms 控制項中的屬性](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)
