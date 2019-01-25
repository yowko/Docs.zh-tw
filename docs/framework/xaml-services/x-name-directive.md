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
ms.openlocfilehash: 164b0283864cdeb60ef7b8e19c9d457f80ee4eb9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54696460"
---
# <a name="xname-directive"></a>x:Name 指示詞
可唯一識別 XAML 定義 XAML 名稱範圍中的項目。 XAML 名稱範圍和其唯一性模型可以套用至具現化的物件，當架構提供的 Api，或實作在執行階段存取 XAML 建立的物件圖形的行為。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<object x:Name="XAMLNameValue".../>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`XAMLNameValue`|字串，符合的限制[XamlName 文法](../../../docs/framework/xaml-services/xamlname-grammar.md)。|  
  
## <a name="remarks"></a>備註  
 之後`x:Name`會套用到一種架構之支援的程式設計模型，名稱就相當於保留物件參考或執行個體建構函式所傳回的變數。  
  
 值`x:Name`指示詞的使用方式中必須是唯一的 XAML 名稱範圍。 根據預設時使用的.NET Framework XAML 服務 API，主要的 XAML 名稱範圍定義於單一的 XAML 生產環境中，XAML 根項目，並包含該 XAML 生產環境中所包含的項目。 其他離散 XAML 名稱範圍，可能是單一的 XAML 生產環境中可以定義來解決此特定案例的架構。 例如，在 WPF 中，新的 XAML 名稱範圍定義和任何也會定義在該 XAML 生產的範本所建立。 如需有關 （但相關的許多 XAML 名稱範圍概念方式撰寫 for WPF） XAML 名稱範圍的詳細資訊，請參閱[WPF XAML Namescopes](../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)。  
  
 一般情況下，`x:Name`也使用的情況下應該不會套用`x:Key`。 現有的架構特定 XAML 實作引進了替代概念之間`x:Key`和`x:Name`，但並不是建議的作法。 .NET framework XAML 服務不支援這類替代概念，例如處理名稱/金鑰資訊時<xref:System.Windows.Markup.INameScope>或<xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>。  
  
 規則的 permittance`x:Name`名稱唯一性強制執行以及可能由定義特定實作的架構。 不過，可在.NET Framework XAML 服務，XAML 名稱範圍唯一性的架構定義應與一致的定義<xref:System.Windows.Markup.INameScope>資訊在本文件中，而且應該使用相同的規則相關的位置資訊會套用。 例如，[!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]實作會將各種不同的標記項目分成個別<xref:System.Windows.NameScope>範圍，例如資源字典內容、 頁面層級的 XAML、 範本和其他延後所建立的邏輯樹狀結構，並再強制執行 XAML每個這些 XAML 名稱範圍內的唯一名稱。  
  
 對於使用.NET Framework XAML 服務 XAML 物件寫入器的自訂型別，屬性對應至`x:Name`上可以建立或變更類型。 參考名稱的屬性，以與對應的定義此行為<xref:System.Windows.Markup.RuntimeNamePropertyAttribute>型別定義程式碼中。  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> 是型別層級的屬性。  
  
 Using.NET Framework XAML 服務 XAML 名稱範圍支援的支援邏輯可以藉由實作定義的 framework 中性方式<xref:System.Windows.Markup.INameScope>介面。  
  
