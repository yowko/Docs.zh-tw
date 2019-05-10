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
# <a name="how-to-position-controls-on-windows-forms"></a><span data-ttu-id="b08ff-102">HOW TO：定位 Windows Forms 的控制項</span><span class="sxs-lookup"><span data-stu-id="b08ff-102">How to: Position Controls on Windows Forms</span></span>

<span data-ttu-id="b08ff-103">若要調整控制項的位置，使用 Visual Studio 中的 Windows Form 設計工具，或者指定<xref:System.Windows.Forms.Control.Location%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="b08ff-103">To position controls, use the Windows Forms Designer in Visual Studio or specify the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a><span data-ttu-id="b08ff-104">調整 Windows Form 設計工具的設計介面上控制項的位置</span><span class="sxs-lookup"><span data-stu-id="b08ff-104">Position a control on the design surface of the Windows Forms Designer</span></span>

<span data-ttu-id="b08ff-105">在 Visual Studio 中，將控制項拖曳至適當的位置，使用滑鼠。</span><span class="sxs-lookup"><span data-stu-id="b08ff-105">In Visual Studio, drag the control to the appropriate location with the mouse.</span></span>

> [!NOTE]
> <span data-ttu-id="b08ff-106">選取的控制項，然後移動它具有箭號將它放在更精確索引鍵。</span><span class="sxs-lookup"><span data-stu-id="b08ff-106">Select the control and move it with the ARROW keys to position it more precisely.</span></span> <span data-ttu-id="b08ff-107">此外，*對齊線*協助您放置在表單上精確的控制項。</span><span class="sxs-lookup"><span data-stu-id="b08ff-107">Also, *snaplines* assist you in placing controls precisely on your form.</span></span> <span data-ttu-id="b08ff-108">如需詳細資訊，請參閱[逐步解說：排列控制項，在 Windows Form 使用對齊線](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)。</span><span class="sxs-lookup"><span data-stu-id="b08ff-108">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>

## <a name="position-a-control-using-the-properties-window"></a><span data-ttu-id="b08ff-109">使用 [屬性] 視窗將控制項</span><span class="sxs-lookup"><span data-stu-id="b08ff-109">Position a control using the Properties window</span></span>

1. <span data-ttu-id="b08ff-110">在 Visual Studio 中，按一下您要放置的控制項。</span><span class="sxs-lookup"><span data-stu-id="b08ff-110">In Visual Studio, click the control you want to position.</span></span>

2. <span data-ttu-id="b08ff-111">在 [**屬性**] 視窗中，型別值<xref:System.Windows.Forms.Control.Location%2A>屬性，以逗號分隔，其容器內控制項的位置。</span><span class="sxs-lookup"><span data-stu-id="b08ff-111">In the **Properties** window, type values for the <xref:System.Windows.Forms.Control.Location%2A> property, separated by a comma, to position the control within its container.</span></span>

     <span data-ttu-id="b08ff-112">第一個數字 (X) 是從容器; 左框線的距離第二個數字 (Y) 是從容器工作區，以像素表示上框線的距離。</span><span class="sxs-lookup"><span data-stu-id="b08ff-112">The first number (X) is the distance from the left border of the container; the second number (Y) is the distance from the upper border of the container area, measured in pixels.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b08ff-113">您可以展開<xref:System.Windows.Forms.Control.Location%2A>類型的屬性**X**並**Y**個別值。</span><span class="sxs-lookup"><span data-stu-id="b08ff-113">You can expand the <xref:System.Windows.Forms.Control.Location%2A> property to type the **X** and **Y** values individually.</span></span>

## <a name="position-a-control-programmatically"></a><span data-ttu-id="b08ff-114">以程式設計方式調整控制項的位置</span><span class="sxs-lookup"><span data-stu-id="b08ff-114">Position a control programmatically</span></span>

