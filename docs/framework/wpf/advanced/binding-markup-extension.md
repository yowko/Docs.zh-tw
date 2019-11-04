---
title: 繫結標記延伸
ms.date: 03/30/2017
f1_keywords:
- Binding
helpviewer_keywords:
- Binding markup extensions [WPF]
- XAML [WPF], Binding markup extension
ms.assetid: 83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63
ms.openlocfilehash: d0a437e756da16db978d8074c4355fd83d211b67
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73453608"
---
# <a name="binding-markup-extension"></a>繫結標記延伸
將屬性值延遲為數據系結的值，建立中繼運算式物件，並在執行時間解讀套用至元素及其系結的資料內容。  
  
## <a name="binding-expression-usage"></a>系結運算式使用方式  
  
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
  
## <a name="syntax-notes"></a>語法注意事項  
 在這些語法中，`[]` 和 `*` 不是常值。 它們屬於標記法的一部分，表示可以使用零或多個*bindProp*`=`*值*組，並在兩者之間加上 `,` 分隔符號和前面的*bindProp*`=`*值*配對。  
  
 「可使用系結延伸模組設定的系結屬性」區段中所列的任何屬性，都可以改用 <xref:System.Windows.Data.Binding> 物件專案的屬性來設定。 不過，這不是真正 <xref:System.Windows.Data.Binding>的標記延伸使用方式，只是設定 CLR <xref:System.Windows.Data.Binding> 類別屬性之屬性的一般 XAML 處理。 換句話說，`<Binding` *bindProp1*`="`*value1*`"[` *bindPropN*`="`*值*`"]*/>` 是 <xref:System.Windows.Data.Binding> 物件專案使用方式（而非 `Binding` 運算式使用方式）之屬性的對等語法。 若要瞭解 <xref:System.Windows.Data.Binding>的特定屬性之 XAML 屬性用法，請參閱 .NET Framework 類別庫中 <xref:System.Windows.Data.Binding> 相關屬性的「XAML 屬性使用方式」一節。  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`bindProp1, bindPropN`|要設定的 <xref:System.Windows.Data.Binding> 或 <xref:System.Windows.Data.BindingBase> 屬性的名稱。 並非所有 <xref:System.Windows.Data.Binding> 屬性都可以使用 `Binding` 延伸模組來設定，而且有些屬性只能使用進一步的嵌套標記延伸，在 `Binding` 運算式內設定。 請參閱「可使用系結延伸模組設定的系結屬性」一節。|  
|`value1, valueN`|要將屬性設定為的值。 屬性值的處理最終是特定于所設定之特定 <xref:System.Windows.Data.Binding> 屬性的型別和邏輯。|  
|`path`|設定隱含 <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> 屬性的路徑字串。 另請參閱[PROPERTYPATH XAML 語法](propertypath-xaml-syntax.md)。|  
  
## <a name="unqualified-binding"></a>不合格的 {Binding}  
 「系結運算式使用方式」中所顯示的 `{Binding}` 用法，會建立具有預設值的 <xref:System.Windows.Data.Binding> 物件，其中包含 `null`的初始 <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>。 這在許多情況下仍然很有用，因為建立的 <xref:System.Windows.Data.Binding> 可能依賴索引鍵資料系結屬性，例如在執行時間資料內容中設定的 <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> 和 <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType>。 如需資料內容概念的詳細資訊，請參閱[資料](../data/data-binding-wpf.md)系結。  
  
## <a name="implicit-path"></a>隱含路徑  
 `Binding` 標記延伸使用 <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> 做為概念「預設屬性」，其中 `Path=` 不需要出現在運算式中。 如果您指定具有隱含路徑的 `Binding` 運算式，則隱含路徑必須先出現在運算式中，在任何其他 `bindProp`=`value` 組之前，其中 <xref:System.Windows.Data.Binding> 屬性是以名稱指定。 例如： `{Binding PathString}`，其中 `PathString` 是在標記延伸使用方式所建立的 <xref:System.Windows.Data.Binding> 中，評估為 <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> 值的字串。 您可以在逗號分隔符號後面附加具有其他命名屬性的隱含路徑，例如 `{Binding LastName, Mode=TwoWay}`。  
  
