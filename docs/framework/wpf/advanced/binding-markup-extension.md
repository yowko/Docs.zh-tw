---
title: 繫結標記延伸
ms.date: 03/30/2017
f1_keywords:
- Binding
helpviewer_keywords:
- Binding markup extensions [WPF]
- XAML [WPF], Binding markup extension
ms.assetid: 83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63
ms.openlocfilehash: 960bc953345e3f6ed632b7a136b626978c8a9bce
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379181"
---
# <a name="binding-markup-extension"></a>繫結標記延伸
延遲是資料繫結的值，建立中繼運算式物件，並解譯會套用至項目和其在執行階段的繫結的資料內容的屬性值。  
  
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
 這些語法，在`[]`和`*`不是常值。 它們屬於的標記法來表示零個或多個*bindProp*`=`*值*可用組，使用`,`上述它們之間的分隔符號*bindProp* `=`*值*組。  
  
 任何 「 繫結屬性，可以是設定與繫結延伸模組 」 一節中所列的屬性可以改為設定使用屬性的<xref:System.Windows.Data.Binding>物件項目。 不過，這並非真正的標記延伸使用方式<xref:System.Windows.Data.Binding>，它會設定屬性的 clr 屬性的只是一般 XAML 處理<xref:System.Windows.Data.Binding>類別。 亦即`<Binding` *bindProp1*`="`*value1* `"[` *bindPropN*`="`*看值*`"]*/>`是屬性的對等語法<xref:System.Windows.Data.Binding>物件項目使用方式，而不是`Binding`運算式使用方式。 若要了解的特定屬性的 XAML 屬性使用方式<xref:System.Windows.Data.Binding>，請參閱相關的屬性"XAML 屬性使用方式 」 一節<xref:System.Windows.Data.Binding>.NET Framework 類別庫中。  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`bindProp1, bindPropN`|名稱<xref:System.Windows.Data.Binding>或<xref:System.Windows.Data.BindingBase>屬性來設定。 並非所有<xref:System.Windows.Data.Binding>可以設定屬性，與`Binding`延伸模組和某些屬性會設定內`Binding`運算式只能藉由進一步使用巢狀標記延伸。 請參閱 < 繫結屬性，可以是設定與繫結延伸模組 > 一節。|  
|`value1, valueN`|若要將屬性設定為值。 屬性值的處理是最終特有的類型和一個特定的邏輯<xref:System.Windows.Data.Binding>所設定的屬性。|  
|`path`|設定隱含的路徑字串<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>屬性。 另請參閱[PropertyPath XAML 語法](propertypath-xaml-syntax.md)。|  
  
## <a name="unqualified-binding"></a>不合格的 {Binding}  
 `{Binding}` 「 繫結運算式使用量 」 所示的使用方式建立<xref:System.Windows.Data.Binding>物件使用預設值，其中包含初始<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>的`null`。 使用此方法仍在許多情況下，因為建立<xref:System.Windows.Data.Binding>可能會依賴索引鍵的資料繫結屬性這類<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>和<xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType>正在的內容中設定執行階段資料。 如需有關資料內容的概念的詳細資訊，請參閱[資料繫結](../data/data-binding-wpf.md)。  
  
## <a name="implicit-path"></a>隱含的路徑  
 `Binding`標記延伸模組會使用<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>概念為 「 預設屬性 」，其中`Path=`不需要出現在運算式中。 如果您指定`Binding`運算式具有隱含的路徑，隱含的路徑必須最先出現在運算式中之前的任何其他, `bindProp` = `value`配對，其中<xref:System.Windows.Data.Binding>名稱所指定屬性。 例如： `{Binding PathString}`，其中`PathString`是評估為值的字串<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>在<xref:System.Windows.Data.Binding>標記延伸使用方式所建立。 您可以附加之後使用逗號分隔符號，隱含的路徑，與其他具名的屬性，例如`{Binding LastName, Mode=TwoWay}`。  
  
