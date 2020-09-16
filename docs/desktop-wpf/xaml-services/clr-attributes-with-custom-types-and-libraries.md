---
title: 自訂類型和程式庫的 XAML 相關 CLR 屬性
ms.date: 03/30/2017
helpviewer_keywords:
- CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
ms.openlocfilehash: a4b8a58ea2c7d9de2b59ed78dc37e4ce1c434b79
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90535393"
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a>自訂類型和程式庫的 XAML 相關 CLR 屬性

本主題說明 .NET XAML 服務所定義 (CLR) 屬性的 common language runtime。 此外，也會說明在 .NET 中定義的其他 CLR 屬性，這些屬性會針對應用程式的元件或類型，具有與 XAML 相關的案例。 使用這些 CLR 屬性（attribute）將元件、類型或成員的屬性（attribute）提供與類型相關的 XAML 類型系統資訊。 資訊會提供給任何使用 .NET XAML 服務的 XAML 取用者，以便直接或透過專用的 XAML 讀取器和 XAML 寫入器處理 XAML 節點資料流程。

## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a>自訂類型和自訂成員的 XAML 相關 CLR 屬性

使用 CLR 屬性時，您必須使用整體 CLR 來定義您的類型，否則無法使用這類屬性。 如果您使用 CLR 來定義型別支援，則 .NET XAML 服務 XAML 寫入器所使用的預設 XAML 架構內容，可以透過反映針對支援元件來讀取 CLR 屬性。

下列各節說明可套用至自訂類型或自訂成員的 XAML 相關屬性。 每個 CLR 屬性都會傳達與 XAML 類型系統相關的資訊。 在載入路徑中，屬性化資訊可協助 XAML 讀取器形成有效的 XAML 節點資料流程，或協助 XAML 寫入器產生有效的物件圖形。 在儲存路徑中，屬性化資訊可協助 XAML 讀取器形成有效的 XAML 節點資料流程，以重組 XAML 類型系統資訊;或者，它會宣告 XAML 寫入器或其他 XAML 取用者的序列化提示或需求。

### <a name="ambientattribute"></a>AmbientAttribute

**參考檔：**<xref:System.Windows.Markup.AmbientAttribute>

**適用于：**`get`支援可附加屬性的類別、屬性或存取子成員。

**引數：** 沒有

<xref:System.Windows.Markup.AmbientAttribute> 指出屬性（property）或所有採用屬性化型別的屬性（property），都應該在 XAML 的環境屬性概念下解讀。 環境概念與 XAML 處理器如何判斷成員類別擁有者有關。 環境屬性是一種屬性，它會在建立物件圖形時，將值預期在剖析器內容中，但在這種情況下，會針對正在建立的立即 XAML 節點集暫停一般的型別成員查閱。

環境概念可以套用至可附加的成員，這些成員不會以 CLR 屬性定義的形式來表示 <xref:System.AttributeTargets> 。 方法屬性的使用方式應僅適用于 `get` 支援 XAML 可附加用法的存取子。

### <a name="constructorargumentattribute"></a>ConstructorArgumentAttribute

**參考檔：**  <xref:System.Windows.Markup.ConstructorArgumentAttribute>

**適用于：** 類

**引數：** 字串，指定符合單一函式引數的屬性名稱。

<xref:System.Windows.Markup.ConstructorArgumentAttribute> 指定可以使用非參數化的函式語法來初始化物件，且指定之名稱的屬性會提供結構資訊。 這項資訊主要供 XAML 序列化之用。 如需詳細資訊，請參閱<xref:System.Windows.Markup.ConstructorArgumentAttribute>。

### <a name="contentpropertyattribute"></a>ContentPropertyAttribute

**參考檔：**  <xref:System.Windows.Markup.ContentPropertyAttribute>

**適用于：** 類

**引數：** 字串，指定屬性型別之成員的名稱。

<xref:System.Windows.Markup.ContentPropertyAttribute> 指出由引數命名的屬性應做為該類型的 XAML 內容屬性。 XAML 內容屬性定義會繼承到可指派給定義型別的所有衍生型別。 您可以 <xref:System.Windows.Markup.ContentPropertyAttribute> 在特定的衍生型別上套用，藉以覆寫特定衍生型別的定義。

