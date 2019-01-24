---
title: OpenType 字型功能
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [WPF], OpenType
- typography [WPF], OpenType font technology
- OpenType font technology [WPF]
ms.assetid: 4061a9d1-fe8b-4921-9e17-18ec7d2e3ea2
ms.openlocfilehash: 5751efe0c6621425b8b54c642d51127118c0b6bf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54529776"
---
# <a name="opentype-font-features"></a>OpenType 字型功能
本主題提供 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 的 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型技術重要功能概觀。  
  

  
<a name="overview"></a>   
## <a name="opentype-font-format"></a>OpenType 字型格式  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型格式是 [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] 字型格式的延伸模組，新增 PostScript 字型資料的支援。 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型格式是由 [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] 和 Adobe Corporation 共同開發。 支援 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型的 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型和作業系統服務，提供使用者簡單的字型安裝與使用方式，無論字型包含 [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] 外框或 CFF (PostScript) 外框。  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型格式解決下列開發人員難題︰  
  
-   更廣泛的多平台支援。  
  
-   更好的國際字元集支援。  
  
-   更好的字型資料保護。  
  
-   較小的檔案大小，讓字型發佈更有效率。  
  
-   進階印刷樣式控制項的廣泛支援。  
  
> [!NOTE]
>  此 Windows SDK 包含一組範例 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型，可與 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式搭配使用。 本主題後文會說明這些字型提供的大部分功能。 如需詳細資訊，請參閱[範例 OpenType 字型套件](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md)。  
  
 如需 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型格式的詳細資訊，請參閱 [OpenType 規格](https://go.microsoft.com/fwlink/?LinkId=96731)。  
  
### <a name="advanced-typographic-extensions"></a>進階的印刷樣式延伸模組  
 進階印刷樣式資料表 ([!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 版面配置表格) 使用 [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] 或 CFF 外框來擴充字型功能。 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 版面配置字型包含延伸字型功能的其他資訊，支援高品質的國際印刷樣式。 大部分 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型只公開總計的 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 可用功能子集。 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型提供下列功能。  
  
-   字元與字符之間的豐富對應，支援連音符號、位置形式、替代項目，以及其他字型替代項目。  
  
-   支援二維定位與字符附件。  
  
-   字型中包含明確的指令碼和語言資訊，因此文字處理應用程式可據以調整其行為。  
  
 在 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 規格的[字型檔案表格＞](https://www.microsoft.com/typography/otspec/otff.htm)一節中，會詳細說明 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 版面配置表格。  
  
 本概觀的其餘部分會介紹一些視覺有趣的彈性與廣度[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]的屬性所公開的功能<xref:System.Windows.Documents.Typography>物件。 如需此物件的詳細資訊，請參閱[印刷樣式類別](#typography_class)。  
  
<a name="variants"></a>   
## <a name="variants"></a>變異  
 用來轉譯不同印刷樣式的變數，例如上標和下標。  
  
### <a name="superscripts-and-subscripts"></a>上標和下標  
 <xref:System.Windows.Documents.Typography.Variants%2A>屬性可讓您設定的上標和下標值[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]字型。  
  
 下列文字顯示上標 Palatino Linotype 字型。  
  
 ![使用 OpenType 上標的文字](../../../../docs/framework/wpf/advanced/media/opentypefont14.gif "opentypefont14")  
使用 OpenType 上標的文字  
  
 下列標記範例示範如何定義上標 Palatino Linotype 字型，使用的屬性<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xaml[OpenTypeFontSamples#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#12)]  
  
 下列文字顯示下標 Palatino Linotype 字型。  
  
 ![使用 OpenType 下標的文字](../../../../docs/framework/wpf/advanced/media/opentypefont15.gif "opentypefont15")  
使用 OpenType 下標的文字  
  
 下列標記範例示範如何定義下標 Palatino Linotype 字型，使用的屬性<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xaml[OpenTypeFontSamples#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#13)]  
  
### <a name="decorative-uses-of-superscripts-and-subscripts"></a>上標和下標的裝飾性用途  
 您也可以使用上標和下標建立混合大小寫文字的裝飾效果。 下列文字顯示 Palatino Linotype 字型的上下標文字。 請注意，大寫字不受影響。  
  
 ![使用 OpenType 上標和下標的文字](../../../../docs/framework/wpf/advanced/media/opentypefont16.gif "opentypefont16")  
使用 OpenType 上標和下標的文字  
  
 下列標記範例示範如何定義上標和下標的字型，使用的屬性<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xaml[OpenTypeFontSamples#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#14)]  
  
<a name="capitals"></a>   
## <a name="capitals"></a>大寫字  
 大寫字是一組以大寫樣式字符轉譯文字的印刷格式。 一般而言，當文字全部轉譯為大寫時，字母之間的間距可能太近，字母的加權和比例會過重。 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 支援數種大寫字樣式格式，包括小型大寫字、特小大寫字、標題和大寫字母間距。 這些樣式格式可讓您控制大寫字的外觀。  
  
 下列文字顯示 Pescadero 字型的標準大寫字母，後面接著樣式設定為 "SmallCaps" 和 "AllSmallCaps" 的字母。 在此情況下，三個單字全都使用相同的字型大小。  
  
 ![使用 OpenType 大寫的文字](../../../../docs/framework/wpf/advanced/media/opentypefont11.gif "opentypefont11")  
使用 OpenType 大寫的文字  
  
 下列標記範例示範如何定義使用的屬性 Pescadero 字型的大寫字<xref:System.Windows.Documents.Typography>物件。 使用 "SmallCaps" 格式時會略過任何開頭的大寫字母。  
  
 [!code-xaml[OpenTypeFontSamples#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
### <a name="titling-capitals"></a>標題大寫字  
 標題大寫字的加權和比例較輕，設計目的是為了比正常大寫字母看起來更雅緻。 標題大寫字通常用於較大的字型大小作為標題。 下列文字顯示 Pescadero 字型的正常和標題大寫字。 請注意第二行文字較窄的主體寬度。  
  
 ![使用 OpenType 標題用大寫的文字](../../../../docs/framework/wpf/advanced/media/opentypefont20.gif "OpenTypeFont20")  
使用 OpenType 標題用大寫的文字  
  
 下列標記範例示範如何定義 Pescadero 字型，使用的屬性標題大寫字<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet17)]  
  
### <a name="capital-spacing"></a>大寫字母間距  
 大寫字母間距功能可讓您在全部使用大寫字的文字中，提供更多的間距。 大寫字母通常會設計為與小寫字母混合在一起。 大寫字母和小寫字母間看起來很不錯的間距，在全部使用大寫字母時會看起來很擠。 下列文字顯示 Pescadero 字型的正常和大寫字間距。  
  
 ![使用 opentype 大寫留空的文字](../../../../docs/framework/wpf/advanced/media/opentypefont21.gif "OpenTypeFont21")  
使用 OpenType 大寫留空的文字  
  
 下列標記範例示範如何定義 Pescadero 字型，使用的屬性的大寫字母間距<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet18)]  
  
<a name="ligatures"></a>   
## <a name="ligatures"></a>連音符號  
 連音符號是兩個或以上的字符，形成單一字符以建立更清晰或更美觀的文字。 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型支援四種連音符號︰  
  
-   **標準連音符號**。 設計目的旨在增進可讀性。 標準連音符號包括 "fi"、"fl" 和 "ff"。  
  
-   **內容連音符號**。 設計目的旨在提供組成連音符號的字元間更好的聯結行為，以提升可讀性。  
  
-   **Discretionary 連音符號**。 設計成裝飾之用，並不是特別針對可讀性設計。  
  
-   **過往連音符號**。 設計成記錄之用，並不是特別針對可讀性所設計。  
  
 下列文字顯示 Pericles 字型的標準連音符號字符。  
  
 ![使用 OpenType 標準連音符號的文字](../../../../docs/framework/wpf/advanced/media/opentypefont04.gif "opentypefont04")  
使用 OpenType 標準連字的文字  
  
 下列標記範例示範如何定義 Pericles 字型，使用的屬性的標準連音符號字符<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xaml[OpenTypeFontSamples#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#4)]  
  
 下列文字顯示 Pericles 字型 Discretionary 連音符號。  
  
 ![使用 OpenType discretionary 連音符號的文字](../../../../docs/framework/wpf/advanced/media/opentypefont05.gif "opentypefont05")  
使用 OpenType Discretionary 連字的文字  
  
 下列標記範例示範如何定義使用的屬性 Pericles 字型 discretionary 連音符號字符<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xaml[OpenTypeFontSamples#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#5)]  
  
 根據預設，[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型會啟用標準連音符號。 例如，如果您使用 Palatino Linotype 字型，標準連音符號 "fi"、"ff" 和 "fl" 會顯示為合併的字元字符。 請注意，每個標準連音符號的成對字元都彼此相鄰。  
  
 ![使用 OpenType 標準連音符號的文字](../../../../docs/framework/wpf/advanced/media/opentypefont06.gif "opentypefont06")  
使用 OpenType 標準連字的文字  
  
 不過，您可以停用標準連音符號功能，讓 "ff" 等標準連音符號顯示為兩個分開的字符，而不是合併的字元字符。  
  
 ![文字使用已停用 OpenType 標準連音符號](../../../../docs/framework/wpf/advanced/media/opentypefont07.gif "opentypefont07")  
使用已停用之 OpenType 標準連字的文字  
  
 下列標記範例示範如何停用 Palatino Linotype 字型，使用的屬性的標準連音符號字符<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xaml[OpenTypeFontSamples#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#6)]  
  
<a name="swashes"></a>   
## <a name="swashes"></a>花飾字  
 花飾字是裝飾性字符，使用精心設計且通常與書寫體相關聯的裝飾。 下列文字顯示 Pescadero 字型的標準和花飾字字符。  
  
 ![使用 OpenType 標準和花飾字字符的文字](../../../../docs/framework/wpf/advanced/media/opentypefont08.gif "opentypefont08")  
使用 OpenType 標準和勾耳圖像的文字  
  
 花飾字通常用為簡短片語中的裝飾項目，例如事件宣告。 下列文字使用花飾字強調大寫字母的事件名稱。  
  
 ![使用 OpenType 花飾字的文字](../../../../docs/framework/wpf/advanced/media/opentypefont09.gif "opentypefont09")  
使用 OpenType 勾耳的文字  
  
 下列標記範例示範如何定義使用的內容的字型的花飾字<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xaml[OpenTypeFontSamples#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#7)]  
  
### <a name="contextual-swashes"></a>內容花飾字  
 某些花飾字字符的組合會導致不討喜的外觀，例如相鄰字母的伸尾部分重疊。 使用內容花飾字可讓您使用會產生更佳外觀的替代花飾字字符。 下列文字顯示套用內容花飾字之前和之後的相同字組。  
  
 ![使用 OpenType 內容花飾字的文字](../../../../docs/framework/wpf/advanced/media/opentypefont19.gif "OpenTypeFont19")  
使用 OpenType 視內容來勾耳的文字  
  
 下列標記範例示範如何定義 Pescadero 字型，使用的屬性的內容花飾字<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet16)]  
  
<a name="alternates"></a>   
## <a name="alternates"></a>替代項目  
 替代項目是可以取代標準字符的字符。 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型，例如下例使用的 Pericles 字型，可以包含替代字符，您可用來建立不同的文字外觀。 下列文字顯示 Pericles 字型的標準字符。  
  
 ![使用 OpenType 標準字符的文字](../../../../docs/framework/wpf/advanced/media/opentypefont01.gif "opentypefont01")  
使用 OpenType 標準圖像的文字  
  
 Pericles [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型包含其他字符，可為標準字符集提供文體替代項目。 下列文字顯示文體替代字符。  
  
 ![使用 OpenType 文體替代字符的文字](../../../../docs/framework/wpf/advanced/media/opentypefont02.gif "opentypefont02")  
使用 OpenType 文體替代圖像的文字  
  
 下列標記範例示範如何定義使用的屬性 Pericles 字型的文體替代字符<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xaml[OpenTypeFontSamples#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#2)]  
  
 下列文字顯示數個 Pericles 字型的其他文體替代字符。  
  
 ![使用 OpenType 文體替代字符的文字](../../../../docs/framework/wpf/advanced/media/opentypefont03.gif "opentypefont03")  
使用 OpenType 文體替代圖像的文字  
  
 下列標記範例示範如何定義這些其他文體替代字符。  
  
 [!code-xaml[OpenTypeFontSamples#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#3)]  
  
### <a name="random-contextual-alternates"></a>隨機內容替代項目  
 隨機內容替代項目提供單一字元的多個替代字符。 以書寫體字型實作時，這項功能可以使用一組隨機選擇的字符，在外觀上略加變動來模擬手寫。 下列文字使用 Lindsey 字型的隨機內容替代項目。 請注意，字母 "a" 的外觀略有不同。  
  
 ![使用 OpenType 隨機內容替代的文字](../../../../docs/framework/wpf/advanced/media/opentypefont23.gif "OpenTypeFont23")  
使用 OpenType 隨機內容替代的文字  
  
 下列標記範例示範如何定義 Lindsey 字型，使用的屬性的隨機內容替代項目<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet20)]  
  
### <a name="historical-forms"></a>古體形式  
 古體形式是過去常用的印刷樣式慣例。 下列文字使用 Palatino Linotype 字型的古體形式字符顯示 "Boston, Massachusetts" 片語。  
  
 ![使用 opentype 古體形式的文字](../../../../docs/framework/wpf/advanced/media/opentypefont10.gif "opentypefont10")  
使用 OpenType 古體形式的文字  
  
 下列標記範例示範如何定義 Palatino Linotype 字型，請使用屬性的古體形式<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xaml[OpenTypeFontSamples#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#8)]  
  
<a name="numerical_styles"></a>   
## <a name="numerical-styles"></a>數字的樣式  
 OpenType 字型支援大量可搭配文字中數值使用的功能。  
  
### <a name="fractions"></a>分數  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型支援分數樣式，包括斜式和直式。  
  
 下列文字顯示 Palatino Linotype 字型的分數樣式。  
  
 ![使用 OpenType 斜式和直式分數](../../../../docs/framework/wpf/advanced/media/opentypefont12.gif "opentypefont12")  
使用 OpenType 斜式和直式分數的文字  
  
 下列標記範例示範如何定義 Palatino Linotype 字型，使用的屬性的分數樣式<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xaml[OpenTypeFontSamples#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#10)]  
  
### <a name="old-style-numerals"></a>舊樣式數字  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型支援舊樣式數字格式。 此格式適用於顯示樣式不再標準的數字。 下列文字使用 Palatino Linotype 字型的標準和舊樣式數字格式顯示 18 世紀的日期。  
  
 ![使用 OpenType 舊樣式數字的文字](../../../../docs/framework/wpf/advanced/media/opentypefont24.gif "OpenTypeFont24")  
使用 OpenType 舊樣式數字的文字  
  
 下列文字顯示 Palatino Linotype 字型的標準數字，後面接著舊樣式數字的數字。  
  
 ![使用 OpenType 舊樣式數字集的文字](../../../../docs/framework/wpf/advanced/media/opentypefont13.gif "opentypefont13")  
使用 OpenType 舊樣式數字集的文字  
  
 下列標記範例示範如何定義 Palatino Linotype 字型，使用的屬性的舊樣式數字<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xaml[OpenTypeFontSamples#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#11)]  
  
### <a name="proportional-and-tabular-figures"></a>調和間距與表格式數字  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型支援在使用數字時，以調和間距與表格式數字功能控制寬度對齊。 調和間距數字會將每一個數字視為具有不同的寬度，"1" 比 "5" 窄。 表格式數字則視為等寬數字，以便垂直對齊，可提高財務類資訊的可讀性。  
  
 下列文字在第一個資料行中顯示使用 Miramonte 字型的兩個調和間距數字。 請注意數字 "5" 和 "1" 之間的寬度差異。 第二個資料行顯示相同的兩個數值，使用表格式數字功能調整其寬度。  
  
 ![使用 OpenType 調和間距與表格式數字的文字](../../../../docs/framework/wpf/advanced/media/opentypefont22.gif "OpenTypeFont22")  
使用 OpenType 調和間距與表格式數字的文字  
  
 下列標記範例示範如何定義 Miramonte 字型，使用的屬性的調和間距與表格式數字<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet19)]  
  
### <a name="slashed-zero"></a>加斜線的零  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型支援加斜線的零數字格式，以強調字母 "O" 與數字 "0" 之間的差異。 加斜線的零數字通常用於財務和商務資訊中的識別碼。  
  
 下列文字顯示使用 Miramonte 字型的範例訂單識別碼。 第一行使用標準的數字。 第二行使用加斜線的零數字，以突顯與大寫字母 "O" 的對比。  
  
 ![使用 OpenType 斜式零的數字](../../../../docs/framework/wpf/advanced/media/opentypefont17.gif "OpenTypeFont17")  
使用 OpenType 零帶有斜線之數字的文字  
  
 下列標記範例示範如何定義斜線零數字 Miramonte 字型，使用的屬性<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet15)]  
  
<a name="typography_class"></a>   
## <a name="typography-class"></a>印刷樣式類別  
 <xref:System.Windows.Documents.Typography>物件會公開一組功能，[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]字型支援。 藉由設定的屬性<xref:System.Windows.Documents.Typography>在標記中，您可以輕鬆撰寫充分利用的文件[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]功能。  
  
 下列文字顯示 Pescadero 字型的標準大寫字母，後面接著樣式設定為 "SmallCaps" 和 "AllSmallCaps" 的字母。 在此情況下，三個單字全都使用相同的字型大小。  
  
 ![使用 OpenType 大寫的文字](../../../../docs/framework/wpf/advanced/media/opentypefont11.gif "opentypefont11")  
使用 OpenType 大寫的文字  
  
 下列標記範例示範如何定義使用的屬性 Pescadero 字型的大寫字<xref:System.Windows.Documents.Typography>物件。 使用 "SmallCaps" 格式時會略過任何開頭的大寫字母。  
  
 [!code-xaml[OpenTypeFontSamples#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
 下列程式碼範例可以完成與先前標記範例相同的工作。  
  
 [!code-csharp[TypographyCodeSnippets#TypographyCodeSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TypographyCodeSnippets/CSharp/Page1.xaml.cs#typographycodesnippet1)]
 [!code-vb[TypographyCodeSnippets#TypographyCodeSnippet1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TypographyCodeSnippets/visualbasic/page1.xaml.vb#typographycodesnippet1)]  
  
### <a name="typography-class-properties"></a>印刷樣式類別屬性  
 下表列出的屬性、 值和預設設定<xref:System.Windows.Documents.Typography>物件。  
  
|屬性|值|預設值|  
|--------------|----------------|-------------------|  
|<xref:System.Windows.Documents.Typography.AnnotationAlternates%2A>|數值 - 位元組|0|  
|<xref:System.Windows.Documents.Typography.Capitals%2A>|<xref:System.Windows.FontCapitals.AllPetiteCaps> &#124; <xref:System.Windows.FontCapitals.AllSmallCaps> &#124; <xref:System.Windows.FontCapitals.Normal> &#124; <xref:System.Windows.FontCapitals.PetiteCaps> &#124; <xref:System.Windows.FontCapitals.SmallCaps> &#124; <xref:System.Windows.FontCapitals.Titling> &#124; <xref:System.Windows.FontCapitals.Unicase>|<xref:System.Windows.FontCapitals.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.CapitalSpacing%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.CaseSensitiveForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.ContextualAlternates%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualSwashes%2A>|數值 - 位元組|0|  
|<xref:System.Windows.Documents.Typography.DiscretionaryLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianExpertForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianLanguage%2A>|<xref:System.Windows.FontEastAsianLanguage.HojoKanji> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis04> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis78> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis83> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis90> &#124; <xref:System.Windows.FontEastAsianLanguage.NlcKanji> &#124; <xref:System.Windows.FontEastAsianLanguage.Normal> &#124; <xref:System.Windows.FontEastAsianLanguage.Simplified> &#124; <xref:System.Windows.FontEastAsianLanguage.Traditional> &#124; <xref:System.Windows.FontEastAsianLanguage.TraditionalNames>|<xref:System.Windows.FontEastAsianLanguage.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.EastAsianWidths%2A>|<xref:System.Windows.FontEastAsianWidths.Full> &#124; <xref:System.Windows.FontEastAsianWidths.Half> &#124; <xref:System.Windows.FontEastAsianWidths.Normal> &#124; <xref:System.Windows.FontEastAsianWidths.Proportional> &#124; <xref:System.Windows.FontEastAsianWidths.Quarter> &#124; <xref:System.Windows.FontEastAsianWidths.Third>|<xref:System.Windows.FontEastAsianWidths.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.Fraction%2A>|<xref:System.Windows.FontFraction.Normal> &#124; <xref:System.Windows.FontFraction.Slashed> &#124; <xref:System.Windows.FontFraction.Stacked>|<xref:System.Windows.FontFraction.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.HistoricalForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.HistoricalLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.Kerning%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.MathematicalGreek%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.NumeralAlignment%2A>|<xref:System.Windows.FontNumeralAlignment.Normal> &#124; <xref:System.Windows.FontNumeralAlignment.Proportional> &#124; <xref:System.Windows.FontNumeralAlignment.Tabular>|<xref:System.Windows.FontNumeralAlignment.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.NumeralStyle%2A>|<xref:System.Boolean>|<xref:System.Windows.FontNumeralStyle.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.SlashedZero%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StandardLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.StandardSwashes%2A>|數值 - 位元組|0|  
|<xref:System.Windows.Documents.Typography.StylisticAlternates%2A>|數值 - 位元組|0|  
|<xref:System.Windows.Documents.Typography.StylisticSet1%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet2%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet3%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet4%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet5%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet6%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet7%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet8%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet9%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet10%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet11%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet12%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet13%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet14%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet15%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet16%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet17%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet18%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet19%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet20%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.Variants%2A>|<xref:System.Windows.FontVariants.Inferior> &#124; <xref:System.Windows.FontVariants.Normal> &#124; <xref:System.Windows.FontVariants.Ordinal> &#124; <xref:System.Windows.FontVariants.Ruby> &#124; <xref:System.Windows.FontVariants.Subscript> &#124; <xref:System.Windows.FontVariants.Superscript>|<xref:System.Windows.FontVariants.Normal?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Documents.Typography>
- [OpenType 規格](https://go.microsoft.com/fwlink/?LinkId=96731)
- [WPF 中的印刷樣式](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)
- [範例 OpenType 字型套件](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md)
- [將字型與應用程式一起封裝](../../../../docs/framework/wpf/advanced/packaging-fonts-with-applications.md)
