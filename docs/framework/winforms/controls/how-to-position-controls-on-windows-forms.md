---
title: 作法：定位 Windows Forms 的控制項
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1cc2cb4c749b7290a6edf914a8e6a697006ef43c
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987075"
---
# <a name="how-to-position-controls-on-windows-forms"></a><span data-ttu-id="013f8-102">HOW TO：在 Windows Forms 上放置控制項</span><span class="sxs-lookup"><span data-stu-id="013f8-102">How to: Position controls on Windows Forms</span></span>

<span data-ttu-id="013f8-103">若要定位控制項, 請使用 Visual Studio 中的 Windows Form 設計工具, <xref:System.Windows.Forms.Control.Location%2A>或指定屬性。</span><span class="sxs-lookup"><span data-stu-id="013f8-103">To position controls, use the Windows Forms Designer in Visual Studio or specify the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a><span data-ttu-id="013f8-104">將控制項放在 Windows Form 設計工具的設計介面上</span><span class="sxs-lookup"><span data-stu-id="013f8-104">Position a control on the design surface of the Windows Forms Designer</span></span>

<span data-ttu-id="013f8-105">在 Visual Studio 中, 使用滑鼠將控制項拖曳至適當的位置。</span><span class="sxs-lookup"><span data-stu-id="013f8-105">In Visual Studio, drag the control to the appropriate location with the mouse.</span></span>

> [!NOTE]
> <span data-ttu-id="013f8-106">選取控制項, 並使用方向鍵將它移動, 以更精確地定位。</span><span class="sxs-lookup"><span data-stu-id="013f8-106">Select the control and move it with the ARROW keys to position it more precisely.</span></span> <span data-ttu-id="013f8-107">此外,*對齊線*可協助您精確地將控制項放在表單上。</span><span class="sxs-lookup"><span data-stu-id="013f8-107">Also, *snaplines* assist you in placing controls precisely on your form.</span></span> <span data-ttu-id="013f8-108">如需詳細資訊，請參閱[逐步解說：使用對齊線](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)排列 Windows Forms 上的控制項。</span><span class="sxs-lookup"><span data-stu-id="013f8-108">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>

## <a name="position-a-control-using-the-properties-window"></a><span data-ttu-id="013f8-109">使用屬性視窗放置控制項</span><span class="sxs-lookup"><span data-stu-id="013f8-109">Position a control using the Properties window</span></span>

1. <span data-ttu-id="013f8-110">在 Visual Studio 中, 選取您想要放置的控制項。</span><span class="sxs-lookup"><span data-stu-id="013f8-110">In Visual Studio, select the control you want to position.</span></span>

2. <span data-ttu-id="013f8-111">在 [**屬性**] 視窗中, 輸入<xref:System.Windows.Forms.Control.Location%2A>屬性的值 (以逗號分隔), 以將控制項放在其容器內。</span><span class="sxs-lookup"><span data-stu-id="013f8-111">In the **Properties** window, enter values for the <xref:System.Windows.Forms.Control.Location%2A> property, separated by a comma, to position the control within its container.</span></span>

   <span data-ttu-id="013f8-112">第一個數位 (X) 是與容器左邊框線之間的距離;第二個數字 (Y) 是距容器區域上框線的距離, 以圖元為單位。</span><span class="sxs-lookup"><span data-stu-id="013f8-112">The first number (X) is the distance from the left border of the container; the second number (Y) is the distance from the upper border of the container area, measured in pixels.</span></span>

   > [!NOTE]
   > <span data-ttu-id="013f8-113">您可以展開<xref:System.Windows.Forms.Control.Location%2A>屬性, 以個別輸入**X**和**Y**值。</span><span class="sxs-lookup"><span data-stu-id="013f8-113">You can expand the <xref:System.Windows.Forms.Control.Location%2A> property to type the **X** and **Y** values individually.</span></span>