## <a name="binding-properties-that-can-be-set-with-the-binding-extension"></a>可以使用系結延伸模組設定的系結屬性  
 本主題所顯示的語法會使用泛型 `bindProp`=`value` 近似值，因為有許多 <xref:System.Windows.Data.BindingBase> 或 <xref:System.Windows.Data.Binding> 的讀取/寫入屬性可以透過 `Binding` 標記延伸/運算式語法來設定。 它們可以依任何順序設定，但隱含 <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>除外。 （您可以選擇明確指定 `Path=`，在此情況下，可以依任何順序設定）。 基本上，您可以使用 `bindProp`=`value` 組（以逗號分隔），在下列清單中設定零個或多個屬性。  
  
 其中有幾個屬性值需要的物件類型不支援 XAML 中文字語法的原生類型轉換，因此需要標記延伸才能設定為屬性值。 如需詳細資訊，請查看每個屬性的 .NET Framework 類別庫中的 XAML 屬性使用方式一節。您用於具有或不含進一步標記延伸使用方式之 XAML 屬性語法的字串，基本上與您在 `Binding` 運算式中指定的值相同，唯一的例外是您不會將引號括在每個 `bindProp`=`value``Binding` 運算式。  
  
- <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>：識別可能的系結群組的字串。 這是相當先進的系結概念;請參閱 <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>的參考頁面。  
  
- <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>：布林值，可以是 `true` 或 `false`。 預設為 `false`。  
  
- <xref:System.Windows.Data.Binding.Converter%2A>：可以設定為運算式中的 `bindProp`=`value` 字串，但若要這麼做，則需要值的物件參考，例如[StaticResource 標記延伸](staticresource-markup-extension.md)。 此案例中的值是自訂轉換器類別的實例。  
  
- <xref:System.Windows.Data.Binding.ConverterCulture%2A>：可在運算式中設定為以標準為基礎的識別碼;如需 <xref:System.Windows.Data.Binding.ConverterCulture%2A>，請參閱參考主題。  
  
- <xref:System.Windows.Data.Binding.ConverterParameter%2A>：可以設定為運算式中的 `bindProp`=`value` 字串，但這取決於所傳遞的參數類型。 如果傳遞值的參考型別，則此使用方式需要物件參考，例如嵌套的[StaticResource 標記延伸](staticresource-markup-extension.md)。  
  
- <xref:System.Windows.Data.Binding.ElementName%2A>：互斥與 <xref:System.Windows.Data.Binding.RelativeSource%2A> 和 <xref:System.Windows.Data.Binding.Source%2A>;這些系結屬性每一個都代表特定的系結方法。 請參閱資料系結[總覽](../data/data-binding-overview.md)。  
  
- <xref:System.Windows.Data.BindingBase.FallbackValue%2A>：可以設定為運算式中的 `bindProp`=`value` 字串，但這取決於所傳遞值的類型。 如果傳遞參考型別，則需要物件參考，例如 nested [StaticResource 標記延伸](staticresource-markup-extension.md)。  
  
- <xref:System.Windows.Data.Binding.IsAsync%2A>：布林值，可以是 `true` 或 `false`。 預設為 `false`。  
  
- <xref:System.Windows.Data.Binding.Mode%2A>：*值*是來自 <xref:System.Windows.Data.BindingMode> 列舉的常數名稱。 例如，`{Binding Mode=OneWay}`。  
  
- <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>：布林值，可以是 `true` 或 `false`。 預設為 `false`。  
  
- <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>：布林值，可以是 `true` 或 `false`。 預設為 `false`。  
  
- <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>：布林值，可以是 `true` 或 `false`。 預設為 `false`。  
  
- <xref:System.Windows.Data.Binding.Path%2A>：描述資料物件或一般物件模型之路徑的字串。 格式提供了數種不同的慣例，可用於遍歷無法在本主題中適當描述的物件模型。 請參閱[PROPERTYPATH XAML 語法](propertypath-xaml-syntax.md)。  
  
- <xref:System.Windows.Data.Binding.RelativeSource%2A>：與 <xref:System.Windows.Data.Binding.ElementName%2A> 和 <xref:System.Windows.Data.Binding.Source%2A>互斥（& x）;這些系結屬性每一個都代表特定的系結方法。 請參閱資料系結[總覽](../data/data-binding-overview.md)。 需要使用 nested [RelativeSource MarkupExtension](relativesource-markupextension.md)來指定值。  
  
- <xref:System.Windows.Data.Binding.Source%2A>：互斥與 <xref:System.Windows.Data.Binding.RelativeSource%2A> 和 <xref:System.Windows.Data.Binding.ElementName%2A>;這些系結屬性每一個都代表特定的系結方法。 請參閱資料系結[總覽](../data/data-binding-overview.md)。 需要使用嵌套的擴充功能，通常是[StaticResource 標記延伸](staticresource-markup-extension.md)，它會參考索引資源字典中的物件資料來源。  
  
