---
title: HOW TO：設定 Windows Forms 的定位順序
ms.date: 03/30/2017
f1_keywords:
- TabStop
- TabIndex
helpviewer_keywords:
- tab order [Windows Forms], controls on Windows forms
- Windows Forms controls, setting tab order
- controls [Windows Forms], setting tab order
- Windows Forms, setting tab order
ms.assetid: 71fa8e76-0472-414b-ad3c-0f90166e0ad7
ms.openlocfilehash: 50f5f91a946aeebc4d82630b25d18d8f8d2ea4be
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59339901"
---
# <a name="how-to-set-the-tab-order-on-windows-forms"></a>HOW TO：設定 Windows Forms 的定位順序
定位順序是以使用者焦點從某個控制項移動到另一個按下 TAB 鍵的順序。 每個表單有它自己的定位順序。 根據預設，定位順序是您可以在其中建立控制項的順序相同。 定位順序編號從 0 開始。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-set-the-tab-order-of-a-control"></a>若要設定控制項的定位順序  
  
1. 在 **檢視**功能表上，按一下**定位順序**。  
  
     這樣會啟動在表單上的定位順序選取模式。 數字 (表示<xref:System.Windows.Forms.Control.TabIndex%2A>屬性) 會出現在每個控制項的左上角。  
  
2. 按一下控制項以循序方式建立您想要的索引標籤順序。  
  
    > [!NOTE]
    >  在定位順序中的控制項位置可以設定為任何值，大於或等於 0。 重複項目發生時，會評估兩個控制項疊置順序，並在最上層控制項定位為第一個。 （圖層順序是沿著表單的 z 軸 [深度] 表單上控制項的視覺分層。 疊置順序會決定哪些控制項其他控制項的前面）。如需有關疊置順序的詳細資訊，請參閱[Windows Forms 上的分層物件](how-to-layer-objects-on-windows-forms.md)。  
  
3. 當您完成時，按一下**定位順序**上**檢視**以離開定位順序模式的功能表。  
  
    > [!NOTE]
    >  無法取得焦點的控制項，以及已停用和不可見的控制項，並沒有<xref:System.Windows.Forms.Control.TabIndex%2A>屬性並不包含在定位順序。 當使用者按下 TAB 鍵，則會略過這些控制項。  
  
 或者，可以設定定位順序中的 [屬性] 視窗使用<xref:System.Windows.Forms.Control.TabIndex%2A>屬性。 <xref:System.Windows.Forms.Control.TabIndex%2A>控制項的屬性會決定其所在的定位順序。 根據預設，已繪製的第一個控制項<xref:System.Windows.Forms.Control.TabIndex%2A>值為 0，第二個具有<xref:System.Windows.Forms.Control.TabIndex%2A>為 1，依此類推。  
  
 此外，根據預設，<xref:System.Windows.Forms.GroupBox>控制項都有它自己<xref:System.Windows.Forms.Control.TabIndex%2A>是整數的值。 A<xref:System.Windows.Forms.GroupBox>控制項本身不能有焦點，在執行階段。 因此，每個控制項內<xref:System.Windows.Forms.GroupBox>有它自己的小<xref:System.Windows.Forms.Control.TabIndex%2A>.0 為開頭的值。 當然，作為<xref:System.Windows.Forms.Control.TabIndex%2A>的<xref:System.Windows.Forms.GroupBox>控制項就會遞增，控制項將會相應地遞增。 如果您變更<xref:System.Windows.Forms.Control.TabIndex%2A>值為 6，5<xref:System.Windows.Forms.Control.TabIndex%2A>其群組中的第一個控制項的值會自動變更到 6.0 中，以此類推。  
  
 定位順序中最後，略過您的表單上的任何控制項。 通常，連續按 TAB 鍵在執行的階段選取定位順序中的每個控制項。 藉由關閉<xref:System.Windows.Forms.Control.TabStop%2A>屬性，您可以進行表單的定位順序中，透過傳遞的控制項。  
  
#### <a name="to-remove-a-control-from-the-tab-order"></a>若要移除的控制項，從定位順序  
  
1. 將控制項的<xref:System.Windows.Forms.Control.TabStop%2A>屬性設`false`屬性 視窗中。  
  
     控制項<xref:System.Windows.Forms.Control.TabStop%2A>屬性已設定為`false`仍保持在定位順序中中的位置，即使當您使用 TAB 鍵循環的控制項時，會略過控制項。  
  
    > [!NOTE]
    >  選項按鈕群組有一個索引標籤停止在執行階段。 [選取] 按鈕 (也就是具有按鈕其<xref:System.Windows.Forms.RadioButton.Checked%2A>屬性設定為`true`) 具有其<xref:System.Windows.Forms.Control.TabStop%2A>屬性會自動設定為`true`，而其他按鈕有其<xref:System.Windows.Forms.Control.TabStop%2A>屬性設定為`false`。 如需有關分組<xref:System.Windows.Forms.RadioButton>控制項，請參閱[當成一組群組 Windows Form RadioButton 控制項](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)。  
  
## <a name="see-also"></a>另請參閱

- [Windows Forms 控制項](index.md)
- [排列 Windows Forms 上的控制項](arranging-controls-on-windows-forms.md)
- [在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)
- [依功能區分 Windows Forms 控制項](windows-forms-controls-by-function.md)
