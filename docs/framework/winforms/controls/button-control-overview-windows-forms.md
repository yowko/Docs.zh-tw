---
title: Button 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- Button
helpviewer_keywords:
- Button control [Windows Forms], about Button control
- buttons [Windows Forms], about buttons
ms.assetid: 255b291b-51a9-4a92-a1a4-2400cd82443f
ms.openlocfilehash: 88255882d3255eff112b9048a906182b64d75084
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526018"
---
# <a name="button-control-overview-windows-forms"></a>Button 控制項概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.Button> 控制項可讓使用者按一下以執行動作。 按一下按鈕時，按鈕看起來就像被推入又釋放。 每當使用者按一下按鈕，<xref:System.Windows.Forms.Control.Click>叫用事件處理常式。 您將程式碼放入<xref:System.Windows.Forms.Control.Click>事件處理常式來執行您所選擇的任何動作。  
  
 在按鈕上顯示的文字包含於<xref:System.Windows.Forms.Control.Text%2A>屬性。 如果您的文字超過按鈕的寬度，它會自動換行至下一行。 不過，它會裁剪若控制項無法容納的整個高度。 如需詳細資訊，請參閱[How to： 設定 Windows Form 控制項所顯示的文字](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)。 <xref:System.Windows.Forms.Control.Text%2A>屬性可以包含便捷鍵可讓使用者控制 「 按一下 」 藉由按下 ALT 鍵及存取金鑰。 如需詳細資訊，請參閱[How to： 建立存取金鑰的 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)。 文字的外觀由<xref:System.Windows.Forms.Control.Font%2A>屬性和<xref:System.Windows.Forms.ButtonBase.TextAlign%2A>屬性。  
  
 <xref:System.Windows.Forms.Button>控制項也可以顯示使用的影像<xref:System.Windows.Forms.ButtonBase.Image%2A>和<xref:System.Windows.Forms.ButtonBase.ImageList%2A>屬性。 如需詳細資訊，請參閱[How to： 設定 Windows Form 控制項所顯示的影像](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.Button>  
 [操作說明：回應 Windows Forms Button 按一下動作](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [選取 Windows Forms Button 控制項的方法](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [操作說明：使用設計工具將 Windows Forms 按鈕指定為接受按鈕](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md)  
 [操作說明：使用設計工具將 Windows Forms 按鈕指定為取消按鈕](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md)  
 [Button 控制項](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
