---
title: 如何：將控制項定位在 Windows Form 上
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
ms.openlocfilehash: 6843c22fec964de92c41760f1108d1c83e1f5bf8
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2018
ms.locfileid: "43332477"
---
# <a name="how-to-position-controls-on-windows-forms"></a><span data-ttu-id="fad37-102">如何：將控制項定位在 Windows Form 上</span><span class="sxs-lookup"><span data-stu-id="fad37-102">How to: Position Controls on Windows Forms</span></span>
<span data-ttu-id="fad37-103">若要調整控制項的位置，使用 Windows Form 設計工具中，或指定<xref:System.Windows.Forms.Control.Location%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="fad37-103">To position controls, use the Windows Forms Designer, or specify the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fad37-104">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="fad37-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="fad37-105">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="fad37-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="fad37-106">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="fad37-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a><span data-ttu-id="fad37-107">若要將控制項放置在 Windows Form 設計工具的設計介面上</span><span class="sxs-lookup"><span data-stu-id="fad37-107">To position a control on the design surface of the Windows Forms Designer</span></span>  
  
-   <span data-ttu-id="fad37-108">將控制項拖曳至適當的位置，使用滑鼠。</span><span class="sxs-lookup"><span data-stu-id="fad37-108">Drag the control to the appropriate location with the mouse.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fad37-109">選取的控制項，然後移動它具有箭號將它放在更精確索引鍵。</span><span class="sxs-lookup"><span data-stu-id="fad37-109">Select the control and move it with the ARROW keys to position it more precisely.</span></span> <span data-ttu-id="fad37-110">此外，*對齊線*協助您放置在表單上精確的控制項。</span><span class="sxs-lookup"><span data-stu-id="fad37-110">Also, *snaplines* assist you in placing controls precisely on your form.</span></span> <span data-ttu-id="fad37-111">如需詳細資訊，請參閱 <<c0> [ 逐步解說： 在 Windows Form 使用對齊線排列的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)。</span><span class="sxs-lookup"><span data-stu-id="fad37-111">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>  
  
### <a name="to-position-a-control-using-the-properties-window"></a><span data-ttu-id="fad37-112">若要將使用 [屬性] 視窗的控制項</span><span class="sxs-lookup"><span data-stu-id="fad37-112">To position a control using the Properties window</span></span>  
  
1.  <span data-ttu-id="fad37-113">按一下您要放置的控制項。</span><span class="sxs-lookup"><span data-stu-id="fad37-113">Click the control you want to position.</span></span>  
  
2.  <span data-ttu-id="fad37-114">在 [**屬性**] 視窗中，型別值<xref:System.Windows.Forms.Control.Location%2A>屬性，以逗號分隔，其容器內控制項的位置。</span><span class="sxs-lookup"><span data-stu-id="fad37-114">In the **Properties** window, type values for the <xref:System.Windows.Forms.Control.Location%2A> property, separated by a comma, to position the control within its container.</span></span>  
  
     <span data-ttu-id="fad37-115">第一個數字 (X) 是從容器; 左框線的距離第二個數字 (Y) 是從容器工作區，以像素表示上框線的距離。</span><span class="sxs-lookup"><span data-stu-id="fad37-115">The first number (X) is the distance from the left border of the container; the second number (Y) is the distance from the upper border of the container area, measured in pixels.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fad37-116">您可以展開<xref:System.Windows.Forms.Control.Location%2A>類型的屬性**X**並**Y**個別值。</span><span class="sxs-lookup"><span data-stu-id="fad37-116">You can expand the <xref:System.Windows.Forms.Control.Location%2A> property to type the **X** and **Y** values individually.</span></span>  
  
### <a name="to-position-a-control-programmatically"></a><span data-ttu-id="fad37-117">若要以程式設計方式調整控制項的位置</span><span class="sxs-lookup"><span data-stu-id="fad37-117">To position a control programmatically</span></span>  
  