## <a name="binding-properties-that-can-be-set-with-the-binding-extension"></a>可以使用繫結延伸模組設定的繫結屬性  
 本主題中所顯示的語法使用泛型`bindProp` = `value`近似值，因為有許多的讀取/寫入屬性的<xref:System.Windows.Data.BindingBase>或是<xref:System.Windows.Data.Binding>可以透過設定`Binding`標記延伸模組 /運算式的語法。 他們可以依任何順序，除了隱含設定<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>。 (您也可以選擇明確指定`Path=`，在此情況下以任何順序設定)。 基本上，您可以設定為零或多個屬性，以下清單中使用`bindProp` = `value`組以逗號分隔。  
  
 有幾個屬性值需要不支援原生型別轉換的文字語法中 XAML，並因此需要標記延伸模組，以便設定做為屬性值的物件類型。 檢查 XAML 屬性使用方式區段，在.NET Framework 類別庫，針對每個屬性，如需詳細資訊;使用 XAML 屬性語法，與字串或沒有進一步的標記延伸使用方式基本上就是您在中指定的值相同`Binding`運算式，與未放置引號括住每個例外狀況`bindProp` =`value`在`Binding`運算式。  
  
-   <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>： 識別可能的繫結群組的字串。 這是相當進階的繫結的概念;請參閱參考頁面<xref:System.Windows.Data.BindingBase.BindingGroupName%2A>。  
  
-   <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>：布林值，可以是`true`或`false`。 預設為 `false`。  
  
-   <xref:System.Windows.Data.Binding.Converter%2A>： 可設定為`bindProp` = `value`字串，在運算式中，但若要這樣做需要物件參考的值，例如[StaticResource 標記延伸](staticresource-markup-extension.md)。 在此情況下為自訂轉換子類別的執行個體。  
  
-   <xref:System.Windows.Data.Binding.ConverterCulture%2A>： 可在運算式中的標準為基礎的識別項; 與設定請參閱參考主題<xref:System.Windows.Data.Binding.ConverterCulture%2A>。  
  
-   <xref:System.Windows.Data.Binding.ConverterParameter%2A>： 可設定為`bindProp` = `value`字串運算式，但這是取決於所傳遞的參數類型。 這種使用方式傳遞參考型別值，如果要求物件參考，例如巢狀[StaticResource 標記延伸](staticresource-markup-extension.md)。  
  
-   <xref:System.Windows.Data.Binding.ElementName%2A>： 與互斥<xref:System.Windows.Data.Binding.RelativeSource%2A>和<xref:System.Windows.Data.Binding.Source%2A>; 每個這些繫結屬性代表特定的繫結方法。 請參閱[資料繫結概觀](../data/data-binding-overview.md)。  
  
-   <xref:System.Windows.Data.BindingBase.FallbackValue%2A>： 可設定為`bindProp` = `value`字串運算式，但這是取決於所傳遞的值類型。 如果傳遞參考類型，需要物件參考，例如巢狀[StaticResource 標記延伸](staticresource-markup-extension.md)。  
  
-   <xref:System.Windows.Data.Binding.IsAsync%2A>：布林值，可以是`true`或`false`。 預設為 `false`。  
  
-   <xref:System.Windows.Data.Binding.Mode%2A>:*值*是常數的名稱從<xref:System.Windows.Data.BindingMode>列舉型別。 例如， `{Binding Mode=OneWay}` 。  
  
-   <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>：布林值，可以是`true`或`false`。 預設為 `false`。  
  
-   <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>：布林值，可以是`true`或`false`。 預設為 `false`。  
  
-   <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>：布林值，可以是`true`或`false`。 預設為 `false`。  
  
-   <xref:System.Windows.Data.Binding.Path%2A>： 描述將資料物件或一種一般的物件模型路徑的字串。 格式會提供數個不同的慣例，可周遊無法適當地描述本主題中的物件模型。 請參閱[PropertyPath XAML 語法](propertypath-xaml-syntax.md)。  
  
-   <xref:System.Windows.Data.Binding.RelativeSource%2A>： 與互斥<xref:System.Windows.Data.Binding.ElementName%2A>和<xref:System.Windows.Data.Binding.Source%2A>; 每個這些繫結屬性代表特定的繫結方法。 請參閱[資料繫結概觀](../data/data-binding-overview.md)。 需要的巢狀[RelativeSource 標記延伸](relativesource-markupextension.md)使用量，以指定的值。  
  
-   <xref:System.Windows.Data.Binding.Source%2A>： 與互斥<xref:System.Windows.Data.Binding.RelativeSource%2A>和<xref:System.Windows.Data.Binding.ElementName%2A>; 每個這些繫結屬性代表特定的繫結方法。 請參閱[資料繫結概觀](../data/data-binding-overview.md)。 通常需要巢狀擴充功能使用方式[StaticResource 標記延伸](staticresource-markup-extension.md)索引鍵的資源字典中的參考物件資料來源。  
  
-   <xref:System.Windows.Data.BindingBase.StringFormat%2A>： 描述繫結資料的字串格式慣例的字串。 這是相當進階的繫結的概念;請參閱參考頁面<xref:System.Windows.Data.BindingBase.StringFormat%2A>。  
  
