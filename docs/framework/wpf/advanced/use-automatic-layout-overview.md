---
title: 使用自動配置概觀
ms.date: 03/30/2017
helpviewer_keywords:
- layout [WPF], automatic
- automatic layout [WPF]
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
ms.openlocfilehash: 4cb351b0db83bd83c17aa4aca004b310dc957437
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609599"
---
# <a name="use-automatic-layout-overview"></a>使用自動配置概觀
本主題將介紹如何撰寫的開發人員的指導方針[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]含有可當地語系化的應用程式[!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)]。 在過去，當地語系化的 UI 會是耗時的程序。 針對調整 UI，是每一種語言所需的像素的像素調整。 使用正確的設計和正確的編碼標準，今日[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]可以建構，讓當地語系化人員擁有較少的調整大小和重新調整位置作業執行。 撰寫應用程式都可以更輕鬆地調整大小和重新置放方法稱為自動版面配置，並可藉由使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式的設計。  

<a name="advantages_of_autolayout"></a>   
## <a name="advantages-of-using-automatic-layout"></a>使用自動版面配置的優點  
 因為[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的呈現系統，是功能強大且靈活，提供可以進行調整以符合不同的語言需求的應用程式中的配置元素的能力。 下列清單提出一些自動版面配置的優點。  

-   UI 會顯示能以任何語言。  

-   減少在翻譯文字之後重新調整控制項位置和大小的需求。  
  
-   減少重新調整視窗大小的需求。  

-   以任何語言，UI 配置正確轉譯。  

-   可將當地語系化降低為只比字串翻譯多一點點的程度。  
  
<a name="autolayout_controls"></a>   
## <a name="automatic-layout-and-controls"></a>自動版面配置和控制項  
 自動版面配置可讓應用程式自動調整控制項的大小。 例如，控制項可變更以容納字串的長度。 此功能可讓當地語系化工具翻譯該字串；它們不再需要調整控制項的大小來符合翻譯的文字。 下列範例會建立一個含有英文內容的按鈕。  
  
 [!code-xaml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 在範例中，您唯一需要對西班牙文按鈕做的是變更文字。 例如，套用至物件的  
  
 [!code-xaml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 下圖顯示程式碼範例的輸出。  
  
 ![按鈕相同，但以不同語言的文字](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")  
可自動調整大小的按鈕  
  
<a name="autolayout_coding"></a>   
## <a name="automatic-layout-and-coding-standards"></a>自動版面配置和編碼標準  
 使用自動版面配置方法需要一組編碼和設計標準與規則，以產生完全當地語系化的 UI。 下列指導方針將有助於自動版面配置編碼。  

**請勿使用絕對位置**

- 請勿使用<xref:System.Windows.Controls.Canvas>因為其元素進行絕對定位。

- 使用<xref:System.Windows.Controls.DockPanel>， <xref:System.Windows.Controls.StackPanel>，和<xref:System.Windows.Controls.Grid>來定位控制項。

如需各種面板類型的說明，請參閱[面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)。

**未設定視窗的固定的大小**

- 使用 <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType>。 例如: 

   [!code-xaml[LocalizationGrid#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)]

**新增 <xref:System.Windows.FrameworkElement.FlowDirection%2A>**

- 新增<xref:System.Windows.FrameworkElement.FlowDirection%2A>至您的應用程式的根項目。

   WPF 提供便利的方式，來支援水平、 雙向和垂直版面配置。 在展示架構<xref:System.Windows.FrameworkElement.FlowDirection%2A>屬性可用來定義版面配置。 書寫方向模式如下：
   
     - <xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> (LrTb)-拉丁文、 東亞等的水平配置。
     
     - <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb)，如阿拉伯文、 希伯來文等雙向。

**使用複合字型，而不是實體字型**

- 透過複合字型，<xref:System.Windows.Controls.Control.FontFamily%2A>屬性不需要當地語系化。

- 開發人員可以使用下列其中一個字型，或自行建立。

   - Global User Interface
   - 全域新細明體
   - 全域有襯線字型

**新增 xml: lang**

- 新增`xml:lang`屬性，是在根元素的 UI，例如`xml:lang="en-US"`英文版的應用程式。

- 因為複合字型使用`xml:lang`來判斷要使用的字型，請設定這個屬性，以支援多國語言案例。

<a name="autolay_grids"></a>   
## <a name="automatic-layout-and-grids"></a>自動版面配置和方格  
 <xref:System.Windows.Controls.Grid>項目，可用於自動版面配置，因為它可讓開發人員定位項目。 A<xref:System.Windows.Controls.Grid>控制項可以分散在其子元素之間，使用資料行和資料列的排列方式的可用空間。 UI 項目可以跨越多個資料格，您也可以將方格內部含有方格。 方格非常有用，因為它們可讓您建立並放置複雜的 UI。 下列範例示範如何使用方格來定位部分按鈕和文字。 請注意，儲存格的寬度與高度設為<xref:System.Windows.GridUnitType.Auto>; 因此，包含與映像按鈕的資料格會調整，以符合影像大小。  

 [!code-xaml[LocalizationGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 下圖顯示由先前程式碼所產生的方格。  
  
 ![格線範例](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")  
Grid  
  
<a name="autolay_grids_issharedsizescope"></a>   
## <a name="automatic-layout-and-grids-using-the-issharedsizescope-property"></a>使用 IsSharedSizeScope 屬性的自動版面配置和方格  
 A<xref:System.Windows.Controls.Grid>項目是用於可當地語系化的應用程式，以配合內容調整的控制項。 不過，有時您想要讓控制項不論內容為何，都會維持特定的大小。 例如，如果您擁有 [確定]、[取消] 和 [瀏覽] 按鈕，您可能不想調整按鈕的大小以符合內容。 在此情況下<xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType>附加的屬性可用於共用相同的調整大小，在多個方格元素之間。 下列範例示範如何在共用資料行和調整大小的倍數之間的資料的資料列<xref:System.Windows.Controls.Grid>項目。  
  
 [!code-xaml[gridIssharedsizescopeProp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 **附註**如需完整的程式碼範例，請參閱[共用調整大小屬性方格之間](../../../../docs/framework/wpf/controls/how-to-share-sizing-properties-between-grids.md)  
  
## <a name="see-also"></a>另請參閱
- [WPF 的全球化](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)
- [使用自動版面配置建立按鈕](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)
- [針對自動版面配置使用方格](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)
