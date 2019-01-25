---
title: RadioButton 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- RadioButton
helpviewer_keywords:
- RadioButton control [Windows Forms], about RadioButton control
- RadioButton control [Windows Forms], determining state
- radio buttons [Windows Forms], determining state
- radio buttons [Windows Forms], about radio buttons
ms.assetid: cd11f0c2-d098-4022-adf9-1455bc166a13
ms.openlocfilehash: d07fd4028385dac25ae7413a54f72b331ab91eb6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558389"
---
# <a name="radiobutton-control-overview-windows-forms"></a>RadioButton 控制項概觀 (Windows Form)
Windows Form<xref:System.Windows.Forms.RadioButton>控制項呈現給使用者的一組的兩個或多個互斥的選項。 選項按鈕和核取方塊可能看起來運作同樣地，雖然還有一項重要差異： 當使用者選取的選項按鈕，不能也選取相同的群組中的其他選項按鈕。 相反地，您可以選取任意數目的核取方塊。 定義選項按鈕群組會告知使用者，「 此處 」 一組的其中之一，您可以選擇的選項。  
  
## <a name="using-the-control"></a>使用控制項  
 當<xref:System.Windows.Forms.RadioButton>按一下控制項時，其<xref:System.Windows.Forms.RadioButton.Checked%2A>屬性設定為`true`而<xref:System.Windows.Forms.Control.Click>會呼叫事件處理常式。 <xref:System.Windows.Forms.RadioButton.CheckedChanged>就會引發事件時的值<xref:System.Windows.Forms.RadioButton.Checked%2A>屬性變更。 如果<xref:System.Windows.Forms.RadioButton.AutoCheck%2A>屬性設定為`true`（預設值） 時的選項按鈕已選取所有其他群組中會自動清除。 這個屬性通常是只將設定為`false`時驗證程式碼用來確定已選取選項按鈕是允許的選項。 設定控制項中顯示的文字<xref:System.Windows.Forms.Control.Text%2A>屬性，其中可包含的存取金鑰的捷徑。 便捷鍵可讓使用者藉由按下 ALT 鍵的存取金鑰取代 「 按一下 」 控制項。 如需詳細資訊，請參閱[＜How to：建立 Windows form 控制項的便捷鍵](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)和[How to:設定所顯示之文字的 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)。  
  
 <xref:System.Windows.Forms.RadioButton>控制項可以顯示像命令按鈕，如果已壓下，如果選取，會出現<xref:System.Windows.Forms.RadioButton.Appearance%2A>屬性設定為<xref:System.Windows.Forms.Appearance.Button>。 選項按鈕也可以顯示使用的映像<xref:System.Windows.Forms.ButtonBase.Image%2A>和<xref:System.Windows.Forms.ButtonBase.ImageList%2A>屬性。 如需詳細資訊，請參閱[＜How to：設定所顯示的映像的 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md)。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.RadioButton>
- [Panel 控制項概觀](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)
- [GroupBox 控制項概觀](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md)
- [CheckBox 控制項概觀](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)
- [如何：建立 Windows Form 控制項的便捷鍵](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)
- [如何：設定所顯示之文字的 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [如何：群組 Windows Form RadioButton 控制項為一組的函式](../../../../docs/framework/winforms/controls/how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)
- [RadioButton 控制項](../../../../docs/framework/winforms/controls/radiobutton-control-windows-forms.md)