針對做為 XAML 內容屬性的屬性，可以在 XAML 用法中省略屬性的屬性專案標記。 通常，您會指定 XAML 內容屬性，以針對您的內容和內含專案模型升級簡化的 XAML 標記。 因為只有一個成員可以指定為 XAML 內容屬性，所以您有時會有設計選項，以決定應該將類型的數個容器屬性指定為 XAML 內容屬性。 其他容器屬性必須搭配明確的屬性元素使用。

在 XAML 節點資料流程中，XAML 內容屬性仍會產生 `StartMember` 和 `EndMember` 節點，並使用的屬性名稱 <xref:System.Xaml.XamlMember> 。 若要判斷成員是否為 XAML 內容屬性，請檢查 <xref:System.Xaml.XamlType> 位置的值 `StartObject` ，並取得的值 <xref:System.Xaml.XamlType.ContentProperty%2A> 。

### <a name="contentwrapperattribute"></a>ContentWrapperAttribute

**參考檔：**  <xref:System.Windows.Markup.ContentWrapperAttribute>

**適用于：** 類別，特別是集合類型。

**引數：**<xref:System.Type>，指定要做為外部內容之內容包裝函式類型的型別。

<xref:System.Windows.Markup.ContentWrapperAttribute> 指定將用來包裝外部內容之相關聯集合類型上的一或多個類型。 外部內容是指 [內容] 屬性類型上的類型系統條件約束，不會捕捉擁有類型所支援之 XAML 使用方式的所有可能內容案例的案例。 例如，XAML 支援特定類型內容可能支援強型別泛型中的字串 <xref:System.Collections.ObjectModel.Collection%601> 。 內容包裝函式適用于將預先存在的標記慣例遷移至 XAML 針對集合的可指派值概念，例如，遷移文字相關的內容模型。

若要指定一個以上的內容包裝函式類型，請多次套用此屬性。

### <a name="dependsonattribute"></a>DependsOnAttribute

**參考檔：**  <xref:System.Windows.Markup.DependsOnAttribute>

**適用于：** 財產

**引數：** 字串，指定屬性型別之另一個成員的名稱。

<xref:System.Windows.Markup.DependsOnAttribute> 指出屬性化屬性相依于另一個屬性的值。 將這個屬性套用至屬性定義，可確保相依屬性會先在撰寫的 XAML 物件中處理。 的使用方式 <xref:System.Windows.Markup.DependsOnAttribute> 會指定類型的例外狀況案例，在此類型上必須遵循特定的剖析順序，才能建立有效的物件。

您可以將多個 <xref:System.Windows.Markup.DependsOnAttribute> 案例套用至屬性定義。

### <a name="markupextensionreturntypeattribute"></a>MarkupExtensionReturnTypeAttribute

**參考檔：**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>

**適用于：** 類別，它應該是 <xref:System.Windows.Markup.MarkupExtension> 衍生型別。

**引數：**<xref:System.Type>，指定預期為 `ProvideValue` 屬性化之結果的最精確型別 <xref:System.Windows.Markup.MarkupExtension> 。

如需詳細資訊，請參閱 [XAML 的標記延伸總覽](markup-extensions-overview.md)。

### <a name="namescopepropertyattribute"></a>NameScopePropertyAttribute

**參考檔：**  <xref:System.Windows.Markup.NameScopePropertyAttribute>

**適用于：** 類

**引數：** 支援兩種形式的屬性：

- 字串，指定屬性化型別上的屬性名稱。

- 字串，指定屬性的名稱，以及 <xref:System.Type> 定義已命名屬性之類型的。 此形式適用于將可附加的成員指定為 XAML 名稱範圍屬性。

<xref:System.Windows.Markup.NameScopePropertyAttribute> 指定可為屬性化類別提供 XAML 名稱範圍值的屬性。 XAML 名稱範圍屬性必須參考物件，該物件會執行 <xref:System.Windows.Markup.INameScope> 並保存實際的 XAML 名稱範圍、其存放區和其行為。

### <a name="runtimenamepropertyattribute"></a>RuntimeNamePropertyAttribute

**參考檔：**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>

**適用于：** 類

