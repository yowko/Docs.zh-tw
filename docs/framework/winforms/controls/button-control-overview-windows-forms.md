---
title: Button 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- Button
helpviewer_keywords:
- Button control [Windows Forms], about Button control
- buttons [Windows Forms], about buttons
ms.assetid: 255b291b-51a9-4a92-a1a4-2400cd82443f
ms.openlocfilehash: 505b75d362cea0eddec2b51dc398e2cd8c8d4db8
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713383"
---
# <a name="button-control-overview-windows-forms"></a>Button 控制項概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.Button> 控制項可讓使用者按一下以執行動作。 按一下按鈕時，按鈕看起來就像被推入又釋放。 每當使用者按一下按鈕，<xref:System.Windows.Forms.Control.Click>叫用事件處理常式。 您將程式碼放在<xref:System.Windows.Forms.Control.Click>事件處理常式來執行您所選擇的任何動作。  
  
 在按鈕上顯示的文字包含在<xref:System.Windows.Forms.Control.Text%2A>屬性。 如果您的文字超過按鈕的寬度，它會換行至下一行。 不過，它會裁剪若控制項無法容納其整體的高度。 如需詳細資訊，請參閱[如何：設定所顯示之文字的 Windows Form 控制項](how-to-set-the-text-displayed-by-a-windows-forms-control.md)。 <xref:System.Windows.Forms.Control.Text%2A>屬性可以包含可讓使用者藉由按下 ALT 鍵的存取金鑰取代"click"控制項的存取金鑰。 如需詳細資訊，請參閱[如何：建立 Windows form 控制項的便捷鍵](how-to-create-access-keys-for-windows-forms-controls.md)。 文字的外觀會受到<xref:System.Windows.Forms.Control.Font%2A>屬性和<xref:System.Windows.Forms.ButtonBase.TextAlign%2A>屬性。  
  
 <xref:System.Windows.Forms.Button>控制項也可以顯示使用的映像<xref:System.Windows.Forms.ButtonBase.Image%2A>和<xref:System.Windows.Forms.ButtonBase.ImageList%2A>屬性。 如需詳細資訊，請參閱[如何：設定所顯示的映像的 Windows Form 控制項](how-to-set-the-image-displayed-by-a-windows-forms-control.md)。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.Button>
- [如何：回應 Windows Form Button 按一下動作](how-to-respond-to-windows-forms-button-clicks.md)
- [選取 Windows Forms Button 控制項的方法](ways-to-select-a-windows-forms-button-control.md)
- [如何：將 Windows Form 按鈕指定為接受按鈕使用設計工具](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [如何：將 Windows Form 按鈕指定為取消按鈕使用設計工具](designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [Button 控制項](button-control-windows-forms.md)
