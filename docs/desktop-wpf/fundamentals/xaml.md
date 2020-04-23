---
title: XAML 概觀
description: 瞭解 .NET Core 的 Windows Presentation Foundation （WPF）如何結構化和實作為 XAML 語言。
author: thraka
ms.date: 08/08/2019
ms.author: adegeo
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
ms.openlocfilehash: b0a9357b623fbde08731a5b1ddb8fee3a93824c2
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "82071784"
---
# <a name="xaml-overview-in-wpf"></a>WPF 中的 XAML 總覽

本文說明 XAML 語言的功能，並示範如何使用 XAML 來撰寫 Windows Presentation Foundation （WPF）應用程式。 本文特別說明 WPF 所實作為的 XAML。 XAML 本身是比 WPF 更大的語言概念。

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="what-is-xaml"></a>什麼是 XAML

XAML 是一種宣告式的標記語言。 XAML 適用于 .NET Core 程式設計模型，可簡化 .NET Core 應用程式的 UI 建立。 您可以在宣告式 XAML 標記中建立可見的 UI 元素，然後使用透過部分類別定義聯結至標記的程式碼後置檔案，將 UI 定義與執行時間邏輯分開。 XAML 會以組件中定義的一組支援型別，直接表示物件的執行個體化。 這一點有別於其他大部分的標記語言，通常大部分的標記語言是與支援型別系統沒有此種直接關連的直譯式語言。 XAML 會使用可能不同的工具，讓不同的合作物件可以處理 UI 和應用程式邏輯的工作流程。

XAML 檔案以文字表示時，則為通常有 `.xaml` 副檔名的 XML 檔案。 這些檔案可以採用任何 XML 編碼，但通常會採用 UTF-8 編碼。

下列範例會示範如何建立按鈕做為 UI 的一部分。 這個範例的目的是要讓您瞭解 XAML 如何呈現常見的 UI 程式設計比喻（這不是完整的範例）。

