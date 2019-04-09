---
title: CheckBox 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- CheckBox
helpviewer_keywords:
- CheckBox control [Windows Forms], about CheckBox control
- data binding [Windows Forms], checkbox controls
- check boxes [Windows Forms], about check boxes
ms.assetid: 085a4e0b-9046-473f-b141-d0edddfb2ebb
ms.openlocfilehash: 2a18327d9836d1dbbcd5d5d6e73f217637736d20
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59121783"
---
# <a name="checkbox-control-overview-windows-forms"></a>CheckBox 控制項概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.CheckBox> 控制項表示特定的條件是開啟或關閉。 它通常用來呈現是/否或 True/False 選取項目給使用者。 您可以使用群組中的核取方塊控制項來顯示使用者可以從中選取一個或多個的多重選擇。  
  
 核取方塊控制項是類似於選項按鈕控制項都用來指示使用者所做的選取範圍。 它們之間的差異在於只能有一個選項按鈕群組中的可以選取一次。 與核取方塊控制項，不過，任何數目的核取方塊可能會選取。  
  
 核取方塊可能連接到在資料庫中使用簡單資料繫結的項目。 多個核取方塊可能使用分組<xref:System.Windows.Forms.GroupBox>控制項。 這是視覺外觀以及使用者介面的設計，非常有用，因為群組的控制項可以同時移動表單設計工具上。 如需詳細資訊，請參閱 < [Windows Forms 資料繫結](../windows-forms-data-binding.md)並[GroupBox 控制項](groupbox-control-windows-forms.md)。  
  
 <xref:System.Windows.Forms.CheckBox>控制項有兩個重要屬性，<xref:System.Windows.Forms.CheckBox.Checked%2A>和<xref:System.Windows.Forms.CheckBox.CheckState%2A>。 <xref:System.Windows.Forms.CheckBox.Checked%2A>屬性會傳回`true`或`false`。 <xref:System.Windows.Forms.CheckBox.CheckState%2A>屬性會傳回<xref:System.Windows.Forms.CheckState.Checked>或是<xref:System.Windows.Forms.CheckState.Unchecked>; 或者，如果<xref:System.Windows.Forms.CheckBox.ThreeState%2A>屬性設定為`true`，<xref:System.Windows.Forms.CheckBox.CheckState%2A>也可能會傳回<xref:System.Windows.Forms.CheckState.Indeterminate>。 處於不定狀態，方塊會顯示呈現暗灰色的外觀，以表示無法使用此選項。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.CheckBox>
- [HOW TO：使用 Windows Forms CheckBox 控制項設定選項](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [HOW TO：回應 Windows Forms 核取方塊的按一下動作](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [CheckBox 控制項](checkbox-control-windows-forms.md)
