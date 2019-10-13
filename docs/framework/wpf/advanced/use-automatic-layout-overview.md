---
title: 使用自動配置概觀
ms.date: 03/30/2017
helpviewer_keywords:
- layout [WPF], automatic
- automatic layout [WPF]
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
ms.openlocfilehash: 2fe473da3eeabef3852e3003e61b3b9604332855
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291265"
---
# <a name="use-automatic-layout-overview"></a><span data-ttu-id="0ba44-102">使用自動配置概觀</span><span class="sxs-lookup"><span data-stu-id="0ba44-102">Use Automatic Layout Overview</span></span>

<span data-ttu-id="0ba44-103">本主題將為開發人員介紹如何使用可當地語系化的使用者介面（Ui）撰寫 @no__t 0 應用程式的指導方針。</span><span class="sxs-lookup"><span data-stu-id="0ba44-103">This topic introduces guidelines for developers on how to write [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] applications with localizable user interfaces (UIs).</span></span> <span data-ttu-id="0ba44-104">在過去，UI 的當地語系化是耗時的程式。</span><span class="sxs-lookup"><span data-stu-id="0ba44-104">In the past, localization of a UI was a time consuming process.</span></span> <span data-ttu-id="0ba44-105">UI 針對所需調整的每一種語言，都需要圖元的圖元。</span><span class="sxs-lookup"><span data-stu-id="0ba44-105">Each language that the UI was adapted for required a pixel by pixel adjustment.</span></span> <span data-ttu-id="0ba44-106">現在有了正確的設計和正確的編碼標準，可以將 Ui 結構化，讓當地語系化人員的調整大小和重新置放工作更少。</span><span class="sxs-lookup"><span data-stu-id="0ba44-106">Today with the right design and right coding standards, UIs can be constructed so that localizers have less resizing and repositioning to do.</span></span> <span data-ttu-id="0ba44-107">撰寫可以更輕鬆調整大小和重新置放之應用程式的方法稱為「自動設定」，而且可以使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式設計來達成。</span><span class="sxs-lookup"><span data-stu-id="0ba44-107">The approach to writing applications that can be more easily resized and repositioned is called automatic layout, and can be achieved by using [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application design.</span></span>

<a name="advantages_of_autolayout"></a>

## <a name="advantages-of-using-automatic-layout"></a><span data-ttu-id="0ba44-108">使用自動版面配置的優點</span><span class="sxs-lookup"><span data-stu-id="0ba44-108">Advantages of Using Automatic Layout</span></span>

<span data-ttu-id="0ba44-109">由於 @no__t 0 呈現系統的功能強大且有彈性，因此可讓您在應用程式中版面配置元素，以符合不同語言的需求。</span><span class="sxs-lookup"><span data-stu-id="0ba44-109">Because the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] presentation system is powerful and flexible, it provides the ability to layout elements in an application that can be adjusted to fit the requirements of different languages.</span></span> <span data-ttu-id="0ba44-110">下列清單提出一些自動版面配置的優點。</span><span class="sxs-lookup"><span data-stu-id="0ba44-110">The following list points out some of the advantages of automatic layout.</span></span>

- <span data-ttu-id="0ba44-111">UI 會以任何語言適當地顯示。</span><span class="sxs-lookup"><span data-stu-id="0ba44-111">UI displays well  in any language.</span></span>

- <span data-ttu-id="0ba44-112">減少在翻譯文字之後重新調整控制項位置和大小的需求。</span><span class="sxs-lookup"><span data-stu-id="0ba44-112">Reduces the need to readjust position and size of controls after text is translated.</span></span>

- <span data-ttu-id="0ba44-113">減少重新調整視窗大小的需求。</span><span class="sxs-lookup"><span data-stu-id="0ba44-113">Reduces the need to readjust window size.</span></span>

- <span data-ttu-id="0ba44-114">UI 版面配置會以任何語言正確呈現。</span><span class="sxs-lookup"><span data-stu-id="0ba44-114">UI layout renders properly in any language.</span></span>

- <span data-ttu-id="0ba44-115">可將當地語系化降低為只比字串翻譯多一點點的程度。</span><span class="sxs-lookup"><span data-stu-id="0ba44-115">Localization can be reduced to the point that it is little more than string translation.</span></span>

<a name="autolayout_controls"></a>

## <a name="automatic-layout-and-controls"></a><span data-ttu-id="0ba44-116">自動版面配置和控制項</span><span class="sxs-lookup"><span data-stu-id="0ba44-116">Automatic Layout and Controls</span></span>

