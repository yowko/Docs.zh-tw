---
title: x:Key 指示詞
ms.date: 03/30/2017
f1_keywords:
- xKey
- Key
- x:Key
helpviewer_keywords:
- x:Key attribute [XAML Services]
- Key attribute in XAML [XAML Services]
- XAML [XAML Services], x:Key attribute
ms.assetid: 1985cd45-f197-42d5-b75e-886add64b248
ms.openlocfilehash: c05f98932ceceeb1530b34a09b1923f2af1378b5
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071497"
---
# <a name="xkey-directive"></a>x:Key 指示詞
唯一標識在 XAML 定義的字典中創建和引用的元素。 向`x:Key`XAML 物件元素添加值是標識資源字典中資源的最常見方法,例如在<xref:System.Windows.ResourceDictionary>WPF 中。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a>XAML 屬性使用方式(特定於 WPF)  
  
```xaml  
<object.Resources>  
  <object x:Key="stringKeyValue".../>  
</object.Resources>  
-or-  
<object.Resources>  
  <object x:Key="{markupExtensionUsage}".../>  
</object.Resources>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`stringKeyValue`|用作鍵的文字字串。 文字字串必須符合[XamlName 語法](xamlname-grammar.md)。|  
|`markupExtensionUsage`|在標記延伸分隔符{}中,提供用作鍵的對象的標記擴展用法。 請參閱＜備註＞。|  
  
## <a name="remarks"></a>備註  
 `x:Key`支援 XAML 資源字典概念。 XAML 作為一種語言不會定義資源字典實現,而資源字典實現留給特定的 UI 框架。 要瞭解有關如何在 WPF 中實現 XAML 資源字典的更多資訊,請參閱[XAML 資源](../fundamentals/xaml-resources-define.md)。  
  
 在 XAML 2006 和`x:Key`WPF 中,必須作為屬性提供。 您仍可以使用非字串鍵,但這需要標記擴展用法才能在屬性窗體中提供非字串值。 如果使用 XAML 2009,`x:Key`則可以指定為元素,以顯式支援由字串以外的對象類型鍵控的字典,而無需標記擴展中間。 請參閱本主題中的「XAML 2009」部分。 備註部分的其餘部分特別適用於 XAML 2006 實現。  
  
 的屬性`x:Key`值可以是[XamlName 語法](xamlname-grammar.md)中定義的任何字串,也可以是通過標記擴展計算的物件。 有關 WPF 的範例,請參閱"WPF 使用說明"。  
  
 作為<xref:System.Collections.IDictionary>實現的父元素的子元素通常必須包含`x:Key`指定 該字典中唯一鍵值的屬性。 框架可能實現別名鍵屬性,`x:Key`以替換特定類型;定義此類屬性的類型應歸因於<xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>。  
  
 指定`x:Key`等效的代碼是用於基礎<xref:System.Collections.IDictionary>的鍵。 例如,在`x:Key`WPF 中資源標記中應用的與將資源添加到代碼中的`key`<xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType><xref:System.Windows.ResourceDictionary>WPF 時的參數值等效。  
  
## <a name="wpf-usage-notes"></a>WPF 使用注意事項  
 作為<xref:System.Collections.IDictionary>實現(如 WPF)<xref:System.Windows.ResourceDictionary>的父物件的子物件通常必須`x:Key`包含屬性 ,並且鍵值必須是唯一的字典。 有兩個值得注意的例外:  
  
- 某些 WPF 類型聲明字典用法的隱式鍵。 例如,帶<xref:System.Windows.Style><xref:System.Windows.Style.TargetType%2A>的或<xref:System.Windows.DataTemplate>的<xref:System.Windows.DataTemplate.DataType%2A>和,<xref:System.Windows.ResourceDictionary>可以位於中,並使用隱式鍵。  
  
- WPF 支援合併的資源字典概念。 金鑰可以在合併字典之間共享,並且可以使用<xref:System.Windows.FrameworkContentElement.FindResource%2A>訪問共用密鑰行為。 如需詳細資訊，請參閱[合併的資源字典](../../framework/wpf/advanced/merged-resource-dictionaries.md)。  
  
 在整體 WPF XAML 實現和應用模型中,XAML 標記編譯器不檢查密鑰唯一性。 相反,缺少或非唯`x:Key`一值會導致載入時間 XAML 解析器錯誤。 但是,Visual Studio 處理 WPF 字典時通常可以在設計階段注意到此類錯誤。  
  
 請注意,在所示的語法中,<xref:System.Windows.ResourceDictionary>物件隱化於 WPF XAML 處理器如何生成<xref:System.Windows.FrameworkElement.Resources%2A>集合以填充 集合。 在<xref:System.Windows.ResourceDictionary>標記中,通常不作為元素顯式提供 a,儘管在某些情況下,如果需要,它可以是集合物件元素(<xref:System.Windows.FrameworkElement.Resources%2A>它將是 屬性元素和填充字典中的項之間的集合物件元素)。 有關集合物件在標記中幾乎總是隱式元素的原因的資訊,請參閱[XAML 語法詳細資訊](../../framework/wpf/advanced/xaml-syntax-in-detail.md)。  
  
 在 WPF XAML 實現中,資源字典密鑰<xref:System.Windows.ResourceKey>的處理由 抽象類定義。 但是,WPF XAML 處理器會根據密鑰的用法為密鑰生成不同的基礎擴展類型。 例如,或<xref:System.Windows.DataTemplate>任何派生類的鍵單獨處理,並生成不同的<xref:System.Windows.DataTemplateKey>物件。  
  
 鍵與名稱在基本的`x:Key`XAML`x:Name`定義 中使用不同的指令和語言元素 ( 對 ) 。 WPF 的定義和這些概念的應用也在不同的情況下使用密鑰和名稱。 有關詳細資訊,請參閱[WPF XAML 名稱範圍](../../framework/wpf/advanced/wpf-xaml-namescopes.md)。  
  
 如前所述,鍵的值可以通過標記擴展提供,並且可以不提供字串值。 WPF 專案的範例是,`x:Key`的值 可能是[元件資源金鑰](../../framework/wpf/advanced/componentresourcekey-markup-extension.md)。 某些控件公開自定義樣式資源的該類型的樣式鍵,該樣式資源在不完全替換樣式的情況下會影響該控件的部分外觀和行為。 此鍵的一個例子是<xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>。  
  
 WPF 合併字典功能引入了關鍵唯一性和密鑰查找行為的其他注意事項。 如需詳細資訊，請參閱[合併的資源字典](../../framework/wpf/advanced/merged-resource-dictionaries.md)。  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009`x:Key`放寬了始終以屬性形式提供的限制。  
  
 在 WPF 中,可以使用 XAML 2009 功能,但僅適用於未標記編譯的 XAML。 WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。  
  
 在 XAML 2009 下`x:Key`,您可以通過以下用法指定元素:  
  
### <a name="xaml-element-usage-xaml-2009-only"></a>XAML 元素使用(僅限 XAML 2009)  
  
```xaml  
<object>  
  <x:Key>  
