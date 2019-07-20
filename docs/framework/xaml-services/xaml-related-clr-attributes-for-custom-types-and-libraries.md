---
title: 自訂類型和程式庫的 XAML 相關 CLR 屬性
ms.date: 03/30/2017
helpviewer_keywords:
- CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
ms.openlocfilehash: 2f907d097f52f13e733713d8ad68cc2390b051ed
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364226"
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a>自訂類型和程式庫的 XAML 相關 CLR 屬性
本主題描述 .NET Framework XAML 服務所定義的 common language runtime (CLR) 屬性。 它也會描述在 .NET Framework 中定義的其他 CLR 屬性, 這些屬性具有應用程式對元件或類型的 XAML 相關案例。 將元件、類型或成員加到這些 CLR 屬性的特性, 會提供與您的類型相關的 XAML 類型系統資訊。 會提供資訊給任何使用 .NET Framework XAML 服務的 XAML 取用者, 以直接處理 XAML 節點資料流程, 或透過專屬 XAML 讀取器和 XAML 寫入器。  
  
## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a>自訂類型和自訂成員的 XAML 相關 CLR 屬性  
 使用 CLR 屬性時, 您必須使用整體的 CLR 來定義您的類型, 否則這類屬性無法使用。 如果您使用 CLR 定義類型支援, 則 .NET Framework XAML 服務 XAML 寫入器所使用的預設 XAML 架構內容, 可以透過反映對支援元件讀取 CLR 屬性。  
  
 下列各節描述 XAML 相關的屬性, 您可以將它們套用至自訂類型或自訂成員。 每個 CLR 屬性都會傳達與 XAML 類型系統相關的資訊。 在載入路徑中, 屬性化資訊可以協助 XAML 讀取器形成有效的 XAML 節點資料流程, 或協助 XAML 寫入器產生有效的物件圖形。 在儲存路徑中, 屬性化資訊可以協助 XAML 讀取器形成重組 XAML 類型系統資訊的有效 XAML 節點資料流程;或者, 它會宣告 XAML 寫入器或其他 XAML 取用者的序列化提示或需求。  
  
### <a name="ambientattribute"></a>AmbientAttribute  
 **參考檔:**  <xref:System.Windows.Markup.AmbientAttribute>  
  
 **適用於：** 支援可附加屬性的`get`類別、屬性或存取子成員。  
  
 **參量**無  
  
 <xref:System.Windows.Markup.AmbientAttribute>指出屬性 (或所有採用屬性化類型的屬性) 應該在 XAML 中的環境屬性概念下加以解讀。 環境概念與 XAML 處理器如何判斷成員類別擁有者有關。 環境屬性是一個屬性, 在建立物件圖形時, 應該會在剖析器內容中使用此值, 但針對要建立的立即 XAML 節點集暫停一般的類型成員查閱。  
  
 環境概念可以套用至可附加的成員, 這些成員不會以 CLR 屬性定義<xref:System.AttributeTargets>的方式表示為屬性。 只有在支援可附加的 XAML 用法的存取子`get`時, 才應套用方法屬性用法。  
  
### <a name="constructorargumentattribute"></a>ConstructorArgumentAttribute  
 **參考檔:**  <xref:System.Windows.Markup.ConstructorArgumentAttribute>  
  
 **適用於：** 類別  
  
 **參量**字串, 指定符合單一函式引數的屬性名稱。  
  
 <xref:System.Windows.Markup.ConstructorArgumentAttribute>指定物件可以使用非參數化的函式語法進行初始化, 而指定名稱的屬性則提供結構資訊。 這項資訊主要供 XAML 序列化之用。 如需詳細資訊，請參閱 <xref:System.Windows.Markup.ConstructorArgumentAttribute>。  
  
