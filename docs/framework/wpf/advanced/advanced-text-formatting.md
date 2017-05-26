---
title: "進階文字格式化 | Microsoft Docs"
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
  - "格式化 [WPF]"
  - "文字 [WPF]"
  - "印刷樣式, 文字格式"
ms.assetid: f0a7986e-f5b2-485c-a27d-f8e922022212
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 進階文字格式化
[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 提供一套健全的 [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)]，可供您用來將文字包含在應用程式中。  配置和[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] \(例如 <xref:System.Windows.Controls.TextBlock>\) 提供呈現文字時最常用的一般用途項目。  繪圖 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] \(例如 <xref:System.Windows.Media.GlyphRunDrawing> 和 <xref:System.Windows.Media.FormattedText>\) 則提供在繪圖中包含格式化文字的工具。  若以最先進層級的角度來看，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 提供了可擴充的文字格式化引擎，以控制文字呈現的各個層面，例如文字存放區管理、文字執行格式化管理，以及內嵌物件管理。  
  
 本主題提供 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 文字格式化的簡介，  內容著重於 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 文字格式化引擎的用戶端實作和用法。  
  
> [!NOTE]
>  本文件中的所有程式碼範例都可在[進階文字格式化範例](http://go.microsoft.com/fwlink/?LinkID=159965) \(英文\) 中找到。  
  
   
  
<a name="prereq"></a>   
## 必要條件  
 本主題假設您已相當熟悉用於文字呈現的高階 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]。  大部分的使用者案例都不需要這個主題所討論的進階文字格式化 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]。  如需不同文字 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 的簡介，請參閱 [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)。  
  
<a name="section1"></a>   
## 進階文字格式化  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中的文字配置和 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 控制項提供的格式化屬性，可以讓您輕鬆地在應用程式中加入格式化文字。  這些控制項會公開 \(Expose\) 許多屬性，以處理文字的呈現方式，包括其字樣、大小和色彩。  在一般情況下，這些控制項可以處理應用程式中大部分的文字呈現設定。  不過，某些進階案例則必須同時控制文字的儲存和文字的呈現。  為了因應這種情況，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 提供了可擴充的文字格式化引擎。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 提供的進階文字格式化功能是由文字格式化引擎、文字存放區和格式化屬性所組成。  這個文字格式化引擎 \(即 <xref:System.Windows.Media.TextFormatting.TextFormatter>\) 會建立數行展示用的文字。  建立的方法是啟始格式化處理序 \(Process\)，然後呼叫文字格式子 \(Formatter\) 的 <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>。  文字格式子會透過呼叫文字存放區的 <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> 方法，從存放區擷取文字執行。  接著文字格式子會將 <xref:System.Windows.Media.TextFormatting.TextRun> 物件編排成 <xref:System.Windows.Media.TextFormatting.TextLine> 物件，並將這些物件提供給您的應用程式，以供檢查或顯示之用。  
  
<a name="section2"></a>   
## 使用文字格式子  
 <xref:System.Windows.Media.TextFormatting.TextFormatter> 是 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 文字格式化引擎，並提供格式化及文字分行的服務。  這個文字格式子可以處理不同的文字字元格式和段落樣式，也包含了國際文字配置的支援。  
  
 與傳統文字 [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] 不同的是，<xref:System.Windows.Media.TextFormatting.TextFormatter> 會透過一組回呼方法，與文字配置用戶端互動。  它會要求要用戶端在 <xref:System.Windows.Media.TextFormatting.TextSource> 類別實作中提供這些方法。  下列圖表說明用戶端應用程式和 <xref:System.Windows.Media.TextFormatting.TextFormatter> 之間的文字配置互動。  
  
 ![文字配置用戶端和 TextFormatter 的圖表](../../../../docs/framework/wpf/advanced/media/textformatter01.png "TextFormatter01")  
