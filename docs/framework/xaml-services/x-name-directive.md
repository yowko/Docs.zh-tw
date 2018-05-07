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
ms.openlocfilehash: 7fcb7fe767e892109e48c5e56db26b5943b6ef13
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="xname-directive"></a>x:Name 指示詞
可唯一識別已定義 XAML 的 XAML 名稱範圍中的項目。 XAML 名稱範圍和其唯一性模型可以套用至具現化物件，架構會提供 Api，或實作行為，在執行階段存取 XAML 建立的物件圖形時。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<object x:Name="XAMLNameValue".../>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`XAMLNameValue`|字串，並符合限制的[XamlName 文法](../../../docs/framework/xaml-services/xamlname-grammar.md)。|  
  
## <a name="remarks"></a>備註  
 之後`x:Name`套用至一個架構的備份程式撰寫模型中的名稱是相當於保留物件參考或執行個體建構函式所傳回的變數。  
  
 值`x:Name`指示詞的使用方式必須是唯一的 XAML 名稱範圍內。 根據預設時使用的.NET Framework XAML 服務 API，主要的 XAML 名稱範圍定義於單一的 XAML 生產環境中，XAML 根項目，而且包含在該 XAML 生產環境中所包含的項目。 其他可能會發生在單一 XAML 生產的離散 XAML namescopes 可以解決特定案例的架構定義。 例如，在 WPF 中，新的 XAML 名稱範圍定義和任何也會定義在該 XAML 生產的範本所建立。 如需 （但相關的許多 XAML namescope 概念方式寫入 for WPF） XAML 名稱範圍的詳細資訊，請參閱[WPF XAML Namescopes](../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)。  
  
 一般情況下，`x:Name`不應該套用的情況下，也使用`x:Key`。 由現有的架構特定 XAML 實作已引入之間替換概念`x:Key`和`x:Name`，但並不是建議的作法。 .NET framework XAML 服務時，不支援這類替代概念處理名稱/索引鍵資訊，例如<xref:System.Windows.Markup.INameScope>或<xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>。  
  
 規則的 permittance`x:Name`名稱唯一性的強制執行以及有可能定義的特定實作的架構。 不過，為了能夠使用.NET Framework XAML 服務，XAML namescope 唯一性的架構定義應該與一致的定義<xref:System.Windows.Markup.INameScope>本文中的資訊，而且應該使用相同的規則有關的位置資訊會套用。 例如，[!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]實作各種標記項目分成個別<xref:System.Windows.NameScope>範圍，例如資源字典內容、 XAML 頁面層級、 範本和其他延後所建立之邏輯樹狀結構，並再強制執行 XAML在每一個這些 XAML 名稱範圍內的唯一名稱。  
  
 針對使用.NET Framework XAML 服務 XAML 物件寫入器的自訂類型，屬性對應至`x:Name`上可建立或變更類型。 您定義這項行為會參照要使用對應的屬性名稱<xref:System.Windows.Markup.RuntimeNamePropertyAttribute>型別定義程式碼中。  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> 是型別層級屬性。  
  
 可以藉由實作 framework 中性方式定義 Using.NET Framework XAML 服務 XAML 名稱範圍支援的備份邏輯<xref:System.Windows.Markup.INameScope>介面。  
  
