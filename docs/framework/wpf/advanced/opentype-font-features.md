---
title: "OpenType 字型功能 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "OpenType 字型"
  - "印刷樣式，OpenType 字型技術"
  - "OpenType 字型技術"
ms.assetid: 4061a9d1-fe8b-4921-9e17-18ec7d2e3ea2
caps.latest.revision: 38
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 37
---
# OpenType 字型功能
本主題提供的一些重要功能概觀[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]字型技術[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="overview"></a>   
## <a name="opentype-font-format"></a>OpenType 字型格式  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]字型格式是副檔名為[!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)]字型格式、 新增 PostScript 字型資料的支援。 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]字型格式由共同開發[!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)]和 Adobe Corporation。 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]字型和作業系統服務的支援[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]字型提供使用者一個簡單的方式與安裝和使用字型是否包含字型[!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)]外框或 CFF (PostScript) 的外框。  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]字型格式解決下列開發人員的挑戰︰  
  
-   更廣泛的多重平台支援。  
  
-   加強支援國際字元集。  
  
-   更好的字型資料的保護。  
  
-   縮小檔案大小，以使字型發佈更有效率。  
  
-   進階的印刷樣式控制項的廣泛支援。  
  
> [!NOTE]
>  Windows SDK 包含一組範例[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]字型，您可以使用[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]應用程式。 這些字型提供的大部分功能，本主題的其餘部分中所述。 如需詳細資訊，請參閱[範例 OpenType 字型套件](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md)。  
  
 請參閱[OpenType 規格](http://go.microsoft.com/fwlink/?LinkId=96731)如需詳細資訊的[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]字型格式。  
  
### <a name="advanced-typographic-extensions"></a>進階的印刷樣式擴充功能  
 進階印刷樣式的資料表 ([!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]版面配置表格) 擴充功能的兩個字型[!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)]或 CFF 外框。 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]字型配置包含延伸字型的功能，以支援高品質的國際印刷樣式的其他資訊。 大部分[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]字型公開 （expose) 的總數子集[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]可用的功能。 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]字型提供下列功能。  
  
-   豐富字元與圖像 （glyph） 支援連音符號、 位置形式、 替代項目，以及其他字型替代項目之間的對應。  
  
-   二維定位與圖像附件的支援。  
  
