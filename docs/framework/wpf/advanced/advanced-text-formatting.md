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
ms.openlocfilehash: 0d3b44007524f502d8393d1dc1834142090a7a15
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238651"
---
# <a name="advanced-text-formatting"></a>進階文字格式化
Windows Presentation Foundation (WPF) 提供一組強大的 Api 在您的應用程式中包含文字。 版面配置並[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]Api，例如<xref:System.Windows.Controls.TextBlock>、 提供最常見和一般用途的文字表示的項目。 繪製的 Api，例如<xref:System.Windows.Media.GlyphRunDrawing>和<xref:System.Windows.Media.FormattedText>，提供在繪圖中包括格式化的文字的方法。 在最進階層級，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]提供可延伸的文字格式設定引擎，以控制文字表示，例如文字存放區管理、 文字執行格式設定管理，以及內嵌的物件管理的各個層面。  
  
 本主題提供簡介[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]文字格式設定。 它著重於用戶端實作與使用[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]文字格式設定引擎。  
  
> [!NOTE]
>  此文件中的所有程式碼範例可在[進階文字格式設定範例](https://go.microsoft.com/fwlink/?LinkID=159965)。  

<a name="prereq"></a>   
## <a name="prerequisites"></a>必要條件  
 本主題假設您已熟悉使用較高的層級 Api，用來呈現文字。 大部分使用者案例不需要進階的文字格式化本主題中討論的 Api。 如需不同文字 Api 的簡介，請參閱[WPF 中的文件](documents-in-wpf.md)。  
  
<a name="section1"></a>   
## <a name="advanced-text-formatting"></a>進階文字格式化  
 文字版面配置並[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]中的控制項[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]提供可讓您輕鬆地在您的應用程式中包含格式化的文字格式設定屬性。 這些控制項會公開一些屬性來處理文字的呈現方式，包括其字體、大小和色彩。 在一般情況下，這些控制項可以處理您應用程式中大部分的文字呈現。 不過，某些進階的情節需要控制文字儲存以及文字呈現。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 針對這個用途提供可延伸的文字格式設定引擎。  
  
 進階的文字格式化功能位於[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]包括文字格式設定引擎、 文字存放區、 文字執行，並格式化屬性。 文字格式設定引擎， <xref:System.Windows.Media.TextFormatting.TextFormatter>，建立要用於呈現的文字行。 這起始行格式設定程序，並呼叫文字格式子來達成<xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>。 文字格式子從文字存放區擷取文字執行，藉由呼叫存放區的<xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>方法。 <xref:System.Windows.Media.TextFormatting.TextRun>物件然後形成<xref:System.Windows.Media.TextFormatting.TextLine>文字格式子物件並傳送到您的應用程式，來檢查或顯示。  
  
<a name="section2"></a>   
## <a name="using-the-text-formatter"></a>使用文字格式子  
 <xref:System.Windows.Media.TextFormatting.TextFormatter> 是[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]文字格式設定引擎，並提供格式設定和分隔文字行的服務。 文字格式子可處理不同的文字字元格式和段落樣式，且包含國際文字版面配置的支援。  
  
 不同於傳統的文字 API，<xref:System.Windows.Media.TextFormatting.TextFormatter>互動文字配置用戶端透過一組回呼方法。 它需要用戶端提供這些方法的實作中<xref:System.Windows.Media.TextFormatting.TextSource>類別。 下圖說明用戶端應用程式之間的文字版面配置互動和<xref:System.Windows.Media.TextFormatting.TextFormatter>。  
  
 ![文字配置用戶端和 TextFormatter 的圖表](./media/advanced-text-formatting/text-layout-textformatter-interaction.png)  
  
 文字格式子用來擷取格式化的文字行從文字存放區中，這是實作<xref:System.Windows.Media.TextFormatting.TextSource>。 這是藉由先建立文字格式子的執行個體使用<xref:System.Windows.Media.TextFormatting.TextFormatter.Create%2A>方法。 這個方法會建立文字格式子的執行個體，並設定最大線條高度和寬度的值。 一旦建立文字格式子的執行個體，啟動列的建立程序呼叫<xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>方法。 <xref:System.Windows.Media.TextFormatting.TextFormatter> 呼叫回到文字來源以擷取的文字和文字執行格式設定參數該表單一條線。  
  
 在下列範例中，會顯示格式設定文字存放區的程序。 <xref:System.Windows.Media.TextFormatting.TextFormatter>物件用來從文字存放區擷取文字行，然後格式化文字行，以便繪製到<xref:System.Windows.Media.DrawingContext>。  
  
 [!code-csharp[TextFormatterExample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextFormatterExample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/Window1.xaml.vb#100)]  
  
<a name="section3"></a>   
## <a name="implementing-the-client-text-store"></a>實作用戶端文字存放區  
 當您延伸文字格式設定引擎時，您必須實作與管理文字存放區的所有層面。 這不是簡單的工作。 文字存放區負責追蹤文字執行屬性、段落屬性、內嵌的物件，以及其他類似的內容。 它也提供文字格式子的個別<xref:System.Windows.Media.TextFormatting.TextRun>文字格式子用來建立物件<xref:System.Windows.Media.TextFormatting.TextLine>物件。  
  
 若要處理的文字存放區的虛擬化，文字存放區必須衍生自<xref:System.Windows.Media.TextFormatting.TextSource>。 <xref:System.Windows.Media.TextFormatting.TextSource> 定義文字格式子用來從文字存放區擷取文字執行的方法。 <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> 是由文字格式子用來擷取文字的方法執行用於線條格式。 若要呼叫<xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>重複進行文字格式子到發生下列條件之一為止：  
  
- A<xref:System.Windows.Media.TextFormatting.TextEndOfLine>或子類別會傳回。  
  
- 文字往返的累積的寬度超過建立文字格式子呼叫或文字格式子的呼叫中指定的最大線條寬度<xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>方法。  
  
- A[!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)]傳回新行字元序列，例如"CF"、"LF"或"CRLF"。  
  
<a name="section4"></a>   
## <a name="providing-text-runs"></a>提供文字執行  
 文字格式設定程序的核心是文字格式子與文字存放區之間的互動。 您實作<xref:System.Windows.Media.TextFormatting.TextSource>提供文字格式子使用<xref:System.Windows.Media.TextFormatting.TextRun>物件以及用來格式化的文字往返的屬性。 這種互動由<xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>方法由文字格式子呼叫。  
  
 下表顯示一些預先定義之<xref:System.Windows.Media.TextFormatting.TextRun>物件。  
  
|TextRun 類型|使用量|  
|------------------|-----------|  
|<xref:System.Windows.Media.TextFormatting.TextCharacters>|用來將字元圖像 (glyph) 的表示法傳回文字格式子的特殊文字執行。|  
|<xref:System.Windows.Media.TextFormatting.TextEmbeddedObject>|用來提供內容的特殊文字執行，在這些內容中會整體進行測量、點擊測試和繪製，例如文字內的按鈕或影像。|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfLine>|用來標記行尾的特殊文字執行。|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|用來標記段落結尾的特殊文字執行。|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>|用來尾端的區段，例如先前受影響的範圍結尾的特殊的文字執行<xref:System.Windows.Media.TextFormatting.TextModifier>執行。|  
|<xref:System.Windows.Media.TextFormatting.TextHidden>|用來標記隱藏字元範圍的特殊文字執行。|  
|<xref:System.Windows.Media.TextFormatting.TextModifier>|用來在文字執行範圍中修改其屬性的特殊文字執行。 範圍延伸至下一個相符<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>文字執行或下一個<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>。|  
  
 任何預先定義之<xref:System.Windows.Media.TextFormatting.TextRun>物件可以進行子類別化。 這可讓文字來源提供文字格式子包含自訂資料的文字執行。  
  
 下列範例示範<xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>方法。 此文字存放區傳回<xref:System.Windows.Media.TextFormatting.TextRun>文字格式子進行處理的物件。  
  
 [!code-csharp[TextFormatterExample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/CustomTextSource.cs#101)]
 [!code-vb[TextFormatterExample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/CustomTextSource.vb#101)]  
  
> [!NOTE]
>  在此範例中，文字存放區提供相同的文字屬性給所有文字。 進階的文字存放區必須實作自己的範圍管理，以允許個別字元可以有不同的屬性。  
  
<a name="section5"></a>   
## <a name="specifying-formatting-properties"></a>指定格式設定屬性  
 <xref:System.Windows.Media.TextFormatting.TextRun> 使用文字存放區所提供的屬性時，會格式化物件。 這些屬性可分成兩種類型，<xref:System.Windows.Media.TextFormatting.TextParagraphProperties>和<xref:System.Windows.Media.TextFormatting.TextRunProperties>。 <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> 處理段落包含的屬性，例如<xref:System.Windows.TextAlignment>和<xref:System.Windows.FlowDirection>。 <xref:System.Windows.Media.TextFormatting.TextRunProperties> 屬性可以有不同的每個文字執行中的段落，例如前景筆刷， <xref:System.Windows.Media.Typeface>，和字型大小。 若要實作自訂的段落和自訂的文字執行屬性類型，您的應用程式必須建立衍生自類別<xref:System.Windows.Media.TextFormatting.TextParagraphProperties>和<xref:System.Windows.Media.TextFormatting.TextRunProperties>分別。  
  
## <a name="see-also"></a>另請參閱

- [WPF 中的印刷樣式](typography-in-wpf.md)
- [WPF 中的文件](documents-in-wpf.md)
