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
ms.openlocfilehash: d17d977384962980839fbe2b2c0a4708412d403d
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837216"
---
# <a name="xname-directive"></a>x:Name 指示詞
唯一識別 XAML 名稱範圍中的 XAML 定義元素。 當架構提供 Api 或實行為以在執行時間存取 XAML 建立的物件圖形時，XAML 名稱範圍和其唯一性模型可以套用至具現化的物件。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<object x:Name="XAMLNameValue".../>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`XAMLNameValue`|符合[XamlName 文法](xamlname-grammar.md)限制的字串。|  
  
## <a name="remarks"></a>備註  
 將 `x:Name` 套用至架構的支援程式設計模型之後，此名稱就相當於保存物件參考的變數，或由函式傳回的實例。  
  
 `x:Name` 指示詞使用方式的值在 XAML 名稱範圍內必須是唯一的。 根據預設，當 .NET Framework XAML 服務 API 使用時，主要 XAML 名稱範圍會在單一 XAML 生產的 XAML 根項目上定義，並包含該 XAML 生產環境中包含的元素。 在單一 XAML 生產環境中可能會發生的其他離散 XAML 名稱範圍可由架構定義，以解決特定案例。 例如，在 WPF 中，新的 XAML 名稱範圍是由也定義于該 XAML 生產環境中的任何範本所定義和建立。 如需 XAML 名稱範圍的詳細資訊（針對 WPF 所撰寫但與許多 XAML 名稱範圍概念相關），請參閱[WPF XAML 名稱範圍](../wpf/advanced/wpf-xaml-namescopes.md)。  
  
 一般來說，`x:Name` 不應套用至也使用 `x:Key`的情況。 特定現有架構的 XAML 執行已引進 `x:Key` 和 `x:Name`之間的替代概念，但這不是建議的作法。 .NET Framework XAML 服務在處理名稱/金鑰資訊（例如 <xref:System.Windows.Markup.INameScope> 或 <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>）時，不支援這類替代概念。  
  
 `x:Name` 的 permittance 和名稱唯一性強制的規則，可能是由特定的執行架構所定義。 不過，若要與 .NET Framework XAML 服務搭配使用，XAML 名稱範圍唯一性的架構定義應該與本檔中 <xref:System.Windows.Markup.INameScope> 資訊的定義一致，而且應該使用與資訊套用所在的相同規則。 例如，[!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] 的執行會將各種標記專案分割成不同的 <xref:System.Windows.NameScope> 範圍，例如資源字典、頁面層級 XAML 所建立的邏輯樹狀結構、範本和其他延遲的內容，然後在每個 XAML 名稱範圍內強制執行 XAML 名稱唯一性。  
  
 針對使用 .NET Framework XAML 服務 XAML 物件寫入器的自訂類型，可以建立或變更對應至類型上 `x:Name` 的屬性。 您可以藉由參考屬性的名稱，在類型定義程式碼中與 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> 對應，藉此定義此行為。  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> 是類型層級屬性。  
  
 Using.NET Framework XAML 服務，XAML 名稱範圍支援的支援邏輯可以藉由執行 <xref:System.Windows.Markup.INameScope> 介面，以架構中立的方式來定義。  
  
