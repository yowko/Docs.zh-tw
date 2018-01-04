---
title: "RadioButton 控制項概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: RadioButton
helpviewer_keywords:
- RadioButton control [Windows Forms], about RadioButton control
- RadioButton control [Windows Forms], determining state
- radio buttons [Windows Forms], determining state
- radio buttons [Windows Forms], about radio buttons
ms.assetid: cd11f0c2-d098-4022-adf9-1455bc166a13
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 67befd973dec38628f97a0d3153c399d48c18305
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="radiobutton-control-overview-windows-forms"></a>RadioButton 控制項概觀 (Windows Form)
Windows Form<xref:System.Windows.Forms.RadioButton>控制項向使用者顯示一組兩個或多個互斥。 選項按鈕和核取方塊看起來可能類似函式，而是一項重要差異： 無法選取以及當使用者選取選項按鈕，在相同群組中的其他選項按鈕。 相反地，您可以選取任意數目的核取方塊。 定義選項按鈕群組會告知使用者，"以下是選擇其中之一，您可以選擇一組 」。  
  
## <a name="using-the-control"></a>使用控制項  
 當<xref:System.Windows.Forms.RadioButton>按一下控制項時，其<xref:System.Windows.Forms.RadioButton.Checked%2A>屬性設定為`true`和<xref:System.Windows.Forms.Control.Click>會呼叫事件處理常式。 <xref:System.Windows.Forms.RadioButton.CheckedChanged>就會引發事件時的值<xref:System.Windows.Forms.RadioButton.Checked%2A>屬性變更。 如果<xref:System.Windows.Forms.RadioButton.AutoCheck%2A>屬性設定為`true`（預設值），當選取選項按鈕，所有其他群組中會自動清除。 這個屬性通常是只將設定為`false`時驗證程式碼用來確定已選取的選項按鈕是允許的選項。 設定在控制項中顯示的文字<xref:System.Windows.Forms.Control.Text%2A>屬性，可包含存取金鑰的捷徑。 便捷鍵可讓使用者控制 「 按一下 」 藉由按下 ALT 鍵及存取金鑰。 如需詳細資訊，請參閱[How to： 建立存取金鑰的 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)和[How to： 設定 Windows Form 控制項所顯示的文字](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)。  
  
 <xref:System.Windows.Forms.RadioButton>控制項可以看起來像是命令按鈕，如果已經選取，如果壓下<xref:System.Windows.Forms.RadioButton.Appearance%2A>屬性設定為<xref:System.Windows.Forms.Appearance.Button>。 選項按鈕也可以顯示使用的影像<xref:System.Windows.Forms.ButtonBase.Image%2A>和<xref:System.Windows.Forms.ButtonBase.ImageList%2A>屬性。 如需詳細資訊，請參閱[How to： 設定 Windows Form 控制項所顯示的影像](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.RadioButton>  
 [Panel 控制項概觀](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [GroupBox 控制項概觀](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md)  
 [CheckBox 控制項概觀](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [操作說明：建立 Windows Forms 控制項的便捷鍵](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)  
 [操作說明：設定由 Windows Forms 控制項所顯示的文字](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [操作說明：將 Windows Forms RadioButton 控制項群組成集合使用](../../../../docs/framework/winforms/controls/how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)  
 [RadioButton 控制項](../../../../docs/framework/winforms/controls/radiobutton-control-windows-forms.md)
