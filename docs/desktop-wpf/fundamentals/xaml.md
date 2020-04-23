---
title: XAML 概觀
description: 瞭解 XAML 語言如何由 .NET Core 的 Windows 演示基礎 (WPF) 進行結構化和實現。
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
# <a name="xaml-overview-in-wpf"></a>WPF 中的 XAML 概述

本文介紹了 XAML 語言的功能,並演示了如何使用 XAML 編寫 Windows 演示文稿基礎 (WPF) 應用。 本文專門介紹由 WPF 實現的 XAML。 XAML 本身是一個比 WPF 更大的語言概念。

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="what-is-xaml"></a>什麼是 XAML

XAML 是一種宣告式的標記語言。 應用於 .NET 核心程式設計模型時,XAML 簡化了為 .NET Core 應用創建 UI。 您可以在聲明性 XAML 標籤中建立可見的 UI 元素,然後透過使用透過部分類定義聯接到標記的代碼後面檔將 UI 定義與執行時邏輯分開。 XAML 會以組件中定義的一組支援型別，直接表示物件的執行個體化。 這一點有別於其他大部分的標記語言，通常大部分的標記語言是與支援型別系統沒有此種直接關連的直譯式語言。 XAML 支援一個工作流,其中單獨的各方可以使用可能不同的工具處理 UI 和應用的邏輯。

XAML 檔案以文字表示時，則為通常有 `.xaml` 副檔名的 XML 檔案。 這些檔案可以採用任何 XML 編碼，但通常會採用 UTF-8 編碼。

下面的範例展示如何創建按鈕作為 UI 的一部分。 此示例旨在讓您瞭解 XAML 如何表示常見的 UI 程式設計隱喻(它不是一個完整的範例)。

