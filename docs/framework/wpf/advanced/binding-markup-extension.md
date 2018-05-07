---
title: 繫結標記延伸
ms.date: 03/30/2017
f1_keywords:
- Binding
helpviewer_keywords:
- Binding markup extensions [WPF]
- XAML [WPF], Binding markup extension
ms.assetid: 83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63
ms.openlocfilehash: 8fc860f52f8fde2aed3cae224c05bbcf08b864d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="binding-markup-extension"></a>繫結標記延伸
延後建立中繼運算式物件及解譯資料內容套用至項目，且在執行階段與其繫結的繫結的資料值的屬性值。  
  
## <a name="binding-expression-usage"></a>繫結運算式的使用方式  
  
```  
<object property="{Binding}" .../>  
-or-  
<object property="{Binding  bindProp1=value1[, bindPropN=valueN]*}" ...  
/>  
-or-  
<object property="{Binding path}" .../>  
-or  
<object property="{Binding path[, bindPropN=valueN]*}" .../>  
```  
  
## <a name="syntax-notes"></a>語法資訊  
 在這些語法，`[]`和`*`不是常值。 它們屬於標記法來表示的零或多個*bindProp*`=`*值*可用組，與`,`之間以及上述分隔符號*bindProp* `=`*值*組。  
  
 任何 < 繫結屬性，可以是設定與繫結延伸模組 > 一節中所列的屬性可以改為設定使用屬性的<xref:System.Windows.Data.Binding>物件項目。 不過，不是真正的標記延伸使用方式<xref:System.Windows.Data.Binding>，它是只一般 XAML 處理的設定屬性的 clr 屬性<xref:System.Windows.Data.Binding>類別。 換句話說， `<Binding` *bindProp1*`="`*value1* `"[` *bindPropN*`="`*看值*`"]*/>`是相等的屬性語法<xref:System.Windows.Data.Binding>物件項目使用方式，而不是`Binding`運算式使用。 若要了解屬性的 XAML 用法的特定內容<xref:System.Windows.Data.Binding>，請參閱相關的屬性"XAML 屬性使用方式 」 一節<xref:System.Windows.Data.Binding>.NET Framework 類別庫中。  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`bindProp1, bindPropN`|名稱<xref:System.Windows.Data.Binding>或<xref:System.Windows.Data.BindingBase>屬性來設定。 並非所有<xref:System.Windows.Data.Binding>屬性可以設定與`Binding`延伸模組和某些屬性可以設定內`Binding`運算式只能藉由進一步使用巢狀標記延伸。 請參閱 < 繫結屬性，可以是設定與繫結延伸模組 > 一節。|  
|`value1, valueN`|若要設定屬性值。 屬性值的處理是最終特有的型別和特定的邏輯<xref:System.Windows.Data.Binding>要設定屬性。|  
|`path`|設定隱含的路徑字串<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>屬性。 另請參閱[PropertyPath XAML 語法](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md)。|  
  
## <a name="unqualified-binding"></a>不合格的 {繫結}  
 `{Binding}` 「 繫結的運算式用法 」 所示的使用方式建立<xref:System.Windows.Data.Binding>物件使用預設值，包含初始<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>的`null`。 這仍適用於許多案例中，因為建立<xref:System.Windows.Data.Binding>可能依賴索引鍵的資料繫結屬性例如<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>和<xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType>所設定的執行階段資料內容。 如需有關資料內容的概念的詳細資訊，請參閱[資料繫結](../../../../docs/framework/wpf/data/data-binding-wpf.md)。  
  
## <a name="implicit-path"></a>隱含的路徑  
 `Binding`標記延伸模組會使用<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>概念為 「 預設屬性 」，其中`Path=`不需要出現在運算式中。 如果您指定`Binding`運算式具有隱含的路徑，隱含的路徑必須最先出現在運算式中，在任何其他之前`bindProp` = `value`組 where<xref:System.Windows.Data.Binding>依名稱指定屬性。 例如： `{Binding PathString}`，其中`PathString`是評估為值的字串<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>中<xref:System.Windows.Data.Binding>標記延伸使用方式所建立。 您可以將具有其他具名屬性的隱含路徑，例如附加的逗號分隔符號之後`{Binding LastName, Mode=TwoWay}`。  
  
