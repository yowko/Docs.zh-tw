---
title: "XAML 概觀 (WPF) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "屬性語法 [XAML]"
  - "基底類別 [XAML]"
  - "類別 [XAML]"
  - "程式碼後置檔案 [WPF], XAML"
  - "集合屬性 [XAML]"
  - "內容模型 [XAML]"
  - "事件 [XAML]"
  - "可延伸應用程式標記語言 (請參閱 XAML)"
  - "屬性項目 [XAML]"
  - "根項目 [XAML]"
  - "路由事件"
  - "使用者介面 [XAML]"
  - "XAML [WPF], 關於 XAML"
ms.assetid: a80db4cd-dd0f-479f-a45f-3740017c22e4
caps.latest.revision: 57
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 50
---
# XAML 概觀 (WPF)
本主題說明 XAML 語言的功能，並且示範如何使用 XAML 撰寫 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式。  本主題特別針對以 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 實作的 XAML 進行描述。  就語言概念而言，XAML 本身涵蓋的範圍比 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 還要廣。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="what_is_xaml"></a>   
## 何謂 XAML？  
 XAML 是一種宣告式的標記語言。  XAML 套用至 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] 程式撰寫模型時，可簡化 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] 應用程式的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 建立。  您可以在宣告式 XAML 標記中建立可見的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 項目，然後藉由使用程式碼後置 \(Code\-Behind\) 的檔案 \(已透過部分類別定義而聯結至該標記\)，區隔 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 定義和執行階段邏輯。  XAML 會以組件中定義的一組支援型別，直接表示物件的執行個體化。這一點有別於其他大部分的標記語言，通常大部分的標記語言是與支援型別系統沒有此種直接關連的直譯式語言。  XAML 會啟用工作流程，其中個別獨立的人員因而能夠使用不同的工具，操作應用程式的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 與邏輯。  
  
 XAML 檔案以文字表示時，則為通常有 `.xaml` 副檔名的 XML 檔案。  這些檔案可以採用任何 XML 編碼，但通常會採用 UTF\-8 編碼。  
  
 下列範例示範如何建立按鈕做為 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的一部分。  這個範例只是讓您一窺 XAML 如何呈現常用的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 程式設計共通法則，並不是完整的範例。  
  
 [!code-xml[XAMLOvwSupport#DirtSimple](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]  
  
<a name="xaml_syntax_in_brief"></a>   
## XAML 語法簡介  
 下列各節說明 XAML 語法的基本形式，並且提供簡要的標記範例。  這些章節的目的並不在於提供每一種語法格式的相關完整資訊，例如在支援型別系統中的呈現方式。  如需這個主題所涵蓋每一種語法類型之特定 XAML 語法的詳細資訊，請參閱 [XAML 語法詳細資料](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)。  
  
 如果您之前已經熟悉 XML 語言，則下面幾節中的大部分內容對您而言都很簡單。  這是因為 XAML 的其中一個基本設計原則所致。  XAML 語言定義自己的概念，但是這些概念是在 XML 語言和標記形式內運作。  
  
### XAML 物件項目  
 物件項目通常會宣告型別的執行個體。  該型別定義於組件中，且這些組件會為使用 XAML 語言的技術提供支援型別。  
  
 物件項目語法一定是以左角括弧 \(\<\) 開始，  之後接著您要用於建立執行個體之型別的名稱   \(這個名稱可能會包含前置字元；前置字元的概念將於稍後說明\)。 接著，可以選擇性地在物件項目上宣告屬性 \(Attribute\)。  然後，以右角括弧 \(\>\) 結束，即可完成物件項目標記。  您也可以透過正斜線加上右角括弧 \(\/\>\) 的組合完成標記，改為使用不含任何內容的自我結尾 \(Self\-Closing\) 標記格式。  例如，請回顧先前示範的標記程式碼片段：  
  
 [!code-xml[XAMLOvwSupport#DirtSimple](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]  
  
 該範例指定兩個物件項目：`<StackPanel>` \(含內容並其後接著結束標記\) 以及 `<Button .../>` \(自我結尾格式，具有數個屬性 \(Attribute\)\)。  物件項目 `StackPanel` 和 `Button` 會個別對應到的類別名稱，是由 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 所定義的，並會做為 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 組件的一部分。  當您指定物件項目標記時，您會建立 XAML 處理指示以建立新的執行個體。  到了剖析和載入 XAML 時，即會呼叫基礎型別的預設建構函式來建立每個執行個體。  
  
### 屬性 \(Attribute\) 語法 \(屬性 \(Property\)\)  
 物件的屬性 \(Property\) 通常能夠以物件項目的屬性 \(Attribute\) 來表示。  屬性 \(Attribute\) 語法會命名於屬性 \(Attribute\) 語法中設定的屬性 \(Property\)，並且緊接著指派運算子 \(\=\)。  屬性 \(Attribute\) 的值一定是以利用引號括住的字串指定。  
  
 對於過去曾經使用標記語言的開發人員而言，屬性 \(Attribute\) 語法是最有效率的屬性 \(Property\) 設定語法，也是最為直覺化的使用語法。  舉例來說，下列標記建立的按鈕會以藍底紅字顯示 `Content` 所指定的文字。  
  
 [!code-xml[XAMLOvwSupport#BlueRedButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbutton)]  
  
### 屬性項目語法  
 對於物件項目的某些屬性 \(Property\) 而言，屬性 \(Attribute\) 語法並不適用，這是因為在屬性 \(Attribute\) 語法的引號與字串限制下，無法適當表達提供屬性 \(Property\) 值所需的物件和資訊。  對於這種情況，可以使用另一種稱為屬性 \(Property\) 項目語法的語法。  
  
 屬性 \(Property\) 項目的起始標籤語法是 `<`*型別名稱*`.`*屬性名稱*`>`。  該標籤的內容通常會是型別的物件項目 \(屬性 \(Property\) 會以該型別做為它的值\)。  指定內容後，您必須以結束標籤結束屬性 \(Property\) 項目。  結束標籤的語法是 `</`*型別名稱*`.`*屬性名稱*`>`。  
  
 如果可以使用屬性 \(Attribute\) 語法，則使用屬性 \(Attribute\) 語法通常比較方便，並可以讓標記 \(Markup\) 更為精簡，不過這通常只是樣式上的問題，而非技術上的限制。  下列範例顯示的屬性 \(Property\) 會設定成跟上述屬性 \(Attribute\) 語法範例相同，但這次會對 `Button` 的所有屬性 \(Property\) 使用屬性 \(Property\) 項目語法。  
  
 [!code-xml[XAMLOvwSupport#BlueRedButtonPE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbuttonpe)]  
  
### 集合語法  
 XAML 語言包含一些最佳化特色，能夠產生可讀性更高的標記。  其中一項最佳化特點就是，如果特定屬性 \(Property\) 採用集合型別，那麼您於標記中宣告做為該屬性值之子項目的項目，就會變成該集合的一部分。  在這個情況中，子物件項目的集合會成為要設定給該集合屬性的值。  
  
 下列範例示範設定 <xref:System.Windows.Media.GradientBrush.GradientStops%2A> 屬性值所需使用的集合語法：  
  
```xaml  
<LinearGradientBrush>  
  <LinearGradientBrush.GradientStops>  
    <!-- no explicit new GradientStopCollection, parser knows how to find or create -->  
    <GradientStop Offset="0.0" Color="Red" />  
    <GradientStop Offset="1.0" Color="Blue" />  
  </LinearGradientBrush.GradientStops>  
</LinearGradientBrush>  
```  
  
### XAML 內容屬性  
 XAML 指定有一個語言功能，任一類別能夠因而確實指派其任一屬性做為 XAML 內容屬性。  該物件項目的子項目會用於設定該內容屬性的值。  換言之，對於內容屬性而言 \(其他類屬性則不適用\)，以 XAML 標記設定該屬性時，您可以省略屬性項目，進而在標記中產生更加明顯可見的父\/子比喻。  
  
 例如，<xref:System.Windows.Controls.Border> 指定 <xref:System.Windows.Controls.Decorator.Child%2A> 的內容屬性。  下列兩個 <xref:System.Windows.Controls.Border> 項目的處理方式類似。  第一個利用內容屬性語法的優點，省略了 `Border.Child` 屬性項目。  第二個則明確顯示 `Border.Child`。  
  
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
  
 根據 XAML 語言的規則，XAML 內容屬性值必須完全放在該物件項目上任何其他屬性項目之前或之後。  例如，下列標記無法編譯：  
  
```  
<Button>I am a   
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 如需 XAML 內容屬性這項限制的詳細資訊，請參閱 [XAML 語法詳細資料](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)的＜XAML 內容屬性＞章節。  
  
### 文字內容  
 少數 XAML 項目可以直接將文字當做內容加以處理，  若要啟用這項功能，必須符合下列其中一種情況：  
  
-   類別必須宣告內容屬性，且該內容屬性的型別必須是可以指派字串的型別 \(可能是 <xref:System.Object>\)。  例如，任一 <xref:System.Windows.Controls.ContentControl> 使用 <xref:System.Windows.Controls.ContentControl.Content%2A> 做為它的內容屬性與它的型別 <xref:System.Object>，而且這支援實務 <xref:System.Windows.Controls.ContentControl> 的下列使用方式，例如 <xref:System.Windows.Controls.Button>：`<Button>Hello</Button>`。  
  
-   該型別必須宣告型別轉換子，此時，文字內容便會做為該型別轉換子的初始設定文字。  例如，`<Brush>Blue</Brush>`。  這種使用案例在實務中較不常見。  
  
-   型別必須是已知的 XAML 語言基本型別。  
  
### 內容屬性與集合語法合併  
 請考量以下範例：  
  
```xaml  
<StackPanel>  
  <Button>First Button</Button>  
  <Button>Second Button</Button>  
</StackPanel>  
```  
  
 這裡的每一個 <xref:System.Windows.Controls.Button> 都是 <xref:System.Windows.Controls.StackPanel> 的子項目。  這段有效率而直覺化的標記 \(Markup\)，基於兩個不同理由省略兩個標記 \(Tag\)。  
  
-   **Omitted StackPanel.Children 屬性項目**：<xref:System.Windows.Controls.StackPanel> 衍生自 <xref:System.Windows.Controls.Panel>。  <xref:System.Windows.Controls.Panel> 將 <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=fullName> 定義為它的 XAML 內容屬性。  
  
-   **Omitted UIElementCollection 物件項目**：<xref:System.Windows.Controls.Panel.Children%2A?displayProperty=fullName> 屬性會採用實作 <xref:System.Collections.IList> 的型別 <xref:System.Windows.Controls.UIElementCollection>。  根據 XAML 處理集合 \(<xref:System.Collections.IList>\) 的規則，集合的項目標記可以省略   \(在這個情況中 <xref:System.Windows.Controls.UIElementCollection> 其實並不會被執行個體化，因為這個集合並不會公開預設的建構函式，這也是 <xref:System.Windows.Controls.UIElementCollection> 物件項目以註解顯示的原因\)。  
  
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
  
### 屬性 \(Attribute\) 語法 \(事件\)  
 屬性 \(Attribute\) 語法也可以供屬於事件而非屬性 \(Property\) 的成員使用。  在這個情況下，屬性 \(Attribute\) 名稱就是事件名稱。  在 WPF 的 XAML 事件實作中，屬性值會是實作事件委派之事件處理常式的名稱。  例如，下列標記指派 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件的處理常式給標記中建立的 <xref:System.Windows.Controls.Button>：  
  
 [!code-xml[XAMLOvwSupport#ButtonWithCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]  
  
 除了這個屬性 \(Attribute\) 語法的範例，WPF 中還有更多事件與 XAML 的應用內容。  例如，您也許好奇在此所參照的 `ClickHandler` 究竟代表什麼以及如何它是定義的。  本主題接下來的章節中便會詳加說明。  
  
<a name="case_and_whitespace_in_xaml"></a>   
## XAML 中的大小寫和空白字元  
 XAML 通常會區分大小寫。  為了能夠解析支援型別，WPF XAML 會和 CLR 同樣遵守區分大小寫的規則。  在依名稱與組件的基礎型別或與型別的成員進行比較時，物件項目、屬性 \(Property\) 項目和屬性 \(Attribute\) 名稱都必須以區分大小寫的方式指定。  XAML 語言關鍵字和基本型別也區分大小寫。  值則不一定區分大小寫。  值是否會區分大小寫的決定因素，在於採用該值的屬性 \(Property\) 或屬性 \(Property\) 值型別的相關型別轉換子行為。  例如，接受 <xref:System.Boolean> 型別的屬性 \(Property\) 可以將 `true` 或 `True` 視為對等值，但是這只是因為原生 WPF XAML 剖析器型別轉換已支援將字串轉換成 <xref:System.Boolean>，因此可以使用這些對等用法。  
  
 WPF XAML 處理器和序列化程式會忽略或捨棄所有不重要的空白字元，並將任何必要的空白字元標準化。  這與指定 XAML 時所預設建議的空白字元行為一致。  這個行為通常只不過是您在 XAML 內容屬性 \(Property\) 內指定字串的必然結果。  簡單地說，XAML 會將空白、換行字元和定位字元轉換成為空白，然後在連續字串兩端發現空白時保留一個空白。  本主題並不涵蓋 XAML 空白字元處理的完整解說。  如需詳細資訊，請參閱[XAML 中的泛空白字元處理](../../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)。  
  
<a name="markup_extensions"></a>   
## 標記延伸  
 標記延伸是一種 XAML 語言的概念。  大括號 \(`{` 和 `}`\) 用於提供屬性語法的值時，表示的是一種標記延伸用法。  這項使用會指引 XAML 處理跳脫一般的屬性 \(Attribute\) 值處理方式 \(即視為常值字串或字串轉換值\)。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式設計中最常使用的標記延伸是 [Binding](../../../../docs/framework/wpf/advanced/binding-markup-extension.md) \(用於資料繫結運算式\) 以及資源參考 [StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) 和 [DynamicResource](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)。  使用標記延伸就可以使用屬性 \(Attribute\) 語法為屬性 \(Property\) 提供值，即使該屬性 \(Property\) 通常不支援屬性 \(Attribute\) 語法。  標記延伸經常使用中繼運算式型別啟用延後值或參考其他物件這類僅出現在執行階段的功能。  
  
 例如，下列標記使用屬性 \(Attribute\) 語法來設定 <xref:System.Windows.FrameworkElement.Style%2A> 屬性 \(Property\) 值。  <xref:System.Windows.FrameworkElement.Style%2A> 屬性 \(Property\) 會採用 <xref:System.Windows.Style> 類別的執行個體，根據預設，該類別不可以由屬性 \(Attribute\) 語法字串來執行個體化。  但在這個情況下，屬性 \(Attribute\) 會參考特定的標記延伸 [StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)。  當處理該標記延伸時，所傳回的樣式參考先前是以資源字典中的調整資源來具現化的。  
  
<!-- TODO: review snippet reference  [!CODE [FEResourceSH#XAMLOvwShortResources](FEResourceSH#XAMLOvwShortResources)]  -->  
<!-- TODO: review snippet reference [!CODE [FEResourceSH#XAMLOvwShortResources2](FEResourceSH#XAMLOvwShortResources2)]  -->  
<!-- TODO: review snippet reference [!CODE [FEResourceSH#XAMLOvwShortResources3](FEResourceSH#XAMLOvwShortResources3)]  -->  
  
 如果您特別需要 WPF 中實作之所有 XAML 標記延伸的參考清單，請參閱 [WPF XAML 擴充功能](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)。  如需由 System.Xaml 所定義且更廣泛存在於 .NET Framework XAML 實作的標記延伸參考清單，請參閱 [XAML 命名空間 \(x:\) 語言功能](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)。  如需標記延伸概念的詳細資訊，請參閱[標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。  
  
<a name="type_converters"></a>   
## 型別轉換子  
 一節中說明了屬性 \(Attribute\) 值必須要能夠由字串進行設定。  字串轉換成其他物件型別或基本值的基本原始處理方式，除了依據特定型別的某些原生處理 \(例如 <xref:System.DateTime> 或 <xref:System.Uri>\) 之外，還會依據 <xref:System.String> 型別本身。  但是，這些型別的許多 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 型別或成員會擴充基本字串屬性處理行為，使得更多複雜物件型別的執行個體能夠指定為字串與屬性。  
  
 <xref:System.Windows.Thickness> 結構就是啟用 XAML 用法型別轉換的型別範例。  <xref:System.Windows.Thickness> 會指出巢狀矩形內的度量，並且做為屬性 \(Property\) \(例如 <xref:System.Windows.FrameworkElement.Margin%2A>\) 的值使用。  透過在 <xref:System.Windows.Thickness> 上放置型別轉換子的方式，使用 <xref:System.Windows.Thickness> 的所有屬性 \(Property\) 都可以更輕易地以 XAML 指定，因為這些屬性 \(Property\) 可以指定為屬性 \(Attribute\)。  下列範例使用啟用型別轉換與屬性 \(Attribute\) 語法，提供 <xref:System.Windows.FrameworkElement.Margin%2A> 的值：  
  
 [!code-xml[XAMLOvwSupport#MarginTCE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#margintce)]  
  
 上述屬性 \(Attribute\) 語法範例與下列更為詳細的語法範例是相等的，當中是改為透過包含 <xref:System.Windows.Thickness> 物件項目的屬性 \(Property\) 項目語法來設定 <xref:System.Windows.FrameworkElement.Margin%2A>。  <xref:System.Windows.Thickness> 的四個主要屬性 \(Property\) 都會在新的執行個體上設為屬性 \(Attribute\)：  
  
 [!code-xml[XAMLOvwSupport#MarginVerbose](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#marginverbose)]  
  
> [!NOTE]
>  此外，對於少部分的物件而言，因為型別本身並沒有預設建構函式，所以型別轉換是唯一可以將屬性 \(Property\) 設定為該型別而不需動用子類別的公用方式。  <xref:System.Windows.Input.Cursor> 即為一個範例。  
  
 如需如何支援型別轉換及其屬性 \(Attribute\) 語法使用方法的詳細資訊，請參閱 [TypeConverter 和 XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md)。  
  
<a name="xaml_root_elements_and_xaml_namespaces"></a>   
## XAML 根項目和 XAML 命名空間  
 XAML 檔案只能有一個根項目，這樣才能同時成為語式正確 \(Well\-Formed\) 的 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 檔案以及有效的 XAML 檔案。  在標準的 WPF 情節中，您會使用在 WPF 應用程式模型中具有特殊意義的根項目 \(例如，頁面的 <xref:System.Windows.Window> 或 <xref:System.Windows.Controls.Page>、外部字典的 <xref:System.Windows.ResourceDictionary> 或者是應用程式定義的 <xref:System.Windows.Application>\)。  下列範例顯示 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 頁面典型 XAML 檔案的根項目，根項目為 <xref:System.Windows.Controls.Page>。  
  
 [!code-xml[XAMLOvwSupport#RootOnly](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly)]  
[!code-xml[XAMLOvwSupport#RootOnly2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly2)]  
  
 根項目也包含屬性 \(Attribute\) `xmlns` 和 `xmlns:x`。  這些屬性會向 XAML 處理器指出哪些 XAML 命名空間包含支援型別 \(標記會將這些型別參考為項目\) 的項目定義。  `xmlns` 屬性會明確表示預設的 XAML 命名空間。  在預設的 XAML 命名空間內，標記中的物件項目可以不使用前置字元指定。  對於大部分的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式案例而言，以及 [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] 的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 章節中提供的幾乎所有範例，預設 XAML 命名空間都會對應至 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 命名空間 [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)]。  `xmlns:x` 屬性 \(Attribute\) 會指定另一個對應 XAML 語言命名空間 [!INCLUDE[TLA#tla_xamlxmlnsv1](../../../../includes/tlasharptla-xamlxmlnsv1-md.md)] 的命名空間。  
  
 使用 `xmlns` 定義使用方式和命名空間對應的範圍，與 XML 1.0 規格是一致的。  XAML 命名空間與 XML 命名空間唯一的差異在於 XAML 命名空間也帶有其他意涵，指出當涉及型別解析與剖析 XAML 時，型別會如何支援命名範圍的項目。  
  
 請注意，每個 XAML 檔案的根項目才必須要有 `xmlns` 屬性。  `xmlns` 定義會套用至根項目的所有子項目上 \(這個行為再度與 `xmlns` 的 XML 1.0 規格一致\)。`xmlns` 屬性 \(Attribute\) 也可以用在根項目底下的其他項目上，如果是這樣，則這個屬性 \(Attribute\) 也會套用至該項目下的任何子項目。  然而，過於頻繁地定義或重新定義 XAML 命名空間會造成 XAML 標記樣式難以閱讀。  
  
 XAML 處理器的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 實作包含能夠辨認 WPF 核心組件的基礎結構。  廣為人知的一點是，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 核心組件包含支援將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 對應至預設 XAML 命名空間的型別。  這項功能可以透過屬於專案組建檔以及 WPF 組建與專案系統的組態進行啟用。  因此，必須將預設的 XAML 命名空間宣告為預設的 `xmlns`，才能夠參考來自 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 組件的 XAML 項目。  
  
### x: 前置字元  
 在先前的根目錄項目範例中，前置字元 `x:` 會用於對應 XAML 命名空間 [!INCLUDE[TLA#tla_xamlxmlnsv1](../../../../includes/tlasharptla-xamlxmlnsv1-md.md)]，它是支援 XAML 語言建構的專屬 XAML 命名空間。  這個 `x:` 前置字元會用於對應範例中專案範本中的這個 XAML 命名空間，同時整份 [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] 說明文件中也會使用這個前置字元。  XAML 語言的 XAML 命名空間包含數種您在 XAML 中會經常使用的程式設計建構。  下列清單是您會最常使用的 `x:` 前置字元程式設計建構：  
  
-   [x:Key](../../../../docs/framework/xaml-services/x-key-directive.md)：為 <xref:System.Windows.ResourceDictionary> \(或其他架構中類似字典的概念\) 中的每個資源，設定唯一索引鍵。  您通常在 WPF 應用程式標記中看到的 `x:`，大概有 90% 都是 `x:Key`。  
  
-   [x:Class](../../../../docs/framework/xaml-services/x-class-directive.md)：為提供 XAML 頁面程式碼後置的類別，指定類別的 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 命名空間與類別名稱。  依據 WPF 程式撰寫模型，您必須有這類支援程式碼後置的類別，因此您幾乎都會看到 `x:` 對應，即使沒有資源也一樣。  
  
-   [x:Name](../../../../docs/framework/xaml-services/x-name-directive.md)：針對處理物件項目後存在於執行階段程式碼中的執行個體，指定執行階段物件名稱。  一般而言，您經常會使用 WPF 針對 [x:Name](../../../../docs/framework/xaml-services/x-name-directive.md) 所定義的對等屬性。  這類屬性專門對應至 CLR 支援屬性，因此對於您經常會使用執行階段程式碼來尋找已初始化 XAML 中的具名項目的應用程式設計情境而言，會更方便。  這類屬性中最常見的就是 <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=fullName>。  如果特定型別中不支援對等 [WPF 架構層級](GTMT) <xref:System.Windows.FrameworkElement.Name%2A> 屬性，您仍可使用 [x:Name](../../../../docs/framework/xaml-services/x-name-directive.md)。  這會發生在某些動畫案例中。  
  
-   [x:Static](../../../../docs/framework/xaml-services/x-static-markup-extension.md)：啟用會傳回靜態值的參考，這個值在其他狀況下無法相容於 XAML 的屬性。  
  
-   [x:Type](../../../../docs/framework/xaml-services/x-type-markup-extension.md)：依據型別名稱建構 <xref:System.Type> 參考。  這是用於指定會採用 <xref:System.Type> 的屬性 \(Attribute\)，例如 <xref:System.Windows.Style.TargetType%2A?displayProperty=fullName>，但是因為屬性 \(Property\) 經常具有原生的字串對 <xref:System.Type> 轉換，因此不用 [x:Type](../../../../docs/framework/xaml-services/x-type-markup-extension.md) 標記延伸也沒關係。  
  
 `x:` 前置字元\/XAML 命名空間中還有其他的程式設計建構，但並不常用。  如需詳細資訊，請參閱 [XAML 命名空間 \(x:\) 語言功能](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)。  
  
<a name="custom_prefixes_and_custom_types_in_xaml"></a>   
## XAML 中的自訂前置字元與自訂型別  
 對於您自己的自訂組件或是 WPF 核心 \(PresentationCore、PresentationFramework 與 WindowsBase\) 以外的組件，您可以指定組件做為自訂 `xmlns` 對應的一部分。  接著，只要型別已正確實作為可以支援您嘗試進行的 XAML 用法，您便可以在您的 XAML 中參考該組件中的型別。  
  
 下列範例為自訂前置字元在 XAML 標記中運作方式的基本範例。  前置字元 `custom` 會定義於根項目標記中，且對應到已封裝並隨應用程式提供的特定組件。  這個組件包含 `NumericUpDown` 型別，會實作該型別以支援一般的 XAML 用法，以及使用類別繼承，這個類別繼承允許在 WPF XAML 內容模型的特定位置中插入這個型別。  這個 `NumericUpDown` 控制項的執行個體會透過前置字元的使用宣告為物件項目，如此一來，XAML 剖析器便能得知哪一個 XAML 命名空間包含型別，因而支援組件的所在便是包含型別定義的位置。  
  
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
## 事件和 XAML 程式碼後置  
 大部分的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式都同時由 XAML 標記和程式碼後置所組成。  在專案中，XAML 會撰寫為 `.xaml` 檔案，而 [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] 或 [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] 這類的 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 語言則用於撰寫程式碼後置的檔案。  將 XAML 檔案當做 WPF 程式設計和應用程式模型的一部分而進行標記編譯時，XAML 檔案的 XAML 程式碼後置檔案的位置，是藉由指定命名空間和類別做為 XAML 根項目的 `x:Class` 屬性 \(Attribute\) 來識別。  
  
 在目前的範例中，您已經看過幾種按鈕，但沒有一個按鈕具有任何相關聯的邏輯行為。  用於加入物件項目行為的主要應用程式層級機制，是使用項目類別的現有事件，並為該事件撰寫在執行階段引發該事件時所叫用的特定處理常式。  要使用的事件名稱和處理常式名稱是在標記中指定的，而實作處理常式的程式碼則是在程式碼後置中定義的。  
  
 [!code-xml[XAMLOvwSupport#ButtonWithCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]  
  
 [!code-csharp[XAMLOvwSupport#ButtonWithCodeBehindHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml.cs#buttonwithcodebehindhandler)]
 [!code-vb[XAMLOvwSupport#ButtonWithCodeBehindHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#buttonwithcodebehindhandler)]  
  
 請注意，程式碼後置檔案使用 CLR 命名空間 `ExampleNamespace`，並宣告 `ExamplePage` 做為該命名空間內的部分類別。  這會平行處理標記根項目中所提供 `ExampleNamespace`.`ExamplePage` 的 `x:Class` 屬性 \(Attribute\) 值。  WPF 標記編譯器會藉由從根項目型別衍生類別，為任何編譯的 XAML 檔案自動建立部分類別。  當您提供的程式碼後置也會定義相同的部分類別時，產生的程式碼會結合在編譯過的應用程式的相同命名空間和類別內。  
  
 如需 WPF 中程式碼後置程式設計之需求的詳細資訊，請參閱[WPF 中的程式碼後置和 XAML](../../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md) 的＜程式碼後置、事件處理常式和部分類別需求＞一節。  
  
 如果不想要建立獨立的程式碼後置檔案，您也可以在 XAML 檔案中內嵌 \(Inline\) 程式碼。  然而，內嵌程式碼具有基本的限制，是一個用途較少的技術。  如需詳細資訊，請參閱[WPF 中的程式碼後置和 XAML](../../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)。  
  
### 路由事件  
 對 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 來說有一個基本的特別事件功能，即為[路由事件](GTMT)。  路由事件可以讓項目處理由其他項目引發的事件，只要項目可以透過樹狀結構關係來連接。  當使用 XAML 屬性 \(Attribute\) 指定事件處理時，路由事件可以由任何項目接聽和處理，包括類別成員表中沒有列出該特定事件的項目。  這可以藉由使用主控類別名稱來限定事件名稱屬性而達成。  例如，在持續進行的 `StackPanel` \/ `Button` 範例中的父項目 `StackPanel`，可以註冊子項目按鈕的 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件的處理常式，方法是在 `StackPanel` 物件項目上指定屬性 `Button.Click`，並將處理常式名稱設為屬性值。  如需處理路由事件運作方式的詳細資訊，請參閱[路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)。  
  
<a name="x_name_and_xaml_named_elements"></a>   
## XAML 具名項目  
 根據預設，藉由處理 XAML 物件項目而建立於物件圖形中的物件執行個體，並不會擁有唯一識別項或物件參考。  相反地，如果在程式碼中呼叫建構函式，您幾乎都是使用建構函式結果來設定所建構執行個體的變數，這樣您可於稍後在程式碼中參考執行個體。  為了要對透過標記定義建立的物件提供標準化存取，XAML 定義了 [x:Name 屬性](../../../../docs/framework/xaml-services/x-name-directive.md)。  您可以對任何物件項目設定 `x:Name` 屬性 \(Attribute\) 值。  在程式碼後置中，您選擇的識別項等同於代表建構執行個體的執行個體變數。  就各方面來說，具名項目的運作方式就如同它們是物件執行個體一樣 \(名稱會參考該執行個體\)，而您的程式碼後置可以參考具名項目來處理應用程式內的執行階段互動。  執行個體與變數之間的這種關聯是由 WPF XAML 標記編譯器來達成，更明確地說，其會使用 <xref:System.Windows.Markup.IComponentConnector.InitializeComponent%2A> 之類的功能與模式，但主題不會再就這些功能與模式做詳細討論。  
  
 [WPF 架構層級](GTMT)的 XAML 項目會繼承 <xref:System.Windows.FrameworkElement.Name%2A> 屬性 \(Property\)，該屬性 \(Property\) 等同於 XAML 定義的 `x:Name` 屬性 \(Attribute\)。  某些其他類別也會提供 `x:Name` 的屬性 \(Property\) 層級對等用法，通常也會定義為 `Name` 屬性 \(Property\)。  一般來說，如果在成員表中找不到您所選項目\/型別的 `Name` 屬性 \(Property\)，請改用 `x:Name`。  `x:Name` 值會提供 XAML 項目的識別碼，這個識別碼可在執行階段供特定子系統或公用程式方法 \(例如 <xref:System.Windows.FrameworkElement.FindName%2A>\) 使用。  
  
 下列範例會對 <xref:System.Windows.Controls.StackPanel> 項目設定 <xref:System.Windows.FrameworkElement.Name%2A>。  然後，該 <xref:System.Windows.Controls.StackPanel> 內 <xref:System.Windows.Controls.Button> 的處理常式，會依據 <xref:System.Windows.FrameworkElement.Name%2A> 設定透過其執行個體參考 `buttonContainer` 來參考 <xref:System.Windows.Controls.StackPanel>。  
  
 [!code-xml[XAMLOvwSupport#NamedE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede)]  
[!code-xml[XAMLOvwSupport#NamedE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede2)]  
  
 [!code-csharp[XAMLOvwSupport#NameCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml.cs#namecode)]
 [!code-vb[XAMLOvwSupport#NameCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#namecode)]  
  
 就如同變數一樣，執行個體的 XAML 名稱是由範圍的概念所控制，所以可以強制名稱在可預測的部分範圍內是唯一的。  定義頁面的主要標記，表示一個唯一的 XAML 名稱範圍，而 XAML 名稱範圍的界限則是該頁面的根項目。  然而，其他的標記來源可以於執行階段與頁面互動，例如樣式或樣式內的樣板，而這類標記來源通常具有自己的 XAML 名稱範圍，其名稱範圍並不一定與頁面的 XAML 名稱範圍有所連接。  如需 `x:Name` 與 XAML 命名範圍的詳細資訊，請參閱 <xref:System.Windows.FrameworkElement.Name%2A>、[x:Name 指示詞](../../../../docs/framework/xaml-services/x-name-directive.md) 或 [WPF XAML 名稱範圍](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)。  
  
<a name="attached_properties_and_attached_events"></a>   
## 附加屬性和附加事件  
 XAML 指定有一個語言功能，可以讓某些屬性 \(Property\) 或事件在任何項目上指定，不論在所要設定的項目型別定義中有沒有該屬性或事件。  這個功能的屬性版本稱為[附加屬性](GTMT)，事件版本則稱為[附加事件](GTMT)。  在概念上來說，您可以將附加屬性和附加事件，想像成是可以在任何 XAML 項目\/物件執行個體上設定的全域成員。  不過，該項目\/類別或整個基礎結構必須支援附加值的支援屬性存放區。  
  
 XAML 中的附加屬性 \(Property\) 通常是透過屬性 \(Attribute\) 語法使用。  在屬性 \(Attribute\) 語法中您可以使用型式 \<*擁有者型別*\>.\<*屬性名稱*\> 指定附加屬性 \(Property\)。  
  
 這有點像屬性項目的使用方式，不過這裡所指定的 \<*擁有者型別*\>，一定不能是設定附加屬性之物件項目的型別。  \<*擁有者型別*\> 這個型別所提供的存取子方法，是 XAML 處理器在取得或設定附加屬性值時所必要。  
  
 最常見的附加屬性 \(Property\) 案例，是啟用子項目回報屬性 \(Property\) 值給父項目。  
  
 下列範例說明 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> 附加屬性。  <xref:System.Windows.Controls.DockPanel> 類別會定義 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> 的存取子，因而擁有附加屬性。  <xref:System.Windows.Controls.DockPanel> 類別也包含會逐一查看子項目的邏輯，並會特別檢查每個項目的 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> 設定值。  如果有找到值，就會在配置期間使用該值放置子項目。  <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> 附加屬性和這個放置功能的使用，實際上就是促成 <xref:System.Windows.Controls.DockPanel> 類別的情況。  
  
 [!code-xml[XAMLOvwSupport#DockAP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#dockap)]  
  
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，大多數或所有的附加屬性也會以[相依性屬性](GTMT)的方式實作。  如需詳細資訊，請參閱[附加屬性概觀](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)。  
  
 附加事件使用類似的屬性 \(Attribute\) 語法 \<*擁有者型別*\>.\<*事件名稱*\> 型式。  就像非附加事件一樣，XAML 中附加事件的屬性 \(Attribute\) 值會指定在項目上處理事件時叫用的處理常式方法名稱。  WPF XAML 中的附加事件使用方法較不常見。  如需詳細資訊，請參閱[附加事件概觀](../../../../docs/framework/wpf/advanced/attached-events-overview.md)。  
  
<a name="base_classes_and_xaml"></a>   
## 基底型別和 XAML  
 基礎 WPF XAML 與它的 XAML 命名空間是型別的集合，這些型別除了 XAML 的標記項目之外，還會對應於 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件。  然而，並不是所有的類別都可以對應到項目。  <xref:System.Windows.Controls.Primitives.ButtonBase> 這類的抽象類別 \(Abstract Class\) 和某些非抽象的基底類別，是用於 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件模型中的繼承。  基底類別 \(包含抽象類別\) 對於 XAML 開發而言仍然很重要，因為每個具象的 XAML 項目會繼承階層架構中某些基底類別的成員。  通常這些成員包含的屬性 \(Property\) 可以設定為項目的屬性 \(Attribute\)，或是包含可以處理的事件。  <xref:System.Windows.FrameworkElement> 即是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 於 [WPF 架構層級](GTMT)的具象基底 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 類別。  設計 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 時，您會使用各種圖案、面板、Decorator 或控制項類別，這些都是衍生自 <xref:System.Windows.FrameworkElement>。  有個相關的基底類別 <xref:System.Windows.FrameworkContentElement> 會支援文件導向的項目，藉由使用特意與 <xref:System.Windows.FrameworkElement> 中的 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 左右反轉的 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]，這些項目在流程配置展示方面運作良好。  結合項目層級的屬性 \(Attribute\) 和 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件模型，提供您可以在大部分具象 XAML 項目上設定的通用屬性 \(Property\)，而不用在意特定的 XAML 項目和其基礎型別。  
  
<a name="xaml_security"></a>   
## XAML 安全性  
 XAML 是直接表示物件執行個體化和執行的標記語言。  因此，XAML 中建立的項目在與系統資源互動方面 \(例如網路存取、檔案系統 IO\)，跟對等的產生程式碼具有一樣的能力。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 支援 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 安全性架構[!INCLUDE[TLA#tla_cas](../../../../includes/tlasharptla-cas-md.md)]。  這表示在網際網路區域中執行的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容的執行權限會降低。 「  鬆散的 XAML」\(於載入時間由 XAML 檢視解譯的未編譯 XAML\) 和 [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] 通常是在這個網際網路區域中執行，並具有相同的權限設定。  然而，完全信任應用程式中載入的 XAML，與裝載應用程式具有相同的系統資源存取權限。  如需詳細資訊，請參閱 [WPF 部分信任安全性](../../../../docs/framework/wpf/wpf-partial-trust-security.md)。  
  
<a name="loading_xaml_from_code"></a>   
## 從程式碼載入 XAML  
 XAML 可以用來定義所有 UI，但有時候也比較適合在 XAML 中定義僅一部分的 UI。  這些功能可以用於啟用部分自訂、資訊的區域儲存區、使用 XAML 提供商務物件或是各種可能的案例。  這些案例的關鍵在於 <xref:System.Windows.Markup.XamlReader> 類別和其 <xref:System.Windows.Markup.XamlReader.Load%2A> 方法。  輸入是 XAML 檔案，而輸出則是代表所有物件執行階段樹狀結構並由該標記建立的物件。  接著，您可以將物件插入為應用程式中已經存在的其他物件的屬性 \(Property\)。  只要在具有最後顯示能力且會通知執行引擎有新內容加入到應用程式的內容模型中，該屬性是適當的屬性，那麼藉由載入 XAML 就可以十分輕鬆地修改執行中應用程式的內容。  請注意，這種能力通常只能在完全信任應用程式中使用，因為在應用程式執行時載入檔案會有很顯著的安全性影響。  
  
<a name="whats_next"></a>   
## 下一步  
 本主題提供適用於 WPF 的 XAML 語法概念和用語基本簡介。  如需這裡使用的詞彙的詳細資訊，請參閱 [XAML 語法詳細資料](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)。  
  
 如果還沒有進行 [逐步解說：WPF 使用者入門](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)教學課程主題中的練習，請嘗試完成練習。  當您建立教學課程中涵蓋所的以標記為重點的應用程式時，練習可以幫助您強化本主題說明的許多概念。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用的特別應用程式模型，是以 <xref:System.Windows.Application> 類別為基礎。  如需詳細資訊，請參閱[應用程式管理概觀](../../../../docs/framework/wpf/app-development/application-management-overview.md)。  
  
 關於如何從命令列和使用 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] 建置 XAML 內含的應用程式，[建置 WPF 應用程式](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md) 將提供您更為詳細的資訊。  
  
 [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)提供您有關 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中多樣化屬性的詳細資訊，並介紹[相依性屬性](GTMT)的概念。  
  
## 請參閱  
 [XAML 語法詳細資料](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)   
 [WPF 的 XAML 和自訂類別](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)   
 [XAML 命名空間 \(x:\) 語言功能](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)   
 [WPF XAML 擴充功能](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)   
 [基底項目概觀](../../../../docs/framework/wpf/advanced/base-elements-overview.md)   
 [WPF 中的樹狀結構](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)