## <a name="wpf-usage-notes"></a>WPF 使用注意事項  
 在使用 XAML、部分類別和程式碼後置之 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 應用程式的標準組建設定底下，指定的 `x:Name` 會成為標記編譯組建工作處理 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] 時，在基礎程式碼中建立的功能變數名稱，而且該欄位會保存物件的參考。 根據預設，建立的欄位為 internal。 您可以藉由指定[x:FieldModifier 屬性](x-fieldmodifier-directive.md)來變更欄位存取權。 在 WPF 和 Silverlight 中，標記編譯會定義並命名部分類別中的欄位，但此值一開始是空的。 然後，會從類別的函式中呼叫名為 `InitializeComponent` 的產生方法。 `InitializeComponent` 包含使用部分類別之 XAML 定義部分中存在的每個 `x:Name` 值做為輸入字串的 `FindName` 呼叫。 傳回值接著會指派給 like 命名的欄位參考，以使用從 XAML 剖析所建立的物件來填入域值。 執行 `InitializeComponent` 可以直接使用 `x:Name`/功能變數名稱來參考執行時間物件圖形，而不必在需要 XAML 定義物件的參考時，明確地呼叫 `FindName`。  
  
 針對使用 Microsoft Visual Basic 目標並包含具有 `Page` 組建動作之 XAML 檔案的 WPF 應用程式，在編譯期間會建立個別的參考屬性，將 `WithEvents` 關鍵字加入具有 `x:Name`的所有元素，以支援事件處理常式委派的 `Handles` 語法。 這個屬性一律是公用的。 如需詳細資訊，請參閱 [Visual Basic 和 WPF 事件處理](../wpf/advanced/visual-basic-and-wpf-event-handling.md)。  
  
 WPF XAML 處理器會使用 `x:Name`，在載入時將名稱註冊到 XAML 名稱範圍中，即使頁面不是由組建動作（例如，資源字典的鬆散 XAML）所編譯的情況也是如此。 這種行為的其中一個原因是，<xref:System.Windows.Data.Binding.ElementName%2A> 系結可能需要 `x:Name`。 如需詳細資訊，請參閱資料系結[總覽](../../desktop-wpf/data/data-binding-overview.md)。  
  
 如先前所述，`x:Name` （或 `Name`）不應該套用在也使用 `x:Key`的情況下。 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.ResourceDictionary> 具有將本身定義為 XAML 名稱範圍的特殊行為，但不會將其實作為強制執行此行為的 <xref:System.Windows.Markup.INameScope> Api 或 null 值。 如果 WPF XAML 剖析器在 XAML 定義的 <xref:System.Windows.ResourceDictionary>中遇到 `Name` 或 `x:Name`，則不會將名稱新增至任何 XAML 名稱範圍。 嘗試從任何 XAML 名稱範圍和 `FindName` 方法尋找該名稱，將不會傳回有效的結果。  
  
### <a name="xname-and-name"></a>X：Name 和名稱  
 許多 WPF 應用程式案例都可以避免使用 `x:Name` 屬性，因為數個重要基類（例如 <xref:System.Windows.FrameworkElement> 和 <xref:System.Windows.FrameworkContentElement>）中所指定的 `Name` 相依性屬性，都符合相同的目的。 仍然有一些常見的 XAML 和 WPF 案例，在架構層級沒有 `Name` 屬性的專案的程式碼存取就很重要。 例如，某些動畫和分鏡腳本支援類別不支援 `Name` 屬性，但通常必須在程式碼中參考它們，才能控制動畫。 如果您稍後想要從程式碼參考，請將 `x:Name` 指定為時間軸上的屬性，以及在 XAML 中建立的轉換。  
  
 如果 <xref:System.Windows.FrameworkElement.Name%2A> 可做為類別上的屬性，則 <xref:System.Windows.FrameworkElement.Name%2A> 和 `x:Name` 可以交換當做屬性使用，但如果同時在相同的專案上指定這兩個專案，就會產生 parse 例外狀況。 如果 XAML 是以標記方式編譯，則會在標記編譯時發生例外狀況，否則會在載入時發生。  
  
 <xref:System.Windows.FrameworkElement.Name%2A> 可以使用 XAML 屬性語法來設定，並在程式碼中使用 <xref:System.Windows.DependencyObject.SetValue%2A>;不過，請注意，在程式碼中設定 <xref:System.Windows.FrameworkElement.Name%2A> 屬性，並不會在 xaml 已載入的大多數情況下，于 XAML 名稱範圍內建立代表欄位參考。 不是嘗試在程式碼中設定 <xref:System.Windows.FrameworkElement.Name%2A>，而是針對適當的名稱範圍使用程式碼中 <xref:System.Windows.NameScope> 的方法。  
  
 <xref:System.Windows.FrameworkElement.Name%2A> 也可以使用具有內部文字的屬性專案語法來設定，但這種情況並不常見。 相反地，您無法在 XAML 屬性專案語法中，或使用 <xref:System.Windows.DependencyObject.SetValue%2A>的程式碼中設定 `x:Name`;它只能在物件上使用屬性語法來設定，因為它是指示詞。  
  
## <a name="silverlight-usage-notes"></a>Silverlight 使用方式備註  
 Silverlight 的 `x:Name` 會在其他篇幅中做說明。 如需詳細資訊，請參閱[XAML 命名空間（x：）語言功能（Silverlight）](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95))。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.Name%2A?displayProperty=nameWithType>
- [WPF 中的樹狀結構](../wpf/advanced/trees-in-wpf.md)
