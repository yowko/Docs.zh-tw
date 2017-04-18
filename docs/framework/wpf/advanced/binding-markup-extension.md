---
title: "繫結標記延伸 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Binding"
helpviewer_keywords: 
  - "繫結標記延伸"
  - "XAML, 繫結標記延伸"
ms.assetid: 83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 23
---
# 繫結標記延伸
將屬性值延後以成為資料繫結值，使其建立中繼運算式物件並解譯會在執行階段套用至項目及其繫結的資料內容。  
  
## 繫結運算式使用方式  
  
```  
<object property="{Binding}" .../>  
-or-  
<object property="{Binding  bindProp1=value1[, bindPropN=valueN]*}" ...  
/>  
-or-  
<object property="{Binding path}" .../>  
-or  
<object property="{Binding path[, bindPropN=valueN]*}" .../>  
```  
  
## 語法注意事項  
 在這些語法中，`[]` 與 `*` 都不是常值 \(Literal\)，  它們是標記法的一部分，會指出可以使用的零個或多個 *bindProp*`=`*value* 組，其中會使用 `,` 做為值組的分隔符號，並有 *bindProp*`=`*value* 做為前置值組。  
  
 「可使用繫結延伸進行設定的繫結屬性」一節中列出的所有屬性 \(Property\) 都可以改用 <xref:System.Windows.Data.Binding> 物件項目的屬性 \(Attribute\) 進行設定。  不過，這並不算是真的 <xref:System.Windows.Data.Binding> 標記延伸的應用，這只是屬性 \(Attribute\) 的一般 XAML 處理，這些屬性 \(Attribute\) 會設定 CLR <xref:System.Windows.Data.Binding> 類別的屬性 \(Property\)。  換句話說，`<Binding` *bindProp1*`="`*value1*`"[` *bindPropN*`="`*valueN*`"]*/>` 是 <xref:System.Windows.Data.Binding> 物件項目用法之屬性的對等語法，而非 `Binding` 運算式用法。  若要深入了解如何運用特定 <xref:System.Windows.Data.Binding> 屬性 \(Property\) 的 XAML 屬性 \(Attribute\)，請參閱 .NET Framework 類別庫中相關 <xref:System.Windows.Data.Binding> 屬性 \(Property\) 的「XAML 屬性使用方式」章節。  
  
## XAML 值  
  
|||  
|-|-|  
|`bindProp1, bindPropN`|要設定之 <xref:System.Windows.Data.Binding> 或 <xref:System.Windows.Data.BindingBase> 屬性的名稱。  並非所有  <xref:System.Windows.Data.Binding> 屬性 \(Property\) 都可使用 `Binding` 延伸進行設定，有些屬性 \(Property\) 只能使用進一步巢狀的標記延伸以 `Binding` 運算式進行設定。  請參閱「可使用繫結延伸進行設定的繫結屬性」一節。|  
|`value1, valueN`|要設定給屬性的值。  屬性 \(Attribute\) 值的處理方式最終需視所要設定之 <xref:System.Windows.Data.Binding> 屬性 \(Property\) 的專屬型別與邏輯而定。|  
|`path`|設定隱含 <xref:System.Windows.Data.Binding.Path%2A?displayProperty=fullName> 屬性 \(Property\) 的路徑字串。  請參閱[PropertyPath XAML 語法](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md)。|  
  
## 不合格的 {Binding}  
 「繫結運算式使用方式」中示範的 `{Binding}` 使用方法會利用預設值建立 <xref:System.Windows.Data.Binding> 物件，其中包含 `null` 的初 <xref:System.Windows.Data.Binding.Path%2A?displayProperty=fullName>。  這在許多案例中仍然是相當實用的，因為所建立的 <xref:System.Windows.Data.Binding> 可能會仰賴索引鍵資料繫結屬性 \(Property\)，例如於執行階段資料內容中設定的 <xref:System.Windows.Data.Binding.Path%2A?displayProperty=fullName> 與 <xref:System.Windows.Data.Binding.Source%2A?displayProperty=fullName>。  如需資料內容概念的詳細資訊，請參閱[資料繫結](../../../../docs/framework/wpf/data/data-binding-wpf.md)。  
  
## 隱含路徑  
 `Binding` 標記延伸使用 <xref:System.Windows.Data.Binding.Path%2A?displayProperty=fullName> 做為概念上的預設屬性，其中 `Path=` 不需要出現在運算式中。  如果您使用隱含路徑指定 `Binding` 運算式，該隱含路徑必須出現在運算式的一開始，位置要優先於任何其他的 `bindProp`\=`value` 組，其中 <xref:System.Windows.Data.Binding> 屬性會以名稱指定。  例如：`{Binding PathString}`，其中 `PathString` 是評估為 <xref:System.Windows.Data.Binding.Path%2A?displayProperty=fullName> \(以標記延伸用法建立的 <xref:System.Windows.Data.Binding>\) 之值的字串。  您可以附加具有其他名稱屬性 \(Property\) 的隱含路徑，並在其後使用逗號做為分隔符號，例如 `{Binding LastName, Mode=TwoWay}`。  
  
