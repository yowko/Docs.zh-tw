---
title: WPF 應用程式中收集筆跡
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ink [WPF], collecting
- InkCanvas element [WPF]
- properties [WPF], DrawingAttributes
- collecting digital ink [WPF]
- digital ink [WPF], collecting
- properties [WPF], DefaultDrawingAttributes
- DefaultDrawingAttributes property [WPF]
ms.assetid: 66a3129d-9577-43eb-acbd-56c147282016
ms.openlocfilehash: 25f9c0141a97d8e52e0883b14fd3e1f4574a05ea
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45666885"
---
# <a name="collect-ink"></a><span data-ttu-id="ffd0f-102">收集筆墨</span><span class="sxs-lookup"><span data-stu-id="ffd0f-102">Collect Ink</span></span>

<span data-ttu-id="ffd0f-103">[Windows Presentation Foundation](../../../../docs/framework/wpf/index.md) 平台收集數位筆跡當成其功能的核心部分。</span><span class="sxs-lookup"><span data-stu-id="ffd0f-103">The [Windows Presentation Foundation](../../../../docs/framework/wpf/index.md) platform collects digital ink as a core part of its functionality.</span></span> <span data-ttu-id="ffd0f-104">本主題討論收集筆跡 Windows Presentation Foundation (WPF) 中的方法。</span><span class="sxs-lookup"><span data-stu-id="ffd0f-104">This topic discusses methods for collection of ink in Windows Presentation Foundation (WPF).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ffd0f-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="ffd0f-105">Prerequisites</span></span>

