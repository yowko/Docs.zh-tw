---
title: 繫結標記延伸
ms.date: 03/30/2017
f1_keywords:
- Binding
helpviewer_keywords:
- Binding markup extensions [WPF]
- XAML [WPF], Binding markup extension
ms.assetid: 83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63
ms.openlocfilehash: c6a424e085c7499db08d0a7e6b652f45fb2cdd70
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644075"
---
# <a name="binding-markup-extension"></a>繫結標記延伸
將屬性值延遲為資料綁定值,創建中間運算式物件並解釋在運行時應用於元素及其綁定的數據上下文。  
  
## <a name="binding-expression-usage"></a>繫結式用法  
  
```xaml  
<object property="{Binding}" .../>  
-or-  
<object property="{Binding  bindProp1=value1[, bindPropN=valueN]*}" ...  
/>  
-or-  
<object property="{Binding path}" .../>  
-or  
<object property="{Binding path[, bindPropN=valueN]*}" .../>  
```  
  
## <a name="syntax-notes"></a>語法註解  
 在這些語法中,`[]``*`和 不是文本。 它們是表示法的一部分,用於指示可以使用零個或多個*綁定Prop*`=`*值*對,並在它們之間`,`和前面的*綁定Prop*`=`*值*對之間具有分隔符。  
  
 可以使用<xref:System.Windows.Data.Binding>物件元素的屬性設置"可以使用綁定擴展設置的綁定屬性"部分中列出的任何屬性。 但是,這不是真正的標記擴展用法<xref:System.Windows.Data.Binding>,它只是設置<xref:System.Windows.Data.Binding>CLR 類屬性的屬性的一般 XAML 處理。 換句話說`<Binding`*,bindProp1* `="` `"]*/>` <xref:System.Windows.Data.Binding> `Binding` `"[` *valuepropNvalueN*`="`*valueN*值N是物件元素使用屬性的等效語法,而不是表達式*value1*用法。 要瞭解的 XAML 屬性<xref:System.Windows.Data.Binding>使用方式 ,請參閱 .NET<xref:System.Windows.Data.Binding>框架類庫中的相關 屬性的「XAML 屬性用法」 部分。  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`bindProp1, bindPropN`|要設置的<xref:System.Windows.Data.Binding><xref:System.Windows.Data.BindingBase>或 屬性的名稱。 並非所有<xref:System.Windows.Data.Binding>屬性都可以`Binding`使用 擴展設置,並且某些屬性僅在運算式中僅透過使用`Binding`進一步的嵌套標記擴展進行設置。 請參閱"可以使用綁定擴展設置的綁定屬性" 部分。|  
|`value1, valueN`|設定屬性使用的值。 屬性值的處理最終特定於要設置的特定<xref:System.Windows.Data.Binding>屬性的類型和邏輯。|  
|`path`|設定隱式<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>屬性的路徑字串。 另請參考[屬性路徑 XAML 語法](propertypath-xaml-syntax.md)。|  
  
## <a name="unqualified-binding"></a>不合格 [綁定]  
 "`{Binding}`繫結式用法"中顯示的用法建立具有<xref:System.Windows.Data.Binding>預設值的物件,<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>其中包括的`null`初始值。 這在許多方案中仍然很有用,因為創建的<xref:System.Windows.Data.Binding>可能依賴於關鍵數據綁定屬性,例如<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType><xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType>並在運行時數據上下文中設置。 關於資料內容的詳細資訊,請參考[資料型結 。](../../../desktop-wpf/data/data-binding-overview.md)  
  
## <a name="implicit-path"></a>隱含路徑  
 標記`Binding`延伸用<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>作 概念性的"默認屬性",其中`Path=`不需要出現在表達式中。 如果`Binding`指定具有隱式路徑的表達式,則隱式路徑必須首先出現在表達式中,在任何`bindProp`=`value`其他 由<xref:System.Windows.Data.Binding>名稱指定 該屬性的對之前。 例如: `{Binding PathString}``PathString`, 其中的字串被計算為 標記擴展<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType><xref:System.Windows.Data.Binding>用法 創建的 中的值。 例如,可以在逗號分隔符之後附加隱式路徑和其他命名屬性。 `{Binding LastName, Mode=TwoWay}`  
  
