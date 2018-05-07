---
title: ComponentResourceKey 標記延伸
ms.date: 03/30/2017
f1_keywords:
- ComponentResourceKey
- ComponentResourceKeyExtension
helpviewer_keywords:
- ComponentResourceKey markup extension [WPF]
- XAML [WPF], ComponentResourceKey markup extension
ms.assetid: d6bcdbe6-61b3-40a7-b381-4e02185b5a85
ms.openlocfilehash: d11c26add084165eaa9fd0b319a375c4b98c7fb9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="componentresourcekey-markup-extension"></a>ComponentResourceKey 標記延伸
定義和參考會從外部組件載入的資源索引鍵。 這可讓組件，而不是類別或組件中的明確資源字典中指定的目標類型的資源查閱。  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a>XAML 屬性使用方式 （設定索引鍵，compact）  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a>XAML 屬性使用方式 （設定索引鍵、 詳細）  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a>XAML 屬性使用方式 （提出要求的資源，compact）  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a>XAML 屬性使用方式 （提出要求的資源，詳細資訊）  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`targetTypeName`|公開名稱[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]資源組件中定義的類型。|  
|`targetID`|資源的索引鍵。 資源是在查閱，`targetID`會類似於[X:key 指示詞](../../../../docs/framework/xaml-services/x-key-directive.md)的資源。|  
  
## <a name="remarks"></a>備註  
 上述的使用方式中所見 {`ComponentResourceKey`} 中兩個地方找到標記延伸使用方式：  
  
-   內的主題資源字典，控制項作者所提供的索引鍵定義。  
  
-   從組件存取佈景主題的資源，當您重製樣板控制項但想要使用來自所控制的主題提供資源的屬性值。  
  
 參考來自佈景主題的元件資源，建議您改用`{DynamicResource}`而不是`{StaticResource}`。 這是顯示在 使用方式。 `{DynamicResource}` 建議，因為使用者可以變更本身的佈景主題。 如果您希望元件的資源最接近控制項作者的意圖支援佈景主題，您應該啟用您元件的資源參考也是動態。  
  
 <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>識別存在於實際定義資源的目標組件的類型。 A`ComponentResourceKey`可以定義，以及使用獨立於完全瞭解其中<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>已定義，但最後必須解析參考的組件透過型別。  
  
 針對常見的用法<xref:System.Windows.ComponentResourceKey>是定義為類別的成員然後公開的索引鍵。 若是如此，您用於<xref:System.Windows.ComponentResourceKey>類別建構函式、 標記延伸。 如需詳細資訊，請參閱<xref:System.Windows.ComponentResourceKey>，或主題的 「 定義和參考索引鍵的主題資源 」 一節[控制項撰寫概觀](../../../../docs/framework/wpf/controls/control-authoring-overview.md)。  
  
 建立金鑰和參考做為索引鍵的資源，如屬性語法通常用於`ComponentResourceKey`標記延伸。  
  
 所顯示的精簡語法依賴<xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType>建構函式簽章和標記延伸的位置參數用法。 順序`targetTypeName`和`targetID`會提供很重要。 詳細語法依賴<xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType>預設建構函式，然後按一下 設定<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>和<xref:System.Windows.ComponentResourceKey.ResourceId%2A>類似於物件項目，則為 true 的屬性語法的方式。 在詳細語法中，設定屬性的順序並不重要。 主題中的更多詳細資料中所述的關聯性和這些兩個替代方法 （compact 和詳細資訊） 的機制是[標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。  
  
 技術上來說，值`targetID`可以是任何物件，它不是字串。 不過，在 WPF 中最常見的用法是對齊`targetID`值與字串，而且在這類字串中是有效的表單[XamlName 文法](../../../../docs/framework/xaml-services/xamlname-grammar.md)。  
  
 `ComponentResourceKey` 可用於物件項目語法。 在此情況下，指定的值都<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>和<xref:System.Windows.ComponentResourceKey.ResourceId%2A>來正確地初始化延伸的屬性必要項目。  
  
 在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]讀取器實作，這個標記延伸的處理由定義<xref:System.Windows.ComponentResourceKey>類別。  
  
 `ComponentResourceKey` 是一種標記延伸。 如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的所有標記延伸都會在其屬性語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性。 如需詳細資訊，請參閱[標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.ComponentResourceKey>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [控制項撰寫概觀](../../../../docs/framework/wpf/controls/control-authoring-overview.md)  
 [XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