<span data-ttu-id="ffd0f-106">若要使用下列的範例，您必須先安裝 Visual Studio 和[!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ffd0f-106">To use the following examples, you must first install Visual Studio and the [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)].</span></span> <span data-ttu-id="ffd0f-107">您也應該了解如何撰寫 wpf 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ffd0f-107">You should also understand how to write applications for the WPF.</span></span> <span data-ttu-id="ffd0f-108">如需有關如何開始使用 WPF 的詳細資訊，請參閱[逐步解說： 我第一個 WPF 桌面應用程式](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)。</span><span class="sxs-lookup"><span data-stu-id="ffd0f-108">For more information about getting started with WPF, see [Walkthrough: My first WPF desktop application](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

## <a name="use-the-inkcanvas-element"></a><span data-ttu-id="ffd0f-109">使用 InkCanvas 項目</span><span class="sxs-lookup"><span data-stu-id="ffd0f-109">Use the InkCanvas Element</span></span>

<span data-ttu-id="ffd0f-110"><xref:System.Windows.Controls.InkCanvas?displayProperty=fullName>項目提供 WPF 中收集筆跡最簡單的方式。</span><span class="sxs-lookup"><span data-stu-id="ffd0f-110">The <xref:System.Windows.Controls.InkCanvas?displayProperty=fullName> element provides the easiest way to collect ink in WPF.</span></span> <span data-ttu-id="ffd0f-111">使用<xref:System.Windows.Controls.InkCanvas>接收並顯示筆跡輸入的項目。</span><span class="sxs-lookup"><span data-stu-id="ffd0f-111">Use an <xref:System.Windows.Controls.InkCanvas> element to receive and display ink input.</span></span> <span data-ttu-id="ffd0f-112">您通常是使用手寫筆，其與數位板互動來產生筆跡筆劃以輸入筆跡。</span><span class="sxs-lookup"><span data-stu-id="ffd0f-112">You commonly input ink through the use of a stylus, which interacts with a digitizer to produce ink strokes.</span></span> <span data-ttu-id="ffd0f-113">此外，滑鼠也可以代替手寫筆。</span><span class="sxs-lookup"><span data-stu-id="ffd0f-113">In addition, a mouse can be used in place of a stylus.</span></span> <span data-ttu-id="ffd0f-114">建立的筆劃統稱為<xref:System.Windows.Ink.Stroke>物件，而且它們可以操作以程式設計方式及使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="ffd0f-114">The created strokes are represented as <xref:System.Windows.Ink.Stroke> objects, and they can be manipulated both programmatically and by user input.</span></span> <span data-ttu-id="ffd0f-115"><xref:System.Windows.Controls.InkCanvas>可讓使用者選取、 修改或刪除現有<xref:System.Windows.Ink.Stroke>。</span><span class="sxs-lookup"><span data-stu-id="ffd0f-115">The <xref:System.Windows.Controls.InkCanvas> enables users to select, modify, or delete an existing <xref:System.Windows.Ink.Stroke>.</span></span>

<span data-ttu-id="ffd0f-116">藉由使用 XAML，您可以設定筆跡收集新增輕鬆**InkCanvas**至樹狀結構的項目。</span><span class="sxs-lookup"><span data-stu-id="ffd0f-116">By using XAML, you can set up ink collection as easily as adding an **InkCanvas** element to your tree.</span></span> <span data-ttu-id="ffd0f-117">下列範例會將<xref:System.Windows.Controls.InkCanvas>Visual Studio 中建立的預設 WPF 專案：</span><span class="sxs-lookup"><span data-stu-id="ffd0f-117">The following example adds an <xref:System.Windows.Controls.InkCanvas> to a default WPF project created in Visual Studio:</span></span>

[!code-xaml[DigitalInkTopics#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]

<span data-ttu-id="ffd0f-118">**InkCanvas**元素也可以包含子項目，讓您可以將筆跡註釋功能新增至幾乎任何類型的 XAML 項目。</span><span class="sxs-lookup"><span data-stu-id="ffd0f-118">The **InkCanvas** element can also contain child elements, making it possible to add ink annotation capabilities to almost any type of XAML element.</span></span> <span data-ttu-id="ffd0f-119">比方說，若要將筆跡功能新增至文字項目，讓它的子系<xref:System.Windows.Controls.InkCanvas>:</span><span class="sxs-lookup"><span data-stu-id="ffd0f-119">For example, to add inking capabilities to a text element, simply make it a child of an <xref:System.Windows.Controls.InkCanvas>:</span></span>

[!code-xaml[DigitalInkTopics#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]

<span data-ttu-id="ffd0f-120">新增標記筆墨的映像的支援也一樣簡單：</span><span class="sxs-lookup"><span data-stu-id="ffd0f-120">Adding support for marking up an image with ink is just as easy:</span></span>

[!code-xaml[DigitalInkTopics#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]

### <a name="inkcollection-modes"></a><span data-ttu-id="ffd0f-121">InkCollection 模式</span><span class="sxs-lookup"><span data-stu-id="ffd0f-121">InkCollection Modes</span></span>

<span data-ttu-id="ffd0f-122"><xref:System.Windows.Controls.InkCanvas>提供支援，針對各種輸入模式透過其<xref:System.Windows.Controls.InkCanvas.EditingMode%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="ffd0f-122">The <xref:System.Windows.Controls.InkCanvas> provides support for various input modes through its <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> property.</span></span>

### <a name="manipulate-ink"></a><span data-ttu-id="ffd0f-123">操作筆跡</span><span class="sxs-lookup"><span data-stu-id="ffd0f-123">Manipulate Ink</span></span>

<span data-ttu-id="ffd0f-124"><xref:System.Windows.Controls.InkCanvas>提供許多筆跡編輯作業的支援。</span><span class="sxs-lookup"><span data-stu-id="ffd0f-124">The <xref:System.Windows.Controls.InkCanvas> provides support for many ink editing operations.</span></span> <span data-ttu-id="ffd0f-125">比方說，<xref:System.Windows.Controls.InkCanvas>支援畫筆後清除，並使用任何額外的程式碼，才能將功能新增至項目。</span><span class="sxs-lookup"><span data-stu-id="ffd0f-125">For example, <xref:System.Windows.Controls.InkCanvas> supports back-of-pen erase, and no additional code is needed to add the functionality to the element.</span></span>

#### <a name="selection"></a><span data-ttu-id="ffd0f-126">選取</span><span class="sxs-lookup"><span data-stu-id="ffd0f-126">Selection</span></span>

<span data-ttu-id="ffd0f-127">設定選取模式很簡單，只要設定<xref:System.Windows.Controls.InkCanvasEditingMode>屬性，以**選取**。</span><span class="sxs-lookup"><span data-stu-id="ffd0f-127">Setting selection mode is as simple as setting the <xref:System.Windows.Controls.InkCanvasEditingMode> property to **Select**.</span></span>

<span data-ttu-id="ffd0f-128">下列程式碼設定的值為基礎的編輯模式<xref:System.Windows.Forms.CheckBox>:</span><span class="sxs-lookup"><span data-stu-id="ffd0f-128">The following code sets the editing mode based on the value of a <xref:System.Windows.Forms.CheckBox>:</span></span>

[!code-csharp[DigitalInkTopics#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
[!code-vb[DigitalInkTopics#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]

#### <a name="drawingattributes"></a><span data-ttu-id="ffd0f-129">DrawingAttributes</span><span class="sxs-lookup"><span data-stu-id="ffd0f-129">DrawingAttributes</span></span>

<span data-ttu-id="ffd0f-130">使用<xref:System.Windows.Ink.Stroke.DrawingAttributes%2A>来變更筆跡筆劃的外觀屬性。</span><span class="sxs-lookup"><span data-stu-id="ffd0f-130">Use the <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> property to change the appearance of ink strokes.</span></span> <span data-ttu-id="ffd0f-131">比方說，<xref:System.Windows.Ink.DrawingAttributes.Color%2A>隸屬<xref:System.Windows.Ink.DrawingAttributes>設定的色彩呈現的<xref:System.Windows.Ink.Stroke>。</span><span class="sxs-lookup"><span data-stu-id="ffd0f-131">For instance, the <xref:System.Windows.Ink.DrawingAttributes.Color%2A> member of <xref:System.Windows.Ink.DrawingAttributes> sets the color of the rendered <xref:System.Windows.Ink.Stroke>.</span></span>

<span data-ttu-id="ffd0f-132">下列範例會將選取的筆劃的色彩變更為紅色：</span><span class="sxs-lookup"><span data-stu-id="ffd0f-132">The following example changes the color of the selected strokes to red:</span></span>

[!code-csharp[DigitalInkTopics#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
[!code-vb[DigitalInkTopics#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]

### <a name="defaultdrawingattributes"></a><span data-ttu-id="ffd0f-133">DefaultDrawingAttributes</span><span class="sxs-lookup"><span data-stu-id="ffd0f-133">DefaultDrawingAttributes</span></span>

<span data-ttu-id="ffd0f-134"><xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>屬性可存取的屬性，例如高度、 寬度和色彩在中建立的筆劃<xref:System.Windows.Controls.InkCanvas>。</span><span class="sxs-lookup"><span data-stu-id="ffd0f-134">The <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> property provides access to properties such as the height, width, and color of the strokes to be created in an <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="ffd0f-135">一旦變更<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>，輸入的所有未來筆劃<xref:System.Windows.Controls.InkCanvas>新的屬性值，以呈現。</span><span class="sxs-lookup"><span data-stu-id="ffd0f-135">Once you change the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, all future strokes entered into the <xref:System.Windows.Controls.InkCanvas> are rendered with the new property values.</span></span>

<span data-ttu-id="ffd0f-136">除了修改<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>在程式碼後置檔案中，您可以使用 XAML 語法指定<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="ffd0f-136">In addition to modifying the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> in the code-behind file, you can use XAML syntax for specifying <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> properties.</span></span>

<span data-ttu-id="ffd0f-137">下一個範例示範如何設定<xref:System.Windows.Ink.DrawingAttributes.Color%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="ffd0f-137">The next example demonstrates how to set the <xref:System.Windows.Ink.DrawingAttributes.Color%2A> property.</span></span> <span data-ttu-id="ffd0f-138">若要使用此程式碼，建立新的 WPF 專案，Visual Studio 中稱為"HelloInkCanvas"。</span><span class="sxs-lookup"><span data-stu-id="ffd0f-138">To use this code, create a new WPF project called "HelloInkCanvas" in Visual Studio.</span></span> <span data-ttu-id="ffd0f-139">中的程式碼取代*MainWindow.xaml*為下列程式碼的檔案：</span><span class="sxs-lookup"><span data-stu-id="ffd0f-139">Replace the code in the *MainWindow.xaml* file with the following code:</span></span>

[!code-xaml[HelloInkCanvas#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]

<span data-ttu-id="ffd0f-140">接下來，加入下列的按鈕事件處理常式的程式碼後置檔案，在 MainWindow 類別：</span><span class="sxs-lookup"><span data-stu-id="ffd0f-140">Next, add the following button event handlers to the code behind file, inside the MainWindow class:</span></span>

[!code-csharp[HelloInkCanvas#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]

<span data-ttu-id="ffd0f-141">複製此程式碼之後, 按下**F5**在 Visual Studio 中偵錯工具中執行程式。</span><span class="sxs-lookup"><span data-stu-id="ffd0f-141">After copying this code, press **F5** in Visual Studio to run the program in the debugger.</span></span>

<span data-ttu-id="ffd0f-142">請注意如何<xref:System.Windows.Controls.StackPanel>將按鈕的上方放置<xref:System.Windows.Controls.InkCanvas>。</span><span class="sxs-lookup"><span data-stu-id="ffd0f-142">Notice how the <xref:System.Windows.Controls.StackPanel> places the buttons on top of the <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="ffd0f-143">如果您嘗試透過頂端的按鈕時，筆墨<xref:System.Windows.Controls.InkCanvas>收集並呈現在按鈕後方的筆墨。</span><span class="sxs-lookup"><span data-stu-id="ffd0f-143">If you try to ink over the top of the buttons, the <xref:System.Windows.Controls.InkCanvas> collects and renders the ink behind the buttons.</span></span> <span data-ttu-id="ffd0f-144">這是因為按鈕的同層級<xref:System.Windows.Controls.InkCanvas>相對於子系。</span><span class="sxs-lookup"><span data-stu-id="ffd0f-144">This is because the buttons are siblings of the <xref:System.Windows.Controls.InkCanvas> as opposed to children.</span></span> <span data-ttu-id="ffd0f-145">而且按鈕的級別高於疊置順序，所以筆跡轉譯在其後。</span><span class="sxs-lookup"><span data-stu-id="ffd0f-145">Also, the buttons are higher in the z-order, so the ink is rendered behind them.</span></span>

## <a name="see-also"></a><span data-ttu-id="ffd0f-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffd0f-146">See Also</span></span>

- <xref:System.Windows.Ink.DrawingAttributes>
- <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>
- <xref:System.Windows.Ink>