<span data-ttu-id="0ba44-117">自動版面配置可讓應用程式自動調整控制項的大小。</span><span class="sxs-lookup"><span data-stu-id="0ba44-117">Automatic layout enables an application to adjust the size of a control automatically.</span></span> <span data-ttu-id="0ba44-118">例如，控制項可變更以容納字串的長度。</span><span class="sxs-lookup"><span data-stu-id="0ba44-118">For example, a control can change to accommodate the length of a string.</span></span> <span data-ttu-id="0ba44-119">此功能可讓當地語系化工具翻譯該字串；它們不再需要調整控制項的大小來符合翻譯的文字。</span><span class="sxs-lookup"><span data-stu-id="0ba44-119">This capability enables  localizers to translate the string; they no longer need to resize the control to fit the translated text.</span></span> <span data-ttu-id="0ba44-120">下列範例會建立一個含有英文內容的按鈕。</span><span class="sxs-lookup"><span data-stu-id="0ba44-120">The following example creates a button with English content.</span></span>

[!code-xaml[LocalizationBtn_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]

<span data-ttu-id="0ba44-121">在範例中，您唯一需要對西班牙文按鈕做的是變更文字。</span><span class="sxs-lookup"><span data-stu-id="0ba44-121">In the example, all you have to do to make a Spanish button is change the text.</span></span> <span data-ttu-id="0ba44-122">例如，套用至物件的</span><span class="sxs-lookup"><span data-stu-id="0ba44-122">For example,</span></span>

[!code-xaml[LocalizationBtn#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]

<span data-ttu-id="0ba44-123">下圖顯示程式碼範例的輸出：</span><span class="sxs-lookup"><span data-stu-id="0ba44-123">The following graphic shows the output of the code samples:</span></span>

![按鈕相同，但文字的語言不同](./media/use-automatic-layout-overview/auto-resizable-button.png)

<a name="autolayout_coding"></a>

## <a name="automatic-layout-and-coding-standards"></a><span data-ttu-id="0ba44-125">自動版面配置和編碼標準</span><span class="sxs-lookup"><span data-stu-id="0ba44-125">Automatic Layout and Coding Standards</span></span>

<span data-ttu-id="0ba44-126">使用自動版面配置方法需要一組編碼和設計標準和規則，以產生可完全當地語系化的 UI。</span><span class="sxs-lookup"><span data-stu-id="0ba44-126">Using the automatic layout approach requires a set of coding and design standards and rules to produce a fully localizable UI.</span></span> <span data-ttu-id="0ba44-127">下列指導方針將有助於自動版面配置編碼。</span><span class="sxs-lookup"><span data-stu-id="0ba44-127">The following guidelines will aid your automatic layout coding.</span></span>

<span data-ttu-id="0ba44-128">**不要使用絕對位置**</span><span class="sxs-lookup"><span data-stu-id="0ba44-128">**Do not use absolute positions**</span></span>

- <span data-ttu-id="0ba44-129">請勿使用 <xref:System.Windows.Controls.Canvas>，因為它會將元素放在絕對的位置。</span><span class="sxs-lookup"><span data-stu-id="0ba44-129">Do not use <xref:System.Windows.Controls.Canvas> because it positions elements absolutely.</span></span>

- <span data-ttu-id="0ba44-130">使用 <xref:System.Windows.Controls.DockPanel>、<xref:System.Windows.Controls.StackPanel> 和 <xref:System.Windows.Controls.Grid> 來定位控制項。</span><span class="sxs-lookup"><span data-stu-id="0ba44-130">Use <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel>, and <xref:System.Windows.Controls.Grid> to position controls.</span></span>

<span data-ttu-id="0ba44-131">如需各種面板類型的討論，請參閱[面板總覽](../controls/panels-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="0ba44-131">For a discussion about various types of panels, see [Panels Overview](../controls/panels-overview.md).</span></span>

<span data-ttu-id="0ba44-132">**不要設定視窗的固定大小**</span><span class="sxs-lookup"><span data-stu-id="0ba44-132">**Do not set a fixed size for a window**</span></span>

- <span data-ttu-id="0ba44-133">使用 <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="0ba44-133">Use <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0ba44-134">例如:</span><span class="sxs-lookup"><span data-stu-id="0ba44-134">For example:</span></span>

  [!code-xaml[LocalizationGrid#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)]

<span data-ttu-id="0ba44-135">**新增 <xref:System.Windows.FrameworkElement.FlowDirection%2A>**</span><span class="sxs-lookup"><span data-stu-id="0ba44-135">**Add a <xref:System.Windows.FrameworkElement.FlowDirection%2A>**</span></span>

- <span data-ttu-id="0ba44-136">將 <xref:System.Windows.FrameworkElement.FlowDirection%2A> 新增至應用程式的根項目。</span><span class="sxs-lookup"><span data-stu-id="0ba44-136">Add a <xref:System.Windows.FrameworkElement.FlowDirection%2A> to the root element of your application.</span></span>

  <span data-ttu-id="0ba44-137">WPF 提供便利的方式來支援水準、雙向和垂直版面配置。</span><span class="sxs-lookup"><span data-stu-id="0ba44-137">WPF provides a convenient way to support horizontal, bidirectional, and vertical layouts.</span></span> <span data-ttu-id="0ba44-138">在展示架構中，可以使用 <xref:System.Windows.FrameworkElement.FlowDirection%2A> 屬性來定義版面配置。</span><span class="sxs-lookup"><span data-stu-id="0ba44-138">In presentation framework, the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property can be used to define layout.</span></span> <span data-ttu-id="0ba44-139">書寫方向模式如下：</span><span class="sxs-lookup"><span data-stu-id="0ba44-139">The flow-direction patterns are:</span></span>

  - <span data-ttu-id="0ba44-140"><xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> （LrTb）—拉丁、東亞等的水準配置。</span><span class="sxs-lookup"><span data-stu-id="0ba44-140"><xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> (LrTb) — horizontal layout for Latin, East Asian, and so forth.</span></span>

  - <span data-ttu-id="0ba44-141"><xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> （RlTb）—適用于阿拉伯文、希伯來文等等的雙向。</span><span class="sxs-lookup"><span data-stu-id="0ba44-141"><xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb) — bidirectional for Arabic, Hebrew, and so forth.</span></span>

<span data-ttu-id="0ba44-142">**使用複合字型，而不是實體字型**</span><span class="sxs-lookup"><span data-stu-id="0ba44-142">**Use composite fonts instead of physical fonts**</span></span>

- <span data-ttu-id="0ba44-143">使用複合字型時，<xref:System.Windows.Controls.Control.FontFamily%2A> 屬性不需要當地語系化。</span><span class="sxs-lookup"><span data-stu-id="0ba44-143">With composite fonts, the <xref:System.Windows.Controls.Control.FontFamily%2A> property does not need to be localized.</span></span>

- <span data-ttu-id="0ba44-144">開發人員可以使用下列其中一個字型，或自行建立。</span><span class="sxs-lookup"><span data-stu-id="0ba44-144">Developers can use one of the following fonts or create their own.</span></span>

  - <span data-ttu-id="0ba44-145">Global User Interface</span><span class="sxs-lookup"><span data-stu-id="0ba44-145">Global User Interface</span></span>
  - <span data-ttu-id="0ba44-146">全域新細明體</span><span class="sxs-lookup"><span data-stu-id="0ba44-146">Global San Serif</span></span>
  - <span data-ttu-id="0ba44-147">全域有襯線字型</span><span class="sxs-lookup"><span data-stu-id="0ba44-147">Global Serif</span></span>

<span data-ttu-id="0ba44-148">**新增 xml： lang**</span><span class="sxs-lookup"><span data-stu-id="0ba44-148">**Add xml:lang**</span></span>

- <span data-ttu-id="0ba44-149">在 UI 的根項目中新增 `xml:lang` 屬性，例如英文應用程式的 `xml:lang="en-US"`。</span><span class="sxs-lookup"><span data-stu-id="0ba44-149">Add the `xml:lang` attribute in the root element of your UI, such as `xml:lang="en-US"` for an English application.</span></span>

- <span data-ttu-id="0ba44-150">由於複合字型會使用 `xml:lang` 來判斷要使用的字型，因此請將此屬性設定為支援多語系案例。</span><span class="sxs-lookup"><span data-stu-id="0ba44-150">Because composite fonts use `xml:lang` to determine what font to use, set this property to support multilingual scenarios.</span></span>

<a name="autolay_grids"></a>

## <a name="automatic-layout-and-grids"></a><span data-ttu-id="0ba44-151">自動版面配置和方格</span><span class="sxs-lookup"><span data-stu-id="0ba44-151">Automatic Layout and Grids</span></span>

<span data-ttu-id="0ba44-152">@No__t-0 元素適用于自動版面配置，因為它可讓開發人員定位元素。</span><span class="sxs-lookup"><span data-stu-id="0ba44-152">The <xref:System.Windows.Controls.Grid> element, is useful for automatic layout because it enables a developer to position elements.</span></span> <span data-ttu-id="0ba44-153">@No__t 0 控制項能夠使用資料行和資料列的相片順序，在其子專案之間散發可用的空間。</span><span class="sxs-lookup"><span data-stu-id="0ba44-153">A <xref:System.Windows.Controls.Grid> control is capable of distributing the available space among its child elements, using a column and row arrangement.</span></span> <span data-ttu-id="0ba44-154">UI 元素可以跨越多個資料格，而且格線中可能會有方格。</span><span class="sxs-lookup"><span data-stu-id="0ba44-154">The UI elements can span multiple cells, and it is possible to have grids within grids.</span></span> <span data-ttu-id="0ba44-155">格線很有用，因為它們可讓您建立和定位複雜的 UI。</span><span class="sxs-lookup"><span data-stu-id="0ba44-155">Grids are useful because they enable you to create and position complex UI.</span></span> <span data-ttu-id="0ba44-156">下列範例示範如何使用方格來定位部分按鈕和文字。</span><span class="sxs-lookup"><span data-stu-id="0ba44-156">The following example demonstrates using a grid to position some buttons and text.</span></span> <span data-ttu-id="0ba44-157">請注意，資料格的高度和寬度都設定為 <xref:System.Windows.GridUnitType.Auto>;因此，包含具有影像之按鈕的儲存格會調整以符合影像。</span><span class="sxs-lookup"><span data-stu-id="0ba44-157">Notice that the height and width of the cells are set to <xref:System.Windows.GridUnitType.Auto>; therefore, the cell that contains the button with an image adjusts to fit the image.</span></span>

[!code-xaml[LocalizationGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]

<span data-ttu-id="0ba44-158">下圖顯示由先前程式碼所產生的方格。</span><span class="sxs-lookup"><span data-stu-id="0ba44-158">The following graphic shows the grid produced by the previous code.</span></span>

<span data-ttu-id="0ba44-159">![方格範例](./media/glob-grid.png "glob_grid")方格</span><span class="sxs-lookup"><span data-stu-id="0ba44-159">![Grid example](./media/glob-grid.png "glob_grid") Grid</span></span>

<a name="autolay_grids_issharedsizescope"></a>

## <a name="automatic-layout-and-grids-using-the-issharedsizescope-property"></a><span data-ttu-id="0ba44-160">使用 IsSharedSizeScope 屬性的自動版面配置和方格</span><span class="sxs-lookup"><span data-stu-id="0ba44-160">Automatic Layout and Grids Using the IsSharedSizeScope Property</span></span>

<span data-ttu-id="0ba44-161">@No__t 0 元素在可當地語系化的應用程式中很有用，可以建立調整以符合內容的控制項。</span><span class="sxs-lookup"><span data-stu-id="0ba44-161">A <xref:System.Windows.Controls.Grid> element is useful in localizable applications to create controls that adjust to fit content.</span></span> <span data-ttu-id="0ba44-162">不過，有時您想要讓控制項不論內容為何，都會維持特定的大小。</span><span class="sxs-lookup"><span data-stu-id="0ba44-162">However, at times you want controls to maintain a particular size regardless of content.</span></span> <span data-ttu-id="0ba44-163">例如，如果您擁有 [確定]、[取消] 和 [瀏覽] 按鈕，您可能不想調整按鈕的大小以符合內容。</span><span class="sxs-lookup"><span data-stu-id="0ba44-163">For example, if you have "OK", "Cancel" and "Browse" buttons you probably do not want the buttons sized to fit the content.</span></span> <span data-ttu-id="0ba44-164">在此情況下，@no__t 0 附加屬性適用于在多個方格元素之間共用相同的大小。</span><span class="sxs-lookup"><span data-stu-id="0ba44-164">In this case the <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> attached property is useful for sharing the same sizing among multiple grid elements.</span></span> <span data-ttu-id="0ba44-165">下列範例示範如何在多個 <xref:System.Windows.Controls.Grid> 個元素之間共用資料行和資料列大小。</span><span class="sxs-lookup"><span data-stu-id="0ba44-165">The following example demonstrates how to share column and row sizing data between multiple <xref:System.Windows.Controls.Grid> elements.</span></span>

[!code-xaml[gridIssharedsizescopeProp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]

> [!NOTE]
> <span data-ttu-id="0ba44-166">如需完整的程式碼範例，請參閱[在格線之間共用大小屬性](../controls/how-to-share-sizing-properties-between-grids.md)。</span><span class="sxs-lookup"><span data-stu-id="0ba44-166">For the complete code sample, see [Share Sizing Properties Between Grids](../controls/how-to-share-sizing-properties-between-grids.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0ba44-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ba44-167">See also</span></span>

- [<span data-ttu-id="0ba44-168">WPF 的全球化</span><span class="sxs-lookup"><span data-stu-id="0ba44-168">Globalization for WPF</span></span>](globalization-for-wpf.md)
- [<span data-ttu-id="0ba44-169">使用自動版面配置建立按鈕</span><span class="sxs-lookup"><span data-stu-id="0ba44-169">Use Automatic Layout to Create a Button</span></span>](how-to-use-automatic-layout-to-create-a-button.md)
- [<span data-ttu-id="0ba44-170">針對自動版面配置使用方格</span><span class="sxs-lookup"><span data-stu-id="0ba44-170">Use a Grid for Automatic Layout</span></span>](how-to-use-a-grid-for-automatic-layout.md)
