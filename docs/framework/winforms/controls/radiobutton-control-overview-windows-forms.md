---
title: "RadioButton 控制項概觀 (Windows Form) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RadioButton"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "選項按鈕, 關於選項按鈕"
  - "選項按鈕, 判斷狀態"
  - "RadioButton 控制項 [Windows Form], 關於 RadioButton 控制項"
  - "RadioButton 控制項 [Windows Form], 判斷狀態"
ms.assetid: cd11f0c2-d098-4022-adf9-1455bc166a13
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# RadioButton 控制項概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.RadioButton> 控制項提供使用者一組兩個或多個互斥 \(Mutually Exclusive\) 選項。  選項按鈕和核取方塊的功能雖然類似，但有一個很重要的差異：當使用者選取一個選項按鈕時，便無法選取相同群組中的其他選項按鈕。  相反地，使用者可以選取任何數目的核取方塊。  定義選項按鈕群組就是告訴使用者：「這裡是一組選擇，您只能選擇一個。」  
  
## 使用控制項  
 當按一下 <xref:System.Windows.Forms.RadioButton> 控制項時，就會將它的 <xref:System.Windows.Forms.RadioButton.Checked%2A> 屬性設定為 `true`，同時會呼叫 <xref:System.Windows.Forms.Control.Click> 事件處理常式。  當 <xref:System.Windows.Forms.RadioButton.Checked%2A> 屬性值變更時，則會引發 <xref:System.Windows.Forms.RadioButton.CheckedChanged> 事件。  如果將 <xref:System.Windows.Forms.RadioButton.AutoCheck%2A> 屬性設定為 `true` \(預設值\)，則當選取選項按鈕時，就會自動清除群組中其他所有選項按鈕。  通常只有在使用驗證程式碼來確定選取的選項按鈕是否為允許的選項時，才會將此屬性設定為 `false`。  控制項內顯示的文字是以 <xref:System.Windows.Forms.Control.Text%2A> 屬性來設定，其中可包含便捷鍵 \(Access Key\) 捷徑。  便捷鍵可讓使用者藉由按下 ALT 鍵及便捷鍵來「按一下」其他控制項。  如需詳細資訊，請參閱 [如何：建立 Windows Form 控制項的便捷鍵](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)和 [如何：設定由 Windows Form 控制項所顯示的文字](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)。  
  
 <xref:System.Windows.Forms.RadioButton> 控制項可能出現為命令按鈕，如果已經選取該按鈕，或如果 <xref:System.Windows.Forms.RadioButton.Appearance%2A> 屬性是設定為 <xref:System.Windows.Forms.Appearance>，則按鈕會顯示為已被按下的狀態。  選項按鈕也可以使用 <xref:System.Windows.Forms.ButtonBase.Image%2A> 和 <xref:System.Windows.Forms.ButtonBase.ImageList%2A> 屬性來顯示影像。  如需詳細資訊，請參閱 [如何：設定由 Windows Form 控制項所顯示的影像](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md)。  
  
## 請參閱  
 <xref:System.Windows.Forms.RadioButton>   
 [Panel 控制項概觀](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)   
 [GroupBox 控制項概觀](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md)   
 [CheckBox 控制項概觀](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)   
 [如何：建立 Windows Form 控制項的便捷鍵](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)   
 [如何：設定由 Windows Form 控制項所顯示的文字](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)   
 [如何：將 Windows Form RadioButton 控制項群組成集合使用](../../../../docs/framework/winforms/controls/how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)   
 [RadioButton 控制項](../../../../docs/framework/winforms/controls/radiobutton-control-windows-forms.md)