### <a name="contentpropertyattribute"></a>ContentPropertyAttribute  
 **參考檔:**  <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
 **適用於：** 類別  
  
 **參量**字串, 指定屬性型別之成員的名稱。  
  
 <xref:System.Windows.Markup.ContentPropertyAttribute>表示由引數命名的屬性應該作為該類型的 XAML 內容屬性。 XAML 內容屬性定義會繼承到可指派給定義類型的所有衍生類型。 您可以在特定衍生型別上套用, 藉此<xref:System.Windows.Markup.ContentPropertyAttribute>覆寫特定衍生型別的定義。  
  
 針對做為 XAML 內容屬性的屬性, XAML 使用方式中可以省略屬性的屬性專案標記。 一般來說, 您會指定 XAML 內容屬性, 為您的內容和內含專案模型升級簡化的 XAML 標記。 因為只有一個成員可以指定為 XAML 內容屬性, 所以有時候您會有設計選擇, 以便將類型的數個容器屬性指定為 XAML 內容屬性。 其他容器屬性必須與明確的屬性專案搭配使用。  
  
 在 xaml 節點資料流程中, xaml 內容屬性仍會`StartMember`產生`EndMember`和節點, 並使用的屬性<xref:System.Xaml.XamlMember>名稱。 若要判斷成員是否為 XAML 內容屬性, 請檢查<xref:System.Xaml.XamlType> `StartObject`位置的值<xref:System.Xaml.XamlType.ContentProperty%2A>, 並取得的值。  
  
### <a name="contentwrapperattribute"></a>ContentWrapperAttribute  
 **參考檔:**  <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
 **適用於：** 類別, 特別是集合類型。  
  
 **參量**<xref:System.Type> , 指定用來做為外部內容之內容包裝函式類型的類型。  
  
 <xref:System.Windows.Markup.ContentWrapperAttribute>在將用來包裝外部內容的相關聯集合類型上, 指定一或多個類型。 外部內容指的是上下文屬性類型上的類型系統條件約束, 不會捕捉擁有類型的 XAML 使用方式所支援的所有可能內容案例。 例如, 特定類型之內容的 XAML 支援可能會支援強型別泛型<xref:System.Collections.ObjectModel.Collection%601>中的字串。 內容包裝函式適用于將預先存在的標記慣例, 遷移至集合的可指派值的 XAML 概念, 例如, 遷移文字相關的內容模型。  
  
 若要指定一個以上的內容包裝函式類型, 請多次套用屬性。  
  
### <a name="dependsonattribute"></a>DependsOnAttribute  
 **參考檔:**  <xref:System.Windows.Markup.DependsOnAttribute>  
  
 **適用於：** 屬性  
  
 **參量**字串, 指定屬性型別之另一個成員的名稱。  
  
 <xref:System.Windows.Markup.DependsOnAttribute>表示屬性化屬性相依于另一個屬性的值。 將此屬性套用至屬性定義, 可確保會先在撰寫 XAML 物件時處理相依屬性。 的<xref:System.Windows.Markup.DependsOnAttribute>使用方式指定類型上屬性的例外狀況, 其中必須遵循特定的剖析順序, 才能建立有效的物件。  
  
 您可以將多<xref:System.Windows.Markup.DependsOnAttribute>個案例套用至屬性定義。  
  
### <a name="markupextensionreturntypeattribute"></a>MarkupExtensionReturnTypeAttribute  
 **參考檔:**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
 **適用於：** 類別, 應<xref:System.Windows.Markup.MarkupExtension>為衍生類型。  
  
 **參量**, 指定要`ProvideValue`做為屬性<xref:System.Windows.Markup.MarkupExtension>之結果的最精確類型。 <xref:System.Type>  
  
 如需詳細資訊, 請參閱[XAML 的標記延伸總覽](markup-extensions-for-xaml-overview.md)。  
  
### <a name="namescopepropertyattribute"></a>NameScopePropertyAttribute  
 **參考檔:**  <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
 **適用於：** 類別  
  
 **參量**支援兩種形式的屬性:  
  
- 字串, 指定屬性化類型上的屬性名稱。  
  
- 指定屬性名稱的字串, 以及<xref:System.Type>定義命名屬性之類型的。 這個表單是用來指定可附加的成員做為 XAML 名稱範圍屬性。  
  
 <xref:System.Windows.Markup.NameScopePropertyAttribute>指定屬性, 該屬性會提供屬性化類別的 XAML 名稱範圍值。 Xaml 名稱範圍屬性應參考的物件<xref:System.Windows.Markup.INameScope>會執行並保存實際的 XAML 名稱範圍、其存放區和其行為。  
  
