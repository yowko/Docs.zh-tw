---
title: HOW TO：錨定 Windows Forms 上的控制項
ms.date: 03/30/2017
helpviewer_keywords:
- Anchor property [Windows Forms], enabling resizable forms
- Windows Forms controls, screen resolutions
- resizing forms [Windows Forms]
- Windows Forms controls, size
- screen resolution and control display
- controls [Windows Forms], anchoring
- forms [Windows Forms], resizing
- Windows Forms, resizing
- controls [Windows Forms], positioning
ms.assetid: 59ea914f-fbd3-427a-80fe-decd02f7ae6d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 94fa6fe90e5583a3bfecf376af59d53f6d8528af
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987496"
---
# <a name="how-to-anchor-controls-on-windows-forms"></a>HOW TO：Windows Forms 上的錨定控制項

如果您要設計一個表單, 讓使用者可以在執行時間調整其大小, 您的表單上的控制項應該會調整大小並正確重新置放。 若要使用表單動態調整控制項大小, 您可以<xref:System.Windows.Forms.Control.Anchor%2A>使用 Windows Forms 控制項的屬性。 <xref:System.Windows.Forms.Control.Anchor%2A>屬性會定義控制項的錨點位置。 當控制項錨定至表單, 且表單已調整大小時, 控制項會維持控制項與錨點位置之間的距離。 例如, 如果您<xref:System.Windows.Forms.TextBox>的控制項已錨定至表單的左、右和下邊緣, 則當表單調整大小時<xref:System.Windows.Forms.TextBox> , 控制項會水準調整大小, 讓它維持與表單右邊和左側相同的距離。 此外, 控制項的位置會垂直, 使其位置一律與表單下邊緣的距離相同。 如果控制項未錨定, 而表單已調整大小, 則控制項相對於表單邊緣的位置會變更。

<xref:System.Windows.Forms.Control.Anchor%2A>屬性會<xref:System.Windows.Forms.Control.AutoSize%2A>與屬性互動。 如需詳細資訊, 請參閱[AutoSize 屬性總覽](autosize-property-overview.md)。

## <a name="anchor-a-control-on-a-form"></a>錨定表單上的控制項

1. 在 Visual Studio 中, 選取您要錨定的控制項。

    > [!NOTE]
    > 您可以按下 CTRL 鍵, 按一下每個控制項來選取它, 然後遵循此程式的其餘部分, 以同時錨定多個控制項。

2. 在 [**屬性**] 視窗中, 按一下<xref:System.Windows.Forms.Control.Anchor%2A>屬性右邊的箭號。

     隨即顯示一個顯示交叉的編輯器。

3. 若要設定錨點, 請按一下交叉的頂端、左側、右側或底部區段。

     控制項預設會錨定到頂端和左側。

4. 若要清除已錨定之控制項的側邊, 請按一下 [交叉] 的 arm。

5. 若要關閉<xref:System.Windows.Forms.Control.Anchor%2A>屬性編輯器, 請再次<xref:System.Windows.Forms.Control.Anchor%2A>按一下屬性名稱。

當您的表單在執行時間顯示時, 控制項會調整大小以維持與表單邊緣相同的距離。 距錨定邊緣的距離一律會與控制項位於 Windows Form 設計工具中時所定義的距離保持相同。

> [!NOTE]
> 某些控制項 (例如<xref:System.Windows.Forms.ComboBox>控制項) 具有其高度的限制。 將控制項錨定到其表單或容器的底部, 無法強制控制項超過其高度限制。

繼承的控制項必須`Protected`能夠錨定。 若要變更控制項的存取層級, 請在`Modifiers` [**屬性**] 視窗中設定其屬性。

## <a name="see-also"></a>另請參閱

- [Windows Forms 控制項](index.md)
- [AutoSize 屬性概觀](autosize-property-overview.md)
- [如何：將控制項停駐在 Windows Forms](how-to-dock-controls-on-windows-forms.md)
- [逐步解說：使用 FlowLayoutPanel 排列 Windows Forms 上的控制項](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [逐步解說：使用 TableLayoutPanel 排列 Windows Forms 上的控制項](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [逐步解說：配置具有填補、邊界和 AutoSize 屬性的 Windows Forms 控制項](windows-forms-controls-padding-autosize.md)
