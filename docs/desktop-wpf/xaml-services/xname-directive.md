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
ms.openlocfilehash: 9f812a49a3217a563be1bd7f1d999b641c28463d
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071448"
---
# <a name="xname-directive"></a>x:Name 指示詞

唯一識別 XAML 定義的元素在 XAML 命名範圍中。 當框架提供 API 或實現在執行時存取 XAML 創建的物件圖的行為時,XAML 命名範圍及其唯一性模型可以應用於實例化物件。

## <a name="xaml-attribute-usage"></a>XAML Attribute Usage

```xaml
<object x:Name="XAMLNameValue".../>
```

## <a name="xaml-values"></a>XAML 值

|||
|-|-|
|`XAMLNameValue`|符合[XamlName 語法](xamlname-grammar.md)限制的字串。|

## <a name="remarks"></a>備註

應用於`x:Name`框架的備份程式設計模型後,名稱等效於保存物件引用的變數或構造函數返回的實例。

`x:Name`指令用法的值必須在 XAML 名稱範圍內是唯一的。 預設情況下,當 .NET XAML 服務 API 使用時,主 XAML 命名範圍在單個 XAML 生產的 XAML 根元素中定義,並包含該 XAML 生產中包含的元素。 框架可以定義單個 XAML 生產中可能發生的其他離散 XAML 命名範圍,以解決特定方案。 例如,在 WPF 中,新的 XAML 命名範圍由在 XAML 生產上定義的任何範本定義和創建。 有關 XAML 名稱範圍的詳細資訊(為 WPF 編寫,但與許多 XAML 名稱範圍概念相關),請參閱[WPF XAML 名稱範圍](../../framework/wpf/advanced/wpf-xaml-namescopes.md)。

通常,`x:Name`不應應用於也`x:Key`使用 的情況。 由特定現有框架實現的 XAML`x:Key``x:Name`在和 之間引入了替換概念,但這不是建議的做法。 .NET XAML 服務在處理名稱/金鑰資訊(<xref:System.Windows.Markup.INameScope><xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>如 或 ) 時不支援此類替換概念。

允許`x:Name`性規則以及名稱唯一性實施可能由特定的實現框架定義。 但是,要與 .NET XAML 服務一起使用,XAML 命名範圍的唯一性的框架定義應<xref:System.Windows.Markup.INameScope>與本文檔中的資訊定義一致,並且應該使用有關資訊應用位置的相同規則。 例如,[!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]實現將各種標記元素劃分為單獨<xref:System.Windows.NameScope>的 範圍,例如資源字典、由頁面級 XAML 創建的邏輯樹、範本和其他延遲內容,然後在每個 XAML 命名範圍內強制實施 XAML 名稱唯一性。

對於使用 .NET XAML 服務 XAML 物件編寫`x:Name`器的自定義類型 ,可以建立或更改映射到類型的屬性。 通過引用要使用類型定義代碼<xref:System.Windows.Markup.RuntimeNamePropertyAttribute>中映射的屬性的名稱來定義此行為。  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>是類型級屬性。

Using.NET XAML 服務,<xref:System.Windows.Markup.INameScope>可以通過實現 介面以框架中立的方式定義 XAML 命名範圍支援的備份邏輯。

## <a name="wpf-usage-notes"></a>WPF 使用注意事項

在使用 XAML、[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]部分類和代碼後面的應用程式的標準生成配置下`x:Name`,指定將成為在標記編譯生成任務[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]處理時 在基礎代碼中創建的欄位的名稱,並且該欄位包含對物件的引用。 預設情況下,創建的欄位是內部欄位。 您可以通過指定[x:欄位修改器屬性](xfieldmodifier-directive.md)來更改欄位訪問。 在 WPF 和 Silverlight 中,序列是標記編譯定義和命名部分類中的欄位,但該值最初為空。 然後,從類構造函數`InitializeComponent`中調用名為 生成的方法。 `InitializeComponent`由`FindName`使用部分類 XAML 定義部分`x:Name`中存在的每個 值作為輸入字串的調用組成。 然後,返回值分配給類似命名的欄位引用,以使用從 XAML 分析創建的物件填充欄位值。 執行`InitializeComponent`後 ,可以`x:Name`直接使用 / 欄位名稱引用執行時物件圖,而不必在需要`FindName`引用 XAML 定義的物件時顯式調用。

