---
title: 進階文字格式化
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- formatting [WPF]
- text [WPF]
- typography [WPF], text formatting
ms.assetid: f0a7986e-f5b2-485c-a27d-f8e922022212
ms.openlocfilehash: 745d20e0bd4f877f9d4559f9fc7829b56689d35c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185934"
---
# <a name="advanced-text-formatting"></a>進階文字格式化
Windows 演示基礎 （WPF） 提供了一組強大的 API，用於在應用程式中包含文本。 佈局和[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]API（如<xref:System.Windows.Controls.TextBlock>）為文本表示提供了最常用和最常用的元素。 繪圖 API（如<xref:System.Windows.Media.GlyphRunDrawing>和<xref:System.Windows.Media.FormattedText>）提供了一種在圖形中包含格式化文字的方法。 在最先進的級別上，WPF 提供了一個可擴展的文本格式引擎來控制文本表示的各個方面，如文本存儲管理、文本運行格式管理和內嵌物件管理。  
  
 本主題介紹了 WPF 文本格式。 它側重于用戶端實現和使用 WPF 文本格式引擎。  
  
> [!NOTE]
> 本文檔中的所有代碼示例都可以在[高級文本格式示例](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI/TextFormatting)中找到。  

<a name="prereq"></a>
## <a name="prerequisites"></a>必要條件  
 本主題假定您熟悉用於文本表示的更高級別 API。 大多數使用者方案不需要本主題中討論的高級文本格式 API。 有關不同文本 API 的介紹，請參閱[WPF 中的文檔](documents-in-wpf.md)。  
  
<a name="section1"></a>
## <a name="advanced-text-formatting"></a>進階文字格式化  
 WPF 中[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]的文本佈局和控制項提供格式屬性，允許您輕鬆地在應用程式中包含格式化文字。 這些控制項會公開一些屬性來處理文字的呈現方式，包括其字體、大小和色彩。 在一般情況下，這些控制項可以處理您應用程式中大部分的文字呈現。 不過，某些進階的情節需要控制文字儲存以及文字呈現。 為此，WPF 提供了可擴展的文本格式引擎。  
  
 WPF 中的高級文本格式設置功能包括文本格式引擎、文本存儲、文本運行和格式設置屬性。 文本格式引擎 ，<xref:System.Windows.Media.TextFormatting.TextFormatter>創建要用於表示的文本行。 這是通過啟動行格式設置過程並調用文本格式化的 來實現的<xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>。 文本 formatter 通過調用存儲<xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>的方法檢索文本存儲運行的文本。 然後<xref:System.Windows.Media.TextFormatting.TextRun>，物件由文本物質<xref:System.Windows.Media.TextFormatting.TextLine>組成物件，並提供給應用程式進行檢查或顯示。  
  