keyObject  
  </x:Key>  
...  
</object>  
```  
  
### <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`keyObject`|物件的物件元素,該物件用作專用字典中給定`object`項的鍵。|  
  
- 此種使用的容器/父級不在此處顯示。 `object`應作為表示專用字典實現的物件元素的子元素。 `keyObject`應作為該特定專用字典實現的關鍵的物件實例(或值類型的值)。  
  
- WPF 不實現需要此用法的字典。 對象鍵是 XAML 語言的一個常規功能,對於某些自定義字典方案可能很有用,在其中需要在 XAML 中創建字典。 對於 WPF 功能(如使用非字串鍵進行資源化的隱式樣式),存在其他用於建立或指定鍵的技術,因此無需使用物件鍵。  
  
- `keyObject`也可以是物件元素形式的標記擴展用法,而不是直接的物件實例。  
  
## <a name="silverlight-usage-notes"></a>銀光使用說明  
 `x:Key`銀光單獨記錄。 有關詳細資訊,請參閱[XAML 命名空間 (x:)語言功能(銀光)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).  
  
## <a name="see-also"></a>另請參閱

- [XAML 資源](../fundamentals/xaml-resources-define.md)
- [資源和程式碼](../../framework/wpf/advanced/resources-and-code.md)
- [StaticResource 標記延伸](../../framework/wpf/advanced/staticresource-markup-extension.md)