### <a name="runtimenamepropertyattribute"></a>RuntimeNamePropertyAttribute  
 **參考檔:**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
 **適用於：** 類別  
  
 **參量**字串, 指定屬性類型上執行時間名稱屬性的名稱。  
  
 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>報告對應至 XAML [x:Name](x-name-directive.md)指示詞的屬性 (property) 型別 (property)。 屬性的類型<xref:System.String>必須是, 而且必須是讀取/寫入。  
  
 定義會繼承至所有可指派給定義類型的衍生類型。 您可以在特定衍生型別上套用, 藉此<xref:System.Windows.Markup.RuntimeNamePropertyAttribute>覆寫特定衍生型別的定義。  
  
### <a name="trimsurroundingwhitespaceattribute"></a>TrimSurroundingWhitespaceAttribute  
 **參考檔:**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
 **適用於：** 型別  
  
 **參量**無。  
  
 <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>會套用至可能會在空白字元中顯示為子項目的特定類型 (具有<xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>的集合所持有的內容)。 <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>主要與儲存路徑有關, 但會藉由檢查<xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType>, 在載入路徑的 XAML 類型系統中提供。 如需詳細資訊, 請參閱[XAML 中](whitespace-processing-in-xaml.md)的空白字元處理。  
  
### <a name="typeconverterattribute"></a>TypeConverterAttribute  
 **參考檔:**  <xref:System.ComponentModel.TypeConverterAttribute>  
  
 **適用於：** 類別、屬性、方法 (唯一的 XAML 有效方法案例是支援可`get`附加成員的存取子)。  
  
 **參量**<xref:System.Type> 的 <xref:System.ComponentModel.TypeConverter>。  
  
 <xref:System.ComponentModel.TypeConverterAttribute>在 XAML 內容中, 會參考<xref:System.ComponentModel.TypeConverter>自訂的。 這<xref:System.ComponentModel.TypeConverter>會提供自訂類型的類型轉換行為, 或該類型的成員。  
  
 您會將<xref:System.ComponentModel.TypeConverterAttribute>屬性套用至您的類型, 並參考您的類型轉換器實作為。 您可以在類別、結構或介面上定義 XAML 的類型轉換器。 您不需要提供列舉的類型轉換, 該轉換原本就會啟用。  
  
 您的類型轉換器應該可以從用於標記中屬性或初始化文字的字串轉換成您想要的目的地類型。 如需詳細資訊, 請參閱[TypeConverters 和 XAML](../wpf/advanced/typeconverters-and-xaml.md)。  
  
 XAML 的類型轉換子行為也可以在特定屬性上建立, 而不是套用至類型的所有值。 在此情況下, 您<xref:System.ComponentModel.TypeConverterAttribute>會將套用至屬性定義 (外部定義, 而不`get`是`set`特定的和定義)。  
  
 您可以藉由<xref:System.ComponentModel.TypeConverterAttribute>將套用`get`至支援 xaml 使用方式的方法存取子, 來指派自訂可附加成員的 XAML 使用類型轉換器行為。  
  
 類似于<xref:System.ComponentModel.TypeConverterAttribute> , 在存在於 XAML 之前, .NET Framework 中存在, 而類型轉換器模型則是針對其他目的而提供。 <xref:System.ComponentModel.TypeConverter> 為了參考和使用<xref:System.ComponentModel.TypeConverterAttribute>, 您必須完整限定它, 或提供的`using`語句<xref:System.ComponentModel>。 您也必須將系統元件包含在專案中。  
  
### <a name="uidpropertyattribute"></a>UidPropertyAttribute  
 **參考檔:**  <xref:System.Windows.Markup.UidPropertyAttribute>  
  
 **適用於：** 類別  
  
 **參量**依名稱參考相關屬性的字串。  
  
 表示類別的 CLR 屬性, 其別名為[x:Uid](x-uid-directive.md)指示詞。  
  
### <a name="usableduringinitializationattribute"></a>UsableDuringInitializationAttribute  
 **參考檔:**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute>  
  
 **適用於：** 類別  
  
 **參量**布林值。 如果用於屬性的預期目的, 應一律將此指定為`true`。  
  
 表示這個類型是否在 XAML 物件圖形建立期間由上而下建置。 這是一種很先進的概念, 這可能與程式設計模型的定義緊密相關。 如需詳細資訊，請參閱 <xref:System.Windows.Markup.UsableDuringInitializationAttribute>。  
  
