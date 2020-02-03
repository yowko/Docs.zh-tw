---
title: 位置控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Location
- Location.Y
- Location.X
helpviewer_keywords:
- controls [Windows Forms]
- controls [Windows Forms], moving
- snaplines
- controls [Windows Forms], positioning
ms.assetid: 4693977e-34a4-4f19-8221-68c3120c2b2b
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 144a0021c74f0fb5afec1d511315168fb28528e9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735907"
---
# <a name="how-to-position-controls-on-windows-forms"></a>如何：在 Windows Forms 上放置控制項

若要定位控制項，請使用 Visual Studio 中的 Windows Form 設計工具，或指定 <xref:System.Windows.Forms.Control.Location%2A> 屬性。

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a>將控制項放在 Windows Form 設計工具的設計介面上

在 Visual Studio 中，使用滑鼠將控制項拖曳至適當的位置。

> [!NOTE]
> 選取控制項，並使用方向鍵將它移動，以更精確地定位。 此外，*對齊線*可協助您精確地將控制項放在表單上。 如需詳細資訊，請參閱[逐步解說：使用對齊線排列 Windows Forms 上的控制項](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)。

## <a name="position-a-control-using-the-properties-window"></a>使用屬性視窗放置控制項

1. 在 Visual Studio 中，選取您想要放置的控制項。

2. 在 [**屬性**] 視窗中，輸入 <xref:System.Windows.Forms.Control.Location%2A> 屬性的值（以逗號分隔），將控制項放在其容器內。

   第一個數位（X）是與容器左邊框線之間的距離;第二個數字（Y）是距容器區域上框線的距離，以圖元為單位。

   > [!NOTE]
   > 您可以展開 [<xref:System.Windows.Forms.Control.Location%2A>] 屬性，以個別輸入**X**和**Y**值。

## <a name="position-a-control-programmatically"></a>以程式設計方式放置控制項

1. 將控制項的 [<xref:System.Windows.Forms.Control.Location%2A>] 屬性設定為 [<xref:System.Drawing.Point>]。

    ```vb
    Button1.Location = New Point(100, 100)
    ```

    ```csharp
    button1.Location = new Point(100, 100);
    ```

    ```cpp
    button1->Location = Point(100, 100);
    ```

2. 使用 <xref:System.Windows.Forms.Control.Left%2A> 子屬性變更控制項位置的 X 座標。

    ```vb
    Button1.Left = 300
    ```

    ```csharp
    button1.Left = 300;
    ```

    ```cpp
    button1->Left = 300;
    ```

## <a name="increment-a-controls-location-programmatically"></a>以程式設計方式遞增控制項的位置

設定 <xref:System.Windows.Forms.Control.Left%2A> 子屬性，以遞增控制項的 X 座標。

```vb
Button1.Left += 200
```

```csharp
button1.Left += 200;
```

```cpp
button1->Left += 200;
```

> [!NOTE]
> 使用 [<xref:System.Windows.Forms.Control.Location%2A>] 屬性，同時設定控制項的 X 和 Y 位置。 若要個別設定位置，請使用控制項的 [<xref:System.Windows.Forms.Control.Left%2A> （**X**）] 或 [<xref:System.Windows.Forms.Control.Top%2A> （**Y**）] 子屬性。 請勿嘗試隱含地設定代表按鈕位置之 <xref:System.Drawing.Point> 結構的 X 和 Y 座標，因為此結構包含按鈕座標的複本。

## <a name="see-also"></a>另請參閱

- [Windows Forms 控制項](index.md)
- [逐步解說：使用對齊線排列 Windows Forms 上的控制項](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [逐步解說：使用 TableLayoutPanel 排列 Windows Forms 上的控制項](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [逐步解說：使用 FlowLayoutPanel 排列 Windows Forms上的控制項](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [標記個別 Windows Forms 控制項並提供其捷徑](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)
- [依功能區分 Windows Forms 控制項](windows-forms-controls-by-function.md)
- [如何：設定 Windows Forms 的螢幕位置](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))
