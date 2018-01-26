---
title: "XAML 概觀 (WPF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user interfaces [XAML]
- classes [XAML]
- root element [XAML]
- XAML [WPF], about XAML
- base classes [XAML]
- routed events [WPF]
- code-behind files [WPF], XAML
- collection properties [XAML]
- events [XAML]
- property element [XAML]
- content models [XAML]
- Extensible Application Markup Language (see XAML)
- attribute syntax [XAML]
ms.assetid: a80db4cd-dd0f-479f-a45f-3740017c22e4
caps.latest.revision: "57"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ce83713d2483320569bde0d5c9a677f0b357ebf2
ms.sourcegitcommit: c3ebb11a66e85a465c9ba2c42592222630b7ff9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="xaml-overview-wpf"></a>XAML 概觀 (WPF)
本主題說明 XAML 語言的功能，並示範如何使用 XAML 撰寫 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式。 本主題特別針對以 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 實作的 XAML 進行描述。 就語言概念而言，XAML 本身涵蓋的範圍比 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 還要廣。  
  
  
  
<a name="what_is_xaml"></a>   
## <a name="what-is-xaml"></a>何謂 XAML？  
 XAML 是一種宣告式的標記語言。 XAML 套用至 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] 程式撰寫模型時，可簡化 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] 應用程式的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 建立。 您可以在宣告式 XAML 標記中建立可見的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 元素，然後藉由使用程式碼後置的檔案 (已透過部分類別定義而聯結至該標記)，區隔 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 定義和執行階段邏輯。 XAML 會以組件中定義的一組支援型別，直接表示物件的執行個體化。 這一點有別於其他大部分的標記語言，通常大部分的標記語言是與支援型別系統沒有此種直接關連的直譯式語言。 XAML 會啟用工作流程，其中個別獨立的人員因而能夠使用不同的工具，操作應用程式的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 與邏輯。  
  
 XAML 檔案以文字表示時，則為通常有 `.xaml` 副檔名的 XML 檔案。 這些檔案可以採用任何 XML 編碼，但通常會採用 UTF-8 編碼。  
  
 下列範例示範如何建立按鈕作為 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的一部分。 這個範例只是讓您一窺 XAML 如何呈現常用的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 程式設計共通法則，並不是完整的範例。  
  
 [!code-xaml[XAMLOvwSupport#DirtSimple](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]  
  
<a name="xaml_syntax_in_brief"></a>   
## <a name="xaml-syntax-in-brief"></a>XAML 語法簡介  
 下列各節說明 XAML 語法的基本形式，並提供簡短的標記範例。 這些章節的目的並不在於提供每一種語法格式的相關完整資訊，例如在支援型別系統中的呈現方式。 如需這個主題所涵蓋每一種語法格式之特定 XAML 語法特點的詳細資訊，請參閱 [XAML 語法詳細資料](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)。  
  
 若您之前已經熟悉 XML 語言，則下面幾節中的大部分內容對您而言都很簡單。 這是因為 XAML 的其中一個基本設計原則所致。  XAML 語言定義自己的概念，但是這些概念工作表單中之 XML 語言和標記。  
  
### <a name="xaml-object-elements"></a>XAML 物件元素  
 物件元素通常會宣告型別的執行個體。 該型別定義於組件中，而這些組件會為使用 XAML 語言的技術提供支援型別。  
  
 物件元素語法一定是以左角括弧 (\<) 開始。 之後接著您要用於建立執行個體之型別的名稱  (這個名稱可能會包含前置詞；前置詞的概念將於稍後說明)。接著，可以選擇性地在物件元素上宣告屬性。 然後，以右角括弧 (>) 結束，即可完成物件元素標記。 您也可以透過正斜線加上右角括弧 (/ >) 的組合完成標記，改為使用不含任何內容的自我結尾格式。 例如，請回顧先前示範的標記程式碼片段：  
  
 [!code-xaml[XAMLOvwSupport#DirtSimple](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]  
  
 此範例指定兩個物件元素：`<StackPanel>` (含內容且其後接著結束標記) 以及 `<Button .../>` (自我結尾格式，具有數個屬性)。 物件元素 `StackPanel` 和 `Button` 會個別對應到的類別名稱，是由 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 所定義的，並會作為 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 組件的一部分。 當您指定物件元素標記時，您會建立 XAML 處理指示以建立新的執行個體。 在剖析和載入 XAML 時，即會呼叫基礎型別的預設建構函式來建立每個執行個體。  
  
### <a name="attribute-syntax-properties"></a>屬性 (Attribute) 語法 (屬性(Property))  
 物件的屬性 (Property) 通常能夠以物件元素的屬性 (Attribute) 來表示。 屬性 (Attribute) 語法會命名在屬性 (Attribute) 語法中設定的屬性 (Property)，並且緊接著指派運算子 (=)。 屬性 (Attribute) 的值一定是以利用引號括住的字串指定。  
  
 對於過去曾經使用標記語言的開發人員而言，屬性 (Attribute) 語法是最有效率的屬性 (Property) 設定語法，也是最為直覺化的使用語法。 舉例來說，下列標記建立的按鈕會以藍底紅字顯示 `Content` 所指定的文字。  
  
 [!code-xaml[XAMLOvwSupport#BlueRedButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbutton)]  
  
### <a name="property-element-syntax"></a>屬性元素語法  
 對於物件元素的某些屬性 (Property) 而言，屬性 (Attribute) 語法並不適用，這是因為在屬性 (Attribute) 語法的引號與字串限制下，無法適當表達提供屬性 (Property) 值所需的物件和資訊。 對於這種情況，可以使用另一種稱為屬性 (Property) 元素語法的語法。  
  
 屬性 (Property) 元素開始標記的語法是 `<`*typeName*`.`*propertyName*`>`。 該標記的內容通常會是型別的物件元素 (屬性 (Property) 會以該型別作為它的值)。 指定內容後，您必須以結束標記結束屬性 (Property) 元素。 結束標記的語法則是 `</`*typeName*`.`*propertyName*`>`。  
  
 若可以使用屬性 (Attribute) 語法，則使用屬性 (Attribute) 語法通常比較方便，並且可以讓標記 (Markup) 更為精簡，不過這通常只是樣式上的問題，而非技術上的限制。 下列範例顯示的屬性 (Property) 會設定成跟上述屬性 (Attribute) 語法範例相同，但這次會對 `Button` 的所有屬性 (Property) 使用屬性 (Property) 元素語法。  
  
 [!code-xaml[XAMLOvwSupport#BlueRedButtonPE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbuttonpe)]  
  
### <a name="collection-syntax"></a>集合語法  
 XAML 語言包含一些最佳化特色，能夠產生可讀性更高的標記。 其中一項最佳化特點就是，如果特定屬性 (Property) 採用集合型別，那麼您於標記中宣告為該屬性值之子元素的項目，就會變成該集合的一部分。 在此情況下，子物件元素的集合會成為要設定給該集合屬性的值。  
  
 下列範例顯示集合語法的值設定<xref:System.Windows.Media.GradientBrush.GradientStops%2A>屬性：  
  
```xaml  
<LinearGradientBrush>  
  <LinearGradientBrush.GradientStops>  
    <!-- no explicit new GradientStopCollection, parser knows how to find or create -->  
    <GradientStop Offset="0.0" Color="Red" />  
    <GradientStop Offset="1.0" Color="Blue" />  
  </LinearGradientBrush.GradientStops>  
</LinearGradientBrush>  
```  
  
### <a name="xaml-content-properties"></a>XAML 內容屬性  
 XAML 指定了一個語言功能，類別可藉此確實指派其中一個屬性作為 XAML 內容屬性。 該物件元素的子元素會用來設定該內容屬性的值。 換言之，對於內容屬性而言 (其他類屬性則不適用)，以 XAML 標記設定該屬性時，您可以省略屬性元素，進而在標記中產生更加明顯可見的父/子比喻。  
  
 例如，<xref:System.Windows.Controls.Border>指定內容屬性<xref:System.Windows.Controls.Decorator.Child%2A>。 下面兩個<xref:System.Windows.Controls.Border>項目會視為完全相同。 第一個利用內容屬性語法的優點，省略了 `Border.Child` 屬性元素。 第二個則明確顯示 `Border.Child`。  
  
```xaml  
<Border>  
  <TextBox Width="300"/>  
</Border>  
<!--explicit equivalent-->  
<Border>  
  <Border.Child>  
    <TextBox Width="300"/>  
  </Border.Child>  
</Border>  
```  
  
 根據 XAML 語言的規則，XAML 內容屬性值必須完全放在該物件元素上任何其他屬性元素之前或之後。 例如，下列標記無法編譯：  
  
```  
<Button>I am a   
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 如需 XAML 內容屬性這項限制的詳細資訊，請參閱 [XAML 語法詳細資料](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)。  
  
### <a name="text-content"></a>文字內容  
 少數 XAML 元素可以直接將文字作為其內容加以處理。 若要啟用這項功能，必須符合下列其中一種情況：  
  
-   類別必須宣告為內容屬性，且該內容屬性必須是指派給字串的型別 (類型可以是<xref:System.Object>)。 比方說，任何<xref:System.Windows.Controls.ContentControl>使用<xref:System.Windows.Controls.ContentControl.Content%2A>做為其內容的屬性，而且它是型別<xref:System.Object>，而且這支援下列使用量上實際<xref:System.Windows.Controls.ContentControl>例如<xref:System.Windows.Controls.Button>: `<Button>Hello</Button>`。  
  
-   該型別必須宣告型別轉換子，此時，文字內容便會作為該型別轉換子的初始設定文字。 例如，`<Brush>Blue</Brush>`。 這種案例在實務中較不常見。  
  
-   型別必須是已知的 XAML 語言基本型別。  
  
### <a name="content-properties-and-collection-syntax-combined"></a>內容屬性和集合語法合併  
 請考量以下範例：  
  
```xaml  
<StackPanel>  
  <Button>First Button</Button>  
  <Button>Second Button</Button>  
</StackPanel>  
```  
  
 在這裡，每個<xref:System.Windows.Controls.Button>是子元素的<xref:System.Windows.Controls.StackPanel>。 這段有效率而直覺化的標記 (Markup)，是基於兩個不同理由省略兩個標記 (Tag)。  
  
-   **省略的 StackPanel.Children 屬性項目：** <xref:System.Windows.Controls.StackPanel>衍生自<xref:System.Windows.Controls.Panel>。 <xref:System.Windows.Controls.Panel>定義<xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType>以其 XAML 內容屬性。  
  
-   **省略的 UIElementCollection 物件項目：** <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType>屬性會接受型別<xref:System.Windows.Controls.UIElementCollection>，它會實作<xref:System.Collections.IList>。 集合的項目標記可以省略，例如處理集合的 XAML 規則為基礎<xref:System.Collections.IList>。 (在此情況下，<xref:System.Windows.Controls.UIElementCollection>實際上無法具現化，因此不會公開預設建構函式，這就是為什麼<xref:System.Windows.Controls.UIElementCollection>物件項目會顯示註解化)。  
  
```xaml  
<StackPanel>  
  <StackPanel.Children>  
    <!--<UIElementCollection>-->  
    <Button>First Button</Button>  
    <Button>Second Button</Button>  
    <!--</UIElementCollection>-->  
  </StackPanel.Children>  
</StackPanel>  
```  
  
### <a name="attribute-syntax-events"></a>屬性 (Attribute) 語法 (事件)  
 屬性 (Attribute) 語法也可以供屬於事件而非屬性 (Property) 的成員使用。 在此情況下，屬性 (Attribute) 名稱就是事件名稱。 在 WPF 的 XAML 事件實作中，屬性 (Attribute) 值會是實作該事件委派之事件處理常式的名稱。 例如，下列標記會指派的處理常式<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件<xref:System.Windows.Controls.Button>建立標記中：  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]  
  
 除了這個屬性 (Attribute) 語法的範例，WPF 中還有更多事件與 XAML 的應用內容。 例如，您也許好奇在此所參照的 `ClickHandler` 究竟代表什麼以及它是如何定義的。 本主題接下來的[事件和 XAML 程式碼後置](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md#events_and_xaml_codebehind)章節中便會詳加說明。  
  
<a name="case_and_whitespace_in_xaml"></a>   
## <a name="case-and-whitespace-in-xaml"></a>XAML 中的大小寫和空白字元  
 XAML 通常會區分大小寫。 為了能夠解析支援型別，WPF XAML 會和 CLR 同樣遵守區分大小寫的規則。 在依名稱與組件的基礎型別或與型別的成員進行比較時，物件元素、屬性 (Property) 元素和屬性 (Attribute) 名稱都必須以區分大小寫的方式指定。 XAML 語言關鍵字和基本型別也區分大小寫。 值則不一定區分大小寫。 值是否會區分大小寫的決定因素，在於採用該值的屬性 (Property) 或屬性 (Property) 值型別的相關型別轉換子行為。 例如，需要的屬性<xref:System.Boolean>類型可採用任一`true`或`True`相等的值，但僅限於，因為原生 WPF XAML 剖析器類型的字串轉換為<xref:System.Boolean>已經允許這些為對等用法。  
  
 WPF XAM L 處理器和序列化程式會忽略或捨棄所有不重要的空白字元，並將任何必要的空白字元標準化。 這與指定 XAML 時所預設的空白字元行為建議一致。 這個行為通常只不過是您在 XAML 內容屬性 (Property) 內指定字串的必然結果。 簡單地說，XAML 會將空白、換行字元和定位字元轉換成為空白，然後在連續字串兩端發現空白時保留一個空白。 本主題並未涵蓋 XAML 空白字元處理的完整解說。 如需詳細資訊，請參閱 [XAML 中的空白字元處理](../../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)。  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>標記延伸  
 標記延伸是一種 XAML 語言的概念。 大括號 (`{` 和 `}`) 用於提供屬性 (Attribute) 語法的值時，表示的是一種標記延伸用法。 這項使用會指引 XAML 處理跳脫一般的屬性 (Attribute) 值處理方式 (即視為常值字串或字串可轉換值)。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式設計中最常使用的標記延伸是 [Binding](../../../../docs/framework/wpf/advanced/binding-markup-extension.md) (用於資料繫結運算式) 以及資源參考 [StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) 和 [DynamicResource](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)。 使用標記延伸就可以使用屬性 (Attribute) 語法為屬性 (Property) 提供值，即使該屬性 (Property) 通常不支援屬性 (Attribute) 語法也一樣。 標記延伸經常使用中繼運算式型別啟用延後值或參考其他物件這類僅出現在執行階段的功能。  
  
 例如，下列標記設定的值<xref:System.Windows.FrameworkElement.Style%2A>使用屬性語法的屬性。 <xref:System.Windows.FrameworkElement.Style%2A>屬性可接受的執行個體<xref:System.Windows.Style>類別，其預設值可能不會具現化的屬性語法的字串。 但在此情況下，屬性 (Attribute) 會參考特定的標記延伸 [StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)。 當處理該標記延伸時，所傳回的樣式參考先前是以資源字典中的調整資源來執行個體化。  
  
 [!code-xaml[FEResourceSH_snip#XAMLOvwShortResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources)]  
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources2)]  
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources3)]  
  
 如需 WPF 中特別實作之所有 XAML 標記延伸的參考清單，請參閱 [WPF XAML 擴充功能](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)。 如需由 System.Xaml 所定義且更廣泛存在於 .NET Framework XAML 實作的標記延伸參考清單，請參閱 [XAML 命名空間 (x:) 語言功能](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)。 如需標記延伸概念的詳細資訊，請參閱[標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。  
  
<a name="type_converters"></a>   
## <a name="type-converters"></a>類型轉換器  
 [XAML 語法簡介](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md#xaml_syntax_in_brief)一節中說明了屬性 (Attribute) 值必須要能夠由字串進行設定。 基本的原生的處理方式將字串轉換成其他物件類型或基本值根據<xref:System.String>型別本身此外到原生處理特定類型，例如<xref:System.DateTime>或<xref:System.Uri>。 但是，這些型別的許多 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 型別或成員會擴充基本字串屬性處理行為，使得更多複雜物件型別的執行個體能夠指定為字串與屬性。  
  
 <xref:System.Windows.Thickness>結構是具有型別轉換，以啟用 xaml 的類型的範例。 <xref:System.Windows.Thickness>指出測量的巢狀矩形內，做為值的屬性例如<xref:System.Windows.FrameworkElement.Margin%2A>。 將類型轉換器放置在<xref:System.Windows.Thickness>，使用的所有屬性<xref:System.Windows.Thickness>方式比較簡單，因為它們可以指定為屬性，在 XAML 中指定。 下列範例提供的值使用類型轉換和屬性語法<xref:System.Windows.FrameworkElement.Margin%2A>:  
  
 [!code-xaml[XAMLOvwSupport#MarginTCE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#margintce)]  
  
 上述的屬性語法範例相當於下列更詳細的語法範例中，其中<xref:System.Windows.FrameworkElement.Margin%2A>改為透過屬性項目的語法包含設定<xref:System.Windows.Thickness>物件項目。 四個索引鍵的屬性<xref:System.Windows.Thickness>做為屬性設定新的執行個體上：  
  
 [!code-xaml[XAMLOvwSupport#MarginVerbose](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#marginverbose)]  
  
> [!NOTE]
>  對於少部分的物件而言，因為型別本身並沒有預設建構函式，所以型別轉換是唯一可以將屬性 (Property) 設定為該型別而不需動用子類別的公用方式。 範例是<xref:System.Windows.Input.Cursor>。  
  
 如需如何支援型別轉換及其屬性 (Attribute) 語法用法的詳細資訊，請參閱 [TypeConverters 和 XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md)。  
  
<a name="xaml_root_elements_and_xaml_namespaces"></a>   
## <a name="xaml-root-elements-and-xaml-namespaces"></a>XAML 根元素和 XAML 命名空間  
 XAML 檔案只能有一個根元素，這樣才能同時成為語式正確的 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 檔案以及有效的 XAML 檔案。 一般的 WPF 情況下，您使用 WPF 應用程式模型中具有顯著意義的根項目 (例如，<xref:System.Windows.Window>或<xref:System.Windows.Controls.Page> 頁面上，針對<xref:System.Windows.ResourceDictionary>外部的字典，或<xref:System.Windows.Application>應用程式定義)。 下列範例示範典型的 XAML 檔案的根項目[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的根項目使用 頁面上， <xref:System.Windows.Controls.Page>。  
  
 [!code-xaml[XAMLOvwSupport#RootOnly](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly)]  
[!code-xaml[XAMLOvwSupport#RootOnly2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly2)]  
  
 根元素也包含屬性 (Attribute) `xmlns` 和 `xmlns:x`。 這些屬性會向 XAML 處理器指出哪些 XAML 命名空間包含支援型別 (標記會將這些型別參考為元素) 的型別定義。 `xmlns` 屬性會特別指出預設的 XAML 命名空間。 在預設的 XAML 命名空間內，標記中的物件元素可以不使用前置詞指定。 對於大部分的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式案例，以及 [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] 的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 章節中提供的幾乎所有範例而言，預設 XAML 命名空間都會對應至 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 命名空間 [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)]。 `xmlns:x` 屬性會指定另一個對應 XAML 語言命名空間 [!INCLUDE[TLA#tla_xamlxmlnsv1](../../../../includes/tlasharptla-xamlxmlnsv1-md.md)] 的命名空間。  
  
 使用 `xmlns` 定義命名空間使用和對應的範圍，與 XML 1.0 規格是一致的。 XAML 命名空間與 XML 命名空間唯一的差異在於，XAML 命名空間也帶有其他意涵，指出當涉及型別解析和剖析 XAML 時，型別會如何支援名稱範圍的元素。  
  
 請注意，每個 XAML 檔案的根元素才必須要有 `xmlns` 屬性。 `xmlns` 定義會套用至根元素的所有子元素上 (這個行為再度與 `xmlns` 的 XML 1.0 規格一致)。`xmlns` 屬性也可以用在根元素底下的其他元素上，而且應該套用至定義元素下的任何子元素。 然而，過於頻繁地定義或重新定義 XAML 命名空間會造成 XAML 標記樣式難以閱讀。  
  
 其 XAML 處理器的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 實作包含能夠辨認 WPF 核心組件的基礎結構。 廣為人知的一點是，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 核心組件包含支援將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 對應至預設 XAML 命名空間的型別。 這項功能可以透過屬於專案組建檔以及 WPF 組建與專案系統的組態進行啟用。 因此，必須將預設的 XAML 命名空間宣告為預設的 `xmlns`，才能夠參考來自 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 組件的 XAML 元素。  
  
### <a name="the-x-prefix"></a>x: 前置詞  
 在先前的根元素範例中，前置詞 `x:` 會用於對應 XAML 命名空間 [!INCLUDE[TLA#tla_xamlxmlnsv1](../../../../includes/tlasharptla-xamlxmlnsv1-md.md)]，它是支援 XAML 語言建構的專屬 XAML 命名空間。 這個 `x:` 前置詞會用於對應範例中專案範本的這個 XAML 命名空間，同時整份 [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] 說明文件中也會使用這個前置詞。 XAML 語言的 XAML 命名空間包含數種您在 XAML 中會經常使用的程式設計建構。 下列清單是您最常使用的 `x:` 前置詞程式設計建構：  
  
-   [X:key](../../../../docs/framework/xaml-services/x-key-directive.md)： 設定中的每個資源的唯一索引鍵<xref:System.Windows.ResourceDictionary>（或類似的其他架構的字典概念）。 您通常在 WPF 應用程式標記中看到的 `x:`，大概有 90% 都是 `x:Key`。  
  
-   [x:Class](../../../../docs/framework/xaml-services/x-class-directive.md)為提供 XAML 頁面程式碼後置的類別，指定類別的 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 命名空間與類別名稱。 依據 WPF 程式撰寫模型，您必須有這類支援程式碼後置的類別，因此您幾乎都會看到 `x:` 對應，即使沒有資源也一樣。  
  
-   [x:Name](../../../../docs/framework/xaml-services/x-name-directive.md)：針對處理物件元素後存在於執行階段程式碼中的執行個體，指定執行階段物件名稱。 一般而言，您經常會使用 WPF 針對 [x:Name](../../../../docs/framework/xaml-services/x-name-directive.md) 所定義的對等屬性。 這類屬性專門對應至 CLR 支援屬性，因此對於您經常會使用執行階段程式碼來尋找已初始化 XAML 中的具名元素的應用程式設計情境而言，會更方便。 最常見這種屬性是<xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>。 您仍可能使用[X:name](../../../../docs/framework/xaml-services/x-name-directive.md)時對等 WPF 架構層級<xref:System.Windows.FrameworkElement.Name%2A>特定型別中不支援屬性。 這會發生在某些動畫案例中。  
  
-   [x:Static](../../../../docs/framework/xaml-services/x-static-markup-extension.md)：啟用會傳回靜態值的參考，這個值在其他狀況下無法相容於 XAML 的屬性。  
  
-   [X:type](../../../../docs/framework/xaml-services/x-type-markup-extension.md)： 建構<xref:System.Type>參考根據類型名稱。 這用來指定需要的屬性<xref:System.Type>，例如<xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>，不過，屬性通常有原生字串-到-<xref:System.Type>轉換的方式， [X:type](../../../../docs/framework/xaml-services/x-type-markup-extension.md)是標記延伸使用方式選擇性的。  
  
 `x:` 前置詞/XAML 命名空間中還有其他的程式設計建構，但並不常用。 如需詳細資訊，請參閱 [XAML 命名空間 (x:) 語言功能](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)。  
  
<a name="custom_prefixes_and_custom_types_in_xaml"></a>   
## <a name="custom-prefixes-and-custom-types-in-xaml"></a>XAML 中的自訂前置詞與自訂型別  
 對於您自己的自訂組件或是 WPF 核心 (PresentationCore、PresentationFramework 與 WindowsBase) 以外的組件，您可以指定組件作為自訂 `xmlns` 對應的一部分。 接著，只要型別已正確實作為可以支援您嘗試進行的 XAML 用法，您便可以在您的 XAML 中參考該組件中的型別。  
  
 下列範例為自訂前置詞在 XAML 標記中運作方式的基本範例。 前置詞 `custom` 會定義於根元素標記中，且對應到已封裝並隨應用程式提供的特定組件。 這個組件包含 `NumericUpDown` 型別，會實作該型別以支援一般的 XAML 用法，以及使用類別繼承，這個類別繼承允許在 WPF XAML 內容模型的特定點置中插入這個型別。 這個 `NumericUpDown` 控制項的執行個體會使用前置詞宣告為物件元素，如此一來，XAML 剖析器便能得知哪一個 XAML 命名空間包含型別，因此支援組件的所在便是包含型別定義的位置。  
  
```  
<Page  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"   
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"   
    xmlns:custom="clr-namespace:NumericUpDownCustomControl;assembly=CustomLibrary"  
    >  
  <StackPanel Name="LayoutRoot">  
    <custom:NumericUpDown Name="numericCtrl1" Width="100" Height="60"/>  
...  
  </StackPanel>  
</Page>  
```  
  
 如需 XAML 中自訂型別的詳細資訊，請參閱 [WPF 的 XAML 和自訂類別](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)。  
  
 如需 XML 命名空間和組件中支援程式碼之命名空間的關聯方式的詳細資訊，請參閱 [WPF XAML 的 XAML 命名空間和命名空間對應](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)。  
  
<a name="events_and_xaml_codebehind"></a>   
## <a name="events-and-xaml-code-behind"></a>事件和 XAML 程式碼後置  
 大部分的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式都同時由 XAML 標記和程式碼後置所組成。 在專案中，XAML 會撰寫為 `.xaml` 檔案，而 [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] 或 [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] 這類的 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 語言則用於撰寫程式碼後置的檔案。 將 XAML 檔案作為 WPF 程式設計和應用程式模型的一部分而進行標記編譯時，XAML 檔案的 XAML 程式碼後置檔案的位置，是藉由指定命名空間和類別作為 XAML 根元素的 `x:Class` 屬性 (Attribute) 來識別。  
  
 在目前的範例中，您已經看過幾種按鈕，但沒有一個按鈕具有任何相關聯的邏輯行為。 用於新增物件元素行為的主要應用程式層級機制，是使用元素類別的現有事件，並為該事件撰寫在執行階段引發該事件時所叫用的特定處理常式。 要使用的事件名稱和處理常式名稱是在標記中指定的，而實作處理常式的程式碼則是在程式碼後置中定義。  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]  
  
 [!code-csharp[XAMLOvwSupport#ButtonWithCodeBehindHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml.cs#buttonwithcodebehindhandler)]
 [!code-vb[XAMLOvwSupport#ButtonWithCodeBehindHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#buttonwithcodebehindhandler)]  
  
 請注意，程式碼後置檔案會使用 CLR 命名空間 `ExampleNamespace`，並宣告 `ExamplePage` 作為該命名空間內的部分類別。 這與`x:Class`屬性值為`ExampleNamespace`。`ExamplePage` 提供標記根目錄中。 WPF 標記編譯器會藉由從根元素型別衍生類別，為任何編譯的 XAML 檔案建立部分類別。 當您提供的程式碼後置也會定義相同的部分類別時，產生的程式碼會結合在已編譯應用程式的相同命名空間和類別內。  
  
 如需 WPF 中程式碼後置程式設計之需求的詳細資訊，請參閱 [WPF 中的程式碼後置和 XAML](../../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md) 的＜程式碼後置、事件處理常式和部分類別需求＞一節。  
  
 如果不想要建立獨立的程式碼後置檔案，您也可以在 XAML 檔案中內嵌程式碼。 然而，內嵌程式碼具有基本的限制，是一個用途較少的技術。 如需詳細資訊，請參閱 [WPF 中的程式碼後置和 XAML](../../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)。  
  
### <a name="routed-events"></a>路由事件  
 對 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 來說有一個基本的特別事件功能，即為路由事件。 路由事件可以讓元素處理由其他元素引發的事件，只要元素可以透過樹狀結構關係來連接即可。 在使用 XAML 屬性 (Attribute) 指定事件處理時，路由事件可以由任何元素接聽和處理，包括類別成員表中沒有列出該特定事件的元素。 這可以藉由使用主控類別名稱來限定事件名稱屬性而達成。 比方說，父`StackPanel`中持續`StackPanel`  /  `Button`範例無法在子系項目 按鈕的處理常式登錄<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件指定屬性，藉以`Button.Click`上`StackPanel`物件項目，以您的處理常式名稱做為屬性值。 如需路由事件運作方式的詳細資訊，請參閱[路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)。  
  
<a name="x_name_and_xaml_named_elements"></a>   
## <a name="xaml-named-elements"></a>XAML 具名元素  
 根據預設，藉由處理 XAML 物件元素而建立於物件圖形中的物件執行個體，並不會擁有唯一識別項或物件參考。 相反地，如果在程式碼中呼叫建構函式，您幾乎都是使用建構函式結果來設定所建構執行個體的變數，這樣您可於稍後在程式碼中參考執行個體。 為了要對透過標記定義建立的物件提供標準化存取，XAML 定義了 [x:Name 屬性](../../../../docs/framework/xaml-services/x-name-directive.md)。 您可以對任何物件元素設定 `x:Name` 屬性值。 在程式碼後置中，您選擇的識別項等同於代表所建構執行個體的執行個體變數。 就各方面來說，具名元素的運作方式就如同它們是物件執行個體一樣 (名稱會參考該執行個體)，而您的程式碼後置可以參考具名元素來處理應用程式內的執行階段互動。 這個執行個體與變數之間的連線透過 WPF XAML 標記編譯器，和多個特別涉及功能和模式例如<xref:System.Windows.Markup.IComponentConnector.InitializeComponent%2A>，將不在本主題中詳細討論。  
  
 WPF 架構層級 XAML 項目繼承<xref:System.Windows.FrameworkElement.Name%2A>屬性，這是相當於 XAML 定義`x:Name`屬性。 某些其他類別也會提供 `x:Name` 的屬性 (Property) 層級對等用法，通常也會定義為 `Name` 屬性 (Property)。 一般來說，如果在成員表中找不到您所選元素/型別的 `Name` 屬性 (Property)，請改用 `x:Name`。 `x:Name`值將會提供可在執行階段，特定的子系統或公用程式方法，例如 XAML 項目識別項<xref:System.Windows.FrameworkElement.FindName%2A>。  
  
 下列範例會設定<xref:System.Windows.FrameworkElement.Name%2A>上<xref:System.Windows.Controls.StackPanel>項目。 然後上的處理常式<xref:System.Windows.Controls.Button>在<xref:System.Windows.Controls.StackPanel>參考<xref:System.Windows.Controls.StackPanel>透過其執行個體參考`buttonContainer`為設定由<xref:System.Windows.FrameworkElement.Name%2A>。  
  
 [!code-xaml[XAMLOvwSupport#NamedE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede)]  
[!code-xaml[XAMLOvwSupport#NamedE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede2)]  
  
 [!code-csharp[XAMLOvwSupport#NameCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml.cs#namecode)]
 [!code-vb[XAMLOvwSupport#NameCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#namecode)]  
  
 就如同變數一樣，執行個體的 XAML 名稱是由範圍的概念所控制，所以可以強制名稱在可預測的部分範圍內是唯一的。 定義頁面的主要標記，表示一個唯一的 XAML 名稱範圍，而 XAML 名稱範圍的界限則是該頁面的根元素。 然而，其他的標記來源可以於執行階段與頁面互動，例如樣式或樣式內的範本，而這類標記來源通常具有自己的 XAML 名稱範圍，其名稱範圍並不一定與頁面的 XAML 名稱範圍有所連接。 如需有關`x:Name`和 XAML 名稱範圍，請參閱<xref:System.Windows.FrameworkElement.Name%2A>， [X:name 指示詞](../../../../docs/framework/xaml-services/x-name-directive.md)，或[WPF XAML Namescopes](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)。  
  
<a name="attached_properties_and_attached_events"></a>   
## <a name="attached-properties-and-attached-events"></a>附加屬性和附加事件  
 XAML 指定了一個語言功能，可讓某些屬性 (Property) 或事件在任何元素上指定，不論在所要設定的元素型別定義中有沒有該屬性或事件。 這個功能的屬性版本稱為附加屬性，事件版本則稱為附加事件。 在概念上來說，您可以將附加屬性和附加事件，想像成是可以在任何 XAML 元素/物件執行個體上設定的全域成員。 不過，該元素/類別或整個基礎結構必須支援附加值的支援屬性存放區。  
  
 XAML 中的附加屬性 (Property) 通常是透過屬性 (Attribute) 語法使用。 在屬性 (Attribute) 語法中，您可以使用型式 *ownerType*.*propertyName* 指定附加屬性 (Property)。  
  
 這有點像屬性元素的使用方式，不過這裡所指定的 *ownerType*，一定不能是設定附加屬性之物件元素的型別。 *ownerType* 這個型別所提供的存取子方法，是 XAML 處理器在取得或設定附加屬性值時所需的項目。  
  
 最常見的附加屬性案例，是啟用子元素回報屬性值給父元素。  
  
 下列範例說明<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>附加屬性。 <xref:System.Windows.Controls.DockPanel>類別定義的存取子<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>，並因此擁有附加的屬性。 <xref:System.Windows.Controls.DockPanel>類別也包含邏輯來逐一查看其子項目，並特別檢查每個項目集值<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>。 若有找到值，就會在配置期間使用該值來放置子元素。 使用<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>附加的屬性和這個位置的能力實際上是激勵案例<xref:System.Windows.Controls.DockPanel>類別。  
  
 [!code-xaml[XAMLOvwSupport#DockAP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#dockap)]  
  
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，大多數或所有的附加屬性也會以相依性屬性的方式實作。 如需詳細資訊，請參閱[附加屬性概觀](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)。  
  
 附加事件使用類似的屬性 (Attribute) 語法 *ownerType*.*eventName* 型式。 就像非附加事件一樣，XAML 中附加事件的屬性 (Attribute) 值會指定在元素上處理事件時叫用的處理常式方法名稱。 WPF XAML 中的附加事件用法較不常見。 如需詳細資訊，請參閱 [附加事件概觀](../../../../docs/framework/wpf/advanced/attached-events-overview.md)。  
  
<a name="base_classes_and_xaml"></a>   
## <a name="base-types-and-xaml"></a>基底型別和 XAML  
 基礎 WPF XAML 與它的 XAML 命名空間是型別的集合，這些型別除了 XAML 的標記元素之外，還會對應於 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件。 然而，並不是所有的類別都可以對應到元素。 抽象類別，例如<xref:System.Windows.Controls.Primitives.ButtonBase>，並使用特定的非抽象基底類別來進行中的繼承[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]物件模型。 基底類別 (包含抽象類別) 對於 XAML 開發而言仍然很重要，因為每個具象的 XAML 元素會繼承階層架構中某些基底類別的成員。 通常這些成員會包含可以設定為元素屬性 (Attribute) 的屬性 (Property)，或是包含可以處理的事件。 <xref:System.Windows.FrameworkElement>是具象基底[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]類別[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]WPF 架構層級。 設計時[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，您會使用各種圖形、 面板、 裝飾項目，或控制項的類別，所有衍生自<xref:System.Windows.FrameworkElement>。 相關的基底類別， <xref:System.Windows.FrameworkContentElement>，支援流程版面配置簡報，文件導向的元素，可使用[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]刻意鏡像[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]中<xref:System.Windows.FrameworkElement>。 結合元素層級的屬性 (Attribute) 和 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件模型，提供您可以在大部分具象 XAML 元素上設定的通用屬性 (Property)，而不用在意特定的 XAML 元素和其基礎型別。  
  
<a name="xaml_security"></a>   
## <a name="xaml-security"></a>XAML 安全性  
 XAML 是直接表示物件執行個體化和執行的標記語言。 因此，XAML 中建立的元素在與系統資源互動方面 (例如網路存取、檔案系統 IO)，跟對等的產生程式碼具有一樣的能力。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 支援  [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 安全性架構 [!INCLUDE[TLA#tla_cas](../../../../includes/tlasharptla-cas-md.md)]。 這表示在網際網路區域中執行的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容的執行權限會降低。 「鬆散的 XAML」(於載入時間由 XAML 檢視器解譯的未編譯 XAML 的頁面) 和 [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] 通常是在這個網際網路區域中執行，並具有相同的權限設定。  然而，完全信任應用程式中載入的 XAML，具有與裝載應用程式相同的系統資源存取權限。 如需詳細資訊，請參閱 [WPF 部分信任安全性](../../../../docs/framework/wpf/wpf-partial-trust-security.md)。  
  
<a name="loading_xaml_from_code"></a>   
## <a name="loading-xaml-from-code"></a>從程式碼載入 XAML  
 XAML 可以用來定義所有 UI，但有時候也比較適合在 XAML 中定義僅一部分的 UI。 這些功能可以用於啟用部分自訂、資訊的區域儲存區、使用 XAML 提供商務物件或是各種可能的案例。 這些案例的索引鍵是<xref:System.Windows.Markup.XamlReader>類別和其<xref:System.Windows.Markup.XamlReader.Load%2A>方法。 輸入是 XAML 檔案，而輸出則是代表所有物件執行階段樹狀結構並由該標記建立的物件。 接著，您可以將物件插入為應用程式中已經存在的其他物件的屬性。 只要在具有最後顯示能力且會通知執行引擎有新內容加入到應用程式的內容模型中，該屬性是適當的屬性，那麼藉由載入 XAML 就可以十分輕鬆地修改執行中應用程式的內容。 請注意，這種能力通常只能在完全信任應用程式中使用，因為在應用程式執行時載入檔案會有很顯著的安全性影響。  
  
<a name="whats_next"></a>   
## <a name="whats-next"></a>後續步驟  
 本主題提供適用於 WPF 的 XAML 語法概念和用語基本簡介。 如需這裡使用的詞彙的詳細資訊，請參閱 [XAML 語法詳細資料](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)。  
  
 如果您尚未這樣做，請嘗試教學課程 > 主題中的練習[逐步解說： 第一個 WPF 桌面應用程式](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)。 當您建立教學課程中所涵蓋以標記為重點的應用程式時，練習可以幫助您強化本主題說明的許多概念。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用特定的應用程式模型為基礎的<xref:System.Windows.Application>類別。 如需詳細資訊，請參閱 [應用程式管理概觀](../../../../docs/framework/wpf/app-development/application-management-overview.md)。  
  
 關於如何從命令列和使用 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] 建置 XAML 內含的應用程式，[建置 WPF 應用程式](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md) 將提供您更為詳細的資訊。  
  
 [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md) 提供您有關 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中多樣化屬性的詳細資訊，並介紹相依性屬性的概念。  
  
## <a name="see-also"></a>請參閱  
 [XAML 語法詳細資料](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)  
 [WPF 的 XAML 和自訂類別](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)  
 [XAML 命名空間 (x:) 語言功能](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)  
 [WPF XAML 延伸](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)  
 [基底項目概觀](../../../../docs/framework/wpf/advanced/base-elements-overview.md)  
 [WPF 中的樹狀結構](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)
