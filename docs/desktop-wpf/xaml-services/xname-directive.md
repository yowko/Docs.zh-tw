---
title: x:Name 指示詞
ms.date: 03/30/2017
f1_keywords:
- x:Name
- xName
- Name
helpviewer_keywords:
- x:Name attribute [XAML Services]
- XAML [XAML Services], x:Name attribute
- Name attribute in XAML [XAML Services]
ms.assetid: b7e61222-e8cf-48d2-acd0-6df3b7685d48
ms.openlocfilehash: ddaa35b18d1c632fc49b18dabf0d992dc1c78fcc
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549479"
---
# <a name="xname-directive"></a>x:Name 指示詞

在 XAML 名稱範圍中唯一識別 XAML 定義的元素。 當架構提供 Api 或實行為，以便在執行時間存取 XAML 建立的物件圖形時，XAML 名稱範圍及其唯一性模型可以套用至具現化的物件。

## <a name="xaml-attribute-usage"></a>XAML Attribute Usage

```xaml
<object x:Name="XAMLNameValue".../>
```

## <a name="xaml-values"></a>XAML 值

|||
|-|-|
|`XAMLNameValue`|符合 [XamlName 文法](xamlname-grammar.md)限制的字串。|

## <a name="remarks"></a>備註

套用 `x:Name` 至架構的支援程式設計模型之後，該名稱就相當於保存函式所傳回之物件參考或實例的變數。

指示詞使用的值在 `x:Name` XAML 名稱範圍內必須是唯一的。 依預設，.NET XAML 服務 API 使用時，主要 XAML 名稱範圍是在單一 XAML 生產的 XAML 根項目上定義，並包含該 XAML 生產中包含的元素。 可能會在單一 XAML 生產環境中發生的其他離散 XAML 名稱範圍，可由架構定義以處理特定案例。 例如，在 WPF 中，新的 XAML 名稱範圍是由也在該 XAML 生產環境中定義的任何範本所定義和建立。 如需 XAML 名稱範圍 (針對 WPF 撰寫的詳細資訊，但) 的許多 XAML 名稱範圍概念相關的詳細資訊，請參閱 [WPF XAML 名稱範圍](/dotnet/desktop/wpf/advanced/wpf-xaml-namescopes)。

一般情況下， `x:Name` 不應該在也使用的情況下套用 `x:Key` 。 特定現有架構的 XAML 執行已在和之間引進替代概念 `x:Key` `x:Name` ，但這並不是建議的作法。 .NET XAML 服務在處理名稱/金鑰資訊（例如或）時，不支援這類替代概念 <xref:System.Windows.Markup.INameScope> <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute> 。

Permittance 和 `x:Name` 名稱唯一性強制的規則，可能會由特定的執行架構定義。 不過，若要與 .NET XAML 服務搭配使用，XAML 名稱範圍唯一性的架構定義應該與 <xref:System.Windows.Markup.INameScope> 本檔中的資訊定義一致，而且應該使用與該資訊套用所在的相同規則。 例如，執行會將 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] 各種標記專案分成不同的 <xref:System.Windows.NameScope> 範圍，例如資源字典、頁面層級 XAML 所建立的邏輯樹狀結構、範本和其他延後的內容，然後在這些 xaml 名稱範圍內強制執行 xaml 名稱唯一性。

針對使用 .NET XAML 服務 XAML 物件寫入器的自訂類型， `x:Name` 可建立或變更對應至類型的屬性。 您可以 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> 在類型定義程式碼中參考要對應之屬性的名稱，以定義此行為。  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> 是類型層級的屬性。

Using.NET XAML 服務可讓您藉由執行介面，以架構中立的方式定義 XAML 名稱範圍支援的支援邏輯 <xref:System.Windows.Markup.INameScope> 。

## <a name="wpf-usage-notes"></a>WPF 使用注意事項

在 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 使用 XAML、部分類別和程式碼後端之應用程式的標準組建設定下， `x:Name` 當標記編譯組建工作處理時，指定的會成為基礎程式碼中所建立之欄位的名稱 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] ，而該欄位會保存物件的參考。 依預設，建立的欄位為內部。 您可以藉由指定 [x:FieldModifier 屬性](xfieldmodifier-directive.md)來變更欄位存取權。 在 WPF 和 Silverlight 中，此順序是標記編譯定義並命名部分類別中的欄位，但值一開始是空的。 然後， `InitializeComponent` 會從類別的函式中呼叫名為的產生方法。 `InitializeComponent` 包含 `FindName` 使用 `x:Name` 部分類別之 XAML 定義部分中的每個值做為輸入字串的呼叫。 傳回值接著會指派給 like 命名欄位參考，以使用從 XAML 剖析建立的物件填滿域值。 執行 `InitializeComponent` 可讓您直接使用/功能變數名稱參考執行時間物件圖形 `x:Name` ，而不 `FindName` 需要在您需要 XAML 定義物件的參考時明確呼叫。