1. <span data-ttu-id="b08ff-115">設定<xref:System.Windows.Forms.Control.Location%2A>屬性來控制<xref:System.Drawing.Point>。</span><span class="sxs-lookup"><span data-stu-id="b08ff-115">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the control to a <xref:System.Drawing.Point>.</span></span>

    ```vb
    Button1.Location = New Point(100, 100)
    ```

    ```csharp
    button1.Location = new Point(100, 100);
    ```

    ```cpp
    button1->Location = Point(100, 100);
    ```

2. <span data-ttu-id="b08ff-116">變更控制項的位置的 X 座標使用<xref:System.Windows.Forms.Control.Left%2A>子屬性。</span><span class="sxs-lookup"><span data-stu-id="b08ff-116">Change the X coordinate of the control's location using the <xref:System.Windows.Forms.Control.Left%2A> subproperty.</span></span>

    ```vb
    Button1.Left = 300
    ```

    ```csharp
    button1.Left = 300;
    ```

    ```cpp
    button1->Left = 300;
    ```

## <a name="increment-a-controls-location-programmatically"></a><span data-ttu-id="b08ff-117">以程式設計方式遞增控制項的位置</span><span class="sxs-lookup"><span data-stu-id="b08ff-117">Increment a control's location programmatically</span></span>

<span data-ttu-id="b08ff-118">設定<xref:System.Windows.Forms.Control.Left%2A>遞增控制項的 X 座標的子屬性。</span><span class="sxs-lookup"><span data-stu-id="b08ff-118">Set the <xref:System.Windows.Forms.Control.Left%2A> subproperty to increment the X coordinate of the control.</span></span>

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
> <span data-ttu-id="b08ff-119">使用<xref:System.Windows.Forms.Control.Location%2A>屬性來設定控制項的 X 和 Y 位置同時。</span><span class="sxs-lookup"><span data-stu-id="b08ff-119">Use the <xref:System.Windows.Forms.Control.Location%2A> property to set a control's X and Y positions simultaneously.</span></span> <span data-ttu-id="b08ff-120">若要個別設定的位置，使用控制項的<xref:System.Windows.Forms.Control.Left%2A>(**X**) 或<xref:System.Windows.Forms.Control.Top%2A>(**Y**) 子屬性。</span><span class="sxs-lookup"><span data-stu-id="b08ff-120">To set a position individually, use the control's <xref:System.Windows.Forms.Control.Left%2A> (**X**) or <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subproperty.</span></span> <span data-ttu-id="b08ff-121">請勿嘗試將隱含地設定 X 和 Y 座標<xref:System.Drawing.Point>結構，表示按鈕的位置，因為此結構包含一份按鈕的座標。</span><span class="sxs-lookup"><span data-stu-id="b08ff-121">Do not try to implicitly set the X and Y coordinates of the <xref:System.Drawing.Point> structure that represents the button's location, because this structure contains a copy of the button's coordinates.</span></span>

## <a name="see-also"></a><span data-ttu-id="b08ff-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b08ff-122">See also</span></span>

- [<span data-ttu-id="b08ff-123">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="b08ff-123">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="b08ff-124">逐步解說：使用對齊線的 Windows Form 上排列控制項</span><span class="sxs-lookup"><span data-stu-id="b08ff-124">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="b08ff-125">逐步解說：排列 Windows Form 使用 TableLayoutPanel 控制項</span><span class="sxs-lookup"><span data-stu-id="b08ff-125">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="b08ff-126">逐步解說：排列 Windows Form 使用 FlowLayoutPanel 控制項</span><span class="sxs-lookup"><span data-stu-id="b08ff-126">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="b08ff-127">排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="b08ff-127">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="b08ff-128">標記個別 Windows Forms 控制項並提供其捷徑</span><span class="sxs-lookup"><span data-stu-id="b08ff-128">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="b08ff-129">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="b08ff-129">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="b08ff-130">依功能區分 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="b08ff-130">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- <span data-ttu-id="b08ff-131">[如何：設定 Windows Form 的畫面位置](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b08ff-131">[How to: Set the Screen Location of Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span></span>
