---
title: "收集筆墨"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cbf55b5d84420a6aa7af06e94497a85a2b54a0c0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="collecting-ink"></a><span data-ttu-id="235ae-102">收集筆墨</span><span class="sxs-lookup"><span data-stu-id="235ae-102">Collecting Ink</span></span>
<span data-ttu-id="235ae-103">[Windows Presentation Foundation](../../../../docs/framework/wpf/index.md) 平台收集數位筆跡當成其功能的核心部分。</span><span class="sxs-lookup"><span data-stu-id="235ae-103">The [Windows Presentation Foundation](../../../../docs/framework/wpf/index.md) platform collects digital ink as a core part of its functionality.</span></span> <span data-ttu-id="235ae-104">本主題討論 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 中收集筆跡的方法。</span><span class="sxs-lookup"><span data-stu-id="235ae-104">This topic discusses methods for collection of ink in [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="235ae-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="235ae-105">Prerequisites</span></span>  
 <span data-ttu-id="235ae-106">若要使用下列範例，您必須先安裝 [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] 和 [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="235ae-106">To use the following examples, you must first install [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] and the [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)].</span></span> <span data-ttu-id="235ae-107">您也應該了解如何撰寫適用於 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="235ae-107">You should also understand how to write applications for the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="235ae-108">如需開始使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，請參閱[逐步解說： 第一個 WPF 桌面應用程式](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)。</span><span class="sxs-lookup"><span data-stu-id="235ae-108">For more information about getting started with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], see [Walkthrough: My first WPF desktop application](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>  
  
## <a name="using-the-inkcanvas-element"></a><span data-ttu-id="235ae-109">使用 InkCanvas 項目</span><span class="sxs-lookup"><span data-stu-id="235ae-109">Using the InkCanvas Element</span></span>  
 <span data-ttu-id="235ae-110"><xref:System.Windows.Controls.InkCanvas>項目會提供最簡單的方式收集中的筆墨[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="235ae-110">The <xref:System.Windows.Controls.InkCanvas> element provides the easiest way to collect ink in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="235ae-111"><xref:System.Windows.Controls.InkCanvas>項目是類似於[Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/microsoft.ink.inkoverlay\(v=vs.90\).aspx)物件從[!INCLUDE[TLA2#tla_tpclssdk](../../../../includes/tla2sharptla-tpclssdk-md.md)]及較早版本。</span><span class="sxs-lookup"><span data-stu-id="235ae-111">The <xref:System.Windows.Controls.InkCanvas> element is similar to the [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/microsoft.ink.inkoverlay\(v=vs.90\).aspx) object from the [!INCLUDE[TLA2#tla_tpclssdk](../../../../includes/tla2sharptla-tpclssdk-md.md)] and earlier versions.</span></span>  
  
 <span data-ttu-id="235ae-112">使用<xref:System.Windows.Controls.InkCanvas>來接收和顯示筆墨輸入的項目。</span><span class="sxs-lookup"><span data-stu-id="235ae-112">Use an <xref:System.Windows.Controls.InkCanvas> element to receive and display ink input.</span></span> <span data-ttu-id="235ae-113">您通常是使用手寫筆，其與數位板互動來產生筆跡筆劃以輸入筆跡。</span><span class="sxs-lookup"><span data-stu-id="235ae-113">You commonly input ink through the use of a stylus, which interacts with a digitizer to produce ink strokes.</span></span> <span data-ttu-id="235ae-114">此外，滑鼠也可以代替手寫筆。</span><span class="sxs-lookup"><span data-stu-id="235ae-114">In addition, a mouse can be used in place of a stylus.</span></span> <span data-ttu-id="235ae-115">建立的筆觸會表示為<xref:System.Windows.Ink.Stroke>物件，而且它們可以操作以程式設計方式和由使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="235ae-115">The created strokes are represented as <xref:System.Windows.Ink.Stroke> objects, and they can be manipulated both programmatically and by user input.</span></span> <span data-ttu-id="235ae-116"><xref:System.Windows.Controls.InkCanvas>可讓使用者選取、 修改或刪除現有<xref:System.Windows.Ink.Stroke>。</span><span class="sxs-lookup"><span data-stu-id="235ae-116">The <xref:System.Windows.Controls.InkCanvas> enables users to select, modify, or delete an existing <xref:System.Windows.Ink.Stroke>.</span></span>  
  
 <span data-ttu-id="235ae-117">使用 XAML 可以設定筆跡收集，如將 `InkCanvas` 項目新增至樹狀結構一樣容易。</span><span class="sxs-lookup"><span data-stu-id="235ae-117">By using XAML, you can set up ink collection as easily as adding an `InkCanvas` element to your tree.</span></span> <span data-ttu-id="235ae-118">下列範例會將<xref:System.Windows.Controls.InkCanvas>預設[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]中建立專案[!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="235ae-118">The following example adds an <xref:System.Windows.Controls.InkCanvas> to a default [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] project created in [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)].</span></span>  
  
 [!code-xaml[DigitalInkTopics#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]  
  
 <span data-ttu-id="235ae-119">`InkCanvas` 項目也可以包含子項目，以將筆跡註釋功能新增至幾乎任何類型的 XAML 項目。</span><span class="sxs-lookup"><span data-stu-id="235ae-119">The `InkCanvas` element can also contain child elements, making it possible to add ink annotation capabilities to almost any type of XAML element.</span></span> <span data-ttu-id="235ae-120">比方說，將筆跡的功能加入至文字項目，只會保持它的子系<xref:System.Windows.Controls.InkCanvas>。</span><span class="sxs-lookup"><span data-stu-id="235ae-120">For example, to add inking capabilities to a text element, simply make it a child of an <xref:System.Windows.Controls.InkCanvas>.</span></span>  
  
 [!code-xaml[DigitalInkTopics#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]  
  
 <span data-ttu-id="235ae-121">新增以筆跡標記映像的支援就是這麼簡單。</span><span class="sxs-lookup"><span data-stu-id="235ae-121">Adding support for marking up an image with ink is just as easy.</span></span>  
  
 [!code-xaml[DigitalInkTopics#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]  
  
### <a name="inkcollection-modes"></a><span data-ttu-id="235ae-122">InkCollection 模式</span><span class="sxs-lookup"><span data-stu-id="235ae-122">InkCollection Modes</span></span>  
 <span data-ttu-id="235ae-123"><xref:System.Windows.Controls.InkCanvas>支援的各種輸入模式透過其<xref:System.Windows.Controls.InkCanvas.EditingMode%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="235ae-123">The <xref:System.Windows.Controls.InkCanvas> provides support for various input modes through its <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> property.</span></span>  
  
### <a name="manipulating-ink"></a><span data-ttu-id="235ae-124">操作筆跡</span><span class="sxs-lookup"><span data-stu-id="235ae-124">Manipulating Ink</span></span>  
 <span data-ttu-id="235ae-125"><xref:System.Windows.Controls.InkCanvas>許多筆墨編輯作業提供支援。</span><span class="sxs-lookup"><span data-stu-id="235ae-125">The <xref:System.Windows.Controls.InkCanvas> provides support for many ink editing operations.</span></span> <span data-ttu-id="235ae-126">例如，<xref:System.Windows.Controls.InkCanvas>支援畫筆後清除任何額外的程式碼，才能將功能加入至項目。</span><span class="sxs-lookup"><span data-stu-id="235ae-126">For example, <xref:System.Windows.Controls.InkCanvas> supports back-of-pen erase with no additional code needed to add the functionality to the element.</span></span>  
  
#### <a name="selection"></a><span data-ttu-id="235ae-127">選取</span><span class="sxs-lookup"><span data-stu-id="235ae-127">Selection</span></span>  
 <span data-ttu-id="235ae-128">設定選取範圍模式很簡單，只設定<xref:System.Windows.Controls.InkCanvasEditingMode>屬性**選取**。</span><span class="sxs-lookup"><span data-stu-id="235ae-128">Setting selection mode is as simple as setting the <xref:System.Windows.Controls.InkCanvasEditingMode> property to **Select**.</span></span> <span data-ttu-id="235ae-129">下列程式碼中設定的值為基礎的編輯模式<xref:System.Windows.Forms.CheckBox>:</span><span class="sxs-lookup"><span data-stu-id="235ae-129">The following code sets the editing mode based on the value of a <xref:System.Windows.Forms.CheckBox>:</span></span>  
  
 [!code-csharp[DigitalInkTopics#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
 [!code-vb[DigitalInkTopics#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]  
  
#### <a name="drawingattributes"></a><span data-ttu-id="235ae-130">DrawingAttributes</span><span class="sxs-lookup"><span data-stu-id="235ae-130">DrawingAttributes</span></span>  
 <span data-ttu-id="235ae-131">使用<xref:System.Windows.Ink.Stroke.DrawingAttributes%2A>来變更的筆墨筆劃外觀屬性。</span><span class="sxs-lookup"><span data-stu-id="235ae-131">Use the <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> property to change the appearance of ink strokes.</span></span> <span data-ttu-id="235ae-132">比方說，<xref:System.Windows.Ink.DrawingAttributes.Color%2A>隸屬<xref:System.Windows.Ink.DrawingAttributes>設定轉譯的色彩<xref:System.Windows.Ink.Stroke>。</span><span class="sxs-lookup"><span data-stu-id="235ae-132">For instance, the <xref:System.Windows.Ink.DrawingAttributes.Color%2A> member of <xref:System.Windows.Ink.DrawingAttributes> sets the color of the rendered <xref:System.Windows.Ink.Stroke>.</span></span> <span data-ttu-id="235ae-133">下例會將所選筆劃的色彩變更為紅色。</span><span class="sxs-lookup"><span data-stu-id="235ae-133">The following example changes the color of the selected strokes to red.</span></span>  
  
 [!code-csharp[DigitalInkTopics#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
 [!code-vb[DigitalInkTopics#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]  
  
### <a name="defaultdrawingattributes"></a><span data-ttu-id="235ae-134">DefaultDrawingAttributes</span><span class="sxs-lookup"><span data-stu-id="235ae-134">DefaultDrawingAttributes</span></span>  
 <span data-ttu-id="235ae-135"><xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>屬性可存取屬性，例如高度、 寬度和色彩中建立的筆劃<xref:System.Windows.Controls.InkCanvas>。</span><span class="sxs-lookup"><span data-stu-id="235ae-135">The <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> property provides access to properties such as the height, width, and color of the strokes to be created in an <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="235ae-136">一旦變更<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>，輸入的所有未來筆劃<xref:System.Windows.Controls.InkCanvas>會轉譯與新的屬性值。</span><span class="sxs-lookup"><span data-stu-id="235ae-136">Once you change the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, all future strokes entered into the <xref:System.Windows.Controls.InkCanvas> are rendered with the new property values.</span></span>  
  
 <span data-ttu-id="235ae-137">除了修改<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>在程式碼後置檔案中，您可以使用 XAML 語法來指定<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="235ae-137">In addition to modifying the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> in the code-behind file, you can use XAML syntax for specifying <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> properties.</span></span> <span data-ttu-id="235ae-138">下列 XAML 程式碼示範如何設定<xref:System.Windows.Ink.DrawingAttributes.Color%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="235ae-138">The following XAML code demonstrates how to set the <xref:System.Windows.Ink.DrawingAttributes.Color%2A> property.</span></span> <span data-ttu-id="235ae-139">若要使用此程式碼，請建立新的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 專案，在 Visual Studio 2005 中稱為 "HelloInkCanvas"。</span><span class="sxs-lookup"><span data-stu-id="235ae-139">To use this code, create a new [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] project called "HelloInkCanvas" in Visual Studio 2005.</span></span> <span data-ttu-id="235ae-140">以下列程式碼取代 Window1.xaml 檔案中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="235ae-140">Replace the code in the Window1.xaml file with the following code.</span></span>  
  
 [!code-xaml[HelloInkCanvas#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="235ae-141">接下來，將以下按鈕事件處理常式新增至 Window1 類別內的程式碼後置檔案。</span><span class="sxs-lookup"><span data-stu-id="235ae-141">Next, add the following button event handlers to the code behind file, inside the Window1 class.</span></span>  
  
 [!code-csharp[HelloInkCanvas#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]  
  
 <span data-ttu-id="235ae-142">複製此程式碼之後，請在 Microsoft Visual Studio 2005 中按 **F5** 執行偵錯工具中的程式。</span><span class="sxs-lookup"><span data-stu-id="235ae-142">After copying this code, press **F5** in Microsoft Visual Studio 2005 to run the program in the debugger.</span></span>  
  
 <span data-ttu-id="235ae-143">請注意如何<xref:System.Windows.Controls.StackPanel>將上方的按鈕<xref:System.Windows.Controls.InkCanvas>。</span><span class="sxs-lookup"><span data-stu-id="235ae-143">Notice how the <xref:System.Windows.Controls.StackPanel> places the buttons on top of the <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="235ae-144">如果您嘗試透過頂端的按鈕時，筆墨<xref:System.Windows.Controls.InkCanvas>收集並呈現按鈕之後的筆墨。</span><span class="sxs-lookup"><span data-stu-id="235ae-144">If you try to ink over the top of the buttons, the <xref:System.Windows.Controls.InkCanvas> collects and renders the ink behind the buttons.</span></span> <span data-ttu-id="235ae-145">這是因為按鈕的同層級<xref:System.Windows.Controls.InkCanvas>而不是子系。</span><span class="sxs-lookup"><span data-stu-id="235ae-145">This is because the buttons are siblings of the <xref:System.Windows.Controls.InkCanvas> as opposed to children.</span></span> <span data-ttu-id="235ae-146">而且按鈕的級別高於疊置順序，所以筆跡轉譯在其後。</span><span class="sxs-lookup"><span data-stu-id="235ae-146">Also, the buttons are higher in the z-order, so the ink is rendered behind them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="235ae-147">請參閱</span><span class="sxs-lookup"><span data-stu-id="235ae-147">See Also</span></span>  
 <xref:System.Windows.Ink.DrawingAttributes>  
 <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>  
 <xref:System.Windows.Ink>
