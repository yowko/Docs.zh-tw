---
title: "Introduction to the Line and Shape Controls (Visual Studio) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Line control, overview"
  - "Shape control, overview"
  - "lines, drawing"
  - "shapes, drawing"
ms.assetid: 5c4e8b1a-0733-4020-af6c-f582f4026728
caps.latest.revision: 6
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 6
---
# Introduction to the Line and Shape Controls (Visual Studio)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Visual Basic Power Packs 中的 Line 和 Shape 控制項是一組三種圖形的控制項，可讓您在表單與容器上繪製線條及形狀。  <xref:Microsoft.VisualBasic.PowerPacks.LineShape> 控制項用來繪製水平線、垂直線和對角線。  <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> 控制項用來繪製圓形和橢圓形，而 <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> 控制項用來繪製矩形和正方形。  
  
## Line 和 Shape 控制項  
 Line 和 Shape 控制項封裝了許多包含在 <xref:System.Drawing> 命名空間中的圖形方法，  讓您只要做一個步驟就能完成繪製線條及形狀，而不必建立圖形物件、畫筆與筆刷。  複雜的圖形技巧 \(例如漸層填滿\) 也只要設定一些屬性便能實現。  
  
 雖然也有可能使用圖形方法繪製線條及形狀，但使用 Line 和 Shape 控制項有幾個好處：  
  
-   圖形方法只能在執行階段呼叫。  您可以在設計階段將 Line 和 Shape 控制項加入表單中，  這麼一來，您就能知道圖形的樣子以及並準確定位，您也可以在執行階段加入這些控制項。  
  
-   Line 和 Shape 控制項在執行階段是可選取的，並提供 <xref:Microsoft.VisualBasic.PowerPacks.Shape.Click> 和 <xref:Microsoft.VisualBasic.PowerPacks.Shape.OnDoubleClick%2A> 等事件。  無法選取圖形方法的輸出，而且並未提供事件。  
  
-   Line 和 Shape 控制項提供的 <xref:Microsoft.VisualBasic.PowerPacks.Shape.BringToFront%2A> 及 <xref:Microsoft.VisualBasic.PowerPacks.Shape.SendToBack%2A> 方法，有助於在設計階段與執行階段控制其疊置順序。  圖形方法的疊置順序只能在執行階段透過變更其執行順序來進行控制。  
  
-   Line 和 Shape 控制項是無視窗 \(Windowless\) 控制項，它們沒有視窗控制代碼 \(Window Handle\)，因此使用的系統資源較少。  
  
### 物件模型  
 Line 和 Shape 控制項衍生自 <xref:Microsoft.VisualBasic.PowerPacks.Shape> 基底類別 \(Base Class\)，這個類別會定義它們的共用屬性、方法及事件。  
  
 下圖顯示 Line 和 Shape 物件階層架構。  
  
 ![Line 和 Shape 物件階層架構的圖表](../../../visual-basic/developing-apps/windows-forms/media/lineshapeobject.png "LineShapeObject")  
Line 和 Shape 物件階層架構  
  
 衍生的 <xref:Microsoft.VisualBasic.PowerPacks.LineShape> 類別包含線條特有的屬性、方法及事件。  衍生的 <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape> 類別是 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> 和 <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> 的基底類別；它包含所有形狀通用的屬性、方法及事件。  您也可以從 <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape> 衍生，以建立自己的 `Shape` 控制項。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> 和 <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> 類別可以用來繪製圓形、橢圓形、矩形及圓角矩形。  
  
 當 Line 或 Shape 控制項加入到表單或容器時，會建立不可見的 <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> 物件。  <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> 在容器控制項內為形狀的畫布；每一個 <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> 都有對應的 <xref:Microsoft.VisualBasic.PowerPacks.ShapeCollection>，可讓您逐一查看 Line 和 Shape 控制項。  此外，使用剪貼或拖曳的方式，可以將形狀從一個容器移到另一個容器。  從容器中移除最後一個形狀時，會一併移除 <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer>。  
  
> [!NOTE]
>  並非所有容器控制項都支援 Line 和 Shape 控制項。  您無法在 <xref:System.Windows.Forms.TableLayoutPanel> 或 <xref:System.Windows.Forms.FlowLayoutPanel> 上裝載 Line 和 Shape 控制項。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.PowerPacks>   
 [How to: Draw Lines with the LineShape Control](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)   
 [How to: Draw Shapes with the OvalShape and RectangleShape Controls](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)   
 [How to: Enable Tabbing Between Shapes](../../../visual-basic/developing-apps/windows-forms/how-to-enable-tabbing-between-shapes-visual-studio.md)