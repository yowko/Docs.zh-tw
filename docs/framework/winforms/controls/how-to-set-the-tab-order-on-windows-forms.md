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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8a0a1c76b996f10de0ca963c5d8bdc2325a3f6b6
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987101"
---
# <a name="how-to-set-the-tab-order-on-windows-forms"></a>HOW TO：在 Windows Forms 上設定定位順序

定位順序是使用者按下 Tab 鍵將焦點從一個控制項移至另一個控制項的順序。 每個表單都有自己的定位順序。 根據預設, 定位順序與您建立控制項的順序相同。 定位字元順序編號的開頭為零。

## <a name="to-set-the-tab-order-of-a-control"></a>設定控制項的定位順序

1. 在 Visual Studio 的 [ **View** ] 功能表上, 選取 [定位**順序]** 。

   這會啟動表單上的索引標籤順序選取模式。 數位 (代表<xref:System.Windows.Forms.Control.TabIndex%2A>屬性) 會出現在每個控制項的左上角。

2. 依序按一下控制項, 以建立您想要的定位順序。

   > [!NOTE]
   > 控制項在定位順序內的位置可以設定為任何大於或等於0的值。 發生重複時, 會評估這兩個控制項的迭置順序, 並將頂端的控制項設為優先。 ([迭置順序] 是表單上控制項的視覺分層, 沿著表單的 Z 軸 [深度]。 迭置順序會決定哪些控制項位於其他控制項前面)。如需有關迭置順序的詳細資訊, 請參閱[Windows Forms 上的分層物件](how-to-layer-objects-on-windows-forms.md)。

3. 當您完成時, 請再次選取 [ **View** ] 功能表上的 [定位**順序]** , 離開定位順序模式。

   > [!NOTE]
   > 無法取得焦點的控制項, 以及停用和隱藏的控制項<xref:System.Windows.Forms.Control.TabIndex%2A>都沒有屬性, 而且不會包含在定位順序中。 當使用者按下 Tab 鍵時, 會略過這些控制項。

或者, 您可以使用<xref:System.Windows.Forms.Control.TabIndex%2A>屬性, 在屬性視窗中設定定位順序。 控制項<xref:System.Windows.Forms.Control.TabIndex%2A>的屬性會決定它在定位順序中的位置。 根據預設, 第一個繪製<xref:System.Windows.Forms.Control.TabIndex%2A>的控制項的值為 0, 第二個<xref:System.Windows.Forms.Control.TabIndex%2A>則為 1, 依此類推。

此外, 根據預設, <xref:System.Windows.Forms.GroupBox>控制項有自己<xref:System.Windows.Forms.Control.TabIndex%2A>的值, 也就是整數。 <xref:System.Windows.Forms.GroupBox>控制項本身在執行時間不能有焦點。 因此, 中的<xref:System.Windows.Forms.GroupBox>每個控制項都有自己的十進位<xref:System.Windows.Forms.Control.TabIndex%2A>值, 從. 0 開始。 自然地, 隨著<xref:System.Windows.Forms.Control.TabIndex%2A> <xref:System.Windows.Forms.GroupBox>控制項的遞增, 其內的控制項也會遞增。 如果您將<xref:System.Windows.Forms.Control.TabIndex%2A>值從5變更為 6 <xref:System.Windows.Forms.Control.TabIndex%2A> , 則其群組中第一個控制項的值會自動變更為 6.0, 依此類推。

最後, 您可以在定位順序中略過許多表單上的任何控制項。 通常, 在執行時間連續按 Tab 鍵, 會選取定位順序中的每個控制項。 藉由關閉屬性, 您可以讓控制項在表單的定位順序中傳遞。 <xref:System.Windows.Forms.Control.TabStop%2A>

## <a name="to-remove-a-control-from-the-tab-order"></a>若要從定位順序中移除控制項

在 [**屬性**] <xref:System.Windows.Forms.Control.TabStop%2A>視窗中, 將控制項的屬性設定為 [ **false** ]。

其<xref:System.Windows.Forms.Control.TabStop%2A>屬性已設定為`false`的控制項, 仍然會在定位順序中維持其位置, 即使在使用 tab 鍵迴圈流覽控制項時略過控制項也一樣。

> [!NOTE]
> 選項按鈕群組在執行時間會有一個定位停駐點。 選取的按鈕 (也就<xref:System.Windows.Forms.RadioButton.Checked%2A>是其屬性設為`true`的按鈕) 會自動將<xref:System.Windows.Forms.Control.TabStop%2A>其屬性設<xref:System.Windows.Forms.Control.TabStop%2A>為`true`, 而其他按鈕的屬性會設定為`false`。 如需群組<xref:System.Windows.Forms.RadioButton>控制項的詳細資訊, 請參閱[群組 Windows Forms 選項按鈕控制項以作為集合](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)。

## <a name="see-also"></a>另請參閱

- [Windows Forms 控制項](index.md)
- [在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)
- [依功能區分 Windows Forms 控制項](windows-forms-controls-by-function.md)