## <a name="wpf-usage-notes"></a>WPF 使用注意事項  
 下的標準組建組態[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]應用程式，使用 XAML、 部分類別，以及程式碼後置指定`x:Name`成為的名稱建立在基礎的欄位。 程式碼時[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]處理的標記編譯建置工作，而該欄位會保存物件的參考。 根據預設，建立的欄位是內部。 您可以變更欄位存取權，藉由指定[X:fieldmodifier 屬性](../../../docs/framework/xaml-services/x-fieldmodifier-directive.md)。 在 WPF 和 Silverlight，序列是定義編譯標記，以及名稱欄位中的部分類別，但是這個值最初是空的。 然後，產生的方法命名為`InitializeComponent`類別建構函式中呼叫。 `InitializeComponent` 組成`FindName`呼叫使用每個`x:Name`值做為部分類別的已定義 XAML 的部分存在於輸入字串。 傳回值則以填滿與從 XAML 所建立物件的欄位值剖析指派名稱相同的欄位參考中。 執行`InitializeComponent`進行執行的階段物件 graph 使用的參考可能`x:Name`/ 直接，欄位名稱，而不必呼叫`FindName`明確每當您需要的 XAML 定義物件的參考。  
  
 Wpf 使用 Microsoft Visual Basic 應用程式為目標並包含與 XAML 檔案`Page`建置動作，個別的參考屬性將加入的編譯期間建立`WithEvents`有的所有項目的關鍵字`x:Name`，以支援`Handles`事件處理常式委派的語法。 這個屬性一定是公用的。 如需詳細資訊，請參閱 [Visual Basic 和 WPF 事件處理](../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md)。  
  
 `x:Name` 可由 WPF XAML 處理器來註冊到 XAML 名稱範圍的名稱，在載入時間，即使的情況，頁面未標記編譯的建置動作 (例如，鬆散的 XAML 資源字典的)。 此行為的其中一個原因是因為`x:Name`可能需要<xref:System.Windows.Data.Binding.ElementName%2A>繫結。 如需詳細資訊，請參閱[資料繫結概觀](../../../docs/framework/wpf/data/data-binding-overview.md)。  
  
 如前所述， `x:Name` (或`Name`) 不應該套用的情況下，也使用`x:Key`。 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.ResourceDictionary>具有特殊行為定義本身為 XAML 名稱範圍，但未實作或 null 值傳回<xref:System.Windows.Markup.INameScope>Api 來強制執行此行為。 如果 WPF XAML 剖析器遇到`Name`或`x:Name`XAML 定義<xref:System.Windows.ResourceDictionary>，名稱不會加入至任何 XAML 名稱範圍。 嘗試尋找該名稱，從任何 XAML 名稱範圍和`FindName`方法不會傳回有效的結果。  
  
### <a name="xname-and-name"></a>x: Name 和名稱  
 許多的 WPF 應用程式案例可以避免使用的任何`x:Name`屬性，因為`Name`做為相依性屬性中指定的預設 XAML 命名空間的數個重要的基底類別例如<xref:System.Windows.FrameworkElement>和<xref:System.Windows.FrameworkContentElement>滿足這個相同的目的。 仍有一些常見的 XAML 和 WPF 案例其中程式碼存取項目不含`Name`在架構層級的屬性是非常重要。 不支援某些動畫和分鏡腳本的支援類別，例如`Name`屬性，但是它們通常需要為了控制動畫，程式碼中參考。 您應該指定`x:Name`做時刻表和轉換建立在 XAML 中，如果您想要稍後參考它們從程式碼上的屬性。  
  
 如果<xref:System.Windows.FrameworkElement.Name%2A>是做為屬性類別上使用<xref:System.Windows.FrameworkElement.Name%2A>和`x:Name`可交換使用做為屬性，但如果同時指定這兩者在相同的元素，就會產生剖析例外狀況。 如果標記編譯 XAML，會發生例外狀況上編譯標記，否則它就會發生在載入。  
  
 <xref:System.Windows.FrameworkElement.Name%2A> 可以使用 XAML 屬性的語法，來設定和在程式碼中使用<xref:System.Windows.DependencyObject.SetValue%2A>; 不過請注意該設定<xref:System.Windows.FrameworkElement.Name%2A>程式碼中的屬性不會建立在大部分情況下，XAML 其中已經是 XAML 名稱範圍內的代表性的欄位參考載入。 而不是嘗試設定<xref:System.Windows.FrameworkElement.Name%2A>在程式碼，使用<xref:System.Windows.NameScope>從程式碼中，針對適當的名稱範圍的方法。  
  
 <xref:System.Windows.FrameworkElement.Name%2A> 也可以設定內部文字中，使用屬性項目語法，但這不常發生。 相反地，`x:Name`無法在 XAML 屬性項目語法，或在程式碼中使用設定<xref:System.Windows.DependencyObject.SetValue%2A>; 只能設定在物件上使用屬性語法，因為它是指示詞。  
  
## <a name="silverlight-usage-notes"></a>Silverlight 的使用方式附註  
 `x:Name` silverlight 被說明文件。 如需詳細資訊，請參閱[XAML 命名空間 （x:）語言功能 (Silverlight)](http://go.microsoft.com/fwlink/?LinkId=199081)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>  
 <xref:System.Windows.FrameworkContentElement.Name%2A?displayProperty=nameWithType>  
 [WPF 中的樹狀結構](../../../docs/framework/wpf/advanced/trees-in-wpf.md)
