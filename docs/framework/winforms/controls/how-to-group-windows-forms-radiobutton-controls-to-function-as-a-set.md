---
title: HOW TO：將 Windows Forms RadioButton 控制項分組成函式集
ms.date: 03/30/2017
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
ms.openlocfilehash: 857e61bc89e072aebcf34793d7e8504ece3318c7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59307249"
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a>HOW TO：將 Windows Forms RadioButton 控制項分組成函式集
Windows Form<xref:System.Windows.Forms.RadioButton>控制項的設計，讓使用者在兩個或多個設定，其中只有一個可以指派給程序或物件之間的選擇。 比方說，一群<xref:System.Windows.Forms.RadioButton>控制項可能會顯示各種套件電訊廠商的訂單，但將使用的電訊廠商的其中之一。 因此只有一個<xref:System.Windows.Forms.RadioButton>一次可被選取，即使它是功能群組的一部分。  
  
 您藉由繪製這些容器內這類群組選項按鈕<xref:System.Windows.Forms.Panel>控制項，<xref:System.Windows.Forms.GroupBox>控制項或表單。 所有選項按鈕，會直接新增至表單變成一個群組。 若要新增個別的群組，您必須將它們放在面板或群組方塊內。 如需面板或群組方塊的詳細資訊，請參閱[Panel 控制項概觀](panel-control-overview-windows-forms.md)或是[GroupBox 控制項概觀](groupbox-control-overview-windows-forms.md)。  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a>RadioButton 控制項群組設為獨立於其他組的函式  
  
1. 拖曳<xref:System.Windows.Forms.GroupBox>或是<xref:System.Windows.Forms.Panel>控制從**Windows Forms**索引標籤上**工具箱**拖曳至表單。  
  
2. 繪製<xref:System.Windows.Forms.RadioButton>上的控制項<xref:System.Windows.Forms.GroupBox>或<xref:System.Windows.Forms.Panel>控制項。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.RadioButton>
- [RadioButton 控制項概觀](radiobutton-control-overview-windows-forms.md)
- [Panel 控制項概觀](panel-control-overview-windows-forms.md)
- [GroupBox 控制項概觀](groupbox-control-overview-windows-forms.md)
- [CheckBox 控制項概觀](checkbox-control-overview-windows-forms.md)
- [RadioButton 控制項](radiobutton-control-windows-forms.md)