## 可使用繫結延伸進行設定的繫結屬性  
 本主題顯示的語法使用泛型 `bindProp`\=`value` 近似值，因為 <xref:System.Windows.Data.BindingBase> 或 <xref:System.Windows.Data.Binding> 有許多讀取\/寫入屬性 \(Property\) 可透過 `Binding` 標記延伸\/運算式語法進行設定。  除了隱含 <xref:System.Windows.Data.Binding.Path%2A?displayProperty=fullName> 以外，這些語法並沒有一定的設定的順序   \(您可以選擇是否要明確指定 `Path=`，在此情況下，可以將其設定為任何順序\)。  基本上，您可以使用以逗號分隔的 `bindProp`\=`value` 組，設定下列清單中的零個或多個屬性 \(Property\)。  
  
 這些屬性 \(Property\) 值中的幾個值，所需要的物件型別不支援 XAML 中文字語法的原生型別轉換，因此需要標記延伸以便設定為屬性 \(Attribute\) 值。  如需詳細資訊，請參閱 .NET Framework 類別庫中每一個屬性的「XAML 屬性使用方式」一節。您用於 XAML 屬性 \(Attribute\) 語法的字串是否需要進一步搭配標記延伸用法，基本上與以 `Binding` 運算式指定值的方式相同，不過其中有一項例外，在 `Binding` 運算式中，每一個 `bindProp`\=`value` 組的前後不需要加上引號。  
  
-   <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>：識別可能繫結群組的字串。  相對而言，這算是進階的繫結概念，請參閱 <xref:System.Windows.Data.BindingBase.BindingGroupName%2A> 的參考頁面。  
  
-   <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>：布林值，可以為 `true` 或 `false`。  預設值為 `false`。  
  
-   <xref:System.Windows.Data.Binding.Converter%2A>：可以設為運算式中的 `bindProp`\=`value` 字串，但是不需要值的物件參考，例如 [StaticResource 標記延伸](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)。  在此情況下，這個值會是自訂轉換子類別的執行個體。  
  
-   <xref:System.Windows.Data.Binding.ConverterCulture%2A>：可以設定為運算式中的標準識別項，請參閱 <xref:System.Windows.Data.Binding.ConverterCulture%2A> 的參考主題。  
  
-   <xref:System.Windows.Data.Binding.ConverterParameter%2A>：可以設定為運算式中的 `bindProp`\=`value` 字串，但是這需視所傳遞之參數型別而定。  如果對值傳遞參考型別，這種用法就需要物件參考，例如巢狀 [StaticResource 標記延伸](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)。  
  
-   <xref:System.Windows.Data.Binding.ElementName%2A>：與 <xref:System.Windows.Data.Binding.RelativeSource%2A> 和 <xref:System.Windows.Data.Binding.Source%2A> 互斥，這些屬性個別表示特定的繫結方法。  請參閱 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。  
  
-   <xref:System.Windows.Data.BindingBase.FallbackValue%2A>：可以設定為運算式中的 `bindProp`\=`value` 字串，但是這需視所傳遞之值的型別而定。  如果參考型別，則需要物件參考，例如巢狀 [StaticResource 標記延伸](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)。  
  
-   <xref:System.Windows.Data.Binding.IsAsync%2A>：布林值，可以為 `true` 或 `false`。  預設值為 `false`。  
  
-   <xref:System.Windows.Data.Binding.Mode%2A>：*value* 為來自 <xref:System.Windows.Data.BindingMode> 列舉的常數名稱。  例如 `{Binding Mode=OneWay}`。  
  
-   <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>：布林值，可以為 `true` 或 `false`。  預設值為 `false`。  
  
-   <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>：布林值，可以為 `true` 或 `false`。  預設值為 `false`。  
  
-   <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>：布林值，可以為 `true` 或 `false`。  預設值為 `false`。  
  
-   <xref:System.Windows.Data.Binding.Path%2A>：描述資料物件路徑或一般物件模型的字串。  這個格式提供多種不同用於周遊物件模型的慣例，在此主題中沒有詳加說明。  請參閱 [PropertyPath XAML 語法](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md)。  
  
-   <xref:System.Windows.Data.Binding.RelativeSource%2A>：與 <xref:System.Windows.Data.Binding.ElementName%2A> 和 <xref:System.Windows.Data.Binding.Source%2A> 互斥 \(Mutually Exclusive\)，這些繫結屬性中的每個都表示特定的繫結方法。  請參閱 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。  需要使用巢狀 [RelativeSource 標記延伸](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md) 以指定值。  
  
-   <xref:System.Windows.Data.Binding.Source%2A>：與 <xref:System.Windows.Data.Binding.RelativeSource%2A> 和 <xref:System.Windows.Data.Binding.ElementName%2A> 互斥，這些屬性個別表示特定的繫結方法。  請參閱 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。  需要使用巢狀延伸，通常是 [StaticResource 標記延伸](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)，其參考已編排索引之資源字典中的物件資料。  
  
