---
title: Line 和 Shape 控制項簡介 (Visual Studio)
ms.date: 07/20/2015
helpviewer_keywords:
- Line control [Visual Basic], overview
- Shape control [Visual Basic], overview
- lines, drawing
- shapes, drawing
ms.assetid: 5c4e8b1a-0733-4020-af6c-f582f4026728
ms.openlocfilehash: 3623c2363f39150fd4bb202ba61ebd51df383ca8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54699918"
---
# <a name="introduction-to-the-line-and-shape-controls-visual-studio"></a>Line 和 Shape 控制項簡介 (Visual Studio)
Visual Basic Power Pack 線條和圖案控制項是一組三個圖形化的控制項可讓您在表單和容器上繪製線條和形狀。 <xref:Microsoft.VisualBasic.PowerPacks.LineShape>控制項用來繪製水平、 垂直和對角直線。 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>控制項用來繪製圓形和橢圓形和<xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>控制項用來繪製矩形和正方形。  
  
## <a name="line-and-shape-controls"></a>Line 和 Shape 控制項  
 Line 與 Shape 控制項封裝的許多圖形方法中所包含<xref:System.Drawing>命名空間。 這可讓您在單一步驟中繪製線條和形狀，而不需要建立圖形物件、 畫筆和筆刷。 只要設定一些屬性即可複雜的圖形技術，例如漸層填滿。  
  
 此外，也可以使用圖形方法來繪製線條和形狀，雖然有使用 Line 與 Shape 控制項的數個優點：  
  
-   只有在執行階段，就可以呼叫圖形方法。 Line 與 Shape 控制項可以加入至表單，在設計階段。 這可讓您以查看其外觀，並將它們放置到一樣大。它們也可以在執行階段加入。  
  
-   Line 與 Shape 控制項是可選取在執行階段，提供事件，例如<xref:Microsoft.VisualBasic.PowerPacks.Shape.Click>和<xref:Microsoft.VisualBasic.PowerPacks.Shape.OnDoubleClick%2A>。 圖形方法的輸出不能選取，並不會提供事件。  
  
-   Line 與 Shape 控制項提供<xref:Microsoft.VisualBasic.PowerPacks.Shape.BringToFront%2A>和<xref:Microsoft.VisualBasic.PowerPacks.Shape.SendToBack%2A>可讓您控制他們的疊置順序，在設計階段和執行階段的方法。 可以控制圖形方法疊置順序，只是藉由變更其在執行階段的執行順序。  
  
-   Line 與 Shape 控制項是無視窗控制項;它們有沒有視窗控制代碼，並因此使用較少的系統資源。  
  
### <a name="object-model"></a>物件模型  
 Line 與 Shape 控制項是衍生自基底<xref:Microsoft.VisualBasic.PowerPacks.Shape>定義其共用的屬性、 方法和事件的類別。  
  
 下圖顯示 Line 與 Shape 物件階層架構。  
  
 ![Line 與 Shape 物件階層架構圖表](../../../visual-basic/developing-apps/windows-forms/media/lineshapeobject.png "LineShapeObject")  
Line 與 Shape 物件階層架構  
  
 在衍生<xref:Microsoft.VisualBasic.PowerPacks.LineShape>類別包含屬性、 方法和行特有的事件。 衍生<xref:Microsoft.VisualBasic.PowerPacks.SimpleShape>類別是基底類別<xref:Microsoft.VisualBasic.PowerPacks.OvalShape>和<xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>; 它包含屬性、 方法和事件通用於所有的圖形。 您也可以衍生自<xref:Microsoft.VisualBasic.PowerPacks.SimpleShape>建立您自己`Shape`控制項。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>和<xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>類別可以用來繪製圓形、 橢圓形、 矩形和具有圓角矩形。  
  
 當線條或圖形控制項加入至表單或容器，看不<xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer>建立物件。 <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer>做為畫布，使每個容器控制項中的圖形，每個<xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer>都有對應<xref:Microsoft.VisualBasic.PowerPacks.ShapeCollection>，可讓您逐一查看的 Line 與 Shape 控制項。 您可以移動圖形從一個容器到另一個使用剪下和貼上或拖放。 從容器移除最後一個圖形時<xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer>也會移除。  
  
> [!NOTE]
>  並非所有的容器控制項支援 Line 與 Shape 控制項。 您無法將線條或圖形控制項裝載於<xref:System.Windows.Forms.TableLayoutPanel>或<xref:System.Windows.Forms.FlowLayoutPanel>。  
  
## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualBasic.PowerPacks>
- [如何：使用 LineShape 控制項繪製線條](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)
- [如何：使用 OvalShape 和 RectangleShape 控制項繪製圖案](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)
- [如何：圖案間啟用定位處理](../../../visual-basic/developing-apps/windows-forms/how-to-enable-tabbing-between-shapes-visual-studio.md)
