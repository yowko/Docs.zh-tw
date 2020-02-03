---
title: Button 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- Button
helpviewer_keywords:
- Button control [Windows Forms], about Button control
- buttons [Windows Forms], about buttons
ms.assetid: 255b291b-51a9-4a92-a1a4-2400cd82443f
ms.openlocfilehash: 4ba7b333e5414efb4814d64ce50c55e08b27f859
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747084"
---
# <a name="button-control-overview-windows-forms"></a>Button 控制項概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.Button> 控制項可讓使用者按一下以執行動作。 按一下按鈕時，按鈕看起來就像被推入又釋放。 每當使用者按一下按鈕時，就會叫用 <xref:System.Windows.Forms.Control.Click> 事件處理常式。 您會將程式碼放在 <xref:System.Windows.Forms.Control.Click> 事件處理常式中，以執行您所選擇的任何動作。  
  
 顯示在按鈕上的文字會包含在 [<xref:System.Windows.Forms.Control.Text%2A>] 屬性中。 如果您的文字超過按鈕的寬度，則會換行至下一行。 不過，如果控制項無法容納其整體高度，則會加以裁剪。 如需詳細資訊，請參閱[如何：設定 Windows Forms 控制項所顯示的文字](how-to-set-the-text-displayed-by-a-windows-forms-control.md)。 <xref:System.Windows.Forms.Control.Text%2A> 屬性可以包含存取金鑰，這可讓使用者按下 ALT 鍵與存取金鑰以「按一下」控制項。 如需詳細資訊，請參閱[如何：建立 Windows Forms 控制項的存取金鑰](how-to-create-access-keys-for-windows-forms-controls.md)。 文字的外觀是由 [<xref:System.Windows.Forms.Control.Font%2A>] 屬性和 [<xref:System.Windows.Forms.ButtonBase.TextAlign%2A>] 屬性所控制。  
  
 <xref:System.Windows.Forms.Button> 控制項也可以使用 <xref:System.Windows.Forms.ButtonBase.Image%2A> 和 <xref:System.Windows.Forms.ButtonBase.ImageList%2A> 屬性來顯示影像。 如需詳細資訊，請參閱[如何：設定 Windows Forms 控制項所顯示的影像](how-to-set-the-image-displayed-by-a-windows-forms-control.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Button>
- [操作說明：回應 Windows Forms Button 按一下動作](how-to-respond-to-windows-forms-button-clicks.md)
- [選取 Windows Forms Button 控制項的方法](ways-to-select-a-windows-forms-button-control.md)
- [操作說明：使用設計工具將 Windows Forms 按鈕指定為接受按鈕](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [操作說明：使用設計工具將 Windows Forms 按鈕指定為取消按鈕](designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [Button 控制項](button-control-windows-forms.md)
