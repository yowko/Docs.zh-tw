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
ms.openlocfilehash: b373b33fcc962e49aa220f31e24b1484a0a8cd98
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401598"
---
# <a name="componentresourcekey-markup-extension"></a>ComponentResourceKey 標記延伸
定義和參考從外部元件載入之資源的索引鍵。 這可讓資源查閱指定元件中的目標型別, 而不是元件或類別上的明確資源字典。  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a>XAML 屬性使用方式 (設定金鑰、壓縮)  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a>XAML 屬性使用方式 (設定索引鍵, 詳細資訊)  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a>XAML 屬性使用方式 (要求資源, compact)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a>XAML 屬性使用方式 (要求資源, 詳細資訊)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`targetTypeName`|在資源元件中定義的公用 common language runtime (CLR) 類型名稱。|  
|`targetID`|資源的索引鍵。 查閱資源時, `targetID`會類似于資源的[x:Key](../../xaml-services/x-key-directive.md)指示詞。|  
  
## <a name="remarks"></a>備註  
 如上所述, {`ComponentResourceKey`} 標記延伸使用方式可在兩個地方找到:  
  
- 主題資源字典中的索引鍵定義, 如同控制項作者所提供。  
  
- 當您重新範本化控制項, 但想要使用來自控制項主題所提供之資源的屬性值時, 從元件存取主題資源。  
  
 若要參考來自主題的元件資源, 通常建議您使用`{DynamicResource}` `{StaticResource}`而不是。 這會顯示在使用方式中。 `{DynamicResource}`建議使用, 因為使用者可以變更主題本身。 如果您想 懽搰 支援佈景主題的控制項作者的意圖元件資源時，您應該啟用您的元件資源參考也是動態。  
  
 會<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>識別存在於實際定義資源之目標群組件中的類型。 可以單獨定義和使用, 而不需要確切瞭解定義<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>的位置, 但最終必須透過參考的元件來解析類型。 `ComponentResourceKey`  
  
 的常見用法<xref:System.Windows.ComponentResourceKey>是定義接著公開為類別成員的索引鍵。 在這種情況下, 您<xref:System.Windows.ComponentResourceKey>可以使用類別的「函式」, 而不是標記延伸。 如需詳細資訊, <xref:System.Windows.ComponentResourceKey>請參閱或主題[控制項撰寫總覽](../controls/control-authoring-overview.md)的「定義和參考主題資源的索引鍵」一節。  
  
 對於建立金鑰和參考索引鍵, 屬性語法通常用於`ComponentResourceKey`標記延伸。  
  
 所顯示的精簡語法會依賴<xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType>標記延伸的「函式簽章」和「位置參數使用方式」。 指定`targetTypeName` 和`targetID`的順序很重要。 Verbose 語法依賴無參數的<xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType>函式, 然後以類似物件<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>專案<xref:System.Windows.ComponentResourceKey.ResourceId%2A>上 true 屬性語法的方式來設定和。 在 verbose 語法中, 屬性的設定順序並不重要。 這兩種替代方案的關聯性和機制 (compact 和 verbose) 在主題[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)中有更詳細的說明。  
  
 就技術上而言, `targetID`的值可以是任何物件, 而不一定是字串。 不過, WPF 中最常見的用法是將`targetID`值與字串的形式對齊, 這類字串在[XamlName 文法](../../xaml-services/xamlname-grammar.md)中是有效的。  
  
 `ComponentResourceKey`可以在物件專案語法中使用。 在此情況下, 必須同時<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>指定和<xref:System.Windows.ComponentResourceKey.ResourceId%2A>屬性的值, 才能正確地初始化延伸模組。  
  
 在讀取[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]器的[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]執行中, 此標記<xref:System.Windows.ComponentResourceKey>延伸的處理是由類別所定義。  
  
 `ComponentResourceKey` 是一種標記延伸。 如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的所有標記延伸都會在其屬性語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性。 如需詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.ComponentResourceKey>
- <xref:System.Windows.Controls.ControlTemplate>
- [控制項撰寫概觀](../controls/control-authoring-overview.md)
- [XAML 概觀 (WPF)](xaml-overview-wpf.md)
- [標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)