## <a name="binding-properties-that-can-be-set-with-the-binding-extension"></a>您可以將繫結延伸模組的繫結屬性  
 本主題中所顯示的語法會使用泛型`bindProp` = `value`近似值，因為有許多的讀取/寫入屬性的<xref:System.Windows.Data.BindingBase>或<xref:System.Windows.Data.Binding>可以透過設定`Binding`標記延伸 /運算式語法。 您可以依任何順序，除了隱含設定<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>。 (您也可以選擇明確指定`Path=`，它在此情況下設定任何順序)。 基本上，您可以設定為零或多個屬性，以下清單中使用`bindProp` = `value`組以逗號分隔。  
  
 這些屬性值的數個需要不支援在 XAML 中，文字語法從原生類型轉換，因此需要為了設定做為屬性值的標記延伸的物件類型。 檢查 XAML 屬性使用方式區段，以在.NET Framework 類別庫，針對每個屬性，如需詳細資訊。XAML 屬性語法，與使用字串，或沒有進一步的標記延伸使用方式基本上就是您在中指定的值相同`Binding`具有未放置引號括住每個例外狀況的運算式， `bindProp` =`value`中`Binding`運算式。  
  
-   <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>： 識別可能的繫結群組的字串。 這是相對較進階的繫結的概念。請參閱 < 參考頁面的<xref:System.Windows.Data.BindingBase.BindingGroupName%2A>。  
  
-   <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>： 布林值，可以是`true`或`false`。 預設值為 `false`。  
  
-   <xref:System.Windows.Data.Binding.Converter%2A>： 可設定為`bindProp` = `value`字串在運算式中，但若要這樣做需要物件參考的值，例如[StaticResource 標記延伸](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)。 值在此情況下會為自訂轉換子類別的執行個體。  
  
-   <xref:System.Windows.Data.Binding.ConverterCulture%2A>： 可設定為標準為基礎的識別項; 在運算式中請參閱參考主題<xref:System.Windows.Data.Binding.ConverterCulture%2A>。  
  
-   <xref:System.Windows.Data.Binding.ConverterParameter%2A>： 可設定為`bindProp` = `value`字串運算式，但這是取決於所傳遞的參數類型。 這種使用方式傳遞參考類型的值，如果需要的物件參考，例如巢狀[StaticResource 標記延伸](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)。  
  
-   <xref:System.Windows.Data.Binding.ElementName%2A>： 相對於互斥<xref:System.Windows.Data.Binding.RelativeSource%2A>和<xref:System.Windows.Data.Binding.Source%2A>; 每個這些繫結屬性表示的特定繫結方法。 請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。  
  
-   <xref:System.Windows.Data.BindingBase.FallbackValue%2A>： 可設定為`bindProp` = `value`字串運算式，但這會相依於所傳遞的值的類型。 如果傳遞參考類型，需要物件參考，例如巢狀[StaticResource 標記延伸](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)。  
  
-   <xref:System.Windows.Data.Binding.IsAsync%2A>： 布林值，可以是`true`或`false`。 預設值為 `false`。  
  
-   <xref:System.Windows.Data.Binding.Mode%2A>:*值*是中的常數名稱<xref:System.Windows.Data.BindingMode>列舉型別。 例如，`{Binding Mode=OneWay}`。  
  
-   <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>： 布林值，可以是`true`或`false`。 預設值為 `false`。  
  
-   <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>： 布林值，可以是`true`或`false`。 預設值為 `false`。  
  
-   <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>： 布林值，可以是`true`或`false`。 預設值為 `false`。  
  
-   <xref:System.Windows.Data.Binding.Path%2A>： 為資料物件或一種一般的物件模型描述路徑的字串。 格式提供數個不同的慣例周遊無法充分說明本主題中的物件模型。 請參閱[PropertyPath XAML 語法](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md)。  
  
-   <xref:System.Windows.Data.Binding.RelativeSource%2A>： 相對於與互斥<xref:System.Windows.Data.Binding.ElementName%2A>和<xref:System.Windows.Data.Binding.Source%2A>; 每個這些繫結屬性表示的特定繫結方法。 請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。 需要的巢狀[RelativeSource MarkupExtension](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md)使用量對指定的值。  
  
-   <xref:System.Windows.Data.Binding.Source%2A>： 相對於互斥<xref:System.Windows.Data.Binding.RelativeSource%2A>和<xref:System.Windows.Data.Binding.ElementName%2A>; 每個這些繫結屬性表示的特定繫結方法。 請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。 通常需要的巢狀擴充功能使用方式， [StaticResource 標記延伸](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)從索引鍵的資源字典的物件資料來源參考。  
  