## <a name="binding-properties-that-can-be-set-with-the-binding-extension"></a>可以使用繫結延伸設定的結合屬性  
 本主題中顯示的語法使用泛型`bindProp`=`value`近似值,因為有許多讀/寫屬性<xref:System.Windows.Data.BindingBase>,<xref:System.Windows.Data.Binding>`Binding`或者 可以通過 標記擴展/表達式語法進行設置。 它們可以按任何順序設定,但隱式<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>。 (您確實可以選擇顯式指定`Path=`,在這種情況下,可以按任意順序設置它)。 基本上,您可以使用用逗號分隔的`bindProp`=`value`對設置下面清單中的零個或多個屬性。  
  
 其中一些屬性值要求物件類型不支援從 XAML 中的文本語法轉換本機類型,因此需要標記擴展才能設置為屬性值。 有關詳細資訊,請查看 .NET 框架類庫中的 XAML 屬性使用部分,瞭解每個屬性;用於 XAML 屬性語法(無論是否具有進一步標記擴展用法)的字串與表達`Binding`式 中指定的值基本相同,但表達`bindProp`=`value``Binding`式中 每個值不放置引號除外。  
  
- <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>:標識可能的綁定組的字串。 這是一個相對先進的綁定概念;請參閱<xref:System.Windows.Data.BindingBase.BindingGroupName%2A>參考 頁。  
  
- <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>: 布林,可以`true``false`是或 。 預設值為 `false`。  
  
- <xref:System.Windows.Data.Binding.Converter%2A>`bindProp`=:`value`可以設定為表示式的字串,但這樣做需要值的物件參考,如[靜態資源標記延伸](staticresource-markup-extension.md)。 在這種情況下,值是自定義轉換器類的實例。  
  
- <xref:System.Windows.Data.Binding.ConverterCulture%2A>:在表示式中設置為基於標準的標識符;請參閱 的<xref:System.Windows.Data.Binding.ConverterCulture%2A>參考 主題。  
  
- <xref:System.Windows.Data.Binding.ConverterParameter%2A>: 可以設定`bindProp`=`value`為 表示式中的字串,但這取決於傳遞的參數的類型。 如果傳遞值的引用類型,則此用法需要物件引用,如嵌套[的靜態資源標記延伸](staticresource-markup-extension.md)。  
  
- <xref:System.Windows.Data.Binding.ElementName%2A>: 相互<xref:System.Windows.Data.Binding.RelativeSource%2A>排斥<xref:System.Windows.Data.Binding.Source%2A>與 和 ;每個綁定屬性都表示特定的綁定方法。 請參考[資料連結的概述](../../../desktop-wpf/data/data-binding-overview.md)。  
  
- <xref:System.Windows.Data.BindingBase.FallbackValue%2A>: 可以設定`bindProp`=`value`為 表示式中的字串,但這取決於要傳遞的值的類型。 如果傳遞參考類型,則需要物件引用,如嵌套[的靜態資源標記延伸](staticresource-markup-extension.md)。  
  
- <xref:System.Windows.Data.Binding.IsAsync%2A>: 布林,可以`true``false`是或 。 預設值為 `false`。  
  
- <xref:System.Windows.Data.Binding.Mode%2A>:*值*是枚<xref:System.Windows.Data.BindingMode>舉中的 常量名稱。 例如： `{Binding Mode=OneWay}` 。  
  
- <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>: 布林,可以`true``false`是或 。 預設值為 `false`。  
  
- <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>: 布林,可以`true``false`是或 。 預設值為 `false`。  
  
- <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>: 布林,可以`true``false`是或 。 預設值為 `false`。  
  
- <xref:System.Windows.Data.Binding.Path%2A>描述資料物件或常規物件模型的路徑的字串。 該格式提供了幾個不同的約定來遍歷本主題中無法充分描述的物件模型。 請參考[屬性路徑 XAML 語法](propertypath-xaml-syntax.md)。  
  
- <xref:System.Windows.Data.Binding.RelativeSource%2A>: 與<xref:System.Windows.Data.Binding.ElementName%2A><xref:System.Windows.Data.Binding.Source%2A>和 的相互排斥;每個綁定屬性都表示特定的綁定方法。 請參考[資料連結的概述](../../../desktop-wpf/data/data-binding-overview.md)。 需要嵌套[相對源標記擴展](relativesource-markupextension.md)用法來指定值。  
  
- <xref:System.Windows.Data.Binding.Source%2A>: 相互<xref:System.Windows.Data.Binding.RelativeSource%2A>排斥<xref:System.Windows.Data.Binding.ElementName%2A>與 和 ;每個綁定屬性都表示特定的綁定方法。 請參考[資料連結的概述](../../../desktop-wpf/data/data-binding-overview.md)。 需要嵌入法,通常是引言鍵控制的字典中的物件資料來源的[靜態資源標記延伸](staticresource-markup-extension.md)。  
  