**引數：** 字串，指定屬性化型別上執行時間名稱屬性的名稱。

<xref:System.Windows.Markup.RuntimeNamePropertyAttribute> 報告對應至 XAML [x：Name](xname-directive.md)指示詞之屬性化型別的屬性（property）。 屬性必須是型別 <xref:System.String> ，而且必須是讀取/寫入。

定義會繼承到可指派給定義型別的所有衍生型別。 您可以 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> 在特定的衍生型別上套用，藉以覆寫特定衍生型別的定義。

### <a name="trimsurroundingwhitespaceattribute"></a>TrimSurroundingWhitespaceAttribute

**參考檔：**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>

**適用于：** 類型

**引數：** 沒有。

<xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> 會套用至特定類型，而這些類型可能會顯示為泛空白字元內的子項目， (內容由具有) 之集合所持有的內容 <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> 。 <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> 主要與儲存路徑相關，但在 XAML 型別系統中，可透過檢查來提供給載入路徑 <xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType> 。 如需詳細資訊，請參閱 [XAML 中](white-space-processing.md)的空白字元處理。

### <a name="typeconverterattribute"></a>TypeConverterAttribute

**參考檔：**  <xref:System.ComponentModel.TypeConverterAttribute>

**適用于：** 類別、屬性、方法 (唯一的 XAML 有效方法案例，是 `get` 支援可附加成員) 的存取子。

**引數：** 的 <xref:System.Type> <xref:System.ComponentModel.TypeConverter> 。

<xref:System.ComponentModel.TypeConverterAttribute> 在 XAML 內容中，會參考自訂 <xref:System.ComponentModel.TypeConverter> 。 這 <xref:System.ComponentModel.TypeConverter> 會提供自訂類型的類型轉換行為，或該類型的成員。

將 <xref:System.ComponentModel.TypeConverterAttribute> 屬性套用至您的類型，並參考您的類型轉換子執行。 您可以在類別、結構或介面上定義 XAML 的類型轉換器。 您不需要提供列舉的型別轉換，就會以原生方式啟用轉換。

您的類型轉換器應該能夠從用於標記之屬性或初始化文字的字串轉換成您想要的目的地類型。 如需詳細資訊，請參閱 [typeconverter 和 XAML](/dotnet/desktop/wpf/advanced/typeconverters-and-xaml)。

XAML 的類型轉換子行為也可以在特定屬性上建立，而不是套用至類型的所有值。 在此情況下，您會將 <xref:System.ComponentModel.TypeConverterAttribute> 屬性定義套用 (外部定義，而不是特定 `get` 和 `set` 定義) 。

您可以套用 <xref:System.ComponentModel.TypeConverterAttribute> 至 `get` 支援 xaml 使用方式的方法存取子，藉以指派自訂可附加成員的 XAML 使用類型轉換器行為。

類似于 <xref:System.ComponentModel.TypeConverter> ， <xref:System.ComponentModel.TypeConverterAttribute> .net 存在於 XAML 之前，以及型別轉換子模型為其他用途提供服務。 <xref:System.ComponentModel.TypeConverterAttribute>您必須完整限定或提供的語句，才能參考和使用 `using` <xref:System.ComponentModel> 。 也請在您的專案中包含系統元件。

### <a name="uidpropertyattribute"></a>UidPropertyAttribute

**參考檔：**  <xref:System.Windows.Markup.UidPropertyAttribute>

**適用于：** 類

**引數：** 依名稱參考相關屬性的字串。

指出類別的 CLR 屬性，該類別會為 [x：Uid](xuid-directive.md)指示詞進行別名。

### <a name="usableduringinitializationattribute"></a>UsableDuringInitializationAttribute

**參考檔：**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute>

**適用于：** 類

**引數：** 布林值。 如果用於屬性的預期用途，此值應該設定為 `true` 。

指出型別是否在建立 XAML 物件圖形期間由上而下建立。 這是一個很好的概念，可能與您的程式設計模型定義密切相關。 如需詳細資訊，請參閱<xref:System.Windows.Markup.UsableDuringInitializationAttribute>。

### <a name="valueserializerattribute"></a>ValueSerializerAttribute

