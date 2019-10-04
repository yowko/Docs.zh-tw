---
title: 使用自動配置概觀
ms.date: 03/30/2017
helpviewer_keywords:
- layout [WPF], automatic
- automatic layout [WPF]
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
ms.openlocfilehash: 0253c57f080705b648d9f416368d0fe974ac83ab
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834674"
---
# <a name="use-automatic-layout-overview"></a>使用自動配置概觀

本主題將為開發人員介紹如何使用可當地語系化的 [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)] 撰寫 @no__t 0 應用程式的指導方針。 在過去，UI 的當地語系化是耗時的程式。 UI 針對所需調整的每一種語言，都需要圖元的圖元。 現在有了正確的設計和正確的編碼標準，[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] 可以加以建造，讓當地語系化人員的調整大小和重新置放工作不會改變。 撰寫可以更輕鬆調整大小和重新置放之應用程式的方法稱為「自動設定」，而且可以使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式設計來達成。

<a name="advantages_of_autolayout"></a>

## <a name="advantages-of-using-automatic-layout"></a>使用自動版面配置的優點

由於 @no__t 0 呈現系統的功能強大且有彈性，因此可讓您在應用程式中版面配置元素，以符合不同語言的需求。 下列清單提出一些自動版面配置的優點。

- UI 會以任何語言適當地顯示。

- 減少在翻譯文字之後重新調整控制項位置和大小的需求。

- 減少重新調整視窗大小的需求。

- UI 版面配置會以任何語言正確呈現。

- 可將當地語系化降低為只比字串翻譯多一點點的程度。

<a name="autolayout_controls"></a>

## <a name="automatic-layout-and-controls"></a>自動版面配置和控制項

自動版面配置可讓應用程式自動調整控制項的大小。 例如，控制項可變更以容納字串的長度。 此功能可讓當地語系化工具翻譯該字串；它們不再需要調整控制項的大小來符合翻譯的文字。 下列範例會建立一個含有英文內容的按鈕。

[!code-xaml[LocalizationBtn_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]

在範例中，您唯一需要對西班牙文按鈕做的是變更文字。 例如，套用至物件的

[!code-xaml[LocalizationBtn#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]

下圖顯示程式碼範例的輸出：

![按鈕相同，但文字的語言不同](./media/use-automatic-layout-overview/auto-resizable-button.png)

<a name="autolayout_coding"></a>

## <a name="automatic-layout-and-coding-standards"></a>自動版面配置和編碼標準

使用自動版面配置方法需要一組編碼和設計標準和規則，以產生可完全當地語系化的 UI。 下列指導方針將有助於自動版面配置編碼。

**不要使用絕對位置**

- 請勿使用 <xref:System.Windows.Controls.Canvas>，因為它會將元素放在絕對的位置。

- 使用 <xref:System.Windows.Controls.DockPanel>、<xref:System.Windows.Controls.StackPanel> 和 <xref:System.Windows.Controls.Grid> 來定位控制項。

如需各種面板類型的討論，請參閱[面板總覽](../controls/panels-overview.md)。

**不要設定視窗的固定大小**

- 使用 <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType>。 例如:

  [!code-xaml[LocalizationGrid#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)]

**新增 <xref:System.Windows.FrameworkElement.FlowDirection%2A>**

- 將 <xref:System.Windows.FrameworkElement.FlowDirection%2A> 新增至應用程式的根項目。

  WPF 提供便利的方式來支援水準、雙向和垂直版面配置。 在展示架構中，可以使用 <xref:System.Windows.FrameworkElement.FlowDirection%2A> 屬性來定義版面配置。 書寫方向模式如下：

  - <xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> （LrTb）—拉丁、東亞等的水準配置。

  - <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> （RlTb）—適用于阿拉伯文、希伯來文等等的雙向。

**使用複合字型，而不是實體字型**

- 使用複合字型時，<xref:System.Windows.Controls.Control.FontFamily%2A> 屬性不需要當地語系化。

- 開發人員可以使用下列其中一個字型，或自行建立。

  - Global User Interface
  - 全域新細明體
  - 全域有襯線字型

**新增 xml： lang**

- 在 UI 的根項目中新增 `xml:lang` 屬性，例如英文應用程式的 `xml:lang="en-US"`。

- 由於複合字型會使用 `xml:lang` 來判斷要使用的字型，因此請將此屬性設定為支援多語系案例。

<a name="autolay_grids"></a>

## <a name="automatic-layout-and-grids"></a>自動版面配置和方格

@No__t-0 元素適用于自動版面配置，因為它可讓開發人員定位元素。 @No__t 0 控制項能夠使用資料行和資料列的相片順序，在其子專案之間散發可用的空間。 UI 元素可以跨越多個資料格，而且格線中可能會有方格。 格線很有用，因為它們可讓您建立和定位複雜的 UI。 下列範例示範如何使用方格來定位部分按鈕和文字。 請注意，資料格的高度和寬度都設定為 <xref:System.Windows.GridUnitType.Auto>;因此，包含具有影像之按鈕的儲存格會調整以符合影像。

[!code-xaml[LocalizationGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]

下圖顯示由先前程式碼所產生的方格。

![方格範例](./media/glob-grid.png "glob_grid")方格

<a name="autolay_grids_issharedsizescope"></a>

## <a name="automatic-layout-and-grids-using-the-issharedsizescope-property"></a>使用 IsSharedSizeScope 屬性的自動版面配置和方格

@No__t 0 元素在可當地語系化的應用程式中很有用，可以建立調整以符合內容的控制項。 不過，有時您想要讓控制項不論內容為何，都會維持特定的大小。 例如，如果您擁有 [確定]、[取消] 和 [瀏覽] 按鈕，您可能不想調整按鈕的大小以符合內容。 在此情況下，@no__t 0 附加屬性適用于在多個方格元素之間共用相同的大小。 下列範例示範如何在多個 <xref:System.Windows.Controls.Grid> 個元素之間共用資料行和資料列大小。

[!code-xaml[gridIssharedsizescopeProp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]

> [!NOTE]
> 如需完整的程式碼範例，請參閱[在格線之間共用大小屬性](../controls/how-to-share-sizing-properties-between-grids.md)。

## <a name="see-also"></a>另請參閱

- [WPF 的全球化](globalization-for-wpf.md)
- [使用自動版面配置建立按鈕](how-to-use-automatic-layout-to-create-a-button.md)
- [針對自動版面配置使用方格](how-to-use-a-grid-for-automatic-layout.md)