<a name="section2"></a>
## <a name="using-the-text-formatter"></a>使用文字格式子  
 <xref:System.Windows.Media.TextFormatting.TextFormatter>是 WPF 文本格式設置引擎，並提供格式化和斷開文本行的服務。 文字格式子可處理不同的文字字元格式和段落樣式，且包含國際文字版面配置的支援。  
  
 與傳統文本 API 不同，<xref:System.Windows.Media.TextFormatting.TextFormatter>通過一組回檔方法與文本佈局用戶端進行交互。 它要求用戶端在<xref:System.Windows.Media.TextFormatting.TextSource>類的實現中提供這些方法。 下圖說明瞭用戶端應用程式和<xref:System.Windows.Media.TextFormatting.TextFormatter>之間的文本佈局交互。  
  
 ![文字配置用戶端和 TextFormatter 的圖表](./media/advanced-text-formatting/text-layout-textformatter-interaction.png)  
  
 文本格式化用於從文本存儲檢索格式化的文本行，文本存儲是 的<xref:System.Windows.Media.TextFormatting.TextSource>實現。 這是首先使用 方法創建文本前物質的實例來實現的<xref:System.Windows.Media.TextFormatting.TextFormatter.Create%2A>。 這個方法會建立文字格式子的執行個體，並設定最大線條高度和寬度的值。 一旦創建了文本前物質的實例，行創建過程就會通過調用<xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>方法啟動。 <xref:System.Windows.Media.TextFormatting.TextFormatter>調用回文本源以檢索構成行的文本運行的文本和格式參數。  
  
 在下列範例中，會顯示格式設定文字存放區的程序。 該<xref:System.Windows.Media.TextFormatting.TextFormatter>物件用於從文本存儲中檢索文本行，然後格式化文字行以繪製到 中<xref:System.Windows.Media.DrawingContext>。  
  
 [!code-csharp[TextFormatterExample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextFormatterExample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/Window1.xaml.vb#100)]  
  
<a name="section3"></a>
## <a name="implementing-the-client-text-store"></a>實作用戶端文字存放區  
 當您延伸文字格式設定引擎時，您必須實作與管理文字存放區的所有層面。 這不是簡單的工作。 文字存放區負責追蹤文字執行屬性、段落屬性、內嵌的物件，以及其他類似的內容。 它還為文本前物質用於創建<xref:System.Windows.Media.TextFormatting.TextRun><xref:System.Windows.Media.TextFormatting.TextLine>物件的單個物件提供文本前身。  
  
 要處理文本存儲的虛擬化，文本存儲必須派生自<xref:System.Windows.Media.TextFormatting.TextSource>。 <xref:System.Windows.Media.TextFormatting.TextSource>定義文本前物質用於檢索文本存儲中運行的文本的方法。 <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>是文本格式化用於檢索行格式中使用的文本運行的方法。 調用<xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>由文本事件重複進行，直到出現以下情況之一：  
  
- 返回<xref:System.Windows.Media.TextFormatting.TextEndOfLine>a 或子類。  
  
- 文本運行的累積寬度超過調用中指定的最大行寬，以創建文本 formatter 或對文本 formatter 方法的<xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>調用。  
  
- 返回 Unicode newline 序列，如"CF"、"LF"或"CRLF"。  
  
<a name="section4"></a>
## <a name="providing-text-runs"></a>提供文字執行  
 文字格式設定程序的核心是文字格式子與文字存放區之間的互動。 的<xref:System.Windows.Media.TextFormatting.TextSource>實現為文本格式化提供了<xref:System.Windows.Media.TextFormatting.TextRun>物件和用於設置文本運行格式的屬性。 此交互由<xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>方法處理，該方法由文本前物質調用。  
  
 下表顯示了一些預定義<xref:System.Windows.Media.TextFormatting.TextRun>物件。  
  
|TextRun 類型|使用量|  
|------------------|-----------|  
|<xref:System.Windows.Media.TextFormatting.TextCharacters>|用來將字元圖像 (glyph) 的表示法傳回文字格式子的特殊文字執行。|  
|<xref:System.Windows.Media.TextFormatting.TextEmbeddedObject>|用來提供內容的特殊文字執行，在這些內容中會整體進行測量、點擊測試和繪製，例如文字內的按鈕或影像。|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfLine>|用來標記行尾的特殊文字執行。|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|用來標記段落結尾的特殊文字執行。|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>|用於標記段末尾的專用文本運行，例如結束受上一次<xref:System.Windows.Media.TextFormatting.TextModifier>運行影響的範圍。|  
|<xref:System.Windows.Media.TextFormatting.TextHidden>|用來標記隱藏字元範圍的特殊文字執行。|  
|<xref:System.Windows.Media.TextFormatting.TextModifier>|用來在文字執行範圍中修改其屬性的特殊文字執行。 範圍擴展到下一個匹配<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>的文本運行或下一個<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>。|  
  
 可以對任何預定義<xref:System.Windows.Media.TextFormatting.TextRun>的物件進行子分類。 這可讓文字來源提供文字格式子包含自訂資料的文字執行。  
  
 下面的示例演示了一<xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>種方法。 此文本存儲將<xref:System.Windows.Media.TextFormatting.TextRun>物件返回到文本事件進行處理。  
  
 [!code-csharp[TextFormatterExample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/CustomTextSource.cs#101)]
 [!code-vb[TextFormatterExample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/CustomTextSource.vb#101)]  
  
> [!NOTE]
> 在此範例中，文字存放區提供相同的文字屬性給所有文字。 進階的文字存放區必須實作自己的範圍管理，以允許個別字元可以有不同的屬性。  
  
<a name="section5"></a>
## <a name="specifying-formatting-properties"></a>指定格式設定屬性  
 <xref:System.Windows.Media.TextFormatting.TextRun>物件使用文本存儲提供的屬性進行格式化。 這些屬性有兩種類型，<xref:System.Windows.Media.TextFormatting.TextParagraphProperties>和<xref:System.Windows.Media.TextFormatting.TextRunProperties>。 <xref:System.Windows.Media.TextFormatting.TextParagraphProperties>處理段落包含屬性，如<xref:System.Windows.TextAlignment><xref:System.Windows.FlowDirection>和 。 <xref:System.Windows.Media.TextFormatting.TextRunProperties>對於在段落中運行的每個文本（如前景畫筆和<xref:System.Windows.Media.Typeface>字體大小）可以不同的屬性。 要實現自訂段落和自訂文本運行屬性類型，應用程式必須創建派生自<xref:System.Windows.Media.TextFormatting.TextParagraphProperties>和<xref:System.Windows.Media.TextFormatting.TextRunProperties>派生的類。  
  
## <a name="see-also"></a>另請參閱

- [WPF 中的印刷樣式](typography-in-wpf.md)
- [WPF 中的文件](documents-in-wpf.md)