-   <xref:System.Windows.Data.BindingBase.TargetNullValue%2A>： 可設定為`bindProp` = `value`字串運算式，但這是取決於所傳遞的參數類型。 如果傳遞參考類型的值，需要物件參考，例如巢狀[StaticResource 標記延伸](staticresource-markup-extension.md)。  
  
-   <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>:*值*是常數的名稱從<xref:System.Windows.Data.UpdateSourceTrigger>列舉型別。 例如， `{Binding UpdateSourceTrigger=LostFocus}` 。 特定控制項可能會有不同的預設值，這個繫結屬性。 請參閱 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>。  
  
-   <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>：布林值，可以是`true`或`false`。 預設為 `false`。 請參閱＜備註＞。  
  
-   <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>：布林值，可以是`true`或`false`。 預設為 `false`。 請參閱＜備註＞。  
  
-   <xref:System.Windows.Data.Binding.XPath%2A>： 描述 XML 資料來源的 XMLDOM 路徑的字串。 請參閱[繫結至 XML 資料使用 XMLDataProvider 和 XPath 查詢](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)。  
  
 以下是屬性<xref:System.Windows.Data.Binding>，無法使用來設定`Binding`標記延伸模組 /`{Binding}`運算式格式。  
  
-   <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>： 這個屬性所預期的回呼實作的參考。 XAML 語法中不得參考非事件處理常式的回呼/方法。  
  
-   <xref:System.Windows.Data.Binding.ValidationRules%2A>： 此屬性會採用的泛型集合<xref:System.Windows.Controls.ValidationRule>物件。 這可以表示為屬性項目<xref:System.Windows.Data.Binding>物件項目，但已在使用沒有隨手可得屬性剖析技巧`Binding`運算式。 請參閱參考主題<xref:System.Windows.Data.Binding.ValidationRules%2A>。  
  
-   <xref:System.Windows.Data.Binding.XmlNamespaceManager%2A>  
  
## <a name="remarks"></a>備註  
  
> [!IMPORTANT]
>  相依性屬性在優先順序方面，`Binding`運算式就相當於本機設定值。 如果您設定的屬性，先前的區域數值`Binding`運算式，`Binding`已完全移除。 如需詳細資訊，請參閱[相依性屬性值優先順序](dependency-property-value-precedence.md)。  
  
 本主題並未涵蓋基本的層級的資料繫結。 請參閱[資料繫結概觀](../data/data-binding-overview.md)。  
  
> [!NOTE]
>  <xref:System.Windows.Data.MultiBinding> 並<xref:System.Windows.Data.PriorityBinding>不支援[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]延伸語法。 相反地，您會使用 property 項目。 請參閱參考主題<xref:System.Windows.Data.MultiBinding>和<xref:System.Windows.Data.PriorityBinding>。  
  
 XAML 的布林值不區分大小寫。 例如，您可以指定其中一個`{Binding NotifyOnValidationError=true}`或`{Binding NotifyOnValidationError=True}`。  
  
 涉及資料驗證的繫結通常由明確指定`Binding`項目而`{Binding ...}`運算式，並設定<xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>或<xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>在運算式中不常見。 這是因為同一系列文件屬性<xref:System.Windows.Data.Binding.ValidationRules%2A>無法輕易地設定運算式格式。 如需詳細資訊，請參閱 <<c0> [ 實作繫結驗證](../data/how-to-implement-binding-validation.md)。  
  
 `Binding` 是一種標記延伸。 需要逸出屬性值為常值或處理常式名稱，而且是比在特定類型或屬性上設定屬性的類型轉換器更通用的需求時，通常被實作標記延伸。 在 XAML 使用的所有標記延伸`{`和`}`字元在其屬性語法中，這是用的 XAML 處理器知道某個標記延伸必須處理字串內容的慣例。 如需詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。  
  
 `Binding` 已到達非典型的標記中的延伸模組，<xref:System.Windows.Data.Binding>實作 WPF 的 XAML 實作的擴充功能的類別也會實作數個其他的方法和 XAML 不相關的屬性。 其他成員旨在使<xref:System.Windows.Data.Binding>更具彈性且獨立的類別，可以解決許多除了做為 XAML 標記延伸的資料繫結案例。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Data.Binding>
- [資料繫結概觀](../data/data-binding-overview.md)
- [XAML 概觀 (WPF)](xaml-overview-wpf.md)
- [標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)
