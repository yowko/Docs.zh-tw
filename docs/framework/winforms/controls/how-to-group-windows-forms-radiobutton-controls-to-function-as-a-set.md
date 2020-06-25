---
title: 將選項按鈕控制項當做一組來運作
description: 瞭解如何將 Windows Forms 選項按鈕控制項分組，以獨立于其他集合運作。
ms.date: 03/30/2017
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
ms.openlocfilehash: 9f6795330922e739cca1f2b5c11bb2ec68bb4e84
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325925"
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a>如何：將 Windows Form RadioButton 控制項群組成集合使用
Windows Forms <xref:System.Windows.Forms.RadioButton> 控制項的設計目的是要讓使用者在兩個或多個設定之間做選擇，其中只有一個可以指派給程式或物件。 例如，一組 <xref:System.Windows.Forms.RadioButton> 控制項可能會顯示訂單的套件的選擇，但只會使用其中一個電信公司。 因此 <xref:System.Windows.Forms.RadioButton> ，一次只能選取一個，即使它是功能群組的一部分也一樣。  
  
 在 <xref:System.Windows.Forms.Panel> 控制項、 <xref:System.Windows.Forms.GroupBox> 控制項或表單之類的容器內繪製選項按鈕，即可將其分組。 直接新增至表單的所有選項按鈕都會變成一個群組。 若要加入不同的群組，您必須將它們放在面板或群組方塊中。 如需面板或群組方塊的詳細資訊，請參閱[面板控制項總覽](panel-control-overview-windows-forms.md)或[分組控制項總覽](groupbox-control-overview-windows-forms.md)。  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a>將選項按鈕控制群組成群組，以獨立于其他集合運作  
  
1. 從 [ <xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Panel> **工具箱**] 的 [ **Windows Forms** ] 索引標籤，將或控制項拖曳到表單上。  
  
2. <xref:System.Windows.Forms.RadioButton>在或控制項上繪製控制項 <xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Panel> 。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.RadioButton>
- [RadioButton 控制項概觀](radiobutton-control-overview-windows-forms.md)
- [Panel 控制項概觀](panel-control-overview-windows-forms.md)
- [GroupBox 控制項概觀](groupbox-control-overview-windows-forms.md)
- [CheckBox 控制項概觀](checkbox-control-overview-windows-forms.md)
- [RadioButton 控制項](radiobutton-control-windows-forms.md)
