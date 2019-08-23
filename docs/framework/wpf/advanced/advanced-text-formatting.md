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
ms.openlocfilehash: 469c62691ff38a8c5a01bec3ddfd7b324bab7eca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969072"
---
# <a name="advanced-text-formatting"></a>進階文字格式化
Windows Presentation Foundation (WPF) 提供一組健全的 Api, 以便在您的應用程式中包含文字。 版面配置[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]和 api ( <xref:System.Windows.Controls.TextBlock>例如) 提供最常見且一般的使用專案來呈現文字。 繪製 api (例如<xref:System.Windows.Media.GlyphRunDrawing>和<xref:System.Windows.Media.FormattedText>) 提供了一種方法, 可在繪圖中包含格式化的文字。 在最先進的層級[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]中, 提供可延伸的文字格式設定引擎來控制文字呈現的每個層面, 例如文字存放區管理、文字執行格式管理和内嵌物件管理。  
  
 本主題提供[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]文字格式的簡介。 它著重于用戶端的執行和使用[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]文字格式設定引擎。  
  
> [!NOTE]
> 本檔中的所有程式碼範例都可以在「[先進文字格式」範例](https://go.microsoft.com/fwlink/?LinkID=159965)中找到。  

<a name="prereq"></a>   
## <a name="prerequisites"></a>必要條件  
 本主題假設您熟悉用於文字呈現的較高層級 Api。 大部分的使用者案例都不需要本主題中討論的先進文字格式 Api。 如需不同文字 Api 的簡介, 請參閱[WPF 中的檔](documents-in-wpf.md)。  
  
<a name="section1"></a>   
## <a name="advanced-text-formatting"></a>進階文字格式化  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 中[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]的文字版面配置和控制項提供格式化屬性, 可讓您輕鬆地在應用程式中包含格式化的文字。 這些控制項會公開一些屬性來處理文字的呈現方式，包括其字體、大小和色彩。 在一般情況下，這些控制項可以處理您應用程式中大部分的文字呈現。 不過，某些進階的情節需要控制文字儲存以及文字呈現。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 針對這個用途提供可延伸的文字格式設定引擎。  
  
 中[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]找到的先進文字格式設定功能包含文字格式設定引擎、文字存放區、文字執行, 以及格式化屬性。 文字格式設定引擎<xref:System.Windows.Media.TextFormatting.TextFormatter>會建立要用於簡報的文字行。 這是藉由起始行格式化程式, 並呼叫文字格式器的<xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>來達成。 文字格式子會藉由呼叫存放區的<xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>方法, 從您的文字存放區抓取文字執行。 然後, 文字<xref:System.Windows.Media.TextFormatting.TextLine>格式器會將物件組成物件,並提供給您的應用程式進行檢查或顯示。<xref:System.Windows.Media.TextFormatting.TextRun>  
  
<a name="section2"></a>   
## <a name="using-the-text-formatter"></a>使用文字格式子  
 <xref:System.Windows.Media.TextFormatting.TextFormatter>[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]是文字格式設定引擎, 並提供用於格式化和中斷文字線條的服務。 文字格式子可處理不同的文字字元格式和段落樣式，且包含國際文字版面配置的支援。  
  
 不同于傳統文字 API, <xref:System.Windows.Media.TextFormatting.TextFormatter>會透過一組回呼方法與文字佈局用戶端互動。 它要求用戶端在<xref:System.Windows.Media.TextFormatting.TextSource>類別的執行中提供這些方法。 下圖說明用戶端應用程式與<xref:System.Windows.Media.TextFormatting.TextFormatter>之間的文字版面配置互動。  
  
 ![文字配置用戶端和 TextFormatter 的圖表](./media/advanced-text-formatting/text-layout-textformatter-interaction.png)  
  
 文字格式器是用來從文字存放區取出格式化的文本行, 這是的<xref:System.Windows.Media.TextFormatting.TextSource>實作為。 做法是先使用<xref:System.Windows.Media.TextFormatting.TextFormatter.Create%2A>方法來建立文字格式器的實例。 這個方法會建立文字格式子的執行個體，並設定最大線條高度和寬度的值。 一旦建立了文字格式器的實例, 就會藉由呼叫<xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>方法來啟動程式列建立程式。 <xref:System.Windows.Media.TextFormatting.TextFormatter>回呼至文字來源, 以抓取形成線條之文字執行的文字和格式設定參數。  
  
 在下列範例中，會顯示格式設定文字存放區的程序。 物件是用來從文字存放區中取出文字, 然後將繪製<xref:System.Windows.Media.DrawingContext>的文字行格式化為。 <xref:System.Windows.Media.TextFormatting.TextFormatter>  
  
 [!code-csharp[TextFormatterExample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextFormatterExample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/Window1.xaml.vb#100)]  
  
<a name="section3"></a>   
## <a name="implementing-the-client-text-store"></a>實作用戶端文字存放區  
 當您延伸文字格式設定引擎時，您必須實作與管理文字存放區的所有層面。 這不是簡單的工作。 文字存放區負責追蹤文字執行屬性、段落屬性、內嵌的物件，以及其他類似的內容。 它也會提供文字格式器, <xref:System.Windows.Media.TextFormatting.TextRun>其中包含文字格式子用來建立<xref:System.Windows.Media.TextFormatting.TextLine>物件的個別物件。  
  
 若要處理文字存放區的虛擬化, 文字存放區必須衍生自<xref:System.Windows.Media.TextFormatting.TextSource>。 <xref:System.Windows.Media.TextFormatting.TextSource>定義文字格式器用來從文字存放區取出文字執行的方法。 <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>這是文字格式器用來抓取用於行格式化之文字回合的方法。 的呼叫<xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>是由文字格式子重複執行, 直到發生下列其中一種情況為止:  
  
- 傳回<xref:System.Windows.Media.TextFormatting.TextEndOfLine>或子類別。  
  
- 文字回合的累積寬度超過呼叫以建立文字格式器或呼叫文字格式器的<xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>方法所指定的最大行寬度。  
  
- 傳回[!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)]分行符號序列, 例如 "CF"、"LF" 或 "CRLF"。  
  
<a name="section4"></a>   
## <a name="providing-text-runs"></a>提供文字執行  
 文字格式設定程序的核心是文字格式子與文字存放區之間的互動。 您的<xref:System.Windows.Media.TextFormatting.TextSource>執行會為文字<xref:System.Windows.Media.TextFormatting.TextRun>格式器提供物件, 以及用來格式化文字執行的屬性。 這項互動是由<xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>方法所處理, 而這是由文字格式器所呼叫。  
  
 下表顯示一些預先定義<xref:System.Windows.Media.TextFormatting.TextRun>的物件。  
  
|TextRun 類型|使用量|  
|------------------|-----------|  
|<xref:System.Windows.Media.TextFormatting.TextCharacters>|用來將字元圖像 (glyph) 的表示法傳回文字格式子的特殊文字執行。|  
|<xref:System.Windows.Media.TextFormatting.TextEmbeddedObject>|用來提供內容的特殊文字執行，在這些內容中會整體進行測量、點擊測試和繪製，例如文字內的按鈕或影像。|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfLine>|用來標記行尾的特殊文字執行。|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|用來標記段落結尾的特殊文字執行。|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>|用來標示區段結尾的特製化文字執行, 例如結束先前<xref:System.Windows.Media.TextFormatting.TextModifier>執行所影響的範圍。|  
|<xref:System.Windows.Media.TextFormatting.TextHidden>|用來標記隱藏字元範圍的特殊文字執行。|  
|<xref:System.Windows.Media.TextFormatting.TextModifier>|用來在文字執行範圍中修改其屬性的特殊文字執行。 範圍會延伸到下一個相符<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>的文字執行, 或下<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>一個。|  
  
 任何預先定義<xref:System.Windows.Media.TextFormatting.TextRun>的物件都可以子類別化。 這可讓文字來源提供文字格式子包含自訂資料的文字執行。  
  
 下列範例示範<xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>方法。 此文字存放區<xref:System.Windows.Media.TextFormatting.TextRun>會將物件傳回至文字格式器以進行處理。  
  
 [!code-csharp[TextFormatterExample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/CustomTextSource.cs#101)]
 [!code-vb[TextFormatterExample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/CustomTextSource.vb#101)]  
  
> [!NOTE]
> 在此範例中，文字存放區提供相同的文字屬性給所有文字。 進階的文字存放區必須實作自己的範圍管理，以允許個別字元可以有不同的屬性。  
  
<a name="section5"></a>   
## <a name="specifying-formatting-properties"></a>指定格式設定屬性  
 <xref:System.Windows.Media.TextFormatting.TextRun>物件是使用文字存放區所提供的屬性來格式化。 這些屬性有兩種類型: <xref:System.Windows.Media.TextFormatting.TextParagraphProperties>和<xref:System.Windows.Media.TextFormatting.TextRunProperties>。 <xref:System.Windows.Media.TextFormatting.TextParagraphProperties>處理段落內含屬性<xref:System.Windows.TextAlignment> , 例如和。 <xref:System.Windows.FlowDirection> <xref:System.Windows.Media.TextFormatting.TextRunProperties>這兩個屬性對於段落中的每個文字執行都可能不同, 例如前景筆<xref:System.Windows.Media.Typeface>刷、和字型大小。 若要執行自訂段落和自訂文字執行屬性類型, 您的應用程式必須<xref:System.Windows.Media.TextFormatting.TextParagraphProperties>分別<xref:System.Windows.Media.TextFormatting.TextRunProperties>建立衍生自和的類別。  
  
## <a name="see-also"></a>另請參閱

- [WPF 中的印刷樣式](typography-in-wpf.md)
- [WPF 中的文件](documents-in-wpf.md)