應用程式和 TextFormatter 之間的互動  
  
 文字格式子可用來從文字存放區擷取格式化的文字行，而這是 <xref:System.Windows.Media.TextFormatting.TextSource> 的實作。  實作的方式是先使用 <xref:System.Windows.Media.TextFormatting.TextFormatter.Create%2A> 方法建立文字格式子的執行個體  \(除了建立文字格式子的執行個體之外，這個方法還會設定行高和行寬的最大值\)；  建立文字格式子的執行個體之後，文字行建立處理序就會透過呼叫 <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> 方法啟動。  <xref:System.Windows.Media.TextFormatting.TextFormatter> 會回呼文字來源，以針對構成行的文字執行，擷取文字和格式化參數。  
  
 下列範例顯示格式化文字存放區的處理序。  此範例使用 <xref:System.Windows.Media.TextFormatting.TextFormatter> 物件從文字存放區擷取文字行，然後再格式化要繪製到 <xref:System.Windows.Media.DrawingContext> 的文字行。  
  
 [!code-csharp[TextFormatterExample#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextFormatterExample#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/Window1.xaml.vb#100)]  
  
<a name="section3"></a>   
## 實作用戶端文字存放區  
 擴充文字格式化引擎時，您必須實作並管理文字存放區的所有層面。  這並不是一項簡單的工作。  文字存放區負責追蹤文字執行屬性、段落屬性、內嵌物件和其他類似的內容。  它也為文字格式子提供個別的 <xref:System.Windows.Media.TextFormatting.TextRun> 物件，供文字格式子用來建立 <xref:System.Windows.Media.TextFormatting.TextLine> 物件。  
  
 為了處理文字存放區的虛擬化，文字存放區必須衍生自 <xref:System.Windows.Media.TextFormatting.TextSource>。  <xref:System.Windows.Media.TextFormatting.TextSource> 會定義文字格式子用來從文字存放區擷取文字執行的方法。  <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> 則是文字格式子擷取用於設定行格式的文字執行時所使用的方法。  文字格式子會重複呼叫 <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>，直到發生下列其中一種狀況：  
  
-   傳回 <xref:System.Windows.Media.TextFormatting.TextEndOfLine> 或子類別 \(Subclass\)。  
  
-   文字執行的總寬度超過建立文字格式子呼叫或文字格式子之 <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> 方法呼叫中所指定的最大行寬。  
  
-   傳回 [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] 新行序列，例如 "CF"、"LF" 或 "CRLF"。  
  
<a name="section4"></a>   
## 提供文字執行  
 文字格式化處理序的核心是文字格式子與文字存放區之間的互動。  <xref:System.Windows.Media.TextFormatting.TextSource> 的實作為文字格式子提供了用來格式化文字執行的 <xref:System.Windows.Media.TextFormatting.TextRun> 物件和屬性。  這種互動是由文字格式子所呼叫的 <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> 方法負責處理。  
  
 下表顯示部分慣用的 <xref:System.Windows.Media.TextFormatting.TextRun> 物件。  
  
|TextRun 型別|使用方式|  
|----------------|----------|  
|<xref:System.Windows.Media.TextFormatting.TextCharacters>|用來將字元圖像 \(Glyph\) 表示傳回給文字格式子的特殊文字執行。|  
|<xref:System.Windows.Media.TextFormatting.TextEmbeddedObject>|用於提供完整執行測量、點擊測試 \(Hit Testing\) 和繪圖之內容的特殊文字執行，例如文字內的按鈕或影像。|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfLine>|用來標記行尾的特殊文字執行。|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|用來標記段落結尾的特殊文字執行。|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>|用來標記區段結尾的特殊文字執行，例如結束受先前 <xref:System.Windows.Media.TextFormatting.TextModifier> 執行影響的範圍。|  
|<xref:System.Windows.Media.TextFormatting.TextHidden>|用來標記隱藏字元範圍的特殊文字執行。|  
|<xref:System.Windows.Media.TextFormatting.TextModifier>|用來修改其範圍中文字執行屬性的特殊文字執行。  此範圍延伸到下一個相符的 <xref:System.Windows.Media.TextFormatting.TextEndOfSegment> 文字執行，或是下一個 <xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>。|  
  
 您可以將任何預先定義的 <xref:System.Windows.Media.TextFormatting.TextRun> 物件子類別化 \(Subclass\)，  使文字來源能夠為文字格式子提供包含自訂資料的文字執行。  
  
 下列範例示範 <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> 方法。  這個文字存放區會將 <xref:System.Windows.Media.TextFormatting.TextRun> 物件傳回給文字格式子，供其處理。  
  
 [!code-csharp[TextFormatterExample#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/CustomTextSource.cs#101)]
 [!code-vb[TextFormatterExample#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/CustomTextSource.vb#101)]  
  
> [!NOTE]
>  在這個範例中，文字存放區為所有文字提供相同的文字屬性。  進階文字存放區必須實作自己的範圍管理，以便讓個別字元可以擁有不同的屬性。  
  
<a name="section5"></a>   
## 指定格式化屬性  
 <xref:System.Windows.Media.TextFormatting.TextRun> 物件的格式是使用文字存放區提供的屬性設定。  這些屬性可分成 <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> 和 <xref:System.Windows.Media.TextFormatting.TextRunProperties> 兩種型別。  <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> 負責處理段落內含屬性，例如 <xref:System.Windows.TextAlignment> 和 <xref:System.Windows.FlowDirection>。  <xref:System.Windows.Media.TextFormatting.TextRunProperties> 則是段落內各個文字執行可能採用不同設定的屬性，例如前景筆刷、<xref:System.Windows.Media.Typeface> 和字型大小。  若要實作自訂段落和自訂文字執行屬性型別，您的應用程式必須分別建立衍生自 <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> 和 <xref:System.Windows.Media.TextFormatting.TextRunProperties> 的類別。  
  
## 請參閱  
 [WPF 中的印刷樣式](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)   
 [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)