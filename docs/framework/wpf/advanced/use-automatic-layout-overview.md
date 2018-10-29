---
title: 使用自動配置概觀
ms.date: 03/30/2017
helpviewer_keywords:
- layout [WPF], automatic
- automatic layout [WPF]
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
ms.openlocfilehash: d6ed0da9be32a4a4de4111acfb2d347b7bd5096d
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201552"
---
# <a name="use-automatic-layout-overview"></a><span data-ttu-id="d2960-102">使用自動配置概觀</span><span class="sxs-lookup"><span data-stu-id="d2960-102">Use Automatic Layout Overview</span></span>
<span data-ttu-id="d2960-103">本主題將介紹如何撰寫的開發人員的指導方針[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]含有可當地語系化的應用程式[!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d2960-103">This topic introduces guidelines for developers on how to write [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] applications with localizable [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)].</span></span> <span data-ttu-id="d2960-104">在過去，當地語系化的 UI 會是耗時的程序。</span><span class="sxs-lookup"><span data-stu-id="d2960-104">In the past, localization of a UI was a time consuming process.</span></span> <span data-ttu-id="d2960-105">針對調整 UI，是每一種語言所需的像素的像素調整。</span><span class="sxs-lookup"><span data-stu-id="d2960-105">Each language that the UI was adapted for required a pixel by pixel adjustment.</span></span> <span data-ttu-id="d2960-106">使用正確的設計和正確的編碼標準，今日[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]可以建構，讓當地語系化人員擁有較少的調整大小和重新調整位置作業執行。</span><span class="sxs-lookup"><span data-stu-id="d2960-106">Today with the right design and right coding standards, [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] can be constructed so that localizers have less resizing and repositioning to do.</span></span> <span data-ttu-id="d2960-107">撰寫應用程式都可以更輕鬆地調整大小和重新置放方法稱為自動版面配置，並可藉由使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式的設計。</span><span class="sxs-lookup"><span data-stu-id="d2960-107">The approach to writing applications that can be more easily resized and repositioned is called automatic layout, and can be achieved by using [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application design.</span></span>  

<a name="advantages_of_autolayout"></a>   
## <a name="advantages-of-using-automatic-layout"></a><span data-ttu-id="d2960-108">使用自動版面配置的優點</span><span class="sxs-lookup"><span data-stu-id="d2960-108">Advantages of Using Automatic Layout</span></span>  
 <span data-ttu-id="d2960-109">因為[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的呈現系統，是功能強大且靈活，提供可以進行調整以符合不同的語言需求的應用程式中的配置元素的能力。</span><span class="sxs-lookup"><span data-stu-id="d2960-109">Because the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] presentation system is powerful and flexible, it provides the ability to layout elements in an application that can be adjusted to fit the requirements of different languages.</span></span> <span data-ttu-id="d2960-110">下列清單提出一些自動版面配置的優點。</span><span class="sxs-lookup"><span data-stu-id="d2960-110">The following list points out some of the advantages of automatic layout.</span></span>  

-   <span data-ttu-id="d2960-111">UI 會顯示能以任何語言。</span><span class="sxs-lookup"><span data-stu-id="d2960-111">UI displays well  in any language.</span></span>  

-   <span data-ttu-id="d2960-112">減少在翻譯文字之後重新調整控制項位置和大小的需求。</span><span class="sxs-lookup"><span data-stu-id="d2960-112">Reduces the need to readjust position and size of controls after text is translated.</span></span>  
  
-   <span data-ttu-id="d2960-113">減少重新調整視窗大小的需求。</span><span class="sxs-lookup"><span data-stu-id="d2960-113">Reduces the need to readjust window size.</span></span>  

-   <span data-ttu-id="d2960-114">以任何語言，UI 配置正確轉譯。</span><span class="sxs-lookup"><span data-stu-id="d2960-114">UI layout renders properly in any language.</span></span>  

-   <span data-ttu-id="d2960-115">可將當地語系化降低為只比字串翻譯多一點點的程度。</span><span class="sxs-lookup"><span data-stu-id="d2960-115">Localization can be reduced to the point that it is little more than string translation.</span></span>  
  
<a name="autolayout_controls"></a>   
## <a name="automatic-layout-and-controls"></a><span data-ttu-id="d2960-116">自動版面配置和控制項</span><span class="sxs-lookup"><span data-stu-id="d2960-116">Automatic Layout and Controls</span></span>  
 <span data-ttu-id="d2960-117">自動版面配置可讓應用程式自動調整控制項的大小。</span><span class="sxs-lookup"><span data-stu-id="d2960-117">Automatic layout enables an application to adjust the size of a control automatically.</span></span> <span data-ttu-id="d2960-118">例如，控制項可變更以容納字串的長度。</span><span class="sxs-lookup"><span data-stu-id="d2960-118">For example, a control can change to accommodate the length of a string.</span></span> <span data-ttu-id="d2960-119">此功能可讓當地語系化工具翻譯該字串；它們不再需要調整控制項的大小來符合翻譯的文字。</span><span class="sxs-lookup"><span data-stu-id="d2960-119">This capability enables  localizers to translate the string; they no longer need to resize the control to fit the translated text.</span></span> <span data-ttu-id="d2960-120">下列範例會建立一個含有英文內容的按鈕。</span><span class="sxs-lookup"><span data-stu-id="d2960-120">The following example creates a button with English content.</span></span>  
  
 [!code-xaml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="d2960-121">在範例中，您唯一需要對西班牙文按鈕做的是變更文字。</span><span class="sxs-lookup"><span data-stu-id="d2960-121">In the example, all you have to do to make a Spanish button is change the text.</span></span> <span data-ttu-id="d2960-122">例如，套用至物件的</span><span class="sxs-lookup"><span data-stu-id="d2960-122">For example,</span></span>  
  
 [!code-xaml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="d2960-123">下圖顯示程式碼範例的輸出。</span><span class="sxs-lookup"><span data-stu-id="d2960-123">The following graphic shows the output of the code samples.</span></span>  
  
 <span data-ttu-id="d2960-124">![按鈕相同，但以不同語言的文字](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")</span><span class="sxs-lookup"><span data-stu-id="d2960-124">![The same button with text in different languages](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")</span></span>  
<span data-ttu-id="d2960-125">可自動調整大小的按鈕</span><span class="sxs-lookup"><span data-stu-id="d2960-125">Auto Resizable Button</span></span>  
  
<a name="autolayout_coding"></a>   
## <a name="automatic-layout-and-coding-standards"></a><span data-ttu-id="d2960-126">自動版面配置和編碼標準</span><span class="sxs-lookup"><span data-stu-id="d2960-126">Automatic Layout and Coding Standards</span></span>  
 <span data-ttu-id="d2960-127">使用自動版面配置方法需要一組編碼和設計標準與規則，以產生完全當地語系化的 UI。</span><span class="sxs-lookup"><span data-stu-id="d2960-127">Using the automatic layout approach requires a set of coding and design standards and rules to produce a fully localizable UI.</span></span> <span data-ttu-id="d2960-128">下列指導方針將有助於自動版面配置編碼。</span><span class="sxs-lookup"><span data-stu-id="d2960-128">The following guidelines will aid your automatic layout coding.</span></span>  

<span data-ttu-id="d2960-129">**請勿使用絕對位置**</span><span class="sxs-lookup"><span data-stu-id="d2960-129">**Do not use absolute positions**</span></span>

- <span data-ttu-id="d2960-130">請勿使用<xref:System.Windows.Controls.Canvas>因為其元素進行絕對定位。</span><span class="sxs-lookup"><span data-stu-id="d2960-130">Do not use <xref:System.Windows.Controls.Canvas> because it positions elements absolutely.</span></span>

- <span data-ttu-id="d2960-131">使用<xref:System.Windows.Controls.DockPanel>， <xref:System.Windows.Controls.StackPanel>，和<xref:System.Windows.Controls.Grid>來定位控制項。</span><span class="sxs-lookup"><span data-stu-id="d2960-131">Use <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel>, and <xref:System.Windows.Controls.Grid> to position controls.</span></span>

<span data-ttu-id="d2960-132">如需各種面板類型的說明，請參閱[面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d2960-132">For a discussion about various types of panels, see [Panels Overview](../../../../docs/framework/wpf/controls/panels-overview.md).</span></span>

<span data-ttu-id="d2960-133">**未設定視窗的固定的大小**</span><span class="sxs-lookup"><span data-stu-id="d2960-133">**Do not set a fixed size for a window**</span></span>

- <span data-ttu-id="d2960-134">使用 <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="d2960-134">Use <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d2960-135">例如: </span><span class="sxs-lookup"><span data-stu-id="d2960-135">For example:</span></span>

   [!code-xaml[LocalizationGrid#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)]

<span data-ttu-id="d2960-136">**新增 <xref:System.Windows.FrameworkElement.FlowDirection%2A>**</span><span class="sxs-lookup"><span data-stu-id="d2960-136">**Add a <xref:System.Windows.FrameworkElement.FlowDirection%2A>**</span></span>

- <span data-ttu-id="d2960-137">新增<xref:System.Windows.FrameworkElement.FlowDirection%2A>至您的應用程式的根項目。</span><span class="sxs-lookup"><span data-stu-id="d2960-137">Add a <xref:System.Windows.FrameworkElement.FlowDirection%2A> to the root element of your application.</span></span>

   <span data-ttu-id="d2960-138">WPF 提供便利的方式，來支援水平、 雙向和垂直版面配置。</span><span class="sxs-lookup"><span data-stu-id="d2960-138">WPF provides a convenient way to support horizontal, bidirectional, and vertical layouts.</span></span> <span data-ttu-id="d2960-139">在展示架構<xref:System.Windows.FrameworkElement.FlowDirection%2A>屬性可用來定義版面配置。</span><span class="sxs-lookup"><span data-stu-id="d2960-139">In presentation framework, the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property can be used to define layout.</span></span> <span data-ttu-id="d2960-140">書寫方向模式如下：</span><span class="sxs-lookup"><span data-stu-id="d2960-140">The flow-direction patterns are:</span></span>
   
     - <span data-ttu-id="d2960-141"><xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> (LrTb)-拉丁文、 東亞等的水平配置。</span><span class="sxs-lookup"><span data-stu-id="d2960-141"><xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> (LrTb) — horizontal layout for Latin, East Asian, and so forth.</span></span>
     
     - <span data-ttu-id="d2960-142"><xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb)，如阿拉伯文、 希伯來文等雙向。</span><span class="sxs-lookup"><span data-stu-id="d2960-142"><xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb) — bidirectional for Arabic, Hebrew, and so forth.</span></span>

<span data-ttu-id="d2960-143">**使用複合字型，而不是實體字型**</span><span class="sxs-lookup"><span data-stu-id="d2960-143">**Use composite fonts instead of physical fonts**</span></span>

- <span data-ttu-id="d2960-144">透過複合字型，<xref:System.Windows.Controls.Control.FontFamily%2A>屬性不需要當地語系化。</span><span class="sxs-lookup"><span data-stu-id="d2960-144">With composite fonts, the <xref:System.Windows.Controls.Control.FontFamily%2A> property does not need to be localized.</span></span>

- <span data-ttu-id="d2960-145">開發人員可以使用下列其中一個字型，或自行建立。</span><span class="sxs-lookup"><span data-stu-id="d2960-145">Developers can use one of the following fonts or create their own.</span></span>

   - <span data-ttu-id="d2960-146">Global User Interface</span><span class="sxs-lookup"><span data-stu-id="d2960-146">Global User Interface</span></span>
   - <span data-ttu-id="d2960-147">全域新細明體</span><span class="sxs-lookup"><span data-stu-id="d2960-147">Global San Serif</span></span>
   - <span data-ttu-id="d2960-148">全域有襯線字型</span><span class="sxs-lookup"><span data-stu-id="d2960-148">Global Serif</span></span>

<span data-ttu-id="d2960-149">**新增 xml: lang**</span><span class="sxs-lookup"><span data-stu-id="d2960-149">**Add xml:lang**</span></span>

- <span data-ttu-id="d2960-150">新增`xml:lang`屬性，是在根元素的 UI，例如`xml:lang="en-US"`英文版的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d2960-150">Add the `xml:lang` attribute in the root element of your UI, such as `xml:lang="en-US"` for an English application.</span></span>

- <span data-ttu-id="d2960-151">因為複合字型使用`xml:lang`來判斷要使用的字型，請設定這個屬性，以支援多國語言案例。</span><span class="sxs-lookup"><span data-stu-id="d2960-151">Because composite fonts use `xml:lang` to determine what font to use, set this property to support multilingual scenarios.</span></span>

<a name="autolay_grids"></a>   
## <a name="automatic-layout-and-grids"></a><span data-ttu-id="d2960-152">自動版面配置和方格</span><span class="sxs-lookup"><span data-stu-id="d2960-152">Automatic Layout and Grids</span></span>  
 <span data-ttu-id="d2960-153"><xref:System.Windows.Controls.Grid>項目，可用於自動版面配置，因為它可讓開發人員定位項目。</span><span class="sxs-lookup"><span data-stu-id="d2960-153">The <xref:System.Windows.Controls.Grid> element, is useful for automatic layout because it enables a developer to position elements.</span></span> <span data-ttu-id="d2960-154">A<xref:System.Windows.Controls.Grid>控制項可以分散在其子元素之間，使用資料行和資料列的排列方式的可用空間。</span><span class="sxs-lookup"><span data-stu-id="d2960-154">A <xref:System.Windows.Controls.Grid> control is capable of distributing the available space among its child elements, using a column and row arrangement.</span></span> <span data-ttu-id="d2960-155">UI 項目可以跨越多個資料格，您也可以將方格內部含有方格。</span><span class="sxs-lookup"><span data-stu-id="d2960-155">The UI elements can span multiple cells, and it is possible to have grids within grids.</span></span> <span data-ttu-id="d2960-156">方格非常有用，因為它們可讓您建立並放置複雜的 UI。</span><span class="sxs-lookup"><span data-stu-id="d2960-156">Grids are useful because they enable you to create and position complex UI.</span></span> <span data-ttu-id="d2960-157">下列範例示範如何使用方格來定位部分按鈕和文字。</span><span class="sxs-lookup"><span data-stu-id="d2960-157">The following example demonstrates using a grid to position some buttons and text.</span></span> <span data-ttu-id="d2960-158">請注意，儲存格的寬度與高度設為<xref:System.Windows.GridUnitType.Auto>; 因此，包含與映像按鈕的資料格會調整，以符合影像大小。</span><span class="sxs-lookup"><span data-stu-id="d2960-158">Notice that the height and width of the cells are set to <xref:System.Windows.GridUnitType.Auto>; therefore, the cell that contains the button with an image adjusts to fit the image.</span></span>  

 [!code-xaml[LocalizationGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="d2960-159">下圖顯示由先前程式碼所產生的方格。</span><span class="sxs-lookup"><span data-stu-id="d2960-159">The following graphic shows the grid produced by the previous code.</span></span>  
  
 <span data-ttu-id="d2960-160">![格線範例](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")</span><span class="sxs-lookup"><span data-stu-id="d2960-160">![Grid example](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")</span></span>  
<span data-ttu-id="d2960-161">Grid</span><span class="sxs-lookup"><span data-stu-id="d2960-161">Grid</span></span>  
  
<a name="autolay_grids_issharedsizescope"></a>   
## <a name="automatic-layout-and-grids-using-the-issharedsizescope-property"></a><span data-ttu-id="d2960-162">使用 IsSharedSizeScope 屬性的自動版面配置和方格</span><span class="sxs-lookup"><span data-stu-id="d2960-162">Automatic Layout and Grids Using the IsSharedSizeScope Property</span></span>  
 <span data-ttu-id="d2960-163">A<xref:System.Windows.Controls.Grid>項目是用於可當地語系化的應用程式，以配合內容調整的控制項。</span><span class="sxs-lookup"><span data-stu-id="d2960-163">A <xref:System.Windows.Controls.Grid> element is useful in localizable applications to create controls that adjust to fit content.</span></span> <span data-ttu-id="d2960-164">不過，有時您想要讓控制項不論內容為何，都會維持特定的大小。</span><span class="sxs-lookup"><span data-stu-id="d2960-164">However, at times you want controls to maintain a particular size regardless of content.</span></span> <span data-ttu-id="d2960-165">例如，如果您擁有 [確定]、[取消] 和 [瀏覽] 按鈕，您可能不想調整按鈕的大小以符合內容。</span><span class="sxs-lookup"><span data-stu-id="d2960-165">For example, if you have "OK", "Cancel" and "Browse" buttons you probably do not want the buttons sized to fit the content.</span></span> <span data-ttu-id="d2960-166">在此情況下<xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType>附加的屬性可用於共用相同的調整大小，在多個方格元素之間。</span><span class="sxs-lookup"><span data-stu-id="d2960-166">In this case the <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> attached property is useful for sharing the same sizing among multiple grid elements.</span></span> <span data-ttu-id="d2960-167">下列範例示範如何在共用資料行和調整大小的倍數之間的資料的資料列<xref:System.Windows.Controls.Grid>項目。</span><span class="sxs-lookup"><span data-stu-id="d2960-167">The following example demonstrates how to share column and row sizing data between multiple <xref:System.Windows.Controls.Grid> elements.</span></span>  
  
 [!code-xaml[gridIssharedsizescopeProp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="d2960-168">**附註**如需完整的程式碼範例，請參閱[共用調整大小屬性方格之間](../../../../docs/framework/wpf/controls/how-to-share-sizing-properties-between-grids.md)</span><span class="sxs-lookup"><span data-stu-id="d2960-168">**Note** For the complete code sample, see [Share Sizing Properties Between Grids](../../../../docs/framework/wpf/controls/how-to-share-sizing-properties-between-grids.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2960-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2960-169">See Also</span></span>  
 [<span data-ttu-id="d2960-170">WPF 的全球化</span><span class="sxs-lookup"><span data-stu-id="d2960-170">Globalization for WPF</span></span>](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)  
 [<span data-ttu-id="d2960-171">使用自動版面配置建立按鈕</span><span class="sxs-lookup"><span data-stu-id="d2960-171">Use Automatic Layout to Create a Button</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)  
 [<span data-ttu-id="d2960-172">針對自動版面配置使用方格</span><span class="sxs-lookup"><span data-stu-id="d2960-172">Use a Grid for Automatic Layout</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)