對於使用`Page`Microsoft Visual Basic 目標並包含包含生成操作的 XAML 檔的 WPF`WithEvents`應用程式,在編`x:Name`譯過程中將關鍵字`Handles`添加到具有的所有元素,以支援 事件處理程式委託的語法。 此屬性始終是公共的。 如需詳細資訊，請參閱 [Visual Basic 和 WPF 事件處理](../../framework/wpf/advanced/visual-basic-and-wpf-event-handling.md)。

`x:Name`WPF XAML 處理器在載入時使用該名稱註冊到 XAML 命名範圍中,即使對於頁面未透過生成操作進行標記編譯的情況也是如此(例如,資源字典的鬆散 XAML)。 此行為的原因是綁定可能需要`x:Name`<xref:System.Windows.Data.Binding.ElementName%2A>。 有關詳細資訊,請參閱[資料繫結此概述](../data/data-binding-overview.md)。

如前所述,(`x:Name``Name`或 )不應應用於`x:Key`也使用 的情況。 具有特殊[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.ResourceDictionary>行為,將自身定義為 XAML 命名範圍,但傳回<xref:System.Windows.Markup.INameScope>API 的未實現或 null 值,作為強制執行此行為的一種方式。 如果 WPF XAML 解析`Name`器`x:Name`遇到<xref:System.Windows.ResourceDictionary>或在 XAML 定義中,則名稱不會添加到任何 XAML 名稱範圍。 嘗試從任何 XAML 名稱範圍查找該名稱`FindName`和方法 將不會返回有效結果。

### <a name="xname-and-name"></a>x:名稱與名稱

許多 WPF`x:Name`應用程式方案 可以避免對屬性的任何使用,`Name`因為在預設的 XAML 命名空間中指定的依賴項屬性適用於幾個<xref:System.Windows.FrameworkElement>重要<xref:System.Windows.FrameworkContentElement>基類,如和滿足此相同的用途。 仍有一些常見的 XAML 和 WPF 方案,其中`Name`代碼訪問框架級別 上沒有屬性的元素非常重要。 例如,某些動畫和情節提要支援類不支援`Name`屬性,但它們通常需要在代碼中引用才能控制動畫。 如果以後打算`x:Name`從代碼中引用它們,則應在時間線上指定為屬性,並在 XAML 中創建的轉換中指定屬性。

如果在<xref:System.Windows.FrameworkElement.Name%2A>類上作為屬性可用<xref:System.Windows.FrameworkElement.Name%2A>`x:Name`, 並且可以作為屬性互換使用,但如果在同一元素上指定兩者,則會產生解析異常。 如果編譯了 XAML,則異常將在標記編譯上發生,否則將在載入時發生。

<xref:System.Windows.FrameworkElement.Name%2A>可以使用 XAML 屬性語法與 在<xref:System.Windows.DependencyObject.SetValue%2A>代碼中使用 。但是請注意,在已<xref:System.Windows.FrameworkElement.Name%2A>載入 XAML 的大多數情況下,在代碼中設置屬性不會在 XAML 命名範圍內創建具有代表性的欄位引用。 不要嘗試在代碼中設置<xref:System.Windows.FrameworkElement.Name%2A>,而是根據<xref:System.Windows.NameScope>相應的 名稱範圍使用代碼中的方法。

<xref:System.Windows.FrameworkElement.Name%2A>也可以使用包含內部文本的屬性元素語法進行設置,但這種情況並不常見。 相反,`x:Name`無法在 XAML 屬性元素語法中設定<xref:System.Windows.DependencyObject.SetValue%2A>,也不能在程式碼中使用 。它只能使用物件的屬性語法進行設置,因為它是指令。

## <a name="silverlight-usage-notes"></a>銀光使用說明

`x:Name`銀光單獨記錄。 有關詳細資訊,請參閱[XAML 命名空間 (x:)語言功能(銀光)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.Name%2A?displayProperty=nameWithType>
- [WPF 中的樹狀結構](../../framework/wpf/advanced/trees-in-wpf.md)