## <a name="position-a-control-programmatically"></a><span data-ttu-id="013f8-114">以程式設計方式放置控制項</span><span class="sxs-lookup"><span data-stu-id="013f8-114">Position a control programmatically</span></span>

1. <span data-ttu-id="013f8-115">將控制項<xref:System.Windows.Forms.Control.Location%2A>的屬性設<xref:System.Drawing.Point>為。</span><span class="sxs-lookup"><span data-stu-id="013f8-115">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the control to a <xref:System.Drawing.Point>.</span></span>

    ```vb
    Button1.Location = New Point(100, 100)
    ```

    ```csharp
    button1.Location = new Point(100, 100);
    ```

    ```cpp
    button1->Location = Point(100, 100);
    ```

2. <span data-ttu-id="013f8-116">使用<xref:System.Windows.Forms.Control.Left%2A>子屬性變更控制項位置的 X 座標。</span><span class="sxs-lookup"><span data-stu-id="013f8-116">Change the X coordinate of the control's location using the <xref:System.Windows.Forms.Control.Left%2A> subproperty.</span></span>

    ```vb
    Button1.Left = 300
    ```

    ```csharp
    button1.Left = 300;
    ```

    ```cpp
    button1->Left = 300;
    ```

## <a name="increment-a-controls-location-programmatically"></a><span data-ttu-id="013f8-117">以程式設計方式遞增控制項的位置</span><span class="sxs-lookup"><span data-stu-id="013f8-117">Increment a control's location programmatically</span></span>

<span data-ttu-id="013f8-118">設定子<xref:System.Windows.Forms.Control.Left%2A>屬性, 以遞增控制項的 X 座標。</span><span class="sxs-lookup"><span data-stu-id="013f8-118">Set the <xref:System.Windows.Forms.Control.Left%2A> subproperty to increment the X coordinate of the control.</span></span>

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
> <span data-ttu-id="013f8-119">您可以使用屬性, 同時設定控制項的 X 和 Y 位置。 <xref:System.Windows.Forms.Control.Location%2A></span><span class="sxs-lookup"><span data-stu-id="013f8-119">Use the <xref:System.Windows.Forms.Control.Location%2A> property to set a control's X and Y positions simultaneously.</span></span> <span data-ttu-id="013f8-120">若要個別設定位置, 請使用控制項的<xref:System.Windows.Forms.Control.Left%2A> (**X**) 或<xref:System.Windows.Forms.Control.Top%2A> (**Y**) 子屬性。</span><span class="sxs-lookup"><span data-stu-id="013f8-120">To set a position individually, use the control's <xref:System.Windows.Forms.Control.Left%2A> (**X**) or <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subproperty.</span></span> <span data-ttu-id="013f8-121">請勿嘗試隱含地設定代表按鈕位置之<xref:System.Drawing.Point>結構的 X 和 Y 座標, 因為此結構包含按鈕座標的複本。</span><span class="sxs-lookup"><span data-stu-id="013f8-121">Do not try to implicitly set the X and Y coordinates of the <xref:System.Drawing.Point> structure that represents the button's location, because this structure contains a copy of the button's coordinates.</span></span>

## <a name="see-also"></a><span data-ttu-id="013f8-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="013f8-122">See also</span></span>

- [<span data-ttu-id="013f8-123">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="013f8-123">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="013f8-124">逐步解說：使用對齊線排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="013f8-124">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="013f8-125">逐步解說：使用 TableLayoutPanel 排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="013f8-125">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="013f8-126">逐步解說：使用 FlowLayoutPanel 排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="013f8-126">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="013f8-127">標記個別 Windows Forms 控制項並提供其捷徑</span><span class="sxs-lookup"><span data-stu-id="013f8-127">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="013f8-128">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="013f8-128">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="013f8-129">依功能區分 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="013f8-129">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- <span data-ttu-id="013f8-130">[如何：設定 Windows Forms 的螢幕位置](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="013f8-130">[How to: Set the Screen Location of Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span></span>