[!code-xaml[XAMLOvwSupport#DirtSimple](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]

## <a name="xaml-syntax-in-brief"></a>簡單介紹 XAML 語法

下列各節說明 XAML 語法的基本形式，並提供簡短的標記範例。 這些章節的目的並不在於提供每一種語法格式的相關完整資訊，例如在支援型別系統中的呈現方式。 有關 XAML 語法的詳細資訊,請參閱[XAML 語法詳細資訊](../../framework/wpf/advanced/xaml-syntax-in-detail.md)。

如果您以前熟悉 XML 語言,則以下幾個部分中的許多材料對您來說都是基本內容。 這是因為 XAML 的其中一個基本設計原則所致。 XAML 語言定義其自身的概念,但這些概念在 XML 語言和標記窗體中工作。

### <a name="xaml-object-elements"></a>XAML 物件元素

物件元素通常會宣告型別的執行個體。 該類型在使用 XAML 作為語言的技術引用的程式集中定義。

物件元素語法一定是以左角括弧 (`<`) 開始。 之後接著您要用於建立執行個體之型別的名稱  (名稱可以包括首碼,稍後將解釋這一概念。在此之後,您可以選擇聲明物件元素的屬性。 要完成物件元素標記,以右角括弧 ()`>`結尾。 相反,您可以使用不包含任何內容的自閉式窗體,通過連續使用前斜杠和閉合角度括弧 ()`/>`完成標記。 例如,再次查看前面顯示的標記代碼段。

[!code-xaml[XAMLOvwSupport#DirtSimple](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]

此範例指定兩個物件元素：`<StackPanel>` (含內容且其後接著結束標記) 以及 `<Button .../>` (自我結尾格式，具有數個屬性)。 物件元素`StackPanel``Button`和 每個映射到由 WPF 定義的類的名稱,並且是 WPF 程式集的一部分。 指定物件元素標記時,為 XAML 處理創建指令以創建基礎類型的新實例。 在分析和載入 XAML 時,透過呼叫基礎類型的無參數建構函數創建每個實例。

### <a name="attribute-syntax-properties"></a>屬性語法(屬性)

物件的屬性 (Property) 通常能夠以物件元素的屬性 (Attribute) 來表示。 屬性語法命名要設置的物件屬性,後跟賦值運算符 (*)。 屬性 (Attribute) 的值一定是以利用引號括住的字串指定。

對於過去曾經使用標記語言的開發人員而言，屬性 (Attribute) 語法是最有效率的屬性 (Property) 設定語法，也是最為直覺化的使用語法。 舉例來說，下列標記建立的按鈕會以藍底紅字顯示 `Content` 所指定的文字。

[!code-xaml[XAMLOvwSupport#BlueRedButton](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbutton)]

### <a name="property-element-syntax"></a>屬性元素語法

對於物件元素的某些屬性 (Property) 而言，屬性 (Attribute) 語法並不適用，這是因為在屬性 (Attribute) 語法的引號與字串限制下，無法適當表達提供屬性 (Property) 值所需的物件和資訊。 對於這種情況，可以使用另一種稱為屬性 (Property) 元素語法的語法。

屬性元素開始標記的語法為`<TypeName.PropertyName>`。 通常,該標記的內容是屬性作為其值的類型的物件元素。 指定內容後,必須使用結束標記關閉屬性元素。 結束標記的語法為`</TypeName.PropertyName>`。

若可以使用屬性 (Attribute) 語法，則使用屬性 (Attribute) 語法通常比較方便，並且可以讓標記 (Markup) 更為精簡，不過這通常只是樣式上的問題，而非技術上的限制。 下列範例顯示的屬性 (Property) 會設定成跟上述屬性 (Attribute) 語法範例相同，但這次會對 `Button` 的所有屬性 (Property) 使用屬性 (Property) 元素語法。

[!code-xaml[XAMLOvwSupport#BlueRedButtonPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbuttonpe)]

### <a name="collection-syntax"></a>集合語法

XAML 語言包含一些最佳化特色，能夠產生可讀性更高的標記。 其中一項最佳化特點就是，如果特定屬性 (Property) 採用集合型別，那麼您於標記中宣告為該屬性值之子元素的項目，就會變成該集合的一部分。 在此情況下，子物件元素的集合會成為要設定給該集合屬性的值。

下面的範例顯示用於設置<xref:System.Windows.Media.GradientBrush.GradientStops%2A>屬性值的集合語法。

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

XAML 指定一種語言功能,類可以將其屬性之一準確指定為 XAML_內容_屬性。 該物件元素的子元素會用來設定該內容屬性的值。 換言之，對於內容屬性而言 (其他類屬性則不適用)，以 XAML 標記設定該屬性時，您可以省略屬性元素，進而在標記中產生更加明顯可見的父/子比喻。

例如,<xref:System.Windows.Controls.Border><xref:System.Windows.Controls.Decorator.Child%2A>指定的內容_屬性。_ 以下兩<xref:System.Windows.Controls.Border>個元素的處理方式相同。 第一個利用內容屬性語法的優點，省略了 `Border.Child` 屬性元素。 第二個則明確顯示 `Border.Child`。

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

根據 XAML 語言的規則，XAML 內容屬性值必須完全放在該物件元素上任何其他屬性元素之前或之後。 例如,以下標記不編譯。

```xaml
<Button>I am a
  <Button.Background>Blue</Button.Background>
  blue button</Button>
```

有關 XAML 語法的詳細資訊,請參閱[XAML 語法詳細資訊](../../framework/wpf/advanced/xaml-syntax-in-detail.md)。

### <a name="text-content"></a>文字內容

少數 XAML 元素可以直接將文字作為其內容加以處理。 若要啟用這項功能，必須符合下列其中一種情況：

- 類必須聲明內容屬性,並且內容屬性必須為可分配給字串的類型(類型可以是<xref:System.Object>)。 例如,任何<xref:System.Windows.Controls.ContentControl><xref:System.Windows.Controls.ContentControl.Content%2A>使用都用作其內容屬性,並且它是<xref:System.Object>type,<xref:System.Windows.Controls.ContentControl>並且<xref:System.Windows.Controls.Button>支援`<Button>Hello</Button>`在如 : 上使用以下用法。

- 該型別必須宣告型別轉換子，此時，文字內容便會作為該型別轉換子的初始設定文字。 例如,`<Brush>Blue</Brush>`將`Blue`的內容值轉換為畫筆。 這種案例在實務中較不常見。

- 型別必須是已知的 XAML 語言基本型別。

### <a name="content-properties-and-collection-syntax-combined"></a>內容屬性和集合語法組合在一起

請考慮此示例。

```xaml
<StackPanel>
  <Button>First Button</Button>
  <Button>Second Button</Button>
</StackPanel>
```

在這裡,每個<xref:System.Windows.Controls.Button>元素都是的<xref:System.Windows.Controls.StackPanel>子元素。 這段有效率而直覺化的標記 (Markup)，是基於兩個不同理由省略兩個標記 (Tag)。

- **省略堆疊面板.子屬性元素:**<xref:System.Windows.Controls.StackPanel>將手<xref:System.Windows.Controls.Panel>數的手數 。 <xref:System.Windows.Controls.Panel>定義為<xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType>其 XAML 內容屬性。

- **省略的 UIElement 集合物件元素:** 屬性<xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType>採用<xref:System.Collections.IList><xref:System.Windows.Controls.UIElementCollection>的類型 。 可以根據用於處理集合(如<xref:System.Collections.IList>)的 XAML 規則省略集合的元素標記。 (在這種情況下,<xref:System.Windows.Controls.UIElementCollection>實際上無法實例化,因為它不公開無參數構造函數,這就是<xref:System.Windows.Controls.UIElementCollection>為什麼 物件元素被顯示出來)。

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

### <a name="attribute-syntax-events"></a>屬性語法(事件)

屬性 (Attribute) 語法也可以供屬於事件而非屬性 (Property) 的成員使用。 在此情況下，屬性 (Attribute) 名稱就是事件名稱。 在 WPF 的 XAML 事件實作中，屬性 (Attribute) 值會是實作該事件委派之事件處理常式的名稱。 例如,以下標記將<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件的處理程式分配給在標記中建立的處理程式<xref:System.Windows.Controls.Button>:

[!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]

除了這個屬性 (Attribute) 語法的範例，WPF 中還有更多事件與 XAML 的應用內容。 例如，您也許好奇在此所參照的 `ClickHandler` 究竟代表什麼以及它是如何定義的。 本文即將推出的[事件和 XAML 代碼後面](#events-and-xaml-code-behind)部分將對此進行說明。

## <a name="case-and-white-space-in-xaml"></a>XAML 中的外殼和空白

通常,XAML 區分大小寫。 為了解決支援類型,WPF XAML 受 CLR 區分大小寫的規則區分大小寫。 在依名稱與組件的基礎型別或與型別的成員進行比較時，物件元素、屬性 (Property) 元素和屬性 (Attribute) 名稱都必須以區分大小寫的方式指定。 XAML 語言關鍵字和基元也區分大小寫。 值並不總是區分大小寫。 值是否會區分大小寫的決定因素，在於採用該值的屬性 (Property) 或屬性 (Property) 值型別的相關型別轉換子行為。 例如,<xref:System.Boolean>採用該類型的屬性可以`true`採用`True`或作為等效值,但僅因為本機 WPF XAML 解析器<xref:System.Boolean>類型轉換字串 已允許這些值作為等效值。

WPF XAML 處理器和序列化器將忽略或丟棄所有非顯著的空白,並將規範化任何重要的空白。 這與 XAML 規範的預設空白行為建議一致。 僅當在 XAML 內容屬性中指定字串時,此行為才會產生後果。 簡單來說,XAML 將空格、換行符和製表元轉換為空格,然後在連續字串的任一端找到,則保留一個空格。 本文未介紹 XAML 空白處理的完整說明。 有關詳細資訊,請參閱[XAML 中的空白處理](../xaml-services/white-space-processing.md)。

## <a name="markup-extensions"></a>標記延伸

標記延伸是一種 XAML 語言的概念。 大括號 (`{` 和 `}`) 用於提供屬性 (Attribute) 語法的值時，表示的是一種標記延伸用法。 這項使用會指引 XAML 處理跳脫一般的屬性 (Attribute) 值處理方式 (即視為常值字串或字串可轉換值)。

WPF 應用程式設計中使用的最常見的標記延伸是[`Binding`](../../framework/wpf/advanced/binding-markup-extension.md),用於資料綁定表示式以及資源[`StaticResource`](../../framework/wpf/advanced/staticresource-markup-extension.md)參考[`DynamicResource`](../../framework/wpf/advanced/dynamicresource-markup-extension.md)和 。 使用標記延伸就可以使用屬性 (Attribute) 語法為屬性 (Property) 提供值，即使該屬性 (Property) 通常不支援屬性 (Attribute) 語法也一樣。 標記延伸通常使用中間表達式類型來啟用諸如延遲值或引用僅在運行時存在的其他物件等功能。

例如,以下標記使用屬性語法設置<xref:System.Windows.FrameworkElement.Style%2A>屬性的值。 屬性<xref:System.Windows.FrameworkElement.Style%2A><xref:System.Windows.Style>採用 類的實例,預設情況下,屬性語法字串無法實例化該實例。 但在這種情況下,屬性引用特定的標記擴展。 `StaticResource` 當處理該標記延伸時，所傳回的樣式參考先前是以資源字典中的調整資源來執行個體化。

[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources)]
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources2](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources2)]
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources3](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources3)]

如需 WPF 中特別實作之所有 XAML 標記延伸的參考清單，請參閱 [WPF XAML 擴充功能](../../framework/wpf/advanced/wpf-xaml-extensions.md)。 有關由 System.Xaml 定義且更廣泛地可用於 .NET Core XAML 實現的標記延伸的引用清單,請參閱[XAML 命名空間 (x:)語言功能](../xaml-services/namespace-language-features.md). 如需標記延伸概念的詳細資訊，請參閱[標記延伸和 WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。

## <a name="type-converters"></a>類型轉換器

[XAML 語法簡介](#xaml-syntax-in-brief)一節中說明了屬性 (Attribute) 值必須要能夠由字串進行設定。 除了某些類型(如<xref:System.String><xref:System.DateTime>或<xref:System.Uri>) 的本機處理外,如何將字串轉換為其他物件類型或基元值的基本本機處理基於類型本身。 但是,許多 WPF 類型或這些類型的成員擴展基本字串屬性處理行為,以便將更複雜的物件類型的實例指定為字串和屬性。

該<xref:System.Windows.Thickness>結構是已啟用類型轉換以用於 XAML 用法的類型的範例。 <xref:System.Windows.Thickness>指示嵌套矩形中的度量值,並用作屬性(如<xref:System.Windows.FrameworkElement.Margin%2A>)的值。 通過在上<xref:System.Windows.Thickness>放置類型轉換器,使用<xref:System.Windows.Thickness>的所有 屬性都更容易在 XAML 中指定,因為它們可以指定為屬性。 下面的範例使用類型轉換和屬性語法為<xref:System.Windows.FrameworkElement.Margin%2A>提供的值。

[!code-xaml[XAMLOvwSupport#MarginTCE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#margintce)]

前面的屬性語法示例等效於以下更詳細語法示例,在該示例中,通過包含<xref:System.Windows.FrameworkElement.Margin%2A><xref:System.Windows.Thickness>物件元素的屬性元素語法來設置。 的<xref:System.Windows.Thickness>四個關鍵屬性設定為新實體的屬性:

[!code-xaml[XAMLOvwSupport#MarginVerbose](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#marginverbose)]

> [!NOTE]
> 也有數量有限的物件,其中類型轉換是設置屬性到該類型而不涉及子類的唯一公共方法,因為類型本身沒有無參數構造函數。 例如 <xref:System.Windows.Input.Cursor>。

有關類型轉換的詳細資訊,請參考[類型轉換器和 XAML](../../framework/wpf/advanced/typeconverters-and-xaml.md)。

## <a name="xaml-root-elements-and-xaml-namespaces"></a>XAML 根元素與 XAML 命名空間

XAML 檔案必須只有一個根元素,才能同時成為格式良好的 XML 檔和有效的 XAML 檔。 對於典型的 WPF 方案,使用在 WPF 應用模型中具有突出含義<xref:System.Windows.Window>的根元素<xref:System.Windows.Controls.Page>(<xref:System.Windows.ResourceDictionary>例如,對於<xref:System.Windows.Application>頁面、 外部字典或 應用定義)。 下面的範例顯示 WPF 頁的典型 XAML 檔的根元素,其<xref:System.Windows.Controls.Page>根元素為 。

[!code-xaml[XAMLOvwSupport#RootOnly](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly)]
[!code-xaml[XAMLOvwSupport#RootOnly2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly2)]

根元素也包含屬性 (Attribute) `xmlns` 和 `xmlns:x`。 這些屬性會向 XAML 處理器指出哪些 XAML 命名空間包含支援型別 (標記會將這些型別參考為元素) 的型別定義。 `xmlns` 屬性會特別指出預設的 XAML 命名空間。 在預設的 XAML 命名空間內，標記中的物件元素可以不使用前置詞指定。 對於大多數 WPF 應用方案,以及 SDK 的 WPF 部分中給出的幾乎所有範例,預設 XAML 命名空間`http://schemas.microsoft.com/winfx/2006/xaml/presentation`將映射到 WPF 命名空間 。 `xmlns:x` 屬性會指定另一個對應 XAML 語言命名空間 `http://schemas.microsoft.com/winfx/2006/xaml` 的命名空間。

使用 `xmlns` 定義命名空間使用和對應的範圍，與 XML 1.0 規格是一致的。 XAML 命名空間與 XML 命名空間唯一的差異在於，XAML 命名空間也帶有其他意涵，指出當涉及型別解析和剖析 XAML 時，型別會如何支援名稱範圍的元素。

這些`xmlns`屬性僅在每個 XAML 檔的根元素上是絕對必要的。 `xmlns` 定義會套用至根元素的所有子元素上 (這個行為再度與 `xmlns` 的 XML 1.0 規格一致)。`xmlns` 屬性也可以用在根元素底下的其他元素上，而且應該套用至定義元素下的任何子元素。 然而，過於頻繁地定義或重新定義 XAML 命名空間會造成 XAML 標記樣式難以閱讀。

其 XAML 處理器的 WPF 實現包括一個能夠瞭解 WPF 核心程式集的基礎結構。 眾所周知,WPF 核心程式集包含支援 WPF 映射到預設 XAML 命名空間的類型。 這項功能可以透過屬於專案組建檔以及 WPF 組建與專案系統的組態進行啟用。 因此,將預設 XAML 命名空間`xmlns`聲明為 預設值是引用來自 WPF 程式集的 XAML 元素所必須的。

### <a name="the-x-prefix"></a>x: 前置字串

在先前的根元素範例中，前置詞 `x:` 會用於對應 XAML 命名空間 `http://schemas.microsoft.com/winfx/2006/xaml`，它是支援 XAML 語言建構的專屬 XAML 命名空間。 此`x:`首碼用於映射此 XAML 命名空間的專案範本、範例和整個 SDK 的文檔。 XAML 語言的 XAML 命名空間包含多個程式設計建構,您將在 XAML 中經常使用這些建構。 下列清單是您最常使用的 `x:` 前置詞程式設計建構：

- [x:鍵](../xaml-services/xkey-directive.md):為(或其他框架中的類似字典概<xref:System.Windows.ResourceDictionary>念 )中的每個資源設置一個唯一的鍵。 `x:Key`可能佔您在典型 WPF`x:`應用 標記中看到的用法的 90%。

- [x:類別](../xaml-services/xclass-directive.md):為 XAML 頁提供代碼後面的類指定 CLR 命名空間和類名稱。 依據 WPF 程式撰寫模型，您必須有這類支援程式碼後置的類別，因此您幾乎都會看到 `x:` 對應，即使沒有資源也一樣。

- [x:Name](../xaml-services/xname-directive.md)：針對處理物件元素後存在於執行階段程式碼中的執行個體，指定執行階段物件名稱。 一般而言，您經常會使用 WPF 針對 [x:Name](../xaml-services/xname-directive.md) 所定義的對等屬性。 此類屬性專門映射到 CLR 支援屬性,因此對於應用程式設計更加方便,在應用中,您經常使用運行時代碼從初始化的 XAML 中尋找命名元素。 最常見的此類屬性是<xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>。 當特定類型不支援等效的 WPF<xref:System.Windows.FrameworkElement.Name%2A>框架層級 屬性時,您仍可以使用[x:Name。](../xaml-services/xname-directive.md) 這會發生在某些動畫案例中。

- [x:Static](../xaml-services/xstatic-markup-extension.md)：啟用會傳回靜態值的參考，這個值在其他狀況下無法相容於 XAML 的屬性。

- [x:類型](../xaml-services/xtype-markup-extension.md):基於類型<xref:System.Type>名稱 建構引用。 這用於指定<xref:System.Type>採用的屬性,<xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>如 ,儘管屬性通常具有本機字串<xref:System.Type>到 轉換,其方式使[x:Type](../xaml-services/xtype-markup-extension.md)標記擴展用法是可選的。

`x:` 前置詞/XAML 命名空間中還有其他的程式設計建構，但並不常用。 如需詳細資訊，請參閱 [XAML 命名空間 (x:) 語言功能](../xaml-services/namespace-language-features.md)。

## <a name="custom-prefixes-and-custom-types-in-xaml"></a>XAML 中的自訂前置字串和自訂類型

對於您自己的自定義程式集,或者對於**演示文稿核心**、**演示文稿框架**和**WindowsBase**的 WPF 核心外的程式集,可以將`xmlns`程式集指定為自定義 映射的一部分。 接著，只要型別已正確實作為可以支援您嘗試進行的 XAML 用法，您便可以在您的 XAML 中參考該組件中的型別。

下面是自定義首碼在 XAML 標籤中工作的基本範例。 首碼`custom`在根元素標記中定義,並映射到與應用一起打包和可用的特定程式集。 這個組件包含 `NumericUpDown` 型別，會實作該型別以支援一般的 XAML 用法，以及使用類別繼承，這個類別繼承允許在 WPF XAML 內容模型的特定點置中插入這個型別。 這個 `NumericUpDown` 控制項的執行個體會使用前置詞宣告為物件元素，如此一來，XAML 剖析器便能得知哪一個 XAML 命名空間包含型別，因此支援組件的所在便是包含型別定義的位置。

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

有關程式集中的 XML 命名空間與程式碼的命名空間如何相關的詳細資訊,請參考[WPF XAML 的 XAML 命名空間與命名空間映射](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)。

## <a name="events-and-xaml-code-behind"></a>事件和 XAML 代碼背後

大多數 WPF 應用都包含 XAML 標籤和代碼後面。 在專案中,XAML 編寫`.xaml`為 檔,CLR 語言(如 Microsoft Visual Basic 或 C#)用於編寫代碼背後的檔。 將 XAML 檔案作為 WPF 程式設計和應用程式模型的一部分而進行標記編譯時，XAML 檔案的 XAML 程式碼後置檔案的位置，是藉由指定命名空間和類別作為 XAML 根元素的 `x:Class` 屬性 (Attribute) 來識別。

在目前的範例中，您已經看過幾種按鈕，但沒有一個按鈕具有任何相關聯的邏輯行為。 為物件元素添加行為的主要應用程式級機制是使用元素類的現有事件,併為該事件編寫特定處理程式,該處理程式在運行時引發該事件時調用。 要使用的事件名稱和處理常式名稱是在標記中指定的，而實作處理常式的程式碼則是在程式碼後置中定義。

[!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]

[!code-csharp[XAMLOvwSupport#ButtonWithCodeBehindHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml.cs#buttonwithcodebehindhandler)]
[!code-vb[XAMLOvwSupport#ButtonWithCodeBehindHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#buttonwithcodebehindhandler)]

請注意，程式碼後置檔案會使用 CLR 命名空間 `ExampleNamespace`，並宣告 `ExamplePage` 作為該命名空間內的部分類別。 這與`ExampleNamespace`的屬性值`x:Class`並行。`ExamplePage` 在標記根中提供。 WPF 標記編譯器會藉由從根元素型別衍生類別，為任何編譯的 XAML 檔案建立部分類別。 當您提供定義同一部分類的代碼後方時,生成的代碼將合併到已編譯應用的同一命名空間和類中。

有關 WPF 中代碼後程式設計要求的詳細資訊,請參閱[WPF 中的代碼後面、事件處理程式和部分類要求](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md#code-behind-event-handler-and-partial-class-requirements-in-wpf)。

如果不想要建立獨立的程式碼後置檔案，您也可以在 XAML 檔案中內嵌程式碼。 然而，內嵌程式碼具有基本的限制，是一個用途較少的技術。 有關更多資訊,請參閱[WPF 中的代碼背後和 XAML。](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)

### <a name="routed-events"></a>路由事件

WPF 基礎的特定事件功能是路由事件。 路由事件可以讓元素處理由其他元素引發的事件，只要元素可以透過樹狀結構關係來連接即可。 在使用 XAML 屬性 (Attribute) 指定事件處理時，路由事件可以由任何元素接聽和處理，包括類別成員表中沒有列出該特定事件的元素。 這可以藉由使用主控類別名稱來限定事件名稱屬性而達成。 例如,`StackPanel`正在進行`StackPanel` / `Button`的 範例中的父<xref:System.Windows.Controls.Primitives.ButtonBase.Click>級`Button.Click``StackPanel`可以透過在物件元素上指定屬性(將處理程式名稱為屬性值)來註冊子元素按鈕事件處理程式。 有關詳細資訊,請參閱[路由事件概述](../../framework/wpf/advanced/routed-events-overview.md)。

## <a name="xaml-named-elements"></a>XAML 命名元素

根據預設，藉由處理 XAML 物件元素而建立於物件圖形中的物件執行個體，並不會擁有唯一識別項或物件參考。 相反地，如果在程式碼中呼叫建構函式，您幾乎都是使用建構函式結果來設定所建構執行個體的變數，這樣您可於稍後在程式碼中參考執行個體。 為了要對透過標記定義建立的物件提供標準化存取，XAML 定義了 [x:Name 屬性](../xaml-services/xname-directive.md)。 您可以對任何物件元素設定 `x:Name` 屬性值。 在程式碼後置中，您選擇的識別項等同於代表所建構執行個體的執行個體變數。 在所有方面,命名元素的功能就像它們是物件實例(該實例的名稱引用)一樣,而代碼隱藏可以引用命名元素來處理應用中的運行時交互。 實例和變數之間的此連接由 WPF XAML 標籤編譯器完成,更具體地說,涉及的功能和模式,<xref:System.Windows.Markup.IComponentConnector.InitializeComponent%2A>例如 本文中不會詳細討論的功能和模式。

WPF 框架級 XAML 元素<xref:System.Windows.FrameworkElement.Name%2A>繼承一個屬性,該屬性等效於`x:Name`XAML 定義的 屬性。 某些其他類別也會提供 `x:Name` 的屬性 (Property) 層級對等用法，通常也會定義為 `Name` 屬性 (Property)。 一般來說，如果在成員表中找不到您所選元素/型別的 `Name` 屬性 (Property)，請改用 `x:Name`。 這些`x:Name`值將為 XAML 元素提供識別碼,該元素可在執行時由特定子系統或實用程式方法<xref:System.Windows.FrameworkElement.FindName%2A>(如)使用。

下面的示例在<xref:System.Windows.Controls.StackPanel><xref:System.Windows.FrameworkElement.Name%2A>元素上設置。 <xref:System.Windows.Controls.Button>然後, 在<xref:System.Windows.Controls.StackPanel>中引言<xref:System.Windows.Controls.StackPanel>的處理程式`buttonContainer`<xref:System.Windows.FrameworkElement.Name%2A>參考

[!code-xaml[XAMLOvwSupport#NamedE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede)]
[!code-xaml[XAMLOvwSupport#NamedE2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede2)]

[!code-csharp[XAMLOvwSupport#NameCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml.cs#namecode)]
[!code-vb[XAMLOvwSupport#NameCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#namecode)]

就如同變數一樣，執行個體的 XAML 名稱是由範圍的概念所控制，所以可以強制名稱在可預測的部分範圍內是唯一的。 定義頁面的主要標記，表示一個唯一的 XAML 名稱範圍，而 XAML 名稱範圍的界限則是該頁面的根元素。 但是,其他標記源可以在運行時與頁面進行交互,例如樣式中的樣式或範本,並且此類標記源通常有自己的 XAML 命名範圍,不一定與頁面的 XAML 命名範圍連接。 有關`x:Name`與 XAML 名稱範圍的詳細資訊,<xref:System.Windows.FrameworkElement.Name%2A>請參閱[:x:名稱指令](../xaml-services/xname-directive.md)或[WPF XAML 名稱範圍](../../framework/wpf/advanced/wpf-xaml-namescopes.md)。

## <a name="attached-properties-and-attached-events"></a>附加屬性和附加事件

XAML 指定了一個語言功能，可讓某些屬性 (Property) 或事件在任何元素上指定，不論在所要設定的元素型別定義中有沒有該屬性或事件。 這個功能的屬性版本稱為附加屬性，事件版本則稱為附加事件。 在概念上來說，您可以將附加屬性和附加事件，想像成是可以在任何 XAML 元素/物件執行個體上設定的全域成員。 不過，該元素/類別或整個基礎結構必須支援附加值的支援屬性存放區。

XAML 中的附加屬性 (Property) 通常是透過屬性 (Attribute) 語法使用。 在屬性語法中,在表單`ownerType.propertyName`中指定附加屬性。

從表面上看,這類似於屬性元素的使用,但在這種情況下,`ownerType`您指定的始終與正在設置附加屬性的物件元素類型不同。 `ownerType`是提供 XAML 處理器為獲取或設置附加屬性值所需的訪問器方法的類型。

最常見的附加屬性案例，是啟用子元素回報屬性值給父元素。

下面的示例說明瞭<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>附加的屬性。 類<xref:System.Windows.Controls.DockPanel>定義<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>訪問器,因此擁有附加屬性。 類<xref:System.Windows.Controls.DockPanel>還包括邏輯,用於對子元素進行重新集中,並專門檢查每個元素<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>的 設定值。 若有找到值，就會在配置期間使用該值來放置子元素。 使用<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>附加屬性和這種定位功能實際上是類的<xref:System.Windows.Controls.DockPanel>激勵方案。

[!code-xaml[XAMLOvwSupport#DockAP](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#dockap)]

在 WPF 中,大多數或所有附加屬性也作為依賴項屬性實現。 如需詳細資訊，請參閱[附加屬性概觀](../../framework/wpf/advanced/attached-properties-overview.md)。

附加的事件使用類似的`ownerType.eventName`屬性語法形式。 就像非附加事件一樣，XAML 中附加事件的屬性 (Attribute) 值會指定在元素上處理事件時叫用的處理常式方法名稱。 WPF XAML 中的附加事件用法較不常見。 如需詳細資訊，請參閱 [附加事件概觀](../../framework/wpf/advanced/attached-events-overview.md)。

## <a name="base-types-and-xaml"></a>基型態和 XAML

基礎 WPF XAML 及其 XAML 命名空間是對應於 CLR 物件的類型的集合,此外還有 XAML 的標記元素。 然而，並不是所有的類別都可以對應到元素。 抽象類(如<xref:System.Windows.Controls.Primitives.ButtonBase>)和某些非抽象基類用於 CLR 物件模型中的繼承。 基底類別 (包含抽象類別) 對於 XAML 開發而言仍然很重要，因為每個具象的 XAML 元素會繼承階層架構中某些基底類別的成員。 通常這些成員會包含可以設定為元素屬性 (Attribute) 的屬性 (Property)，或是包含可以處理的事件。 <xref:System.Windows.FrameworkElement>是 WPF 框架級別 WPF 的具體基礎 UI 類。 設計 UI 時,將使用各種形狀、面板、修飾器或控制項類別,這些類別都派<xref:System.Windows.FrameworkElement>生自 。 相關的基類<xref:System.Windows.FrameworkContentElement>支援適用於流佈局表示的文檔元素,使用有意鏡<xref:System.Windows.FrameworkElement>像 中的 API 的 API。 元素等級的屬性和 CLR 物件模型的組合為您提供了一組公共屬性,這些屬性在大多數具體的 XAML 元素上是可設置的,而不考慮特定的 XAML 元素及其基礎類型。

## <a name="xaml-security"></a>XAML 安全性

XAML 是直接表示物件執行個體化和執行的標記語言。 因此，XAML 中建立的元素在與系統資源互動方面 (例如網路存取、檔案系統 IO)，跟對等的產生程式碼具有一樣的能力。 載入完全受信任的應用中的 XAML 對系統資源的存取與託管應用相同。

### <a name="code-access-security-cas-in-wpf"></a>WPF 中的代碼存取安全 (CAS)

**本節僅適用於 .NET 框架。.NET 核心的 WPF 不支援 CAS。有關詳細資訊,請參閱[程式碼存取安全性差異](../migration/differences-from-net-framework.md#code-access-security)。**

.NET 框架的 WPF 支援代碼存取安全性 (CAS)。 這意味著在 Internet 區域中運行的 WPF 內容已減少執行許可權。 "Loose XAML"(未編譯的 XAML 頁面由 XAML 查看器在載入時解釋)和 XBAP 通常在此 Internet 區域中運行,並使用相同的許可權集。 然而，完全信任應用程式中載入的 XAML，具有與裝載應用程式相同的系統資源存取權限。 如需詳細資訊，請參閱 [WPF 部分信任安全性](../../framework/wpf/wpf-partial-trust-security.md)。

## <a name="loading-xaml-from-code"></a>從代碼載入 XAML

XAML 可以用來定義所有 UI，但有時候也比較適合在 XAML 中定義僅一部分的 UI。 這些功能可以用於啟用部分自訂、資訊的區域儲存區、使用 XAML 提供商務物件或是各種可能的案例。 這些方案的關鍵是<xref:System.Windows.Markup.XamlReader>類<xref:System.Windows.Markup.XamlReader.Load%2A>及其 方法。 輸入是 XAML 檔案，而輸出則是代表所有物件執行階段樹狀結構並由該標記建立的物件。 然後,可以將該物件插入為應用中已存在的另一個對象的屬性。 只要該屬性是內容模型中具有最終顯示功能的適當屬性,並且該屬性將通知執行引擎新內容已添加到應用中,則可以通過在 XAML 中載入輕鬆修改正在運行的應用的內容。 對於 .NET Framework,此功能通常僅在完全信任應用程式中可用,因為在檔運行時將檔載入到應用程式中具有明顯的安全影響。

## <a name="see-also"></a>另請參閱

- [XAML 語法詳細資料](../../framework/wpf/advanced/xaml-syntax-in-detail.md)
- [WPF 的 XAML 和自訂類別](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [XAML 命名空間 (x:)語言功能](../xaml-services/namespace-language-features.md)
- [WPF XAML 擴充功能](../../framework/wpf/advanced/wpf-xaml-extensions.md)
- [基底項目概觀](../../framework/wpf/advanced/base-elements-overview.md)
- [WPF 中的樹狀結構](../../framework/wpf/advanced/trees-in-wpf.md)
