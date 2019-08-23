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
ms.openlocfilehash: 7d73176a68d8b4b19b6c980ef52e1f47408127fb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933693"
---
# <a name="opentype-font-features"></a>OpenType 字型功能

本主題提供中[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]OpenType 字型技術的部分主要功能總覽。  
  
<a name="overview"></a>   
## <a name="opentype-font-format"></a>OpenType 字型格式  
 OpenType 字型格式是[!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)]字型格式的延伸模組, 加入 PostScript 字型資料的支援。 OpenType 字型格式是由[!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)]和 Adobe Corporation 共同開發。 Opentype 字型和支援 OpenType 字型的作業系統服務, 可讓使用者使用簡單的方式來安裝和使用字型, 無論字型包含[!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)]外框或 CFF (PostScript) 外框。  
  
 OpenType 字型格式解決下列開發人員的挑戰:  
  
- 更廣泛的多平台支援。  
  
- 更好的國際字元集支援。  
  
- 更好的字型資料保護。  
  
- 較小的檔案大小，讓字型發佈更有效率。  
  
- 進階印刷樣式控制項的廣泛支援。  
  
> [!NOTE]
> Windows SDK 包含一組您可以搭配[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]應用程式使用的範例 OpenType 字型。 本主題後文會說明這些字型提供的大部分功能。 如需詳細資訊，請參閱[範例 OpenType 字型套件](sample-opentype-font-pack.md)。  
  
 如需 OpenType 字型格式的詳細資訊, 請參閱[Opentype 規格](https://go.microsoft.com/fwlink/?LinkId=96731)。  
  
### <a name="advanced-typographic-extensions"></a>進階的印刷樣式延伸模組  
 「先進的印刷樣式表」 (OpenType 版面配置資料表) 使用[!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)]或 CFF 外框來擴充字型的功能。 OpenType 版面配置字型包含額外的資訊, 可延伸字型的功能, 以支援高品質的國際印刷樣式。 大部分的 OpenType 字型只會公開可用的全部 OpenType 功能子集。 OpenType 字型提供下列功能。  
  
- 字元與字符之間的豐富對應，支援連音符號、位置形式、替代項目，以及其他字型替代項目。  
  
- 支援二維定位與字符附件。  
  