1.  <span data-ttu-id="fad37-118">設定<xref:System.Windows.Forms.Control.Location%2A>屬性來控制<xref:System.Drawing.Point>。</span><span class="sxs-lookup"><span data-stu-id="fad37-118">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the control to a <xref:System.Drawing.Point>.</span></span>  
  
    ```vb  
    Button1.Location = New Point(100, 100)  
    ```  
  
    ```csharp  
    button1.Location = new Point(100, 100);  
    ```  
  
    ```cpp  
    button1->Location = Point(100, 100);  
    ```  
  
2.  <span data-ttu-id="fad37-119">變更控制項的位置的 X 座標使用<xref:System.Windows.Forms.Control.Left%2A>子屬性。</span><span class="sxs-lookup"><span data-stu-id="fad37-119">Change the X coordinate of the control's location using the <xref:System.Windows.Forms.Control.Left%2A> subproperty.</span></span>  
  
    ```vb  
    Button1.Left = 300  
    ```  
  
    ```csharp  
    button1.Left = 300;  
    ```  
  
    ```cpp  
    button1->Left = 300;  
    ```  
  
### <a name="to-increment-a-controls-location-programmatically"></a><span data-ttu-id="fad37-120">若要以程式設計方式遞增控制項的位置</span><span class="sxs-lookup"><span data-stu-id="fad37-120">To increment a control's location programmatically</span></span>  
  
1.  <span data-ttu-id="fad37-121">設定<xref:System.Windows.Forms.Control.Left%2A>遞增控制項的 X 座標的子屬性。</span><span class="sxs-lookup"><span data-stu-id="fad37-121">Set the <xref:System.Windows.Forms.Control.Left%2A> subproperty to increment the X coordinate of the control.</span></span>  
  
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
    >  <span data-ttu-id="fad37-122">使用<xref:System.Windows.Forms.Control.Location%2A>屬性來設定控制項的 X 和 Y 位置同時。</span><span class="sxs-lookup"><span data-stu-id="fad37-122">Use the <xref:System.Windows.Forms.Control.Location%2A> property to set a control's X and Y positions simultaneously.</span></span> <span data-ttu-id="fad37-123">若要個別設定的位置，使用控制項的<xref:System.Windows.Forms.Control.Left%2A>(**X**) 或<xref:System.Windows.Forms.Control.Top%2A>(**Y**) 子屬性。</span><span class="sxs-lookup"><span data-stu-id="fad37-123">To set a position individually, use the control's <xref:System.Windows.Forms.Control.Left%2A> (**X**) or <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subproperty.</span></span> <span data-ttu-id="fad37-124">請勿嘗試將隱含地設定 X 和 Y 座標<xref:System.Drawing.Point>結構，表示按鈕的位置，因為此結構包含一份按鈕的座標。</span><span class="sxs-lookup"><span data-stu-id="fad37-124">Do not try to implicitly set the X and Y coordinates of the <xref:System.Drawing.Point> structure that represents the button's location, because this structure contains a copy of the button's coordinates.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fad37-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fad37-125">See Also</span></span>  
 [<span data-ttu-id="fad37-126">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="fad37-126">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="fad37-127">逐步解說：使用對齊線排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="fad37-127">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="fad37-128">逐步解說：使用 TableLayoutPanel 排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="fad37-128">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [<span data-ttu-id="fad37-129">逐步解說：使用 FlowLayoutPanel 排列 Windows Forms上的控制項</span><span class="sxs-lookup"><span data-stu-id="fad37-129">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [<span data-ttu-id="fad37-130">排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="fad37-130">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="fad37-131">標記個別 Windows Forms 控制項並提供其捷徑</span><span class="sxs-lookup"><span data-stu-id="fad37-131">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="fad37-132">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="fad37-132">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="fad37-133">依功能區分 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="fad37-133">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)  
 [<span data-ttu-id="fad37-134">如何： 設定 Windows Form 的畫面位置</span><span class="sxs-lookup"><span data-stu-id="fad37-134">How to: Set the Screen Location of Windows Forms</span></span>](https://msdn.microsoft.com/library/cb023ab7-dea7-4284-9aa6-8c03c59b60c6)