-   <xref:System.Windows.Data.BindingBase.StringFormat%2A>： 描述繫結資料的字串格式慣例的字串。 這是相對較進階的繫結的概念。請參閱 < 參考頁面的<xref:System.Windows.Data.BindingBase.StringFormat%2A>。  
  
-   <xref:System.Windows.Data.BindingBase.TargetNullValue%2A>： 可設定為`bindProp` = `value`字串運算式，但這是取決於所傳遞的參數類型。 如果傳遞參考類型的值，需要物件參考，例如巢狀[StaticResource 標記延伸](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)。  
  
-   <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>:*值*是中的常數名稱<xref:System.Windows.Data.UpdateSourceTrigger>列舉型別。 例如，`{Binding UpdateSourceTrigger=LostFocus}`。 特定控制項可能會有不同的預設值，這個繫結屬性。 請參閱 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>。  
  
-   <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>： 布林值，可以是`true`或`false`。 預設值為 `false`。 請參閱＜備註＞。  
  
-   <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>： 布林值，可以是`true`或`false`。 預設值為 `false`。 請參閱＜備註＞。  
  
-   <xref:System.Windows.Data.Binding.XPath%2A>： 描述 XML 資料來源的 XMLDOM 路徑的字串。 請參閱[繫結至使用 XMLDataProvider 和 XPath 查詢 XML 資料](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)。  
  
 以下是屬性的<xref:System.Windows.Data.Binding>，無法使用設定`Binding`標記延伸 /`{Binding}`運算式形式。  
  
-   <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>： 這個屬性必須要有回呼實作的參考。 回呼/方法以外的事件處理常式不能使用 XAML 語法參考。  
  
-   <xref:System.Windows.Data.Binding.ValidationRules%2A>： 此屬性會採用的泛型集合<xref:System.Windows.Controls.ValidationRule>物件。 這可能表示為屬性項目中<xref:System.Windows.Data.Binding>物件項目，但已在使用沒有立即可用屬性剖析技術`Binding`運算式。 請參閱參考主題<xref:System.Windows.Data.Binding.ValidationRules%2A>。  
  
-   <xref:System.Windows.Data.Binding.XmlNamespaceManager%2A>  
  
## <a name="remarks"></a>備註  
  
> [!IMPORTANT]
>  相依性屬性在優先順序方面，`Binding`運算式就相當於本機設定值。 如果您設定如先前所擁有的屬性為區域數值`Binding`運算式`Binding`完全移除。 如需詳細資訊，請參閱[相依性屬性值優先順序](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)。  
  
 未涵蓋在本主題描述在基本層級的資料繫結。 請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。  
  
> [!NOTE]
>  <xref:System.Windows.Data.MultiBinding> 和<xref:System.Windows.Data.PriorityBinding>不支援[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]延伸語法。 相反地，您會使用屬性項目。 請參閱參考主題<xref:System.Windows.Data.MultiBinding>和<xref:System.Windows.Data.PriorityBinding>。  
  
 針對 XAML 的布林值為不區分大小寫。 例如，您可以指定 `{Binding NotifyOnValidationError=true}`或`{Binding NotifyOnValidationError=True}`。  
  
 通常由明確指定繫結牽涉到資料驗證`Binding`項目而`{Binding ...}`運算式及設定<xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>或<xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>在運算式中是不常見。 這是因為附屬屬性<xref:System.Windows.Data.Binding.ValidationRules%2A>無法輕易地設定運算式格式。 如需詳細資訊，請參閱[實作繫結驗證](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)。  
  
 `Binding` 是一種標記延伸。 要逸出常值或處理常式以外是名稱、 屬性值的需求，而且是比特定類型或屬性上使用屬性的類型轉換器更通用的需求時，通常會實作標記延伸。 所有標記延伸在 XAML 使用`{`和`}`字元在其屬性語法中，也就是，XAML 處理器會辨識的標記延伸必須處理的字串內容的慣例。 如需詳細資訊，請參閱[標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。  
  
 `Binding` 是中的非典型的標記延伸<xref:System.Windows.Data.Binding>實作 WPF 的 XAML 實作的擴充功能的類別也會實作數個其他的方法和不與 XAML 相關的屬性。 其他成員主要要讓<xref:System.Windows.Data.Binding>更具彈性且獨立的類別可以處理許多的資料繫結案例，除了以 XAML 標記延伸的方式運作。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Data.Binding>  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