-   明確指令碼和語言資訊包含在字型，因此文字處理應用程式可據以調整其行為。  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]版面配置表格更詳細地說明[「 字型檔案資料表 」](http://www.microsoft.com/typography/otspec/otff.htm)區段[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]規格。  
  
 本概觀的其餘部分導入一些視覺趣味的彈性與廣度[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]的屬性所公開的功能<xref:System.Windows.Documents.Typography>物件。 如需有關此物件的詳細資訊，請參閱[印刷樣式類別](#typography_class)。  
  
<a name="variants"></a>   
## <a name="variants"></a>變異  
 變數用來呈現不同的印刷樣式，例如上標和下標。  
  
### <a name="superscripts-and-subscripts"></a>上標和下標  
 <xref:System.Windows.Documents.Typography.Variants%2A>屬性可讓您設定上標和下標的值[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]字型。  
  
 下列的文字會顯示上標 Palatino Linotype 字型。  
  
 ![使用 OpenType 上標的文字](../../../../docs/framework/wpf/advanced/media/opentypefont14.png "opentypefont14")  
使用 OpenType 上標的文字  
  
 下列標記範例示範如何定義 Palatino Linotype 字型，請使用屬性的上標<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xml[OpenTypeFontSamples#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#12)]  
  
 下列的文字會顯示 Palatino Linotype 字型的註標。  
  
 ![使用 OpenType 下標的文字](../../../../docs/framework/wpf/advanced/media/opentypefont15.png "opentypefont15")  
使用 OpenType 下標的文字  
  
 下列標記範例示範如何定義 Palatino Linotype 字型，請使用屬性的註標<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xml[OpenTypeFontSamples#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#13)]  
  
### <a name="decorative-uses-of-superscripts-and-subscripts"></a>上標和下標的裝飾性用途  
 若要建立的混合大小寫文字的裝飾效果，您也可以使用上標和下標。 下列的文字會顯示 Palatino Linotype 字型上標和下標的文字。 請注意，大寫字不受影響。  
  
 ![使用 OpenType 上標和下標的文字](../../../../docs/framework/wpf/advanced/media/opentypefont16.png "opentypefont16")  
使用 OpenType 上標和下標的文字  
  
 下列標記範例示範如何定義上標和下標的字型，使用屬性的<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xml[OpenTypeFontSamples#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#14)]  
  
<a name="capitals"></a>   
## <a name="capitals"></a>大寫字母  
 大寫字是一組以大寫樣式圖像呈現文字的印刷格式。 一般而言，全部大寫為轉譯文字時，字母之間的間距可能太近，加權和過重字母的比例。 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]支援數種格式樣式大寫字，包括小型大寫字、 特小大寫字、 標題，和大寫字母間距。 這些樣式設定格式，可讓您控制大寫字的外觀。  
  
 下列的文字會顯示標準的大寫字母 Pescadero 字型，後面接著字母樣式設定為 「 SmallCaps 」 和 「 AllSmallCaps 」。 在此情況下，相同的字型大小用於所有的三個單字。  
  
 ![使用 OpenType 大寫的文字](../../../../docs/framework/wpf/advanced/media/opentypefont11.png "opentypefont11")  
使用 OpenType 大寫的文字  
  
 下列標記範例示範如何定義 Pescadero 字型，請使用屬性的大寫字<xref:System.Windows.Documents.Typography>物件。 使用 「 SmallCaps 」 格式時，會略過任何開頭的大寫字母。  
  
 [!code-xml[OpenTypeFontSamples#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
### <a name="titling-capitals"></a>標題大寫字  
 加標題大寫字母是輕輕又比例和設計目的是為了讓比正常大寫字母更簡潔的外觀。 加標題大寫字母通常用於較大的字型大小作為標題。 下列的文字會顯示 Pescadero 字型的正常和加標題大寫字。 請注意第二行上的文字較窄的 stem 寬度。  
  
 ![使用 OpenType 標題用大寫的文字](../../../../docs/framework/wpf/advanced/media/opentypefont20.png "OpenTypeFont20")  
使用 OpenType 標題用大寫的文字  
  
 下列標記範例示範如何定義 Pescadero 字型，使用的屬性加標題大寫字母<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xml[OpenTypeFontSamples#OpenTypeFontSnippet17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet17)]  
  
### <a name="capital-spacing"></a>大寫字母間距  
 大寫字母間距是一項功能，可讓您在文字中使用全部大寫字時提供更多的間距。 大寫字母通常會設計為與小寫字母混合在一起。 間距之間似乎互相吸引和大寫字母和小寫字母看起來可能太緊時使用全部大寫的字母。 下列的文字會顯示 Pescadero 字型的正常及大寫字母間距。  
  
 ![使用 opentype 大寫留空的文字](../../../../docs/framework/wpf/advanced/media/opentypefont21.png "OpenTypeFont21")  
使用 OpenType 大寫留空的文字  
  
 下列標記範例示範如何定義 Pescadero 字型，請使用屬性的資本間距<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xml[OpenTypeFontSamples#OpenTypeFontSnippet18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet18)]  
  
<a name="ligatures"></a>   
## <a name="ligatures"></a>連音符號  
 連字是兩個或多個這些圖像會形成單一的圖像 （glyph） 以建立更清晰或美觀的文字。 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]字型支援連音符號四種類型︰  
  
-   **標準連字**。 設計可增進可讀性。 標準連字包含"i"、"fl"和"ff"。  
  
-   **內容連字**。 為了提供更好的結合連字所組成的字元之間的行為，以提升可讀性。  
  
-   **判別連字**。 設計成裝飾之用，並不是專門針對可讀性。  
  
-   **過往連音符號**。 設計為歷程記錄，並不是專門針對可讀性。  
  
 下列的文字會顯示標準連字符 Pericles 字型。  
  
 ![使用 OpenType 標準連字的文字](../../../../docs/framework/wpf/advanced/media/opentypefont04.png "opentypefont04")  
使用 OpenType 標準連字的文字  
  
 下列標記範例示範如何定義 Pericles 字型，請使用屬性的標準連字圖像<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xml[OpenTypeFontSamples#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#4)]  
  
 下列的文字會顯示 Pericles 字型判別連字符。  
  
 ![使用 OpenType discretionary 連字的文字](../../../../docs/framework/wpf/advanced/media/opentypefont05.png "opentypefont05")  
使用 OpenType Discretionary 連字的文字  
  
 下列標記範例示範如何定義 Pericles 字型，請使用屬性的判別連字圖像<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xml[OpenTypeFontSamples#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#5)]  
  
 根據預設，[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]中的字型[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]啟用標準連字。 例如，如果您使用 Palatino Linotype 字型，標準連字"i"、"ff"和"fl"顯示為結合的字元圖像。 請注意，對每個標準連字的字元會彼此相鄰。  
  
 ![使用 OpenType 標準連字的文字](../../../../docs/framework/wpf/advanced/media/opentypefont06.png "opentypefont06")  
使用 OpenType 標準連字的文字  
  
 不過，您可以停用標準連字功能，例如"ff"的標準連字顯示為兩個圖像，而不是合併的字元圖像。  
  
 ![使用已停用的 OpenType 標準連字的文字](../../../../docs/framework/wpf/advanced/media/opentypefont07.png "opentypefont07")  
使用已停用之 OpenType 標準連字的文字  
  
 下列標記範例示範如何停用 Palatino Linotype 字型，請使用屬性的標準連字圖像<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xml[OpenTypeFontSamples#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#6)]  
  
<a name="swashes"></a>   
## <a name="swashes"></a>勾耳  
 勾耳會裝飾會使用與書法相關的圖像 （glyph）。 下列文字顯示 Pescadero 字型的標準和勾耳圖像。  
  
 ![使用 OpenType 標準和勾耳圖像的文字](../../../../docs/framework/wpf/advanced/media/opentypefont08.png "opentypefont08")  
使用 OpenType 標準和勾耳圖像的文字  
  
 勾耳通常做為簡短片語，例如事件宣告中的裝飾項目。 下列文字可用於勾耳強調大寫字母的事件名稱。  
  
 ![使用 OpenType 勾耳的文字](../../../../docs/framework/wpf/advanced/media/opentypefont09.png "opentypefont09")  
使用 OpenType 勾耳的文字  
  
 下列標記範例示範如何定義字型，使用內容來勾耳<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xml[OpenTypeFontSamples#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#7)]  
  
### <a name="contextual-swashes"></a>內容勾耳  
 勾耳圖像的某些組合可能會導致不討喜的外觀，例如上相鄰的字母的重疊下移。 使用內容花飾字，可讓您使用替代勾耳圖像 （glyph） 會產生更佳的外觀。 下列文字會顯示相同的字組之前和之後套用內容花飾字。  
  
 ![使用 OpenType 內容勾耳的文字](../../../../docs/framework/wpf/advanced/media/opentypefont19.png "OpenTypeFont19")  
使用 OpenType 視內容來勾耳的文字  
  
 下列標記範例示範如何定義 Pescadero 字型，使用的屬性內容花飾字<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xml[OpenTypeFontSamples#OpenTypeFontSnippet16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet16)]  
  
<a name="alternates"></a>   
## <a name="alternates"></a>替代項目  
 替代項目是可以取代標準圖像的圖像。 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]例如在下列範例中，所使用的 Pericles 字型的字型，可以包含可用來建立不同的外觀，文字的替代字符。 下列的文字會顯示標準圖像 Pericles 字型。  
  
 ![使用 OpenType 標準圖像的文字](../../../../docs/framework/wpf/advanced/media/opentypefont01.png "opentypefont01")  
使用 OpenType 標準圖像的文字  
  
 Pericles[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]字型包含其他圖像 （glyph） 提供文體替代圖像 （glyph） 的標準設定。 下列的文字會顯示文體替代圖像。  
  
 ![使用 OpenType 文體替代圖像的文字](../../../../docs/framework/wpf/advanced/media/opentypefont02.png "opentypefont02")  
使用 OpenType 文體替代圖像的文字  
  
 下列標記範例示範如何定義 Pericles 字型，使用屬性的文體替代圖像<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xml[OpenTypeFontSamples#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#2)]  
  
 下列的文字會顯示數個其他文體替代圖像 Pericles 字型。  
  
 ![使用 OpenType 文體替代圖像的文字](../../../../docs/framework/wpf/advanced/media/opentypefont03.png "opentypefont03")  
使用 OpenType 文體替代圖像的文字  
  
 下列標記範例示範如何定義這些其他文體替代圖像。  
  
 [!code-xml[OpenTypeFontSamples#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#3)]  
  
### <a name="random-contextual-alternates"></a>隨機內容替代字  
 隨機內容替代字提供多個替代圖像的單一字元。 實作時使用的指令碼類型的字型，這項功能可以使用一組隨機選擇圖像上稍有不同的外觀，模擬手寫。 下列文字 Lindsey 字型使用隨機內容替代字。 請注意，字母"a"而稍微不同的外觀  
  
 ![使用 OpenType 隨機內容替代文字](../../../../docs/framework/wpf/advanced/media/opentypefont23.png "OpenTypeFont23")  
使用 OpenType 隨機內容替代的文字  
  
 下列標記範例示範如何定義 Lindsey 字型，使用屬性的隨機內容替代字<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xml[OpenTypeFontSamples#OpenTypeFontSnippet20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet20)]  
  
### <a name="historical-forms"></a>古體形式  
 古體形式是過去常用的印刷樣式慣例。 下列文字會顯示 「 波士頓，麻州"片語 Palatino Linotype 字型的使用歷程記錄的形式的圖像 （glyph）。  
  
 ![使用 OpenType 古體形式的文字](../../../../docs/framework/wpf/advanced/media/opentypefont10.png "opentypefont10")  
使用 OpenType 古體形式的文字  
  
 下列標記範例示範如何定義古體形式的 Palatino Linotype 字型，請使用屬性的<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xml[OpenTypeFontSamples#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#8)]  
  
<a name="numerical_styles"></a>   
## <a name="numerical-styles"></a>數字的樣式  
 OpenType 字型支援大量的功能，可在文字中的數值。  
  
### <a name="fractions"></a>分數  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]字型的分數，包括加斜線和堆疊支援樣式。  
  
 下列文字的顯示比例 Palatino Linotype 字型樣式。  
  
 ![使用 OpenType 斜式和直式分數](../../../../docs/framework/wpf/advanced/media/opentypefont12.png "opentypefont12")  
使用 OpenType 斜式和直式分數的文字  
  
 下列標記範例示範如何定義 Palatino Linotype 字型，請使用屬性的分數樣式<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xml[OpenTypeFontSamples#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#10)]  
  
### <a name="old-style-numerals"></a>舊樣式數字  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]字型支援舊樣式數字格式。 此格式可用於顯示數字中是標準的樣式。 下列文字顯示 18 世紀日期 Palatino Linotype 字型的標準和舊樣式數字格式。  
  
 ![使用 OpenType 舊樣式數字的文字](../../../../docs/framework/wpf/advanced/media/opentypefont24.png "OpenTypeFont24")  
使用 OpenType 舊樣式數字的文字  
  
 下列的文字會顯示標準 Palatino Linotype 字型，後面接著舊樣式數字的數字。  
  
 ![使用 OpenType 舊樣式數字集的文字](../../../../docs/framework/wpf/advanced/media/opentypefont13.png "opentypefont13")  
使用 OpenType 舊樣式數字集的文字  
  
 下列標記範例示範如何定義 Palatino Linotype 字型，請使用屬性的舊樣式的數字<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xml[OpenTypeFontSamples#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#11)]  
  
### <a name="proportional-and-tabular-figures"></a>調和間距與表格式圖形  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]字型支援使用數字時，控制寬度對齊調和間距與表格式圖功能。 調和間距圖形會將每一個數字視為具有不同的寬度，"1"的"5"。 表格式的數字會被視為等寬，以便予以垂直對齊，進而提高財務類型資訊的可讀性。  
  
 下列文字會顯示兩個比例的圖形中使用 Miramonte 字型的第一個資料行。 請注意寬度數字"5"和"1"之間的差異。 第二個資料行顯示相同的兩個數值透過表格式圖形功能來調整其寬度。  
  
 ![使用 OpenType 調和間距 i 表格式圖形的文字](../../../../docs/framework/wpf/advanced/media/opentypefont22.png "OpenTypeFont22")  
使用 OpenType 調和間距與表格式圖形的文字  
  
 下列標記範例示範如何定義 Miramonte 字型，使用屬性的調和間距與表格式圖形<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xml[OpenTypeFontSamples#OpenTypeFontSnippet19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet19)]  
  
### <a name="slashed-zero"></a>加斜線的零  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]字型支援斜線零數字格式，以強調字母"O"與"0"數字之間的差異。 斜線零數字通常用於財務和商務資訊中的識別項。  
  
 下列文字會顯示使用 Miramonte 字型的範例訂單識別碼。 第一行會使用標準的數字。 第二行使用斜線零數字，以提供更好的對比與大寫字母"O"。  
  
 ![使用 OpenType 斜式零的數字](../../../../docs/framework/wpf/advanced/media/opentypefont17.png "OpenTypeFont17")  
使用 OpenType 零帶有斜線之數字的文字  
  
 下列標記範例示範如何定義斜線零數字 Miramonte 字型，使用屬性的<xref:System.Windows.Documents.Typography>物件。  
  
 [!code-xml[OpenTypeFontSamples#OpenTypeFontSnippet15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet15)]  
  
<a name="typography_class"></a>   
## <a name="typography-class"></a>印刷樣式類別  
 <xref:System.Windows.Documents.Typography>物件會公開一組功能，[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]字型支援。 藉由設定屬性<xref:System.Windows.Documents.Typography>在標記中，您可以輕鬆地撰寫充分利用的文件[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]功能。  
  
 下列的文字會顯示標準的大寫字母 Pescadero 字型，後面接著字母樣式設定為 「 SmallCaps 」 和 「 AllSmallCaps 」。 在此情況下，相同的字型大小用於所有的三個單字。  
  
 ![使用 OpenType 大寫的文字](../../../../docs/framework/wpf/advanced/media/opentypefont11.png "opentypefont11")  
使用 OpenType 大寫的文字  
  
 下列標記範例示範如何定義 Pescadero 字型，請使用屬性的大寫字<xref:System.Windows.Documents.Typography>物件。 使用 「 SmallCaps 」 格式時，會略過任何開頭的大寫字母。  
  
 [!code-xml[OpenTypeFontSamples#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
 下列程式碼範例可達成與先前的標記範例相同的工作。  
  
 [!code-csharp[TypographyCodeSnippets#TypographyCodeSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TypographyCodeSnippets/CSharp/Page1.xaml.cs#typographycodesnippet1)]
 [!code-vb[TypographyCodeSnippets#TypographyCodeSnippet1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TypographyCodeSnippets/visualbasic/page1.xaml.vb#typographycodesnippet1)]  
  
### <a name="typography-class-properties"></a>印刷樣式類別屬性  
 下表列出屬性、 值和預設設定<xref:System.Windows.Documents.Typography>物件。  
  
|屬性|值|預設值|  
|--------------|----------------|-------------------|  
|<xref:System.Windows.Documents.Typography.AnnotationAlternates%2A>|數值-位元組|0|  
|<xref:System.Windows.Documents.Typography.Capitals%2A>|<xref:System.Windows.FontCapitals> |<xref:System.Windows.FontCapitals> |<xref:System.Windows.FontCapitals> |<xref:System.Windows.FontCapitals> |<xref:System.Windows.FontCapitals> |<xref:System.Windows.FontCapitals> |<xref:System.Windows.FontCapitals>|<xref:System.Windows.FontCapitals?displayProperty=fullName>|  
|<xref:System.Windows.Documents.Typography.CapitalSpacing%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.CaseSensitiveForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.ContextualAlternates%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualSwashes%2A>|數值-位元組|0|  
|<xref:System.Windows.Documents.Typography.DiscretionaryLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianExpertForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianLanguage%2A>|<xref:System.Windows.FontEastAsianLanguage> |<xref:System.Windows.FontEastAsianLanguage> |<xref:System.Windows.FontEastAsianLanguage> |<xref:System.Windows.FontEastAsianLanguage> |<xref:System.Windows.FontEastAsianLanguage> |<xref:System.Windows.FontEastAsianLanguage> |<xref:System.Windows.FontEastAsianLanguage> |<xref:System.Windows.FontEastAsianLanguage>|<xref:System.Windows.FontEastAsianLanguage>|<xref:System.Windows.FontEastAsianLanguage>|<xref:System.Windows.FontEastAsianLanguage?displayProperty=fullName>|  
|<xref:System.Windows.Documents.Typography.EastAsianWidths%2A>|<xref:System.Windows.FontEastAsianWidths> |<xref:System.Windows.FontEastAsianWidths> |<xref:System.Windows.FontEastAsianWidths> |<xref:System.Windows.FontEastAsianWidths>|<xref:System.Windows.FontEastAsianWidths> |<xref:System.Windows.FontEastAsianWidths>|<xref:System.Windows.FontEastAsianWidths?displayProperty=fullName>|  
|<xref:System.Windows.Documents.Typography.Fraction%2A>|<xref:System.Windows.FontFraction>|<xref:System.Windows.FontFraction> |<xref:System.Windows.FontFraction>|<xref:System.Windows.FontFraction?displayProperty=fullName>|  
|<xref:System.Windows.Documents.Typography.HistoricalForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.HistoricalLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.Kerning%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.MathematicalGreek%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.NumeralAlignment%2A>|<xref:System.Windows.FontNumeralAlignment>|<xref:System.Windows.FontNumeralAlignment>|<xref:System.Windows.FontNumeralAlignment>|<xref:System.Windows.FontNumeralAlignment?displayProperty=fullName>|  
|<xref:System.Windows.Documents.Typography.NumeralStyle%2A>|<xref:System.Boolean>|<xref:System.Windows.FontNumeralStyle?displayProperty=fullName>|  
|<xref:System.Windows.Documents.Typography.SlashedZero%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StandardLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.StandardSwashes%2A>|數值 – 位元組|0|  
|<xref:System.Windows.Documents.Typography.StylisticAlternates%2A>|數值 – 位元組|0|  
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
|<xref:System.Windows.Documents.Typography.Variants%2A>|<xref:System.Windows.FontVariants>|<xref:System.Windows.FontVariants> |<xref:System.Windows.FontVariants> |<xref:System.Windows.FontVariants> |<xref:System.Windows.FontVariants> |<xref:System.Windows.FontVariants>|<xref:System.Windows.FontVariants?displayProperty=fullName>|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Documents.Typography>   
 [OpenType 規格](http://go.microsoft.com/fwlink/?LinkId=96731)   
 [在 WPF 中的印刷樣式](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)   
 [範例 OpenType 字型套件](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md)   
 [字型與應用程式一起封裝](../../../../docs/framework/wpf/advanced/packaging-fonts-with-applications.md)