- 字型中包含明確的指令碼和語言資訊，因此文字處理應用程式可據以調整其行為。  
  
 Opentype 版面配置資料表的詳細說明請參閱 OpenType 規格的「[字型檔案資料表](https://www.microsoft.com/typography/otspec/otff.htm)」一節。  
  
 本總覽的其餘部分將介紹由<xref:System.Windows.Documents.Typography>物件的屬性所公開的一些視覺上有趣的 OpenType 功能的廣度和彈性。 如需此物件的詳細資訊，請參閱[印刷樣式類別](#typography_class)。  
  
<a name="variants"></a>   
## <a name="variants"></a>變異  
 用來轉譯不同印刷樣式的變數，例如上標和下標。  
  
### <a name="superscripts-and-subscripts"></a>上標和下標  
 <xref:System.Windows.Documents.Typography.Variants%2A>屬性可讓您設定 OpenType 字型的上標和下標值。  
  
 下列文字顯示上標 Palatino Linotype 字型。  
  
 ![使用 OpenType 上標的文字](./media/opentype-font-features/opentype-superscripts.gif "使用 OpenType 上標的文字")  
  
 下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 為 Palatino Linotype 字型定義上標。  
  
 [!code-xaml[OpenTypeFontSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#12)]  
  
 下列文字顯示下標 Palatino Linotype 字型。  
  
 ![使用 OpenType]注標的文字(./media/opentype-font-features/opentype-subscripts.gif "使用 OpenType")注標的文字  
  
 下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 定義 Palatino Linotype 字型的注標。  
  
 [!code-xaml[OpenTypeFontSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#13)]  
  
### <a name="decorative-uses-of-superscripts-and-subscripts"></a>上標和下標的裝飾性用途  
 您也可以使用上標和下標建立混合大小寫文字的裝飾效果。 下列文字顯示 Palatino Linotype 字型的上下標文字。 請注意，大寫字不受影響。  
  
 ![使用 OpenType 上標和下標的文字](./media/opentype-font-features/opentype-superscripts-subscripts.gif "使用 OpenType 上標和下標的文字")  

 下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 為字型定義上標和下標。  
  
 [!code-xaml[OpenTypeFontSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#14)]  
  
<a name="capitals"></a>   
## <a name="capitals"></a>大寫字  
 大寫字是一組以大寫樣式字符轉譯文字的印刷格式。 一般而言，當文字全部轉譯為大寫時，字母之間的間距可能太近，字母的加權和比例會過重。 OpenType 支援數個大寫字母的樣式設定格式, 包括 small 大寫字母、特小大大寫字母、標題和大寫字母間距。 這些樣式格式可讓您控制大寫字的外觀。  
  
 下列文字顯示 Pescadero 字型的標準大寫字母，後面接著樣式設定為 "SmallCaps" 和 "AllSmallCaps" 的字母。 在此情況下，三個單字全都使用相同的字型大小。  
  
 ![使用 OpenType 大寫的文字](./media/opentype-font-features/opentype-capitals.gif "使用 OpenType 大寫的文字")  
  
 下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 定義 Pescadero 字型的大寫字母。 使用 "SmallCaps" 格式時會略過任何開頭的大寫字母。  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
### <a name="titling-capitals"></a>標題大寫字  
 標題大寫字的加權和比例較輕，設計目的是為了比正常大寫字母看起來更雅緻。 標題大寫字通常用於較大的字型大小作為標題。 下列文字顯示 Pescadero 字型的正常和標題大寫字。 請注意第二行文字較窄的主體寬度。  
  
 ![使用 OpenType 標題大寫的文字](./media/opentype-font-features/opentype-titling-capitals.gif "使用 OpenType 標題大寫的文字")  
  
 下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 定義 Pescadero 字型的標題大寫。  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet17](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet17)]  
  
### <a name="capital-spacing"></a>大寫字母間距  
 大寫字母間距功能可讓您在全部使用大寫字的文字中，提供更多的間距。 大寫字母通常會設計為與小寫字母混合在一起。 大寫字母和小寫字母間看起來很不錯的間距，在全部使用大寫字母時會看起來很擠。 下列文字顯示 Pescadero 字型的正常和大寫字間距。  
  
 ![使用 OpenType 大寫間距的文字](./media/opentype-font-features/opentype-capital-spacing.gif "使用 OpenType 大寫間距的文字")  
 
 下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 定義 Pescadero 字型的大寫字母間距。  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet18](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet18)]  
  
<a name="ligatures"></a>   
## <a name="ligatures"></a>連音符號  
 連音符號是兩個或以上的字符，形成單一字符以建立更清晰或更美觀的文字。 OpenType 字型支援四種類型的連字:  
  
- **標準連音符號**。 設計目的旨在增進可讀性。 標準連音符號包括 "fi"、"fl" 和 "ff"。  
  
- **內容連音符號**。 設計目的旨在提供組成連音符號的字元間更好的聯結行為，以提升可讀性。  
  
- **Discretionary 連音符號**。 設計成裝飾之用，並不是特別針對可讀性設計。  
  
- **過往連音符號**。 設計成記錄之用，並不是特別針對可讀性所設計。  
  
 下列文字顯示 Pericles 字型的標準連音符號字符。  
  
 ![使用 OpenType 標準連字的文字](./media/opentype-font-features/opentype-standard-ligatures.gif "使用 OpenType 標準連字的文字")  
  
 下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 為 Pericles 字型定義標準的連字號圖像。  
  
 [!code-xaml[OpenTypeFontSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#4)]  
  
 下列文字顯示 Pericles 字型 Discretionary 連音符號。  
  
 ![使用 OpenType 任意連字的文字](./media/opentype-font-features/opentype-discretionary-ligatures.gif "使用 OpenType 任意連字的文字")  
  
 下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 為 Pericles 字型定義任意的連字號圖像。  
  
 [!code-xaml[OpenTypeFontSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#5)]  
  
 根據預設, 中[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]的 OpenType 字型會啟用標準連字。 例如，如果您使用 Palatino Linotype 字型，標準連音符號 "fi"、"ff" 和 "fl" 會顯示為合併的字元字符。 請注意，每個標準連音符號的成對字元都彼此相鄰。  
  
 搭配![Palatino Linotype 使用 OpenType 標準連字的文字]搭配(./media/opentype-font-features/opentype-standard-ligatures-palatino.gif "Palatino Linotype 使用 OpenType 標準連字的文字")    
   
 不過，您可以停用標準連音符號功能，讓 "ff" 等標準連音符號顯示為兩個分開的字符，而不是合併的字元字符。  
  
 ![使用已停用之 OpenType 標準連字的文字](./media/opentype-font-features/disabled-opentype-standard-ligatures.gif "使用已停用之 OpenType 標準連字的文字")  
    
 下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 停用 Palatino Linotype 字型的標準連字號符號。  
  
 [!code-xaml[OpenTypeFontSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#6)]  
  
<a name="swashes"></a>   
## <a name="swashes"></a>花飾字  
 花飾字是裝飾性字符，使用精心設計且通常與書寫體相關聯的裝飾。 下列文字顯示 Pescadero 字型的標準和花飾字字符。  
  
 ![使用 OpenType 標準和花飾字字元的文字](./media/opentype-font-features/opentype-standard-swash-glyphs.gif "使用 OpenType 標準和花飾字字元的文字")  

 花飾字通常用為簡短片語中的裝飾項目，例如事件宣告。 下列文字使用花飾字強調大寫字母的事件名稱。  
  
 ![使用 OpenType 花飾字的文字](./media/opentype-font-features/opentype-swashes.gif "使用 OpenType 花飾字的文字")  
  
 下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 為字型定義花飾字。  
  
 [!code-xaml[OpenTypeFontSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#7)]  
  
### <a name="contextual-swashes"></a>內容花飾字  
 某些花飾字字符的組合會導致不討喜的外觀，例如相鄰字母的伸尾部分重疊。 使用內容花飾字可讓您使用會產生更佳外觀的替代花飾字字符。 下列文字顯示套用內容花飾字之前和之後的相同字組。  
  
 ![使用 OpenType 內容花飾字的文字](./media/opentype-font-features/opentype-contextual-swashes.gif "使用 OpenType 內容花飾字的文字")  
  
 下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 定義 Pescadero 字型的內容花飾字。  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet16](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet16)]  
  
<a name="alternates"></a>   
## <a name="alternates"></a>替代項目  
 替代項目是可以取代標準字符的字符。 OpenType 字型 (例如下列範例中使用的 Pericles 字型) 可以包含替代字元, 您可以用來建立不同的文字外觀。 下列文字顯示 Pericles 字型的標準字符。  
  
 ![使用 OpenType 標準字元的文字](./media/opentype-font-features/opentype-standard-glyphs.gif "使用 OpenType 標準字元的文字")  

 Pericles OpenType 字型包含額外的圖像, 可為標準的圖像集提供樣式替代。 下列文字顯示文體替代字符。  
  
 ![使用 OpenType 樣式替代字元的文字](./media/opentype-font-features/opentype-stylistic-alternate-glyphs.gif "使用 OpenType 樣式替代字元的文字")  
  
 下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 定義 Pericles 字型的樣式替代字元。  
  
 [!code-xaml[OpenTypeFontSamples#2](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#2)]  
  
 下列文字顯示數個 Pericles 字型的其他文體替代字符。  
  
 ![針對 Pericles 字型使用 OpenType 樣式替代字元的文字](./media/opentype-font-features/opentype-stylistic-alternate-glyphs-pericles.gif "針對 Pericles 字型使用 OpenType 樣式替代字元的文字")

 下列標記範例示範如何定義這些其他文體替代字符。  
  
 [!code-xaml[OpenTypeFontSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#3)]  
  
### <a name="random-contextual-alternates"></a>隨機內容替代項目  
 隨機內容替代項目提供單一字元的多個替代字符。 以書寫體字型實作時，這項功能可以使用一組隨機選擇的字符，在外觀上略加變動來模擬手寫。 下列文字使用 Lindsey 字型的隨機內容替代項目。 請注意，字母 "a" 的外觀略有不同。  
  
 ![使用 OpenType 隨機內容替代的文字](./media/opentype-font-features/opentype-random-contextual-alternates.gif "使用 OpenType 隨機內容替代的文字")  
  
 下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 為 Lindsey 字型定義隨機內容的替代項。  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet20](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet20)]  
  
### <a name="historical-forms"></a>古體形式  
 古體形式是過去常用的印刷樣式慣例。 下列文字使用 Palatino Linotype 字型的古體形式字符顯示 "Boston, Massachusetts" 片語。  
  
 ![使用 OpenType 歷程記錄表單的文字](./media/opentype-font-features/opentype-historical-forms.gif "使用 OpenType 歷程記錄表單的文字")  
   
 下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 定義 Palatino Linotype 字型的歷程記錄表單。  
  
 [!code-xaml[OpenTypeFontSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#8)]  
  
<a name="numerical_styles"></a>   
## <a name="numerical-styles"></a>數字的樣式  
 OpenType 字型支援大量可搭配文字中數值使用的功能。  
  
### <a name="fractions"></a>分數  
 OpenType 字型支援分數的樣式, 包括斜線和堆疊。  
  
 下列文字顯示 Palatino Linotype 字型的分數樣式。  
  
 ![使用 OpenType 斜線和堆疊分數的文字](./media/opentype-font-features/opentype-slashed-stacked-fractions.gif "使用 OpenType 斜線和堆疊分數的文字")  
   
 下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 定義 Palatino Linotype 字型的分數樣式。  
  
 [!code-xaml[OpenTypeFontSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#10)]  
  
### <a name="old-style-numerals"></a>舊樣式數字  
 OpenType 字型支援舊的樣式數位格式。 此格式適用於顯示樣式不再標準的數字。 下列文字使用 Palatino Linotype 字型的標準和舊樣式數字格式顯示 18 世紀的日期。  
  
 ![使用 OpenType 舊樣式數位的文字](./media/opentype-font-features/opentype-old-style-numerals.gif "使用 OpenType 舊樣式數位的文字")  
    
 下列文字顯示 Palatino Linotype 字型的標準數字，後面接著舊樣式數字的數字。  
  
 ![使用 OpenType 舊樣式數位集的文字](./media/opentype-font-features/opentype-old-style-numeral-sets.gif "使用 OpenType 舊樣式數位集的文字")  
  
 下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 為 Palatino Linotype 字型定義舊的樣式數位。  
  
 [!code-xaml[OpenTypeFontSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#11)]  
  
### <a name="proportional-and-tabular-figures"></a>調和間距與表格式數字  
 OpenType 字型支援以比例和表格式圖表功能, 在使用數位時控制寬度的對齊方式。 調和間距數字會將每一個數字視為具有不同的寬度，"1" 比 "5" 窄。 表格式數字則視為等寬數字，以便垂直對齊，可提高財務類資訊的可讀性。  
  
 下列文字在第一個資料行中顯示使用 Miramonte 字型的兩個調和間距數字。 請注意數字 "5" 和 "1" 之間的寬度差異。 第二個資料行顯示相同的兩個數值，使用表格式數字功能調整其寬度。  
  
 ![使用 OpenType 比例 & 表格式數位的文字](./media/opentype-font-features/opentype-proportional-tabular-figures.gif "使用 OpenType 比例和表格式數位的文字")  
    
 下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 定義 Miramonte 字型的比例和表格式數位。  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet19](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet19)]  
  
### <a name="slashed-zero"></a>加斜線的零  
 OpenType 字型支援斜線零數位格式, 以強調字母 "O" 與數位 "0" 之間的差異。 加斜線的零數字通常用於財務和商務資訊中的識別碼。  
  
 下列文字顯示使用 Miramonte 字型的範例訂單識別碼。 第一行使用標準的數字。 第二行使用加斜線的零數字，以突顯與大寫字母 "O" 的對比。  
  
 ![使用 OpenType 斜線零數位的文字](./media/opentype-font-features/opentype-slashed-zero-numerals.gif "使用 OpenType 斜線零數位的文字")  
    
 下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 為 Miramonte 字型定義以斜線為零的數位。  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet15](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet15)]  
  
<a name="typography_class"></a>   
## <a name="typography-class"></a>印刷樣式類別  
 <xref:System.Windows.Documents.Typography>物件會公開 OpenType 字型支援的一組功能。 藉由在標記中<xref:System.Windows.Documents.Typography>設定的屬性, 您可以輕鬆地撰寫利用 OpenType 功能的檔。  
  
 下列文字顯示 Pescadero 字型的標準大寫字母，後面接著樣式設定為 "SmallCaps" 和 "AllSmallCaps" 的字母。 在此情況下，三個單字全都使用相同的字型大小。  
  
 ![使用 OpenType 大寫的文字](./media/opentype-font-features/opentype-capitals.gif "使用 OpenType 大寫的文字")  
    
 下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 定義 Pescadero 字型的大寫字母。 使用 "SmallCaps" 格式時會略過任何開頭的大寫字母。  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
 下列程式碼範例可以完成與先前標記範例相同的工作。  
  
 [!code-csharp[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TypographyCodeSnippets/CSharp/Page1.xaml.cs#typographycodesnippet1)]
 [!code-vb[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TypographyCodeSnippets/visualbasic/page1.xaml.vb#typographycodesnippet1)]  
  
### <a name="typography-class-properties"></a>印刷樣式類別屬性  
 下表列出<xref:System.Windows.Documents.Typography>物件的屬性、值和預設設定。  
  
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
- [WPF 中的印刷樣式](typography-in-wpf.md)
- [範例 OpenType 字型套件](sample-opentype-font-pack.md)
- [將字型與應用程式一起封裝](packaging-fonts-with-applications.md)