[!code-xaml[XAMLOvwSupport#DirtSimple](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]

## <a name="xaml-syntax-in-brief"></a>Brief 中的 XAML 語法

下列各節說明 XAML 語法的基本形式，並提供簡短的標記範例。 這些章節的目的並不在於提供每一種語法格式的相關完整資訊，例如在支援型別系統中的呈現方式。 如需 XAML 語法細節的詳細資訊，請參閱[Xaml 語法詳細資料](../../framework/wpf/advanced/xaml-syntax-in-detail.md)。

如果您先前已熟悉 XML 語言，接下來幾節中的大部分內容將會是您的基礎。 這是因為 XAML 的其中一個基本設計原則所致。 XAML 語言會定義它自己的概念，但這些概念會在 XML 語言和標記表單中工作。

### <a name="xaml-object-elements"></a>XAML 物件元素

物件元素通常會宣告型別的執行個體。 該類型是在使用 XAML 做為語言的技術所參考的元件中定義。

物件元素語法一定是以左角括弧 (`<`) 開始。 之後接著您要用於建立執行個體之型別的名稱  （此名稱可包含前置詞，這是稍後將說明的概念）。在此之後，您可以選擇性地宣告物件元素上的屬性。 若要完成物件元素標記，請以右角括弧（`>`）結束。 您可以改為使用沒有任何內容的自我結尾表單，方法是以連續的正斜線和右角括弧來完成標記（`/>`）。 例如，再次查看先前顯示的標記程式碼片段。

[!code-xaml[XAMLOvwSupport#DirtSimple](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]

此範例指定兩個物件元素：`<StackPanel>` (含內容且其後接著結束標記) 以及 `<Button .../>` (自我結尾格式，具有數個屬性)。 物件專案`StackPanel`和`Button`每個都會對應至 wpf 所定義之類別的名稱，而且是 wpf 元件的一部分。 當您指定物件專案標記時，您會建立 XAML 處理的指示，以建立基礎類型的新實例。 在剖析和載入 XAML 時，會藉由呼叫基礎類型的無參數函式來建立每個實例。

### <a name="attribute-syntax-properties"></a>屬性語法（屬性）

物件的屬性 (Property) 通常能夠以物件元素的屬性 (Attribute) 來表示。 屬性語法會命名要設定的物件屬性，後面接著指派運算子（=）。 屬性 (Attribute) 的值一定是以利用引號括住的字串指定。

對於過去曾經使用標記語言的開發人員而言，屬性 (Attribute) 語法是最有效率的屬性 (Property) 設定語法，也是最為直覺化的使用語法。 舉例來說，下列標記建立的按鈕會以藍底紅字顯示 `Content` 所指定的文字。

[!code-xaml[XAMLOvwSupport#BlueRedButton](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbutton)]

### <a name="property-element-syntax"></a>屬性元素語法

對於物件元素的某些屬性 (Property) 而言，屬性 (Attribute) 語法並不適用，這是因為在屬性 (Attribute) 語法的引號與字串限制下，無法適當表達提供屬性 (Property) 值所需的物件和資訊。 對於這種情況，可以使用另一種稱為屬性 (Property) 元素語法的語法。

Property 元素開始標記的語法是`<TypeName.PropertyName>`。 一般而言，該標記的內容是屬性作為其值之類型的物件元素。 指定內容之後，您必須以結束標記關閉屬性專案。 結束標記的語法為`</TypeName.PropertyName>`。

若可以使用屬性 (Attribute) 語法，則使用屬性 (Attribute) 語法通常比較方便，並且可以讓標記 (Markup) 更為精簡，不過這通常只是樣式上的問題，而非技術上的限制。 下列範例顯示的屬性 (Property) 會設定成跟上述屬性 (Attribute) 語法範例相同，但這次會對 `Button` 的所有屬性 (Property) 使用屬性 (Property) 元素語法。

[!code-xaml[XAMLOvwSupport#BlueRedButtonPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbuttonpe)]

### <a name="collection-syntax"></a>集合語法

XAML 語言包含一些最佳化特色，能夠產生可讀性更高的標記。 其中一項最佳化特點就是，如果特定屬性 (Property) 採用集合型別，那麼您於標記中宣告為該屬性值之子元素的項目，就會變成該集合的一部分。 在此情況下，子物件元素的集合會成為要設定給該集合屬性的值。

下列範例顯示設定<xref:System.Windows.Media.GradientBrush.GradientStops%2A>屬性值的集合語法。

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

XAML 指定一個語言功能，讓類別可以只指定其中一個屬性做為 XAML_內容_屬性。 該物件元素的子元素會用來設定該內容屬性的值。 換言之，對於內容屬性而言 (其他類屬性則不適用)，以 XAML 標記設定該屬性時，您可以省略屬性元素，進而在標記中產生更加明顯可見的父/子比喻。

例如， <xref:System.Windows.Controls.Border>會指定的_content_ <xref:System.Windows.Controls.Decorator.Child%2A>內容屬性。 下列兩個<xref:System.Windows.Controls.Border>元素的處理方式相同。 第一個利用內容屬性語法的優點，省略了 `Border.Child` 屬性元素。 第二個則明確顯示 `Border.Child`。

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

根據 XAML 語言的規則，XAML 內容屬性值必須完全放在該物件元素上任何其他屬性元素之前或之後。 例如，下列標記不會進行編譯。

```xaml
<Button>I am a
  <Button.Background>Blue</Button.Background>
  blue button</Button>
```

如需 XAML 語法細節的詳細資訊，請參閱[Xaml 語法詳細資料](../../framework/wpf/advanced/xaml-syntax-in-detail.md)。

### <a name="text-content"></a>文字內容

少數 XAML 元素可以直接將文字作為其內容加以處理。 若要啟用這項功能，必須符合下列其中一種情況：

- 類別必須宣告 content 屬性，而且該內容屬性必須是可指派給字串的類型（此類型可能是<xref:System.Object>）。 例如，任何<xref:System.Windows.Controls.ContentControl>使用<xref:System.Windows.Controls.ContentControl.Content%2A>做為其 content 屬性且其為類型<xref:System.Object>，而這在上<xref:System.Windows.Controls.ContentControl>支援下列用法<xref:System.Windows.Controls.Button>：。 `<Button>Hello</Button>`

- 該型別必須宣告型別轉換子，此時，文字內容便會作為該型別轉換子的初始設定文字。 例如， `<Brush>Blue</Brush>`會將的內容值轉換`Blue`成筆刷。 這種案例在實務中較不常見。

- 型別必須是已知的 XAML 語言基本型別。

### <a name="content-properties-and-collection-syntax-combined"></a>內容屬性和集合語法的結合

請考慮此範例。

```xaml
<StackPanel>
  <Button>First Button</Button>
  <Button>Second Button</Button>
</StackPanel>
```

在這裡， <xref:System.Windows.Controls.Button>每個都是的<xref:System.Windows.Controls.StackPanel>子項目。 這段有效率而直覺化的標記 (Markup)，是基於兩個不同理由省略兩個標記 (Tag)。

- **省略 StackPanel。子屬性元素：** <xref:System.Windows.Controls.StackPanel>衍生自<xref:System.Windows.Controls.Panel>。 <xref:System.Windows.Controls.Panel>定義<xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType>為其 XAML 內容屬性。

- **省略的 system.windows.controls.uielementcollection> 物件元素：**<xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType>屬性會採用型<xref:System.Windows.Controls.UIElementCollection>別，它會<xref:System.Collections.IList>執行。 根據處理集合（例如） <xref:System.Collections.IList>的 XAML 規則，可以省略集合的元素標記。 （在此情況下<xref:System.Windows.Controls.UIElementCollection> ，實際上無法具現化，因為它不會公開無參數的函式， <xref:System.Windows.Controls.UIElementCollection>也就是為什麼會將物件元素標示為批註）。

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

### <a name="attribute-syntax-events"></a>屬性語法（事件）

屬性 (Attribute) 語法也可以供屬於事件而非屬性 (Property) 的成員使用。 在此情況下，屬性 (Attribute) 名稱就是事件名稱。 在 WPF 的 XAML 事件實作中，屬性 (Attribute) 值會是實作該事件委派之事件處理常式的名稱。 例如，下列標記會將<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件的處理常式指派給在標記<xref:System.Windows.Controls.Button>中建立的：

[!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]

除了這個屬性 (Attribute) 語法的範例，WPF 中還有更多事件與 XAML 的應用內容。 例如，您也許好奇在此所參照的 `ClickHandler` 究竟代表什麼以及它是如何定義的。 這會在本文的即將推出的[事件和 XAML 程式碼後](#events-and-xaml-code-behind)置一節中說明。

## <a name="case-and-white-space-in-xaml"></a>XAML 中的大小寫和空白字元

一般而言，XAML 會區分大小寫。 為了解析支援類型，WPF XAML 會受到 CLR 區分大小寫的相同規則區分大小寫。 在依名稱與組件的基礎型別或與型別的成員進行比較時，物件元素、屬性 (Property) 元素和屬性 (Attribute) 名稱都必須以區分大小寫的方式指定。 XAML 語言關鍵字和基本類型也會區分大小寫。 值不一定會區分大小寫。 值是否會區分大小寫的決定因素，在於採用該值的屬性 (Property) 或屬性 (Property) 值型別的相關型別轉換子行為。 <xref:System.Boolean>例如，採用類型的屬性可以`true`採用或`True`做為對<xref:System.Boolean>等的值，但只是因為字串的原生 WPF XAML 剖析器類型轉換已允許使用這些專案。

WPF XAML 處理器和序列化程式會忽略或捨棄所有 nonsignificant 的空白字元，並將任何顯著的空白字元正規化。 這與 XAML 規格的預設「空白字元」行為建議一致。 只有當您在 XAML 內容屬性中指定字串時，才會發生這種行為。 在最簡單的詞彙中，XAML 會將空格、換行字元和定位字元轉換成空格，然後在連續字串的任一結尾處，保留一個空格。 本文未涵蓋 XAML 空白字元處理的完整說明。 如需詳細資訊，請參閱[XAML 中](../xaml-services/white-space-processing.md)的空白字元處理。

## <a name="markup-extensions"></a>標記延伸

標記延伸是一種 XAML 語言的概念。 大括號 (`{` 和 `}`) 用於提供屬性 (Attribute) 語法的值時，表示的是一種標記延伸用法。 這項使用會指引 XAML 處理跳脫一般的屬性 (Attribute) 值處理方式 (即視為常值字串或字串可轉換值)。

WPF 應用程式設計中最常見的標記延伸是[`Binding`](../../framework/wpf/advanced/binding-markup-extension.md)用於資料系結運算式，以及資源參考[`StaticResource`](../../framework/wpf/advanced/staticresource-markup-extension.md)和。 [`DynamicResource`](../../framework/wpf/advanced/dynamicresource-markup-extension.md) 使用標記延伸就可以使用屬性 (Attribute) 語法為屬性 (Property) 提供值，即使該屬性 (Property) 通常不支援屬性 (Attribute) 語法也一樣。 標記延伸通常會使用中繼運算式類型來啟用一些功能，例如延遲值，或參考只存在於執行時間的其他物件。

例如，下列標記會使用屬性語法來設定<xref:System.Windows.FrameworkElement.Style%2A>屬性的值。 <xref:System.Windows.FrameworkElement.Style%2A>屬性會採用<xref:System.Windows.Style>類別的實例，其預設無法由屬性語法字串具現化。 但是在此情況下，屬性會參考特定的標記延伸`StaticResource`。 當處理該標記延伸時，所傳回的樣式參考先前是以資源字典中的調整資源來執行個體化。

[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources)]
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources2](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources2)]
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources3](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources3)]

如需 WPF 中特別實作之所有 XAML 標記延伸的參考清單，請參閱 [WPF XAML 擴充功能](../../framework/wpf/advanced/wpf-xaml-extensions.md)。 如需由 system.string 定義之標記延伸的參考清單，以及更廣泛地提供給 .NET Core XAML 的程式，請參閱[Xaml 命名空間（x：）語言功能](../xaml-services/namespace-language-features.md)。 如需標記延伸概念的詳細資訊，請參閱[標記延伸和 WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。

## <a name="type-converters"></a>類型轉換器

[XAML 語法簡介](#xaml-syntax-in-brief)一節中說明了屬性 (Attribute) 值必須要能夠由字串進行設定。 除了特定類型（例如<xref:System.String> <xref:System.DateTime>或<xref:System.Uri>）的原生處理之外，如何將字串轉換成其他物件類型或基本值的基本、原生處理也是以類型本身為基礎。 但許多 WPF 類型或這些類型的成員會擴充基底字元串屬性處理行為，讓更複雜物件類型的實例可以指定為字串和屬性。

<xref:System.Windows.Thickness>結構是類型的範例，其型別轉換已啟用 XAML 使用方式。 <xref:System.Windows.Thickness>表示在嵌套矩形內的測量，並當做屬性的值使用，例如<xref:System.Windows.FrameworkElement.Margin%2A>。 藉由將類型轉換器放<xref:System.Windows.Thickness>在上，使用的<xref:System.Windows.Thickness>所有屬性都可以在 XAML 中更容易指定，因為它們可指定為屬性。 下列範例會使用類型轉換和屬性語法來提供的值<xref:System.Windows.FrameworkElement.Margin%2A>：

[!code-xaml[XAMLOvwSupport#MarginTCE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#margintce)]

先前的屬性語法範例相當於下列更詳細的語法範例，其中<xref:System.Windows.FrameworkElement.Margin%2A>會改為透過包含<xref:System.Windows.Thickness> object 元素的屬性專案語法來設定。 的四個主要屬性<xref:System.Windows.Thickness>會設定為新實例上的屬性：

[!code-xaml[XAMLOvwSupport#MarginVerbose](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#marginverbose)]

> [!NOTE]
> 也有少數的物件，類型轉換是將屬性設定為該類型而不涉及子類別的唯一公用方式，因為類型本身沒有無參數的函式。 例如 <xref:System.Windows.Input.Cursor>。

如需類型轉換的詳細資訊，請參閱[TypeConverters 和 XAML](../../framework/wpf/advanced/typeconverters-and-xaml.md)。

## <a name="xaml-root-elements-and-xaml-namespaces"></a>XAML 根項目和 XAML 命名空間

XAML 檔案必須只有一個根項目，才能同時是格式正確的 XML 檔案和有效的 XAML 檔案。 在一般 WPF 案例中，您會使用在 WPF 應用程式模型中具有顯著意義的根項目（例如， <xref:System.Windows.Window> <xref:System.Windows.Controls.Page>針對頁面、 <xref:System.Windows.ResourceDictionary>針對外部字典，或<xref:System.Windows.Application>用於應用程式定義）。 下列範例顯示 WPF 頁面的一般 XAML 檔案的根項目，其中根項目為<xref:System.Windows.Controls.Page>。

[!code-xaml[XAMLOvwSupport#RootOnly](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly)]
[!code-xaml[XAMLOvwSupport#RootOnly2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly2)]

根元素也包含屬性 (Attribute) `xmlns` 和 `xmlns:x`。 這些屬性會向 XAML 處理器指出哪些 XAML 命名空間包含支援型別 (標記會將這些型別參考為元素) 的型別定義。 `xmlns` 屬性會特別指出預設的 XAML 命名空間。 在預設的 XAML 命名空間內，標記中的物件元素可以不使用前置詞指定。 對於大部分的 WPF 應用程式案例，以及在 SDK 的 WPF 區段中提供的幾乎所有範例，預設的 XAML 命名空間會對應至 WPF 命名空間`http://schemas.microsoft.com/winfx/2006/xaml/presentation`。 `xmlns:x` 屬性會指定另一個對應 XAML 語言命名空間 `http://schemas.microsoft.com/winfx/2006/xaml` 的命名空間。

使用 `xmlns` 定義命名空間使用和對應的範圍，與 XML 1.0 規格是一致的。 XAML 命名空間與 XML 命名空間唯一的差異在於，XAML 命名空間也帶有其他意涵，指出當涉及型別解析和剖析 XAML 時，型別會如何支援名稱範圍的元素。

屬性`xmlns`在每個 XAML 檔案的根項目上都是絕對必要的。 `xmlns` 定義會套用至根元素的所有子元素上 (這個行為再度與 `xmlns` 的 XML 1.0 規格一致)。`xmlns` 屬性也可以用在根元素底下的其他元素上，而且應該套用至定義元素下的任何子元素。 然而，過於頻繁地定義或重新定義 XAML 命名空間會造成 XAML 標記樣式難以閱讀。

WPF 的 XAML 處理器的實體系，包括知道 WPF 核心元件的基礎結構。 WPF 核心元件已知包含支援 WPF 對應至預設 XAML 命名空間的類型。 這項功能可以透過屬於專案組建檔以及 WPF 組建與專案系統的組態進行啟用。 因此，將預設的 XAML 命名空間宣告為`xmlns`預設值，就是參考來自 WPF 元件的 XAML 元素所需的所有專案。

### <a name="the-x-prefix"></a>X：前置詞

在先前的根元素範例中，前置詞 `x:` 會用於對應 XAML 命名空間 `http://schemas.microsoft.com/winfx/2006/xaml`，它是支援 XAML 語言建構的專屬 XAML 命名空間。 這個`x:`前置詞是用來在專案的範本、範例和整個 SDK 的檔中對應這個 XAML 命名空間。 Xaml 語言的 XAML 命名空間包含數個您將在 XAML 中經常使用的程式設計結構。 下列清單是您最常使用的 `x:` 前置詞程式設計建構：

- [x：Key](../xaml-services/xkey-directive.md)：為中的<xref:System.Windows.ResourceDictionary>每個資源設定唯一索引鍵（或其他架構中的類似字典概念）。 `x:Key`可能會將您會在一般 WPF `x:`應用程式標記中看到的使用量，考慮到90%。

- [x：Class](../xaml-services/xclass-directive.md)：指定類別的 CLR 命名空間和類別名稱，以提供 XAML 頁面的程式碼後置。 依據 WPF 程式撰寫模型，您必須有這類支援程式碼後置的類別，因此您幾乎都會看到 `x:` 對應，即使沒有資源也一樣。

- [x:Name](../xaml-services/xname-directive.md)：針對處理物件元素後存在於執行階段程式碼中的執行個體，指定執行階段物件名稱。 一般而言，您經常會使用 WPF 針對 [x:Name](../xaml-services/xname-directive.md) 所定義的對等屬性。 這類屬性會特別對應至 CLR 支援屬性，因此更方便應用程式設計，您經常會使用執行時間程式碼從初始化的 XAML 尋找已命名的元素。 最常見的這類屬性<xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>是。 當特定類型中[x:Name](../xaml-services/xname-directive.md)不支援對等的 WPF 架構層<xref:System.Windows.FrameworkElement.Name%2A>級屬性時，您仍然可以使用 x：Name。 這會發生在某些動畫案例中。

- [x:Static](../xaml-services/xstatic-markup-extension.md)：啟用會傳回靜態值的參考，這個值在其他狀況下無法相容於 XAML 的屬性。

- [x:Type](../xaml-services/xtype-markup-extension.md)：根據型<xref:System.Type>別名稱來建立參考。 這是用來指定<xref:System.Type>採用的屬性，例如<xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>，雖然屬性通常具有原生字串<xref:System.Type>轉換，但[x:Type](../xaml-services/xtype-markup-extension.md)標記延伸使用方式是選擇性的。

`x:` 前置詞/XAML 命名空間中還有其他的程式設計建構，但並不常用。 如需詳細資訊，請參閱 [XAML 命名空間 (x:) 語言功能](../xaml-services/namespace-language-features.md)。

## <a name="custom-prefixes-and-custom-types-in-xaml"></a>XAML 中的自訂前置詞和自訂類型

針對您自己的自訂群組件，或適用于**PresentationCore**、 **PresentationFramework**和**WindowsBase**的 WPF core 以外的元件，您可以指定元件做為自`xmlns`定義對應的一部分。 接著，只要型別已正確實作為可以支援您嘗試進行的 XAML 用法，您便可以在您的 XAML 中參考該組件中的型別。

以下是自訂前置詞在 XAML 標記中的使用方式的基本範例。 前置`custom`詞會定義在根項目標記中，並對應至應用程式所封裝和可用的特定元件。 這個組件包含 `NumericUpDown` 型別，會實作該型別以支援一般的 XAML 用法，以及使用類別繼承，這個類別繼承允許在 WPF XAML 內容模型的特定點置中插入這個型別。 這個 `NumericUpDown` 控制項的執行個體會使用前置詞宣告為物件元素，如此一來，XAML 剖析器便能得知哪一個 XAML 命名空間包含型別，因此支援組件的所在便是包含型別定義的位置。

```xaml
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

如需 XAML 中自訂型別的詳細資訊，請參閱 [WPF 的 XAML 和自訂類別](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)。

如需有關元件中的 XML 命名空間和程式碼命名空間如何關聯的詳細資訊，請參閱[WPF xaml 的 Xaml 命名空間和命名空間對應](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)。

## <a name="events-and-xaml-code-behind"></a>事件和 XAML 程式碼後置

大部分的 WPF 應用程式都是由 XAML 標記和程式碼後置所組成。 在專案內，XAML 會撰寫為`.xaml`檔案，而 CLR 語言（例如 Microsoft Visual Basic 或 c #）則是用來撰寫程式碼後置檔案。 將 XAML 檔案作為 WPF 程式設計和應用程式模型的一部分而進行標記編譯時，XAML 檔案的 XAML 程式碼後置檔案的位置，是藉由指定命名空間和類別作為 XAML 根元素的 `x:Class` 屬性 (Attribute) 來識別。

在目前的範例中，您已經看過幾種按鈕，但沒有一個按鈕具有任何相關聯的邏輯行為。 為物件專案新增行為的主要應用層級機制是使用專案類別的現有事件，並撰寫該事件的特定處理常式（當執行時間引發該事件時叫用）。 要使用的事件名稱和處理常式名稱是在標記中指定的，而實作處理常式的程式碼則是在程式碼後置中定義。

[!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]

[!code-csharp[XAMLOvwSupport#ButtonWithCodeBehindHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml.cs#buttonwithcodebehindhandler)]
[!code-vb[XAMLOvwSupport#ButtonWithCodeBehindHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#buttonwithcodebehindhandler)]

請注意，程式碼後置檔案會使用 CLR 命名空間 `ExampleNamespace`，並宣告 `ExamplePage` 作為該命名空間內的部分類別。 這等同于`x:Class`的屬性值`ExampleNamespace`。`ExamplePage` 在標記根目錄中提供。 WPF 標記編譯器會藉由從根元素型別衍生類別，為任何編譯的 XAML 檔案建立部分類別。 當您提供的程式碼後置也會定義相同的部分類別時，產生的程式碼會結合在已編譯應用程式的相同命名空間和類別中。

如需 WPF 中程式碼後置程式設計需求的詳細資訊，請參閱 WPF 中的程式[代碼後置、事件處理常式和部分類別需求](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md#code-behind-event-handler-and-partial-class-requirements-in-wpf)。

如果不想要建立獨立的程式碼後置檔案，您也可以在 XAML 檔案中內嵌程式碼。 然而，內嵌程式碼具有基本的限制，是一個用途較少的技術。 如需詳細資訊，請參閱[WPF 中的程式碼後置和 XAML](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)。

### <a name="routed-events"></a>路由事件

WPF 基本的特定事件功能是路由事件。 路由事件可以讓元素處理由其他元素引發的事件，只要元素可以透過樹狀結構關係來連接即可。 在使用 XAML 屬性 (Attribute) 指定事件處理時，路由事件可以由任何元素接聽和處理，包括類別成員表中沒有列出該特定事件的元素。 這可以藉由使用主控類別名稱來限定事件名稱屬性而達成。 比方說，在進行`StackPanel` `StackPanel`  /  `Button`中的範例中，父系可以藉由在<xref:System.Windows.Controls.Primitives.ButtonBase.Click> `Button.Click` `StackPanel`物件專案上指定屬性，並以您的處理常式名稱做為屬性值，為子項目按鈕的事件註冊處理常式。 如需詳細資訊，請參閱[路由事件總覽](../../framework/wpf/advanced/routed-events-overview.md)。

## <a name="xaml-named-elements"></a>XAML 命名元素

根據預設，藉由處理 XAML 物件元素而建立於物件圖形中的物件執行個體，並不會擁有唯一識別項或物件參考。 相反地，如果在程式碼中呼叫建構函式，您幾乎都是使用建構函式結果來設定所建構執行個體的變數，這樣您可於稍後在程式碼中參考執行個體。 為了要對透過標記定義建立的物件提供標準化存取，XAML 定義了 [x:Name 屬性](../xaml-services/xname-directive.md)。 您可以對任何物件元素設定 `x:Name` 屬性值。 在程式碼後置中，您選擇的識別項等同於代表所建構執行個體的執行個體變數。 在所有方面，命名專案的運作方式就如同它們是物件實例（名稱會參考該實例），而您的程式碼後置可以參考已命名的元素，以處理應用程式內的執行時間互動。 實例和變數之間的這個連接是由 WPF XAML 標記編譯器完成，更明確地牽涉到這類<xref:System.Windows.Markup.IComponentConnector.InitializeComponent%2A>功能和模式，這不會在本文中詳細討論。

WPF 架構層級的 XAML 元素會<xref:System.Windows.FrameworkElement.Name%2A>繼承屬性，這相當於 XAML 定義`x:Name`的屬性。 某些其他類別也會提供 `x:Name` 的屬性 (Property) 層級對等用法，通常也會定義為 `Name` 屬性 (Property)。 一般來說，如果在成員表中找不到您所選元素/型別的 `Name` 屬性 (Property)，請改用 `x:Name`。 這些`x:Name`值會提供 XAML 專案的識別碼，該專案可由特定子系統或公用程式方法（例如） <xref:System.Windows.FrameworkElement.FindName%2A>在執行時間使用。

下列範例會在<xref:System.Windows.FrameworkElement.Name%2A> <xref:System.Windows.Controls.StackPanel>元素上設定。 <xref:System.Windows.Controls.Button>然後，在中的處理常式會<xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.StackPanel>透過其由設定的`buttonContainer` <xref:System.Windows.FrameworkElement.Name%2A>實例參考來參考。

[!code-xaml[XAMLOvwSupport#NamedE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede)]
[!code-xaml[XAMLOvwSupport#NamedE2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede2)]

[!code-csharp[XAMLOvwSupport#NameCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml.cs#namecode)]
[!code-vb[XAMLOvwSupport#NameCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#namecode)]

就如同變數一樣，執行個體的 XAML 名稱是由範圍的概念所控制，所以可以強制名稱在可預測的部分範圍內是唯一的。 定義頁面的主要標記，表示一個唯一的 XAML 名稱範圍，而 XAML 名稱範圍的界限則是該頁面的根元素。 不過，其他標記來源可以在執行時間與頁面互動，例如樣式中的樣式或範本，而這類標記來源通常會有自己的 XAML 名稱範圍，且不一定會與頁面的 XAML 名稱範圍進行連接。 `x:Name`如需和 XAML 名稱範圍的詳細資訊<xref:System.Windows.FrameworkElement.Name%2A>，請參閱、 [x：Name](../xaml-services/xname-directive.md)指示詞或[WPF XAML 名稱範圍](../../framework/wpf/advanced/wpf-xaml-namescopes.md)。

## <a name="attached-properties-and-attached-events"></a>附加屬性和附加事件

XAML 指定了一個語言功能，可讓某些屬性 (Property) 或事件在任何元素上指定，不論在所要設定的元素型別定義中有沒有該屬性或事件。 這個功能的屬性版本稱為附加屬性，事件版本則稱為附加事件。 在概念上來說，您可以將附加屬性和附加事件，想像成是可以在任何 XAML 元素/物件執行個體上設定的全域成員。 不過，該元素/類別或整個基礎結構必須支援附加值的支援屬性存放區。

XAML 中的附加屬性 (Property) 通常是透過屬性 (Attribute) 語法使用。 在屬性語法中，您可以在表單`ownerType.propertyName`中指定附加屬性。

表面上，這與屬性專案使用方式類似，但在此`ownerType`情況下，您所指定的類型一定會與要設定附加屬性的物件元素不同。 `ownerType`這是提供 XAML 處理器所需之存取子方法的類型，以便取得或設定附加屬性值。

最常見的附加屬性案例，是啟用子元素回報屬性值給父元素。

下列範例說明<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>附加屬性。 <xref:System.Windows.Controls.DockPanel>類別會定義的存取子<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> ，因此擁有附加屬性。 <xref:System.Windows.Controls.DockPanel>類別也包含會逐一查看其子專案的邏輯，並會特別檢查每個元素的<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>設定值。 若有找到值，就會在配置期間使用該值來放置子元素。 使用<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>附加屬性和此定位功能實際上是<xref:System.Windows.Controls.DockPanel>類別的激發案例。

[!code-xaml[XAMLOvwSupport#DockAP](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#dockap)]

在 WPF 中，大部分或所有附加屬性也會實作為相依性屬性。 如需詳細資訊，請參閱[附加屬性概觀](../../framework/wpf/advanced/attached-properties-overview.md)。

附加事件會使用類似`ownerType.eventName`的屬性語法格式。 就像非附加事件一樣，XAML 中附加事件的屬性 (Attribute) 值會指定在元素上處理事件時叫用的處理常式方法名稱。 WPF XAML 中的附加事件用法較不常見。 如需詳細資訊，請參閱 [附加事件概觀](../../framework/wpf/advanced/attached-events-overview.md)。

## <a name="base-types-and-xaml"></a>基底類型和 XAML

除了 XAML 的標記元素之外，基礎 WPF XAML 及其 XAML 命名空間也是對應至 CLR 物件的類型集合。 然而，並不是所有的類別都可以對應到元素。 抽象類別（例如<xref:System.Windows.Controls.Primitives.ButtonBase>）和某些非抽象基類，會用於 CLR 物件模型中的繼承。 基底類別 (包含抽象類別) 對於 XAML 開發而言仍然很重要，因為每個具象的 XAML 元素會繼承階層架構中某些基底類別的成員。 通常這些成員會包含可以設定為元素屬性 (Attribute) 的屬性 (Property)，或是包含可以處理的事件。 <xref:System.Windows.FrameworkElement>是 wpf 架構層級 WPF 的實體基底 UI 類別。 設計 UI 時，您會使用各種圖形、面板、裝飾專案或控制項類別，這些都是衍生<xref:System.Windows.FrameworkElement>自。 相關的基類<xref:System.Windows.FrameworkContentElement>，支援適用于流程版面配置呈現的檔導向元素，並使用故意鏡像中<xref:System.Windows.FrameworkElement>api 的 api。 元素層級和 CLR 物件模型的屬性組合提供了一組可在大部分具象 XAML 專案上設定的通用屬性，而不論特定 XAML 專案及其基礎類型為何。

## <a name="xaml-security"></a>XAML 安全性

XAML 是直接表示物件執行個體化和執行的標記語言。 因此，XAML 中建立的元素在與系統資源互動方面 (例如網路存取、檔案系統 IO)，跟對等的產生程式碼具有一樣的能力。 載入至完全信任的應用程式的 XAML，與裝載應用程式的系統資源存取權相同。

### <a name="code-access-security-cas-in-wpf"></a>WPF 中的代碼啟用安全性（CAS）

**本節僅適用于 .NET Framework。適用于 .NET Core 的 WPF 不支援 CAS。如需詳細資訊，請參閱[代碼啟用安全性差異](../migration/differences-from-net-framework.md#code-access-security)。**

適用于 .NET Framework 的 WPF 支援代碼啟用安全性（CAS）。 這表示在網際網路區域中執行的 WPF 內容具有較低的執行許可權。 「鬆散的 XAML」（XAML 檢視器在載入時所解讀的 noncompiled XAML 頁面）和 XBAP 通常會在此網際網路區域中執行，並使用相同的許可權集合。 然而，完全信任應用程式中載入的 XAML，具有與裝載應用程式相同的系統資源存取權限。 如需詳細資訊，請參閱 [WPF 部分信任安全性](../../framework/wpf/wpf-partial-trust-security.md)。

## <a name="loading-xaml-from-code"></a>從程式碼載入 XAML

XAML 可以用來定義所有 UI，但有時候也比較適合在 XAML 中定義僅一部分的 UI。 這些功能可以用於啟用部分自訂、資訊的區域儲存區、使用 XAML 提供商務物件或是各種可能的案例。 這些案例的關鍵在於<xref:System.Windows.Markup.XamlReader>類別和其<xref:System.Windows.Markup.XamlReader.Load%2A>方法。 輸入是 XAML 檔案，而輸出則是代表所有物件執行階段樹狀結構並由該標記建立的物件。 接著，您可以插入物件，使其成為應用程式中已存在之另一個物件的屬性。 只要屬性是內容模型中具有最終顯示功能的適當屬性，而且會通知執行引擎已將新內容新增至應用程式，您就可以輕鬆地藉由在 XAML 中載入來修改執行中應用程式的內容。 就 .NET Framework 而言，這項功能通常僅適用于完全信任的應用程式，因為在應用程式執行時將檔案載入到其中的明顯安全性含意。

## <a name="see-also"></a>另請參閱

- [XAML 語法詳細資料](../../framework/wpf/advanced/xaml-syntax-in-detail.md)
- [WPF 的 XAML 和自訂類別](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [XAML 命名空間 (x:)語言功能](../xaml-services/namespace-language-features.md)
- [WPF XAML 擴充功能](../../framework/wpf/advanced/wpf-xaml-extensions.md)
- [基底項目概觀](../../framework/wpf/advanced/base-elements-overview.md)
- [WPF 中的樹狀結構](../../framework/wpf/advanced/trees-in-wpf.md)
