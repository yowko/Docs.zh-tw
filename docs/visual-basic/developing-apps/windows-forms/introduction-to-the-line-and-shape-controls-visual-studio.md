---
title: Line 和 Shape 控制項簡介 (Visual Studio)
ms.date: 07/20/2015
helpviewer_keywords:
- Line control [Visual Basic], overview
- Shape control [Visual Basic], overview
- lines, drawing
- shapes, drawing
ms.assetid: 5c4e8b1a-0733-4020-af6c-f582f4026728
ms.openlocfilehash: 3ad740f7dd15194830959a5493970b4ba54ce142
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="introduction-to-the-line-and-shape-controls-visual-studio"></a>Line 和 Shape 控制項簡介 (Visual Studio)
Visual Basic Power Pack 線條和圖案控制項是一組可讓您在表單和容器上繪製線條和形狀的三個圖形化控制項。 <xref:Microsoft.VisualBasic.PowerPacks.LineShape>控制項用來繪製水平、 垂直和對角線線條。 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>控制項用來繪製圓形和橢圓形，而<xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>控制項用來繪製的矩形和正方形。  
  
## <a name="line-and-shape-controls"></a>Line 和 Shape 控制項  
 Line 和 Shape 控制項封裝的圖形方法中所包含的許多<xref:System.Drawing>命名空間。 這可讓您在單一步驟中繪製線條與圖形，而不需要建立圖形物件，畫筆和筆刷。 複雜圖形技術，例如漸層填滿可藉由直接設定某些屬性。  
  
 此外，也可以使用圖形方法來繪製線條和形狀，雖然有使用線條和圖案控制項的數個優點：  
  
-   可以呼叫圖形方法只能在執行階段。 在設計階段時，可以加入線條和圖案控制項的表單。 這可讓您若要查看其外觀及位置一樣大。它們也可以加入在執行階段。  
  
-   Line 和 Shape 控制項可在執行階段選取，提供的事件，例如<xref:Microsoft.VisualBasic.PowerPacks.Shape.Click>和<xref:Microsoft.VisualBasic.PowerPacks.Shape.OnDoubleClick%2A>。 圖形方法的輸出不能選取，並不提供事件。  
  
-   Line 和 Shape 控制項提供<xref:Microsoft.VisualBasic.PowerPacks.Shape.BringToFront%2A>和<xref:Microsoft.VisualBasic.PowerPacks.Shape.SendToBack%2A>可讓您控制他們的疊置順序，在設計階段和執行階段方法。 可以控制圖形方法疊置順序，只是藉由變更其在執行階段的執行順序。  
  
-   線條和圖案控制項是無視窗控制項。它們有沒有任何視窗控制代碼，因此使用較少的系統資源。  
  
### <a name="object-model"></a>物件模型  
 Line 和 Shape 控制項衍生自基底<xref:Microsoft.VisualBasic.PowerPacks.Shape>類別來定義其共用的屬性、 方法和事件。  
  
 下圖顯示 Line 和 Shape 物件階層架構。  
  
 ![Line 和 Shape 物件階層架構圖表](../../../visual-basic/developing-apps/windows-forms/media/lineshapeobject.png "LineShapeObject")  
Line 和 Shape 物件階層架構  
  
 在衍生<xref:Microsoft.VisualBasic.PowerPacks.LineShape>類別包含屬性、 方法和事件都是唯一的各行。 在衍生<xref:Microsoft.VisualBasic.PowerPacks.SimpleShape>類別是基底類別<xref:Microsoft.VisualBasic.PowerPacks.OvalShape>和<xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>; 它包含屬性、 方法和事件通用於所有形狀。 您也可以衍生自<xref:Microsoft.VisualBasic.PowerPacks.SimpleShape>自行建立`Shape`控制項。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>和<xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>類別可以用來繪製圓形、 橢圓形、 矩形和具有圓角矩形。  
  
 當加入線條或圖形控制項在表單或容器，隱藏<xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer>建立物件。 <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer>做為每個容器控制項中的圖形畫布; 每一個<xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer>都有對應<xref:Microsoft.VisualBasic.PowerPacks.ShapeCollection>，可讓您逐一查看 Line 和 Shape 控制項。 您可以移動圖形從一個容器到另一個使用剪下和貼上或透過拖放。 從容器中，移除最後一個圖形時<xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer>也會移除。  
  
> [!NOTE]
>  並非所有的容器控制項支援線條和圖案控制項。 您無法將裝載線條或圖形控制項上<xref:System.Windows.Forms.TableLayoutPanel>或<xref:System.Windows.Forms.FlowLayoutPanel>。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.PowerPacks>  
 [操作說明：使用 LineShape 控制項繪製線條](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)  
 [操作說明：使用 OvalShape 和 RectangleShape 控制項繪製圖案](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)  
 [操作說明：在圖案間啟用定位停駐點](../../../visual-basic/developing-apps/windows-forms/how-to-enable-tabbing-between-shapes-visual-studio.md)
