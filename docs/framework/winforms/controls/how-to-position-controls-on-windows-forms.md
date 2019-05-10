---
title: HOW TO：定位 Windows Forms 的控制項
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
ms.openlocfilehash: 241edbe60c327493c9123c6cf7bdc19b7ba2b724
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211644"
---
# <a name="how-to-position-controls-on-windows-forms"></a>HOW TO：定位 Windows Forms 的控制項

若要調整控制項的位置，使用 Visual Studio 中的 Windows Form 設計工具，或者指定<xref:System.Windows.Forms.Control.Location%2A>屬性。

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a>調整 Windows Form 設計工具的設計介面上控制項的位置

在 Visual Studio 中，將控制項拖曳至適當的位置，使用滑鼠。

> [!NOTE]
> 選取的控制項，然後移動它具有箭號將它放在更精確索引鍵。 此外，*對齊線*協助您放置在表單上精確的控制項。 如需詳細資訊，請參閱[逐步解說：排列控制項，在 Windows Form 使用對齊線](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)。

## <a name="position-a-control-using-the-properties-window"></a>使用 [屬性] 視窗將控制項

1. 在 Visual Studio 中，按一下您要放置的控制項。

2. 在 [**屬性**] 視窗中，型別值<xref:System.Windows.Forms.Control.Location%2A>屬性，以逗號分隔，其容器內控制項的位置。

     第一個數字 (X) 是從容器; 左框線的距離第二個數字 (Y) 是從容器工作區，以像素表示上框線的距離。

    > [!NOTE]
    > 您可以展開<xref:System.Windows.Forms.Control.Location%2A>類型的屬性**X**並**Y**個別值。

## <a name="position-a-control-programmatically"></a>以程式設計方式調整控制項的位置

1. 設定<xref:System.Windows.Forms.Control.Location%2A>屬性來控制<xref:System.Drawing.Point>。

    ```vb
    Button1.Location = New Point(100, 100)
    ```

    ```csharp
    button1.Location = new Point(100, 100);
    ```

    ```cpp
    button1->Location = Point(100, 100);
    ```

2. 變更控制項的位置的 X 座標使用<xref:System.Windows.Forms.Control.Left%2A>子屬性。

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

設定<xref:System.Windows.Forms.Control.Left%2A>遞增控制項的 X 座標的子屬性。

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
> 使用<xref:System.Windows.Forms.Control.Location%2A>屬性來設定控制項的 X 和 Y 位置同時。 若要個別設定的位置，使用控制項的<xref:System.Windows.Forms.Control.Left%2A>(**X**) 或<xref:System.Windows.Forms.Control.Top%2A>(**Y**) 子屬性。 請勿嘗試將隱含地設定 X 和 Y 座標<xref:System.Drawing.Point>結構，表示按鈕的位置，因為此結構包含一份按鈕的座標。

## <a name="see-also"></a>另請參閱

- [Windows Forms 控制項](index.md)
- [逐步解說：使用對齊線的 Windows Form 上排列控制項](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [逐步解說：排列 Windows Form 使用 TableLayoutPanel 控制項](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [逐步解說：排列 Windows Form 使用 FlowLayoutPanel 控制項](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [排列 Windows Forms 上的控制項](arranging-controls-on-windows-forms.md)
- [標記個別 Windows Forms 控制項並提供其捷徑](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)
- [依功能區分 Windows Forms 控制項](windows-forms-controls-by-function.md)
- [如何：設定 Windows Form 的畫面位置](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))