-   <xref:System.Windows.Data.BindingBase.StringFormat%2A>：描述繫結資料之文字格式慣例的字串。  相對而言，這算是進階的繫結概念，請參閱 <xref:System.Windows.Data.BindingBase.StringFormat%2A> 的參考頁面。  
  
-   <xref:System.Windows.Data.BindingBase.TargetNullValue%2A>：可以設定為運算式中的 `bindProp`\=`value` 字串，但是這需視所傳遞之參數型別而定。  如果對值傳遞參考型別，則需要物件參考，例如巢狀 [StaticResource 標記延伸](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)。  
  
-   <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>：*value* 為來自 <xref:System.Windows.Data.UpdateSourceTrigger> 列舉的常數名稱。  例如 `{Binding UpdateSourceTrigger=LostFocus}`。  針對這個繫結屬性，特定的控制項可能會有不同的預設值。  請參閱 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>。  
  
-   <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>：布林值，可以為 `true` 或 `false`。  預設值為 `false`。  請參閱＜備註＞。  
  
-   <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>：布林值，可以為 `true` 或 `false`。  預設值為 `false`。  請參閱＜備註＞。  
  
-   <xref:System.Windows.Data.Binding.XPath%2A>：描述 XML 資料來源中 XMLDOM 的路徑。  請參閱 [使用 XMLDataProvider 和 XPath 查詢繫結至 XML 資料](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)。  
  
 以下是無法使用 `Binding` 標記延伸 \/`{Binding}` 運算式形式來設定的 <xref:System.Windows.Data.Binding> 屬性。  
  
-   <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>：此屬性會預期回呼實作的參考。  在 XAML 語法中，不能參考事件處理常式以外的回呼或方法。  
  
-   <xref:System.Windows.Data.Binding.ValidationRules%2A>：這個屬性 \(Property\) 採用 <xref:System.Windows.Controls.ValidationRule> 物件的泛型集合。  這可以表示為 <xref:System.Windows.Data.Binding> 物件項目中的屬性 \(Property\) 項目，但是在 `Binding` 運算式中，並沒有現成可以使用的屬性 \(Attribute\) 剖析技術。  請參閱 <xref:System.Windows.Data.Binding.ValidationRules%2A> 的參考主題。  
  
-   <xref:System.Windows.Data.Binding.XmlNamespaceManager%2A>  
  
## 備註  
  
> [!IMPORTANT]
>  就相依性屬性優先順序而言，`Binding` 運算式相當於本機設定值。  如果您為原來具有 `Binding` 運算式的屬性 \(Property\) 設定本機值，這個 `Binding` 將被完全移除。  如需詳細資訊，請參閱[相依性屬性值優先順序](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)。  
  
 本主題並未涵蓋基本層級之資料繫結的描述。  請參閱 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。  
  
> [!NOTE]
>  <xref:System.Windows.Data.MultiBinding>和<xref:System.Windows.Data.PriorityBinding>不支援[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]擴充語法。您將改用屬性的元素。  請參閱 <xref:System.Windows.Data.MultiBinding> 和 <xref:System.Windows.Data.PriorityBinding> 的參考主題。  
  
 XAML 的 Boolean 值不區分大小寫。  例如，您可以指定 `{Binding NotifyOnValidationError=true}` 或 `{Binding NotifyOnValidationError=True}`。  
  
 資料驗證所牽涉的繫結，一般是由明確 `Binding` 項目指定，而非使用 `{Binding ...}` 運算式，而且在運算式中設定 <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> 或 <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> 是不常見的。  這是因為無法以運算式形式輕易設定同伴屬性 <xref:System.Windows.Data.Binding.ValidationRules%2A>。  如需詳細資訊，請參閱 [實作繫結驗證](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)。  
  
 `Binding` 是一種標記延伸。  如果必須將屬性 \(Attribute\) 值加上逸出符號，以免成為常值或處理常式名稱，而且這項需求必須更全面地實施 \(而不是只對特定型別或屬性 \(Property\) 上的設定型別轉換子 \(Type Converter\)\)，則通常會實作標記延伸。  所有 XAML 標記延伸都會在其屬性 \(Attribute\) 語法中使用 `{` 與 `}` 字元，這個慣例讓 XAML 處理器可辨識出某個標記延伸必須處理字串內容。  如需詳細資訊，請參閱 [標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。  
  
 `Binding` 是典型的標記延伸，因為實作 WPF 之 XAML 實作的擴充功能的 <xref:System.Windows.Data.Binding> 類別，也會實作與 XAML 無關的其他數種方法和屬性。  其他成員的用意在於將 <xref:System.Windows.Data.Binding> 設定為更多樣化和獨立的類別，不只能夠發揮 XAML 標記延伸功能，還能因應其他許多資料繫結案例。  
  
## 請參閱  
 <xref:System.Windows.Data.Binding>   
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)