### <a name="valueserializerattribute"></a>ValueSerializerAttribute  
 **參考檔:**  <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
 **適用於：** 類別、屬性、方法 (唯一的 XAML 有效方法案例是支援可`get`附加成員的存取子)。  
  
 **參量**<xref:System.Type> , 指定序列化屬性化型別的所有屬性時, 或特定的屬性化屬性時, 所要使用的值序列化程式支援類別。  
  
 <xref:System.Windows.Markup.ValueSerializer>指定值序列化類別, 其需要比更多的<xref:System.ComponentModel.TypeConverter>狀態和內容。 <xref:System.Windows.Markup.ValueSerializer>可以在可附加成員的靜態<xref:System.Windows.Markup.ValueSerializerAttribute> `get`存取子方法上套用屬性, 藉此與附加成員相關聯。 值序列化也適用于列舉、介面和結構, 但不適用於委派。  
  
### <a name="whitespacesignificantcollectionattribute"></a>WhitespaceSignificantCollectionAttribute  
 **參考檔:**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
 **適用於：** 類別, 特別是預期裝載混合內容的集合類型, 其中物件元素周圍的空白字元對於 UI 表示可能很重要。  
  
 **參量**無。  
  
 <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>表示集合類型應以泛空白字元的方式處理, XAML 處理器會影響集合內 XAML 節點資料流程的值節點的結構。 如需詳細資訊, 請參閱[XAML 中](whitespace-processing-in-xaml.md)的空白字元處理。  
  
### <a name="xamldeferloadattribute"></a>XamlDeferLoadAttribute  
 **參考檔:**  <xref:System.Windows.Markup.XamlDeferLoadAttribute>  
  
 **適用於：** Class、property。  
  
 **參量**支援兩個屬性形式類型做為字串, 或<xref:System.Type>類型為。 請參閱 <xref:System.Windows.Markup.XamlDeferLoadAttribute>。  
  
 表示類別或屬性具有 XAML 的延遲載入使用方式 (例如範本行為), 並報告啟用延遲行為和其目的地/內容類型的類別。  
  
### <a name="xamlsetmarkupextensionattribute"></a>XamlSetMarkupExtensionAttribute  
 **參考檔:**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute>  
  
 **適用於：** 類別  
  
 **參量**命名回呼。  
  
 表示類別可以使用標記延伸來提供其一個或多個屬性的值, 並參考 XAML 寫入器在對類別的任何屬性執行標記延伸設定作業之前, 應該呼叫的處理常式。  
  
### <a name="xamlsettypeconverterattribute"></a>XamlSetTypeConverterAttribute  
 **參考檔:**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute>  
  
 **適用於：** 類別  
  
 **參量**命名回呼。  
  
 表示類別可以使用類型轉換器來提供其一個或多個屬性的值, 並參考 XAML 寫入器在類別的任何屬性上執行類型轉換器設定作業之前, 應呼叫的處理常式。  
  
### <a name="xmllangpropertyattribute"></a>XmlLangPropertyAttribute  
 **參考檔:**  <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
 **適用於：** 類別  
  
 **參量**字串, 指定要`xml:lang`在屬性化型別上做為別名的屬性名稱。  
  
 <xref:System.Windows.Markup.XmlLangPropertyAttribute>報告對應至 XML `lang`指示詞之屬性類型的屬性。 屬性不一定是類型<xref:System.String>, 但必須可從字串指派 (這可以藉由將類型轉換器與屬性的類型或特定屬性產生關聯來完成)。 屬性必須是讀取/寫入。  
  
 對應的案例`xml:lang`是讓執行時間物件模型可以存取 XML 指定的語言資訊, 而不需要特別處理 XMLDOM。  
  
 定義會繼承至所有可指派給定義類型的衍生類型。 您可以<xref:System.Windows.Markup.XmlLangPropertyAttribute>在特定的衍生型別上套用, 藉此覆寫特定衍生型別的定義, 不過這種情況並不常見。  
  
## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a>元件層級的 XAML 相關 CLR 屬性  
 下列各節描述 XAML 相關的屬性, 這些屬性不會套用至類型或成員定義, 而是會套用至元件。 這些屬性與定義包含要在 XAML 中使用之自訂類型之程式庫的整體目標相關。 某些屬性不一定會直接影響 XAML 節點資料流程, 而是在節點資料流程中傳遞, 供其他取用者使用。 資訊的取用者包括需要 XAML 命名空間資訊和相關前置詞資訊的設計環境或序列化程式。 XAML 架構內容 (包括 .NET Framework XAML 服務預設值) 也會使用此資訊。  
  