**參考檔：**  <xref:System.Windows.Markup.ValueSerializerAttribute>

**適用于：** 類別、屬性、方法 (唯一的 XAML 有效方法案例，是 `get` 支援可附加成員) 的存取子。

**引數：**<xref:System.Type>，指定序列化屬性化類型的所有屬性或特定屬性化屬性時所要使用的值序列化程式支援類別。

<xref:System.Windows.Markup.ValueSerializer> 指定需要更多狀態和內容的值序列化類別 <xref:System.ComponentModel.TypeConverter> 。 <xref:System.Windows.Markup.ValueSerializer> 可以在可 <xref:System.Windows.Markup.ValueSerializerAttribute> 附加成員的靜態存取子方法上套用屬性，以便與可附加的成員建立關聯 `get` 。 值序列化也適用于列舉、介面和結構，但不適用於委派。

### <a name="whitespacesignificantcollectionattribute"></a>WhitespaceSignificantCollectionAttribute

**參考檔：**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>

**適用于：** 類別，特別是預期會裝載混合內容的集合型別，其中物件專案周圍的空白字元對於 UI 表示而言可能很重要。

**引數：** 沒有。

<xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> 表示集合類型應該以泛空白字元的方式處理，由 XAML 處理器所影響，而這會影響集合內 XAML 節點資料流程的值節點的結構。 如需詳細資訊，請參閱 [XAML 中](white-space-processing.md)的空白字元處理。

### <a name="xamldeferloadattribute"></a>XamlDeferLoadAttribute

**參考檔：**  <xref:System.Windows.Markup.XamlDeferLoadAttribute>

**適用于：** 類別、屬性。

**引數：** 支援兩種屬性形式的類型做為字串或類型 <xref:System.Type> 。 請參閱 <xref:System.Windows.Markup.XamlDeferLoadAttribute>。

表示類別或屬性具有 XAML 的延後載入使用方式 (例如，範本行為)，並報告啟用延後行為的類別及其目的型別/內容型別。

### <a name="xamlsetmarkupextensionattribute"></a>System.windows.markup.xamlsetmarkupextensionattribute

**參考檔：**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute>

**適用于：** 類

**引數：** 為回呼命名。

指出類別可使用標記延伸來提供其一或多個屬性的值，並參考 XAML 寫入器在針對類別的任何屬性執行標記延伸集作業之前，應該呼叫的處理常式。

### <a name="xamlsettypeconverterattribute"></a>XamlSetTypeConverterAttribute

**參考檔：**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute>

**適用于：** 類

**引數：** 為回呼命名。

指出類別可以使用類型轉換器來提供其一或多個屬性的值，並參考 XAML 寫入器在類別的任何屬性上執行類型轉換器設定作業之前，應該呼叫的處理常式。

### <a name="xmllangpropertyattribute"></a>XmlLangPropertyAttribute

**參考檔：**  <xref:System.Windows.Markup.XmlLangPropertyAttribute>

**適用于：** 類

**引數：** 字串，指定屬性化類型上要別名的屬性名稱 `xml:lang` 。

<xref:System.Windows.Markup.XmlLangPropertyAttribute> 報告與 XML 指示詞對應之屬性化型別的屬性（property） `lang` 。 屬性不一定是型別， <xref:System.String> 但必須可以從字串指派 (指派，方法是將型別轉換器與屬性的型別或特定屬性) 產生關聯。 屬性必須是讀取/寫入。

對應的案例 `xml:lang` 是，執行時間物件模型可以存取 XML 指定的語言資訊，而不需要特別處理 XMLDOM。

定義會繼承到可指派給定義型別的所有衍生型別。 您可以在特定的衍生型別上套用，以覆寫特定衍生型別的定義 <xref:System.Windows.Markup.XmlLangPropertyAttribute> ，雖然這是不常見的情況。

## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a>元件層級的 XAML 相關 CLR 屬性

下列各節描述未套用至類型或成員定義，但改為套用至元件的 XAML 相關屬性。 這些屬性與定義程式庫（其中包含要在 XAML 中使用的自訂類型）的整體目標有關。 某些屬性不一定會直接影響 XAML 節點資料流程，但會在節點資料流程中傳遞給其他取用者使用。 資訊的取用者包括設計環境或需要 XAML 命名空間資訊的序列化程式，以及相關聯的前置詞資訊。 XAML 架構內容 (包括 .NET XAML 服務預設) 也會使用此資訊。