## <a name="wpf-usage-notes"></a>WPF 使用注意事項  
 底下的標準組建組態[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]應用程式使用 XAML、 部分類別和程式碼後置，指定`x:Name`就會變成在基礎建立的欄位名稱程式碼時[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]處理標記編譯建置工作，而該欄位會保留物件的參考。 根據預設，[建立] 欄位則是內部項目。 您可以變更欄位的存取，藉由指定[X:fieldmodifier 屬性](../../../docs/framework/xaml-services/x-fieldmodifier-directive.md)。 在 WPF 和 Silverlight 中，序列會是標記編譯的定義，而且名稱欄位中的部分類別，但是這個值最初是空的。 然後，產生的方法名為`InitializeComponent`類別建構函式中呼叫。 `InitializeComponent` 組成`FindName`使用每個呼叫`x:Name`存在於 XAML 定義的一部分做為部分類別中的值輸入字串。 以填滿與從 XAML 所建立的物件的欄位值剖析，會再傳回的值指派給命名相似的欄位參考。 執行`InitializeComponent`可讓執行的階段物件 graph 使用的參考`x:Name`/ 直接，欄位名稱，而不必呼叫`FindName`明確每當您需要的 XAML 定義物件的參考。  
  
 使用 Microsoft Visual Basic 應用程式目標，包含與 XAML 檔案的 WPF`Page`加入編譯期間建立的建置動作，個別的參考屬性`WithEvents`關鍵字的所有項目來`x:Name`，以支援`Handles`事件處理常式委派的語法。 這個屬性一定是公用的。 如需詳細資訊，請參閱 [Visual Basic 和 WPF 事件處理](../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md)。  
  
 `x:Name` 是由 WPF XAML 處理器用來註冊至 XAML 名稱範圍的名稱，在載入時，即使的情況，頁面未編譯標記的建置動作 (例如，鬆散式 XAML 資源字典)。 此行為的一個原因是因為`x:Name`可能需要<xref:System.Windows.Data.Binding.ElementName%2A>繫結。 如需詳細資訊，請參閱 <<c0> [ 資料繫結概觀](../../../docs/framework/wpf/data/data-binding-overview.md)。  
  
 如先前所述`x:Name`(或`Name`) 也使用的情況下應該不會套用`x:Key`。 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.ResourceDictionary>有特殊的行為本身定義為 XAML 名稱範圍，但未實作或 null 值傳回<xref:System.Windows.Markup.INameScope>Api 來強制執行此行為。 如果 WPF XAML 剖析器碰到`Name`或是`x:Name`中的 XAML 定義<xref:System.Windows.ResourceDictionary>，名稱不會加入至任何 XAML 名稱範圍。 嘗試尋找該名稱，從任何 XAML 名稱範圍和`FindName`方法不會傳回有效的結果。  
  
### <a name="xname-and-name"></a>x： 名稱和名稱  
 許多 WPF 應用程式案例可以避免使用的任何`x:Name`屬性，因為`Name`相依性屬性中指定的預設 XAML 命名空間有幾個重要的基底類別這類<xref:System.Windows.FrameworkElement>和<xref:System.Windows.FrameworkContentElement>符合這個相同的目的。 仍有一些常見的 XAML 和 WPF 案例，程式碼存取的項目沒有`Name`在架構層級的屬性是非常重要。 比方說，不支援某些動畫和分鏡腳本的支援類別`Name`屬性，但它們通常需要參考程式碼中，以控制動畫。 您應該指定`x:Name`做為時間軸和 XAML，如果您想要於稍後參考它們從程式碼所建立的轉換屬性。  
  
 如果<xref:System.Windows.FrameworkElement.Name%2A>可為此類別中的屬性<xref:System.Windows.FrameworkElement.Name%2A>和`x:Name`可以交換使用，做為屬性，但如果同時指定這兩者相同的項目，就會產生剖析例外狀況。 如果 XAML 標記編譯時，會發生例外狀況上標記編譯，否則它就會發生在載入。  
  
 <xref:System.Windows.FrameworkElement.Name%2A> 可設定為使用 XAML 屬性語法，並在程式碼中使用<xref:System.Windows.DependencyObject.SetValue%2A>; 不過請注意這項設定<xref:System.Windows.FrameworkElement.Name%2A>在程式碼中的屬性不會建立在大部分情況下，其中的 XAML 是已經具代表性的欄位參考的 XAML 名稱範圍內載入。 而不是嘗試設定<xref:System.Windows.FrameworkElement.Name%2A>程式碼中，使用<xref:System.Windows.NameScope>從程式碼中，針對適當的名稱範圍的方法。  
  
 <xref:System.Windows.FrameworkElement.Name%2A> 也可以設定使用內部的文字中的屬性項目語法，但這不常見。 相反地，`x:Name`無法在 XAML 屬性項目語法，或設定在程式碼中使用<xref:System.Windows.DependencyObject.SetValue%2A>; 只能設定在物件上使用屬性語法，因為它是指示詞。  
  
## <a name="silverlight-usage-notes"></a>Silverlight 使用方式附註  
 `x:Name` silverlight 會另外記載。 如需詳細資訊，請參閱[XAML 命名空間 （x:）語言功能 (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081)。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.Name%2A?displayProperty=nameWithType>
- [WPF 中的樹狀結構](../../../docs/framework/wpf/advanced/trees-in-wpf.md)