- <xref:System.Windows.Data.BindingBase.StringFormat%2A>：描述系結資料之字串格式慣例的字串。 這是相當先進的系結概念;請參閱 <xref:System.Windows.Data.BindingBase.StringFormat%2A>的參考頁面。  
  
- <xref:System.Windows.Data.BindingBase.TargetNullValue%2A>：可以設定為運算式中的 `bindProp`=`value` 字串，但這取決於所傳遞的參數類型。 如果傳遞值的參考型別，則需要物件參考，例如嵌套的[StaticResource 標記延伸](staticresource-markup-extension.md)。  
  
- <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>：*值*是來自 <xref:System.Windows.Data.UpdateSourceTrigger> 列舉的常數名稱。 例如，`{Binding UpdateSourceTrigger=LostFocus}`。 特定控制項可能會有此系結屬性的不同預設值。 請參閱<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
- <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>：布林值，可以是 `true` 或 `false`。 預設為 `false`。 請參閱＜備註＞。  
  
- <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>：布林值，可以是 `true` 或 `false`。 預設為 `false`。 請參閱＜備註＞。  
  
- <xref:System.Windows.Data.Binding.XPath%2A>：描述 XML 資料來源之 XMLDOM 路徑的字串。 請參閱[使用 XMLDataProvider 和 XPath 查詢系結至 XML 資料](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)。  
  
 以下是無法使用 `Binding` 標記延伸/`{Binding}` 運算式形式設定的 <xref:System.Windows.Data.Binding> 屬性。  
  
- <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>：此屬性需要回呼執行的參考。 不能在 XAML 語法中參考事件處理常式以外的回呼/方法。  
  
- <xref:System.Windows.Data.Binding.ValidationRules%2A>：屬性會接受 <xref:System.Windows.Controls.ValidationRule> 物件的泛型集合。 這可能會表示為 <xref:System.Windows.Data.Binding> 物件專案中的 property 專案，但在 `Binding` 運算式中沒有任何可供使用的屬性剖析技術。 如需 <xref:System.Windows.Data.Binding.ValidationRules%2A>，請參閱參考主題。  
  
- <xref:System.Windows.Data.Binding.XmlNamespaceManager%2A>  
  
## <a name="remarks"></a>備註  
  
> [!IMPORTANT]
> 就相依性屬性優先順序而言，`Binding` 運算式就相當於本機設定的值。 如果您為先前有 `Binding` 運算式的屬性設定本機值，`Binding` 就會完全移除。 如需詳細資訊，請參閱[相依性屬性值優先順序](dependency-property-value-precedence.md)。  
  
 本主題未涵蓋描述基本層級的資料系結。 請參閱資料系結[總覽](../data/data-binding-overview.md)。  
  
> [!NOTE]
> <xref:System.Windows.Data.MultiBinding> 和 <xref:System.Windows.Data.PriorityBinding> 不支援 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 擴充功能語法。 您會改為使用屬性元素。 請參閱 <xref:System.Windows.Data.MultiBinding> 和 <xref:System.Windows.Data.PriorityBinding>的參考主題。  
  
 XAML 的布林值不區分大小寫。 例如，您可以指定 `{Binding NotifyOnValidationError=true}` 或 `{Binding NotifyOnValidationError=True}`。  
  
 牽涉到資料驗證的系結通常是由明確的 `Binding` 專案指定，而非 `{Binding ...}` 運算式，而且在運算式中設定 <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> 或 <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> 並不常見。 這是因為隨附的屬性 <xref:System.Windows.Data.Binding.ValidationRules%2A> 無法在運算式表單中輕鬆設定。 如需詳細資訊，請參閱執行系結[驗證](../data/how-to-implement-binding-validation.md)。  
  
 `Binding` 是一種標記延伸。 標記延伸通常會在需要將屬性值換成常值或處理常式名稱以外，而且需求比特定類型或屬性上的類型轉換器更通用。 XAML 中的所有標記延伸都會使用其屬性語法中的 `{` 和 `}` 字元，這是 XAML 處理器辨識標記延伸必須處理字串內容的慣例。 如需詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。  
  
 `Binding` 是一種典型的標記延伸模組，其中，為 WPF 的 XAML 執行擴充功能的 <xref:System.Windows.Data.Binding> 類別，也會執行與 XAML 無關的數個其他方法和屬性。 其他成員的目的是要讓 <xref:System.Windows.Data.Binding> 更多用途和獨立的類別，除了當做 XAML 標記延伸之外，還可以處理許多資料系結案例。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Data.Binding>
- [資料繫結概觀](../data/data-binding-overview.md)
- [XAML 概觀 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)
