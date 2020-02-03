---
title: RadioButton 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- RadioButton
helpviewer_keywords:
- RadioButton control [Windows Forms], about RadioButton control
- RadioButton control [Windows Forms], determining state
- radio buttons [Windows Forms], determining state
- radio buttons [Windows Forms], about radio buttons
ms.assetid: cd11f0c2-d098-4022-adf9-1455bc166a13
ms.openlocfilehash: bbc93046b69d39caadde4986ff56f067fc206a9e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741143"
---
# <a name="radiobutton-control-overview-windows-forms"></a>RadioButton 控制項概觀 (Windows Form)
Windows Forms <xref:System.Windows.Forms.RadioButton> 控制項會向使用者呈現兩個或多個互斥選項的集合。 雖然選項按鈕和核取方塊的功能可能類似，但有一項重要的差異：當使用者選取選項按鈕時，也無法選取相同群組中的其他選項按鈕。 相反地，您可以選取任意數目的核取方塊。 定義選項按鈕群組會告訴使用者：「以下是一組可供您選擇的選項，也就是其中之一。」  
  
## <a name="using-the-control"></a>使用控制項  
 按一下 <xref:System.Windows.Forms.RadioButton> 控制項時，其 <xref:System.Windows.Forms.RadioButton.Checked%2A> 屬性會設定為 `true` 並呼叫 <xref:System.Windows.Forms.Control.Click> 事件處理常式。 當 <xref:System.Windows.Forms.RadioButton.Checked%2A> 屬性的值變更時，就會引發 <xref:System.Windows.Forms.RadioButton.CheckedChanged> 事件。 如果 [<xref:System.Windows.Forms.RadioButton.AutoCheck%2A>] 屬性設定為 [`true`] （預設值），則在選取選項按鈕時，會自動清除群組中的所有其他專案。 此屬性通常只有在使用驗證碼來確保選取的選項按鈕是允許的選項時，才會設定為 `false`。 控制項中顯示的文字會以 <xref:System.Windows.Forms.Control.Text%2A> 屬性設定，其中可包含存取金鑰快捷方式。 存取金鑰可讓使用者按下 ALT 鍵與存取金鑰，以「按一下」控制項。 如需詳細資訊，請參閱[如何：建立 Windows Forms 控制項的存取金鑰](how-to-create-access-keys-for-windows-forms-controls.md)和[如何：設定 Windows Forms 控制項所顯示的文字](how-to-set-the-text-displayed-by-a-windows-forms-control.md)。  
  
 如已選取 [<xref:System.Windows.Forms.RadioButton.Appearance%2A>] 屬性設為 [<xref:System.Windows.Forms.Appearance.Button>]，<xref:System.Windows.Forms.RadioButton> 控制項可以像命令按鈕一樣出現。 選項按鈕也可以使用 [<xref:System.Windows.Forms.ButtonBase.Image%2A>] 和 [<xref:System.Windows.Forms.ButtonBase.ImageList%2A> 屬性] 來顯示影像。 如需詳細資訊，請參閱[如何：設定 Windows Forms 控制項所顯示的影像](how-to-set-the-image-displayed-by-a-windows-forms-control.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.RadioButton>
- [Panel 控制項概觀](panel-control-overview-windows-forms.md)
- [GroupBox 控制項概觀](groupbox-control-overview-windows-forms.md)
- [CheckBox 控制項概觀](checkbox-control-overview-windows-forms.md)
- [操作說明：建立 Windows Forms 控制項的便捷鍵](how-to-create-access-keys-for-windows-forms-controls.md)
- [操作說明：設定由 Windows Forms 控制項所顯示的文字](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [操作說明：將 Windows Forms RadioButton 控制項群組成集合使用](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)
- [RadioButton 控制項](radiobutton-control-windows-forms.md)
