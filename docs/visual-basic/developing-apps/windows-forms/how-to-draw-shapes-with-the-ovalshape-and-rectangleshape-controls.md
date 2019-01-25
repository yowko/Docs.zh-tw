---
title: HOW TO：繪製圖案使用 OvalShape 和 RectangleShape 控制項 (Visual Studio)
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OvalShape control [Visual Basic]
- shapes, drawing
- RectangleShape control [Visual Basic]
ms.assetid: 0275b4c6-7a13-46c8-90f3-61db308c6b5d
ms.openlocfilehash: fe937236332591f6065e618c49ca5cf2c54b987c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701218"
---
# <a name="how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls-visual-studio"></a>HOW TO：繪製圖案使用 OvalShape 和 RectangleShape 控制項 (Visual Studio)
您可以在設計階段和執行階段使用 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> 控制項，在表單或容器上繪製圓形或橢圓形。 您可以使用 <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> 控制項在表單或容器上繪製正方形、矩形或是有圓角的矩形。 您也可以在設計階段和執行階段使用此控制項來繪製圖形。  
  
 您可以藉由變更框線的寬度、色彩和樣式，來自訂圖形的外觀。 圖形的背景預設是透明的；您可以自訂背景以顯示單色、圖樣、漸層填滿 (從一種色彩轉換到另一種色彩) 或影像。  
  
### <a name="to-draw-a-simple-shape-at-design-time"></a>在設計階段繪製簡單圖形  
  
1.  拖曳<xref:Microsoft.VisualBasic.PowerPacks.OvalShape>或<xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>控制從**Visual Basic PowerPacks**索引標籤 (若要安裝，請參閱[Visual Basic Power Packs 控制項](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)) 中**工具箱**至表單或容器控制項。  
  
2.  拖曳調整大小，並移動控點以調整圖形的大小和位置。  
  
     您也可以調整大小，並調整圖形的位置變更`Size`並`Position`中的屬性**屬性**視窗。  
  
     若要建立具有圓角的矩形，請選取`CornerRadius`中的屬性**屬性**視窗並將它設為大於 0 的值。  
  
3.  在 [**屬性**] 視窗中，選擇性地設定其他屬性，來變更圖形的外觀。  
  
### <a name="to-draw-a-simple-shape-at-run-time"></a>在執行階段繪製簡單圖形  
  
1.  在 [專案] 功能表上，按一下 [新增參考]。  
  
2.  在 **加入參考**對話方塊中，選取**Microsoft.VisualBasic.PowerPacks.VS**，然後按一下**確定**。  
  
3.  在 **程式碼編輯器**，新增`Imports`或`using`頂端的模組的陳述式：  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  在 `Event` 程序中加入下列程式碼：  
  
     [!code-csharp[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.cs)]
     [!code-vb[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.vb)]  
  
## <a name="customizing-shapes"></a>自訂圖形  
 使用預設設定時，<xref:Microsoft.VisualBasic.PowerPacks.OvalShape> 和 <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> 控制項會顯示為一個像素寬的實心黑色框線以及透明背景。 藉由設定屬性，可以變更框線的寬度、樣式和色彩。 其他屬性可讓您將圖形的背景變更為單色、圖樣、漸層填滿或影像。  
  
 變更圖形的背景之前，您應該知道數個屬性互動的方式。  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> 屬性設定沒有任何作用，除非 <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> 屬性設定為 <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>。  
  
-   如果 <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> 屬性設定為 <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid>，<xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A> 會覆寫 <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>。  
  
-   如果 <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> 屬性設定為圖樣值 (如 <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Horizontal> 或 <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Vertical>)，圖樣將顯示在 <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A> 中。 背景將會顯示在 <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> 中，條件是 <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> 屬性設定為 <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>。  
  
-   若要顯示漸層填滿，<xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> 屬性必須設定為 <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid>，且 <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillGradientStyle%2A> 屬性必須設定為 <xref:Microsoft.VisualBasic.PowerPacks.FillGradientStyle.None> 以外的值。  
  
-   將 <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackgroundImage%2A> 屬性設定為影像會覆寫所有其他的背景設定。  
  
#### <a name="to-draw-a-circle-that-has-a-custom-border"></a>繪製有自訂框線的圓形  
  
1.  拖曳`OvalShape`控制項從**Visual Basic PowerPacks**索引標籤**工具箱**到表單或容器控制項。  
  
2.  在 [**屬性**] 視窗，請在`Size`屬性，設定`Height`和`Width`為相等的值。  
  
3.  將 `BorderColor` 屬性設定為所要的色彩。  
  
4.  將 `BorderStyle` 屬性設定為 `Solid` 以外的任何值。  
  
5.  將 `BorderWidth` 設定為您想要的大小 (以像素為單位)。  
  
#### <a name="to-draw-a-circle-that-has-a-solid-fill"></a>繪製有實心填滿的圓形  
  
1.  拖曳`OvalShape`控制項從**Visual Basic PowerPacks**索引標籤**工具箱**到表單或容器控制項。  
  
2.  在 [**屬性**] 視窗，請在`Size`屬性，設定`Height`和`Width`為相等的值。  
  
3.  將 `BackColor` 屬性設定為所要的色彩。  
  
4.  將 `BackStyle` 屬性設定為 `Opaque`。  
  
#### <a name="to-draw-a-circle-that-has-a-patterned-fill"></a>繪製有圖樣填滿的圓形  
  
1.  拖曳`OvalShape`控制項從**Visual Basic PowerPacks**索引標籤**工具箱**到表單或容器控制項。  
  
2.  在 [**屬性**] 視窗，請在`Size`屬性，設定`Height`和`Width`為相等的值。  
  
3.  將 `BackColor` 屬性設定為您想要的背景色彩。  
  
4.  將 `BackStyle` 屬性設定為 `Opaque`。  
  
5.  將 `FillColor` 屬性設定為您想要的圖樣色彩。  
  
6.  將 `FillStyle` 屬性設定為 `Transparent` 或 `Solid` 以外的任何值。  
  
#### <a name="to-draw-a-circle-that-has-a-gradient-fill"></a>繪製有漸層填滿的圓形  
  
1.  拖曳`OvalShape`控制項從**Visual Basic PowerPacks**索引標籤**工具箱**到表單或容器控制項。  
  
2.  在 [**屬性**] 視窗，請在`Size`屬性，設定`Height`和`Width`為相等的值。  
  
3.  將 `FillColor` 屬性設定為您想要的開始色彩。  
  
4.  將 `FillGradientColor` 屬性設定為您想要的結束色彩。  
  
5.  將 `FillGradientStyle` 屬性設定為 `None` 以外的任何值。  
  
#### <a name="to-draw-a-circle-that-is-filled-with-an-image"></a>繪製填滿影像的圓形  
  
1.  拖曳`OvalShape`控制項從**Visual Basic PowerPacks**索引標籤**工具箱**到表單或容器控制項。  
  
2.  在 [**屬性**] 視窗，請在`Size`屬性，設定`Height`和`Width`為相等的值。  
  
3.  選取 `BackgroundImage`屬性，然後按一下**省略符號**按鈕 （...）。  
  
4.  在 [**選取資源**] 對話方塊中，選取要顯示的影像。 如果未不列出任何影像資源，請按一下**匯入**瀏覽至影像的位置。  
  
5.  按一下 **確定**插入影像。  
  
## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>
- <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>
- [Line 和 Shape 控制項簡介](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)
- [如何：使用 LineShape 控制項繪製線條](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)
