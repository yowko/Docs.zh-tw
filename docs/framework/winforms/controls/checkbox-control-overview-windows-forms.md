---
title: CheckBox 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- CheckBox
helpviewer_keywords:
- CheckBox control [Windows Forms], about CheckBox control
- data binding [Windows Forms], checkbox controls
- check boxes [Windows Forms], about check boxes
ms.assetid: 085a4e0b-9046-473f-b141-d0edddfb2ebb
ms.openlocfilehash: b42816cf1bc0ce1ab6db0a2a436b17b0d4370d59
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737102"
---
# <a name="checkbox-control-overview-windows-forms"></a>CheckBox 控制項概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.CheckBox> 控制項表示特定的條件是開啟或關閉。 它通常用來呈現是/否或 True/False 選取項目給使用者。 您可以使用群組中的核取方塊控制項來顯示使用者可以從中選取一個或多個的多重選擇。  
  
 核取方塊控制項類似于選項按鈕控制項，其中每個控制項會用來表示使用者所做的選擇。 兩者不同之處在于，一次只能選取一個群組中的一個選項按鈕。 不過，您可以使用核取方塊控制項，選取任意數目的核取方塊。  
  
 您可以使用簡單的資料系結，將核取方塊連接到資料庫中的元素。 您可以使用 <xref:System.Windows.Forms.GroupBox> 控制項，將多個核取方塊分組。 這適用于視覺外觀，也適用于使用者介面設計，因為群組控制項可以在表單設計工具上四處移動。 如需詳細資訊，請參閱[Windows Forms 資料](../windows-forms-data-binding.md)系結和[分組控制項](groupbox-control-windows-forms.md)。  
  
 <xref:System.Windows.Forms.CheckBox> 控制項有兩個重要的屬性： <xref:System.Windows.Forms.CheckBox.Checked%2A> 和 <xref:System.Windows.Forms.CheckBox.CheckState%2A>。 <xref:System.Windows.Forms.CheckBox.Checked%2A> 屬性會傳回 `true` 或 `false`。 <xref:System.Windows.Forms.CheckBox.CheckState%2A> 屬性會傳回 <xref:System.Windows.Forms.CheckState.Checked> 或 <xref:System.Windows.Forms.CheckState.Unchecked>;或者，如果 <xref:System.Windows.Forms.CheckBox.ThreeState%2A> 屬性設為 `true`，<xref:System.Windows.Forms.CheckBox.CheckState%2A> 也會傳回 <xref:System.Windows.Forms.CheckState.Indeterminate>。 在 [不定] 狀態中，方塊會以暗灰色的外觀顯示，表示無法使用此選項。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.CheckBox>
- [操作說明：使用 Windows Forms CheckBox 控制項設定選項](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [操作說明：回應 Windows Forms CheckBox 按一下動作](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [CheckBox 控制項](checkbox-control-windows-forms.md)