### <a name="xmlnscompatiblewithattribute"></a>XmlnsCompatibleWithAttribute  
 **參考檔:**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
 **參量**  
  
- 字串, 指定要納入之 XAML 命名空間的識別碼。  
  
- 字串, 指定可以從上一個引數納入 XAML 命名空間的 XAML 命名空間識別碼。  
  
 <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>指定 XAML 命名空間可以由另一個 XAML 命名空間建立小計。 一般會在預先定義的 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 中指出建立小計的 XAML 命名空間。 這項技術可用來對程式庫中的 XAML 詞彙進行版本控制, 並使其與先前針對先前版本的詞彙所定義的標記相容。  
  
### <a name="xmlnsdefinitionattribute"></a>XmlnsDefinitionAttribute  
 **參考檔:**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
 **參量**  
  
- 字串, 指定要定義的 XAML 命名空間識別碼。  
  
- 命名 CLR 命名空間的字串。 CLR 命名空間應該在您的元件中定義公用類型, 而且至少要有一個 CLR 命名空間類型適用于 XAML 使用方式。  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>指定 XAML 命名空間和 CLR 命名空間之間以每個元件為基礎的對應, 然後由 XAML 物件寫入器或 XAML 架構內容用於類型解析。  
  
 一個<xref:System.Windows.Markup.XmlnsDefinitionAttribute>以上的可以套用至元件。 這可能是因為下列原因的任何組合而完成:  
  
- 程式庫設計包含多個 CLR 命名空間, 適用于執行時間 API 存取的邏輯組織。不過, 您想要透過參考相同的 XAML 命名空間, 讓這些命名空間中的所有類型都可以使用 XAML。 在這種情況下, 您<xref:System.Windows.Markup.XmlnsDefinitionAttribute>會使用相同<xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A>的值, 但<xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A>不同的值來套用數個屬性。 如果您要為 XAML 命名空間定義對應, 而架構或應用程式想要做為一般使用方式的預設 XAML 命名空間, 這會特別有用。  
  
- 程式庫設計包含多個 CLR 命名空間, 而您想要在這些 CLR 命名空間中的類型使用方式之間進行刻意的 XAML 命名空間分隔。  
  
- 您會在元件中定義 CLR 命名空間, 而且您希望它可以透過多個 XAML 命名空間來存取。 當您使用相同的程式碼基底來支援多個詞彙時, 就會發生此情況。  
  
- 您可以在一或多個 CLR 命名空間中定義 XAML 語言支援。 針對這些, 此<xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A>值應該是`http://schemas.microsoft.com/winfx/2006/xaml`。  
  
### <a name="xmlnsprefixattribute"></a>XmlnsPrefixAttribute  
 **參考檔:**  <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
 **參量**  
  
- 指定 XAML 命名空間識別碼的字串。  
  
- 指定建議前置詞的字串。  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>指定要用於 XAML 命名空間的建議前置詞。 在 .NET Framework xaml 服務<xref:System.Xaml.XamlXmlWriter>所序列化的 xaml 檔案中撰寫專案和屬性時, 或當 xaml 執行的程式庫與具有 XAML 編輯功能的設計環境互動時, 前置詞非常有用。  
  
 一個<xref:System.Windows.Markup.XmlnsPrefixAttribute>以上的可以套用至元件。 這可能是因為下列原因的任何組合而完成:  
  
- 您的元件會定義一個以上 XAML 命名空間的類型。 在此情況下, 您應該為每個 XAML 命名空間定義不同的前置詞值。  
  
- 您支援多個詞彙, 並針對每個詞彙和 XAML 命名空間使用不同的首碼。  
  
- 您在元件中定義 XAML 語言支援, 並具有<xref:System.Windows.Markup.XmlnsDefinitionAttribute> `http://schemas.microsoft.com/winfx/2006/xaml`的。 在此情況下, 您通常應該升級前置`x`詞。  
  
> [!NOTE]
>  .NET Framework XAML 服務也會定義與 XAML 相關的<xref:System.Windows.Markup.RootNamespaceAttribute>屬性。 此屬性是專案系統支援的元件層級屬性, 與 XAML 自訂類型無關。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Attribute>
- [定義可搭配 .NET Framework XAML 服務使用的自訂類型](defining-custom-types-for-use-with-net-framework-xaml-services.md)
