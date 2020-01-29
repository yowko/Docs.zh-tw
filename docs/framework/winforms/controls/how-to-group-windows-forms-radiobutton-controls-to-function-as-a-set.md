---
title: 將選項按鈕控制項當做一組來運作
ms.date: 03/30/2017
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
ms.openlocfilehash: c4b37c84bf0f93837b91c743c7681d39fd83a659
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732947"
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a>如何：將 Windows Form RadioButton 控制項群組成集合使用
Windows Forms <xref:System.Windows.Forms.RadioButton> 控制項的設計目的是要讓使用者在兩個或多個設定之間做選擇，其中只有一個可以指派給程式或物件。 例如，一組 <xref:System.Windows.Forms.RadioButton> 控制項可能會顯示訂單的套件選擇項，但只會使用其中一個電信公司。 因此，一次只能選取一個 <xref:System.Windows.Forms.RadioButton>，即使它是功能群組的一部分也一樣。  
  
 您可以藉由在容器（例如 <xref:System.Windows.Forms.Panel> 控制項、<xref:System.Windows.Forms.GroupBox> 控制項或表單）內繪製來分組選項按鈕。 直接新增至表單的所有選項按鈕都會變成一個群組。 若要加入不同的群組，您必須將它們放在面板或群組方塊中。 如需面板或群組方塊的詳細資訊，請參閱[面板控制項總覽](panel-control-overview-windows-forms.md)或[分組控制項總覽](groupbox-control-overview-windows-forms.md)。  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a>將選項按鈕控制群組成群組，以獨立于其他集合運作  
  
1. 將 <xref:System.Windows.Forms.GroupBox> 或 <xref:System.Windows.Forms.Panel> 控制項從 [**工具箱**] 的 [ **Windows Forms** ] 索引標籤拖曳到表單上。  
  
2. 在 <xref:System.Windows.Forms.GroupBox> 或 <xref:System.Windows.Forms.Panel> 控制項上繪製 <xref:System.Windows.Forms.RadioButton> 控制項。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.RadioButton>
- [RadioButton 控制項概觀](radiobutton-control-overview-windows-forms.md)
- [Panel 控制項概觀](panel-control-overview-windows-forms.md)
- [GroupBox 控制項概觀](groupbox-control-overview-windows-forms.md)
- [CheckBox 控制項概觀](checkbox-control-overview-windows-forms.md)
- [RadioButton 控制項](radiobutton-control-windows-forms.md)
