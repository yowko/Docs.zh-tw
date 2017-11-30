---
title: "如何：將 Windows Form RadioButton 控制項群組成集合使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 37d8571624272f62c6ce327b0ed25e082c5cf713
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a>如何：將 Windows Form RadioButton 控制項群組成集合使用
Windows Form<xref:System.Windows.Forms.RadioButton>控制項的設計，讓使用者在兩個或多個設定，其中只有一個可以指派給程序或物件之間的選擇。 例如，一群<xref:System.Windows.Forms.RadioButton>控制項可能會顯示各種封裝承運業者寄送的訂單，但是會使用承運業者寄送的其中之一。 因此只有一個<xref:System.Windows.Forms.RadioButton>一次可以選取，即使它是功能群組的一部分。  
  
 選項按鈕群組這類容器內繪製其<xref:System.Windows.Forms.Panel>控制項，<xref:System.Windows.Forms.GroupBox>控制項或表單。 所有選項按鈕，直接加入成為表單的一個群組。 若要加入個別的群組，您必須將它們放面板或群組方塊內。 如需面板或群組方塊的詳細資訊，請參閱[Panel 控制項概觀](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)或[GroupBox 控制項概觀](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md)。  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a>群組為一組函式與其他集無關的 RadioButton 控制項  
  
1.  拖曳<xref:System.Windows.Forms.GroupBox>或<xref:System.Windows.Forms.Panel>控制項從**Windows Form**索引標籤上**工具箱**拖曳至表單。  
  
2.  繪製<xref:System.Windows.Forms.RadioButton>控制項<xref:System.Windows.Forms.GroupBox>或<xref:System.Windows.Forms.Panel>控制項。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.RadioButton>  
 [RadioButton 控制項概觀](../../../../docs/framework/winforms/controls/radiobutton-control-overview-windows-forms.md)  
 [Panel 控制項概觀](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [GroupBox 控制項概觀](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md)  
 [CheckBox 控制項概觀](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [RadioButton 控制項](../../../../docs/framework/winforms/controls/radiobutton-control-windows-forms.md)
