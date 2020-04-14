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
ms.openlocfilehash: 4cdba2a61be4e9686cd2120fd90a213534c222c8
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243358"
---
# <a name="componentresourcekey-markup-extension"></a>ComponentResourceKey 標記延伸
定義和引用從外部程式集載入的資源的鍵。 這使資源查找能夠在程式集中指定目標類型,而不是在程式集或類上指定顯式資源字典。  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a>XAML 屬性用法(設定鍵,緊湊)  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a>XAML 屬性用法(設定鍵,詳細)  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a>XAML 屬性使用(請求資源,緊湊)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a>XAML 屬性使用(請求資源,詳細)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`targetTypeName`|在資源程式集中定義的公共通用語言運行時 (CLR) 類型的名稱。|  
|`targetID`|資源的鍵。 當資源被抬起來時`targetID`,將類似於資源的[x:Key 指令](../../../desktop-wpf/xaml-services/xkey-directive.md)。|  
  
## <a name="remarks"></a>備註  
 如上文用法所示,在以下兩`ComponentResourceKey`個位置可以找到 [ 標記延伸用法:  
  
- 主題資源字典中鍵的定義,由控件作者提供。  
  
- 從程式集存取主題資源時,當您重新範本化控制項,但希望使用來自控制項主題提供的資源的屬性值時。  
  
 對於參考來自主題的元件資源,通常建議您使用`{DynamicResource}`而不是`{StaticResource}`。 這在用法中顯示。 `{DynamicResource}`建議使用,因為使用者可以更改主題本身。 如果希望與控制項作者支援主題的意圖最匹配的元件資源,則應使元件資源引用也是動態的。  
  
 <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>標識目標程式集中存在的類型,其中實際定義了資源。 `ComponentResourceKey`可以定義和使用,而確切知道定義<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>的位置 ,但最終必須通過引用的程式集解析類型。  
  
 一個常用法<xref:System.Windows.ComponentResourceKey>種是定義密鑰,然後作為類的成員公開。 對於此用法,<xref:System.Windows.ComponentResourceKey>請使用類建構函數,而不是標記副檔名。 有關詳細資訊,請參閱<xref:System.Windows.ComponentResourceKey>主題[「控件創作概述](../controls/control-authoring-overview.md)」中的「主題資源定義和引用鍵」部分。  
  
 對於建立鍵和引用鍵控資源,屬性語法通常用於`ComponentResourceKey`標記擴展。  
  
 顯示的緊湊語法依賴於標記擴展<xref:System.Windows.ComponentResourceKey.%23ctor%2A>的構造函數簽名和位置參數用法。 `targetTypeName`給出的順序`targetID`很重要。 詳細語法依賴於無<xref:System.Windows.ComponentResourceKey.%23ctor%2A>參數構造函數,然後以類似於物件元素上的真實<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>屬性<xref:System.Windows.ComponentResourceKey.ResourceId%2A>語法 的方式設置 和。 在詳細語法中,屬性的設置順序並不重要。 這兩種備選方案的關係和機制(緊湊和詳細)在主題[標記擴展和WPF XAML](markup-extensions-and-wpf-xaml.md)中進行了更詳細的描述。  
  
 從技術上講,的值`targetID`可以是任何物件,它不必是字串。 但是,WPF 中最常見的用法是`targetID`使 值與字串的窗體對齊,以及此類字串在[XamlName 語法](../../../desktop-wpf/xaml-services/xamlname-grammar.md)中有效的位置。  
  
 `ComponentResourceKey`可用於物件元素語法。 在這種情況下,需要指定<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A><xref:System.Windows.ComponentResourceKey.ResourceId%2A>和屬性的值才能正確初始化擴展。  
  
 讀[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]取器實現中,此標記擴展的處理由<xref:System.Windows.ComponentResourceKey>類定義。  
  
 `ComponentResourceKey` 是一種標記延伸。 如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的所有標記延伸都會在其屬性語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性。 如需詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.ComponentResourceKey>
- <xref:System.Windows.Controls.ControlTemplate>
- [控制項撰寫概觀](../controls/control-authoring-overview.md)
- [XAML 概觀 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)
