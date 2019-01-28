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
ms.openlocfilehash: 78fddd65099d5f6bfc4796d5fa353a92171bda5c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530998"
---
# <a name="componentresourcekey-markup-extension"></a>ComponentResourceKey 標記延伸
定義和參考會從外部組件載入的資源索引鍵。 這可讓組件，而不是明確的資源字典的組件中，或在類別上指定目標類型的資源查閱。  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a>XAML 屬性使用方式 （設定索引鍵、 compact）  
  
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
|`targetTypeName`|公用名稱[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]資源組件中定義的類型。|  
|`targetID`|資源的金鑰。 時，會尋找資源`targetID`將會類似於[X:key 指示詞](../../../../docs/framework/xaml-services/x-key-directive.md)的資源。|  
  
## <a name="remarks"></a>備註  
 上述的使用方式中所示 {`ComponentResourceKey`} 標記延伸使用方式在兩個地方找到：  
  
-   內的佈景主題資源字典，控制項作者所提供的索引鍵定義。  
  
-   從組件存取佈景主題資源，當您是重新範本化控制項，但想要使用來自控制項的佈景主題所提供的資源的屬性值。  
  
 參考來自佈景主題的元件資源，通常建議您改用`{DynamicResource}`而非`{StaticResource}`。 這會顯示使用方式。 `{DynamicResource}` 建議，因為使用者可以變更佈景主題本身。 如果您想支援佈景主題的控制項作者的意圖元件資源時，您應該啟用您的元件資源參考也是動態。  
  
 <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>識別實際定義資源的目標組件中存在的類型。 A`ComponentResourceKey`可以定義和使用獨立於完全知道其中<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>已定義，但最後必須解決透過參考組件的型別。  
  
 常見的用法如<xref:System.Windows.ComponentResourceKey>是定義索引鍵，然後公開做為類別的成員。 若是如此，您用於<xref:System.Windows.ComponentResourceKey>類別建構函式，不是標記延伸。 如需詳細資訊，請參閱 < <xref:System.Windows.ComponentResourceKey>，或主題的 「 定義和參考索引鍵的佈景主題資源 」 一節[控制項撰寫概觀](../../../../docs/framework/wpf/controls/control-authoring-overview.md)。  
  
 建立索引鍵和參考做為索引鍵的資源，如屬性語法通常用於`ComponentResourceKey`標記延伸。  
  
 簡潔的語法所示依賴<xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType>建構函式簽章和標記延伸的位置參數用法。 順序`targetTypeName`和`targetID`有很重要。 詳細的語法會依賴<xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType>預設建構函式，然後按一下 設定<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>和<xref:System.Windows.ComponentResourceKey.ResourceId%2A>類似於物件項目上，則為 true 的屬性語法的方式。 在詳細的語法中，設定屬性的順序並不重要。 關聯性和這些兩個替代方法 （compact 和詳細資訊） 的機制主題中的更多詳細資料中所述[標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。  
  
 技術上來說，值`targetID`可以是任何物件，它不是字串。 不過，在 WPF 中最常見的用法是對齊`targetID`form 字串，而且這類字串中有效的值[XamlName 文法](../../../../docs/framework/xaml-services/xamlname-grammar.md)。  
  
 `ComponentResourceKey` 可用於物件元素語法。 在此案例中，指定的值都<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>和<xref:System.Windows.ComponentResourceKey.ResourceId%2A>屬性，才能正確地初始化 擴充功能。  
  
 在  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]讀取器實作，這個標記延伸的處理由定義<xref:System.Windows.ComponentResourceKey>類別。  
  
 `ComponentResourceKey` 是一種標記延伸。 如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的所有標記延伸都會在其屬性語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性。 如需詳細資訊，請參閱[標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.ComponentResourceKey>
- <xref:System.Windows.Controls.ControlTemplate>
- [控制項撰寫概觀](../../../../docs/framework/wpf/controls/control-authoring-overview.md)
- [XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