### <a name="xmlnscompatiblewithattribute"></a>XmlnsCompatibleWithAttribute

**參考檔：**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>

**引數:**

- 字串，指定要包含的 XAML 命名空間識別碼。

- 字串，指定可從上一個引數包含 XAML 命名空間的 XAML 命名空間識別碼。

  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute> 指定 XAML 命名空間可由另一個 XAML 命名空間建立小計。 一般會在預先定義的 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 中指出建立小計的 XAML 命名空間。 這項技術可以用來在程式庫中設定 XAML 詞彙的版本，並使其與先前已建立版本之詞彙的先前定義標記相容。

### <a name="xmlnsdefinitionattribute"></a>XmlnsDefinitionAttribute

**參考檔：**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>

**引數:**

- 字串，指定要定義的 XAML 命名空間識別碼。

- 命名 CLR 命名空間的字串。 CLR 命名空間應該在您的元件中定義公用類型，而且至少要有一個 CLR 命名空間類型適用于 XAML 用法。

  <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 指定 XAML 命名空間和 CLR 命名空間之間每個元件的對應，然後由 XAML 物件寫入器或 XAML 架構內容用於類型解析。

  您可以將一個以上 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 的應用程式套用至元件。 這可能會因為下列任何組合而完成：

- 程式庫設計包含多個 CLR 命名空間，適用于執行時間 API 存取的邏輯組織;不過，您想要透過參考相同的 XAML 命名空間，讓這些命名空間中的所有型別都可以使用 XAML。 在此情況下，您會 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 使用相同的 <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> 值，但不同的值來套用數個屬性 <xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A> 。 如果您要定義 XAML 命名空間的對應，架構或應用程式想要成為一般使用方式的預設 XAML 命名空間，這會特別有用。

- 程式庫設計包含多個 CLR 命名空間，而您想要在這些 CLR 命名空間中的型別使用方式之間區隔刻意的 XAML 命名空間。

- 您可以在元件中定義 CLR 命名空間，而且想要透過多個 XAML 命名空間來存取它。 當您使用相同的程式碼基底來支援多個詞彙時，就會發生此情況。

- 您可以在一或多個 CLR 命名空間中定義 XAML 語言支援。 在此情況下，此 <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> 值應為 `http://schemas.microsoft.com/winfx/2006/xaml` 。

### <a name="xmlnsprefixattribute"></a>XmlnsPrefixAttribute

**參考檔：**  <xref:System.Windows.Markup.XmlnsPrefixAttribute>

**引數:**

- 指定 XAML 命名空間識別碼的字串。

- 指定建議前置詞的字串。

  <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 指定要用於 XAML 命名空間的建議前置詞。 當您在 .NET XAML 服務所序列化的 XAML 檔案中撰寫專案和屬性時 <xref:System.Xaml.XamlXmlWriter> ，或 xaml 執行程式庫與具有 XAML 編輯功能的設計環境互動時，前置詞會很有用。

  您可以將一個以上 <xref:System.Windows.Markup.XmlnsPrefixAttribute> 的應用程式套用至元件。 這可能會因為下列任何組合而完成：

- 您的元件會定義一個以上的 XAML 命名空間類型。 在此情況下，請為每個 XAML 命名空間定義不同的前置詞值。

- 您支援多個詞彙，且每個詞彙和 XAML 命名空間使用不同的首碼。

- 您可以在元件中定義 XAML 語言支援，並 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 為指定 `http://schemas.microsoft.com/winfx/2006/xaml` 。 在此情況下，您通常應該升級前置詞 `x` 。

> [!NOTE]
> .NET XAML 服務也會定義與 XAML 相關的屬性 <xref:System.Windows.Markup.RootNamespaceAttribute> 。 這個屬性是專案系統支援的元件層級屬性，與 XAML 自訂類型無關。

## <a name="see-also"></a>另請參閱

- <xref:System.Attribute>
- [定義可搭配 .NET XAML 服務使用的自訂類型](define-custom-types.md)