- <xref:System.Windows.Data.BindingBase.StringFormat%2A>:描述綁定數據的字串格式約定的字串。 這是一個相對先進的綁定概念;請參閱<xref:System.Windows.Data.BindingBase.StringFormat%2A>參考 頁。  
  
- <xref:System.Windows.Data.BindingBase.TargetNullValue%2A>: 可以設定`bindProp`=`value`為 表示式中的字串,但這取決於傳遞的參數的類型。 如果傳遞值的引用類型,則需要物件引用(如嵌套[靜態資源標記擴展](staticresource-markup-extension.md))。  
  
- <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>:*值*是枚<xref:System.Windows.Data.UpdateSourceTrigger>舉中的 常量名稱。 例如： `{Binding UpdateSourceTrigger=LostFocus}` 。 特定控制項可能對此綁定屬性具有不同的預設值。 請參閱＜<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>＞。  
  
- <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>: 布林,可以`true``false`是或 。 預設值為 `false`。 請參閱＜備註＞。  
  
- <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>: 布林,可以`true``false`是或 。 預設值為 `false`。 請參閱＜備註＞。  
  
- <xref:System.Windows.Data.Binding.XPath%2A>:描述進入 XML 資料來源 XMLDOM 的路徑的字串。 請參考[XMLData 提供程式與 XPath 查詢連線到 XML 資料](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)。  
  
 以下是無法使用<xref:System.Windows.Data.Binding>`Binding`標記擴展`{Binding}`/ 運算式表單設定的屬性。  
  
- <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>:此屬性需要對回調實現的引用。 無法在 XAML 語法中引用事件處理程式以外的回調/ 方法。  
  
- <xref:System.Windows.Data.Binding.ValidationRules%2A>:屬性採用<xref:System.Windows.Controls.ValidationRule>物件的泛型集合。 這可以表示為<xref:System.Windows.Data.Binding>物件元素中的屬性元素,但沒有現成的屬性解析技術可`Binding`用於 運算式中的使用。 請參考主題<xref:System.Windows.Data.Binding.ValidationRules%2A>。  
  
- <xref:System.Windows.Data.Binding.XmlNamespaceManager%2A>  
  
## <a name="remarks"></a>備註  
  
> [!IMPORTANT]
> 在依賴項屬性優先順序方面,`Binding`運算式等效於本地設置的值。 如果為以前具有`Binding`表示式的屬性設定值,則將完全刪除`Binding`。 如需詳細資訊，請參閱[相依性屬性值優先順序](dependency-property-value-precedence.md)。  
  
 本主題未介紹在基本級別描述數據綁定。 請參考[資料連結的概述](../../../desktop-wpf/data/data-binding-overview.md)。  
  
> [!NOTE]
> <xref:System.Windows.Data.MultiBinding>不支援<xref:System.Windows.Data.PriorityBinding>延伸語[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]法 。 您將使用屬性元素。 請參閱<xref:System.Windows.Data.PriorityBinding><xref:System.Windows.Data.MultiBinding>和 的參考主題。  
  
 XAML 的布爾值不區分大小寫。 例如,您可以指定`{Binding NotifyOnValidationError=true}``{Binding NotifyOnValidationError=True}`或 。  
  
 涉及數據`Binding`驗證的綁定通常由顯式元素`{Binding ...}`而不是 表達式指定,<xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>並且<xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>設置 或運算式中並不常見。 這是因為無法輕鬆在表達式表單<xref:System.Windows.Data.Binding.ValidationRules%2A>中設置配套屬性。 有關詳細資訊,請參閱[實現綁定驗證](../data/how-to-implement-binding-validation.md)。  
  
 `Binding` 是一種標記延伸。 標記延伸通常在需要轉義屬性值為文本值或處理程式名稱以外的時實現,並且該要求比某些類型或屬性上屬性化的類型轉換器更全域。 XAML 中的所有標記擴展在其屬性語法中`{``}`使用和字元,這是 XAML 處理器識別標記擴展必須處理字串內容的約定。 如需詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。  
  
 `Binding`是一個非典型的標記擴展,因為實現<xref:System.Windows.Data.Binding>WPF XAML 實現擴充功能的類還實現了與 XAML 無關的其他幾種方法和屬性。 其他成員旨在創建<xref:System.Windows.Data.Binding>一個功能更通用、自包含的類,除了充當 XAML 標記擴展之外,還可以解決許多數據綁定方案。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Data.Binding>
- [資料繫結概述](../../../desktop-wpf/data/data-binding-overview.md)
- [XAML 概觀 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)