若是使用 Microsoft Visual Basic 目標的 WPF 應用程式，並包含具有組建動作的 XAML 檔案 `Page` ，則在編譯期間會建立個別的參考屬性，將關鍵字加入至 `WithEvents` 所有具有的元素 `x:Name` ，以支援 `Handles` 事件處理常式委派的語法。 此屬性一律為 public。 如需詳細資訊，請參閱 [Visual Basic 和 WPF 事件處理](/dotnet/desktop/wpf/advanced/visual-basic-and-wpf-event-handling)。

`x:Name` WPF XAML 處理器會使用，在載入時間將名稱註冊到 XAML 名稱範圍中，即使頁面不是由組建動作進行標記編譯 (例如，資源字典的鬆散 XAML) 。 這種行為的原因之一，是因為系結 `x:Name` 可能需要這樣做 <xref:System.Windows.Data.Binding.ElementName%2A> 。 如需詳細資料，請參閱資料系結 [總覽](../data/data-binding-overview.md)。

如先前所述， `x:Name` `Name` 在同時使用的情況下， (或) 不應套用 `x:Key` 。 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.ResourceDictionary> 具有將本身定義為 XAML 名稱範圍的特殊行為，但會傳回未實作為或 null 值給 api，以 <xref:System.Windows.Markup.INameScope> 強制執行這種行為。 如果 WPF XAML 剖析器遇到 `Name` 或 `x:Name` 在 xaml 定義中 <xref:System.Windows.ResourceDictionary> ，則名稱不會加入至任何 xaml 名稱範圍。 嘗試從任何 XAML 名稱範圍和方法找出該名稱 `FindName` 將不會傳回有效的結果。

### <a name="xname-and-name"></a>X：Name 和名稱

許多 WPF 應用程式案例都可以避免使用此 `x:Name` 屬性，因為許多 `Name` 重要基類的預設 XAML 命名空間中所指定的相依性屬性（例如 <xref:System.Windows.FrameworkElement> ，和）都會 <xref:System.Windows.FrameworkContentElement> 滿足相同的目的。 仍有一些常見的 XAML 和 WPF 案例，也就是在架構層級沒有屬性之專案的程式碼存取權 `Name` 是很重要的。 例如，某些動畫和分鏡腳本支援類別不支援 `Name` 屬性，但通常需要在程式碼中參考，才能控制動畫。 `x:Name`如果您想要稍後在程式碼中參考它們，您應該在以 XAML 建立的時間軸和轉換上，指定做為屬性。

如果 <xref:System.Windows.FrameworkElement.Name%2A> 可當做類別上的屬性 <xref:System.Windows.FrameworkElement.Name%2A> 來使用，而且 `x:Name` 可以當做屬性交換使用，但如果兩個專案都指定在相同的專案上，則會產生 parse 例外狀況。 如果 XAML 是標記編譯的，則例外狀況會發生在標記編譯中，否則會發生在載入時。

<xref:System.Windows.FrameworkElement.Name%2A> 您可以使用 XAML 屬性語法來設定，並在程式碼中使用， <xref:System.Windows.DependencyObject.SetValue%2A> 但請注意，在程式碼中設定 <xref:System.Windows.FrameworkElement.Name%2A> 屬性不會在已載入 xaml 的大部分情況下，于 xaml 名稱範圍內建立代表欄位參考。 請不要嘗試在程式 <xref:System.Windows.FrameworkElement.Name%2A> 代碼中設定，而是使用程式 <xref:System.Windows.NameScope> 代碼中的方法，針對適當的名稱範圍。

<xref:System.Windows.FrameworkElement.Name%2A> 也可以使用具有內部文字的屬性元素語法來設定，但這種情況並不常見。 相反地， `x:Name` 無法使用 XAML 屬性專案語法或在程式碼中設定， <xref:System.Windows.DependencyObject.SetValue%2A> 它只能使用物件的屬性語法來設定，因為它是指示詞。

## <a name="silverlight-usage-notes"></a>Silverlight 使用注意事項

`x:Name` Silverlight 會另外記載。 如需詳細資訊，請參閱 [XAML 命名空間 (x： ) 語言功能 (Silverlight) ](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95))。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.Name%2A?displayProperty=nameWithType>
- [WPF 中的樹狀結構](/dotnet/desktop/wpf/advanced/trees-in-wpf)
