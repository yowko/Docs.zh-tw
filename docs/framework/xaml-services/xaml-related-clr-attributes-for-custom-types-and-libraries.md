---
title: 自訂類型和程式庫的 XAML 相關 CLR 屬性
ms.date: 03/30/2017
helpviewer_keywords:
- CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
ms.openlocfilehash: ace1b40b25bd12ff7092459e468a90f382434bf4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086204"
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a>自訂類型和程式庫的 XAML 相關 CLR 屬性
本主題描述由.NET Framework XAML 服務所定義的通用語言執行平台 (CLR) 屬性。 它也會說明其他 CLR 屬性定義在.NET Framework 組件或類型的應用程式的 XAML 相關案例。 屬性的組件、 類型或成員設定這些 CLR 屬性提供 XAML 類型系統資訊與您的型別。 處理 XAML 節點資料流直接或透過專用的 XAML 讀取器和 XAML 寫入器會使用.NET Framework XAML 服務任何 XAML 取用者會提供資訊。  
  
## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a>自訂型別和自訂成員的 XAML 相關 CLR 屬性  
 使用 CLR 屬性需要，您用來定義您的型別整體的 CLR，否則不提供這類屬性。 如果您使用 CLR 定義的類型支援時，.NET Framework XAML 服務 XAML 寫入器所使用的預設 XAML 結構描述內容可以讀取透過反映對備份組件的 CLR 屬性。  
  
 下列各節說明您可以套用至自訂類型或自訂的成員的 XAML 相關屬性。 每個 CLR 屬性會將 XAML 類型系統的相關資訊。 在載入路徑中，屬性化的資訊可能有助於形成有效的 XAML 節點資料流，XAML 讀取器，或最好讓產生有效的物件圖形的 XAML 寫入器。 在儲存路徑，是協助構成有效的 XAML 節點資料流，重組 XAML 類型系統資訊，XAML 讀取器的屬性的資訊或者，它會宣告序列化提示或 XAML 寫入器或其他 XAML 取用者需求。  
  
### <a name="ambientattribute"></a>AmbientAttribute  
 **參考文件：**  <xref:System.Windows.Markup.AmbientAttribute>  
  
 **適用於：** 類別、 屬性或`get`支援可附加屬性的存取子成員。  
  
 **引數：** None  
  
 <xref:System.Windows.Markup.AmbientAttribute> 指出應該解譯屬性或所有屬性的屬性化類型中，在 XAML 中的環境屬性概念。 環境概念與 XAML 處理器如何判斷成員類別擁有者有關。 環境屬性是屬性的值，必須是可用於剖析器內容時建立物件圖形，但典型的型別成員查閱已暫止立即設定所建立的 XAML 節點。  
  
 環境概念可以套用至不會表示為方面如何定義 CLR 屬性的屬性中的可附加成員<xref:System.AttributeTargets>。 方法屬性使用方式應該只是套用`get`XAML 支援可附加的使用方式的存取子。  
  
### <a name="constructorargumentattribute"></a>ConstructorArgumentAttribute  
 **參考文件：**  <xref:System.Windows.Markup.ConstructorArgumentAttribute>  
  
 **適用於：** 類別  
  
 **引數：** 指定符合的單一建構函式引數的屬性名稱的字串。  
  
 <xref:System.Windows.Markup.ConstructorArgumentAttribute> 指定可以使用非預設建構函式語法中初始化物件，並指定名稱的屬性提供建構資訊。 這項資訊主要供 XAML 序列化之用。 如需詳細資訊，請參閱<xref:System.Windows.Markup.ConstructorArgumentAttribute>。  
  
### <a name="contentpropertyattribute"></a>ContentPropertyAttribute  
 **參考文件：**  <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
 **適用於：** 類別  
  
 **引數：** 字串，指定名稱的屬性化型別的成員。  
  
 <xref:System.Windows.Markup.ContentPropertyAttribute> 表示引數所命名的屬性，應該做為該類型的 XAML 內容屬性。 XAML 內容屬性定義會繼承所有可指派給定義類型的衍生型別。 您可以藉由套用覆寫特定的衍生型別上定義<xref:System.Windows.Markup.ContentPropertyAttribute>特定衍生型別。  
  
 做為 XAML 內容屬性的屬性，屬性標記的屬性項目可以在 XAML 用法中省略。 一般而言，您會指定升級您的內容和內含項目模型簡化的 XAML 標記的 XAML 內容屬性。 因為只有一個成員可以指定為 XAML 內容屬性中，有時會有數個容器的哪些類型的屬性應該指定為 XAML 內容屬性進行的設計選擇。 使用明確的屬性項目，必須使用其他容器屬性。  
  
 在 XAML 節點資料流，XAML 內容屬性仍會產生`StartMember`並`EndMember`使用的屬性名稱的節點<xref:System.Xaml.XamlMember>。 若要判斷成員是否為 XAML 內容屬性，檢查<xref:System.Xaml.XamlType>值從`StartObject`位置，並取得的值<xref:System.Xaml.XamlType.ContentProperty%2A>。  
  
### <a name="contentwrapperattribute"></a>ContentWrapperAttribute  
 **參考文件：**  <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
 **適用於：** 類別，尤其是集合型別。  
  
 **引數：** A <xref:System.Type> ，指定要使用的內容包裝函式型別做為外部索引內容的型別。  
  
 <xref:System.Windows.Markup.ContentWrapperAttribute> 指定將用來包裝外部內容的相關聯的集合型別上的一個或多個類型。 外部內容是指，型別系統條件約束，內容屬性的型別上沒有擷取所有可能內容的情況下，可支援擁有類型的 XAML 用法的案例。 比方說，XAML 支援特定類型的內容可能會在強型別泛型支援字串<xref:System.Collections.ObjectModel.Collection%601>。 內容包裝函式可用於為 XAML 的一輩子的指派值的集合，例如移轉文字相關的內容模型移轉現有的標記慣例。  
  
 若要指定多個內容包裝函式類型，請套用屬性多次。  
  
### <a name="dependsonattribute"></a>DependsOnAttribute  
 **參考文件：**  <xref:System.Windows.Markup.DependsOnAttribute>  
  
 **適用於：** 屬性  
  
 **引數：** 字串，指定的屬性化類型的另一個成員的名稱。  
  
 <xref:System.Windows.Markup.DependsOnAttribute> 指出屬性化的屬性相依於另一個屬性的值。 將這個屬性套用至屬性定義，可確保相依的屬性，會先處理中 XAML 物件寫入。 使用方式的<xref:System.Windows.Markup.DependsOnAttribute>其中剖析的特定順序必須遵循有效的物件建立的類型上指定屬性例外狀況。  
  
 您可以套用多個<xref:System.Windows.Markup.DependsOnAttribute>至屬性定義的情況。  
  
### <a name="markupextensionreturntypeattribute"></a>MarkupExtensionReturnTypeAttribute  
 **參考文件：**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
 **適用於：** 類別，應該要<xref:System.Windows.Markup.MarkupExtension>衍生型別。  
  
 **引數：** A <xref:System.Type> ，指定最精確的類型為預期`ProvideValue`結果的屬性化<xref:System.Windows.Markup.MarkupExtension>。  
  
 如需詳細資訊，請參閱 < [Markup Extensions for XAML Overview](markup-extensions-for-xaml-overview.md)。  
  
### <a name="namescopepropertyattribute"></a>NameScopePropertyAttribute  
 **參考文件：**  <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
 **適用於：** 類別  
  
 **引數：** 支援兩種形式的屬性：  
  
-   屬性化類型指定的屬性名稱的字串。  
  
-   字串，指定名稱的屬性，以及<xref:System.Type>用於定義具名的屬性的型別。 此表單是用來指定可附加成員的 XAML 名稱範圍屬性。  
  
 <xref:System.Windows.Markup.NameScopePropertyAttribute> 指定提供 XAML namescope 值屬性化類別的屬性。 XAML 名稱範圍屬性應參考該物件會實作<xref:System.Windows.Markup.INameScope>並保留實際 XAML 名稱範圍，其存放區，其行為。  
  
### <a name="runtimenamepropertyattribute"></a>RuntimeNamePropertyAttribute  
 **參考文件：**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
 **適用於：** 類別  
  
 **引數：** 字串，指定屬性化型別上的執行階段名稱屬性的名稱。  
  
 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> 報告的屬性對應到 XAML 的屬性化型別[X:name 指示詞](x-name-directive.md)。 屬性必須是型別<xref:System.String>，而且必須是讀取/寫入。  
  
 定義繼承可指派給定義類型的所有衍生類型。 您可以藉由套用覆寫特定的衍生型別上定義<xref:System.Windows.Markup.RuntimeNamePropertyAttribute>特定衍生型別。  
  
### <a name="trimsurroundingwhitespaceattribute"></a>TrimSurroundingWhitespaceAttribute  
 **參考文件：**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
 **適用於：** 型別  
  
 **引數：** 無。  
  
 <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> 會套用至特定可能顯示為顯著泛空白字元的內容中的子元素的類型 (內容持有的集合，其中具有<xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>)。 <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> 主要是與儲存的路徑，但可在載入路徑 XAML 類型系統中藉由檢查<xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType>。 如需詳細資訊，請參閱 <<c0> [ 泛空白字元處理中 XAML](whitespace-processing-in-xaml.md)。  
  
### <a name="typeconverterattribute"></a>TypeConverterAttribute  
 **參考文件：**  <xref:System.ComponentModel.TypeConverterAttribute>  
  
 **適用於：** 類別、 屬性、 方法 (唯一 XAML 有效的方法案例是`get`支援可附加成員的存取子)。  
  
 **引數：**<xref:System.Type> 的 <xref:System.ComponentModel.TypeConverter>。  
  
 <xref:System.ComponentModel.TypeConverterAttribute> 在 XAML 內容參考自訂<xref:System.ComponentModel.TypeConverter>。 這<xref:System.ComponentModel.TypeConverter>提供自訂型別，或該類型的成員的型別轉換行為。  
  
 您套用<xref:System.ComponentModel.TypeConverterAttribute>屬性設定為您的型別，參考型別轉換子實作。 您可以定義為 XAML 型別轉換子類別、 結構或介面。 您不需要提供的列舉型別轉換，轉換會以原生方式啟用。  
  
 您的型別轉換子，應該能夠從或所用的屬性初始設定文字在標記中，為您想要的目的地類型的字串轉換。 如需詳細資訊，請參閱 < [TypeConverters 和 XAML](../wpf/advanced/typeconverters-and-xaml.md)。  
  
 而不是套用至類型的所有值，XAML 類型轉換器行為可以建立特定的屬性。 在此情況下，您套用<xref:System.ComponentModel.TypeConverterAttribute>屬性定義 (外部定義、 非特定`get`和`set`定義)。  
  
 可以指派自訂的可附加成員的 XAML 用法型別轉換子行為，藉由套用<xref:System.ComponentModel.TypeConverterAttribute>至`get`支援 XAML 用法的方法存取子。  
  
 類似於<xref:System.ComponentModel.TypeConverter>，<xref:System.ComponentModel.TypeConverterAttribute>存在於 XAML，面市之前的.NET Framework 中，而且型別轉換子模型提供的其他用途。 若要參考及使用<xref:System.ComponentModel.TypeConverterAttribute>，您必須完整限定它，或提供`using`陳述式<xref:System.ComponentModel>。 您也必須在專案中包含系統組件。  
  
### <a name="uidpropertyattribute"></a>UidPropertyAttribute  
 **參考文件：**  <xref:System.Windows.Markup.UidPropertyAttribute>  
  
 **適用於：** 類別  
  
 **引數：** 依名稱參考相關屬性的字串。  
  
 表示類別的 CLR 屬性別名[X:uid 指示詞](x-uid-directive.md)。  
  
### <a name="usableduringinitializationattribute"></a>UsableDuringInitializationAttribute  
 **參考文件：**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute>  
  
 **適用於：** 類別  
  
 **引數：** 布林值。 如果使用屬性的目的，這應該一律指定為`true`。  
  
 表示這個類型是否在 XAML 物件圖形建立期間由上而下建置。 這是進階的概念，與您的程式設計模型的定義可能密切相關。 如需詳細資訊，請參閱<xref:System.Windows.Markup.UsableDuringInitializationAttribute>。  
  
### <a name="valueserializerattribute"></a>ValueSerializerAttribute  
 **參考文件：**  <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
 **適用於：** 類別、 屬性、 方法 (唯一 XAML 有效的方法案例是`get`支援可附加成員的存取子)。  
  
 **引數：** A <xref:System.Type> ，指定用於在序列化的屬性化類型中，所有屬性的值序列化程式支援類別或特定屬性的屬性。  
  
 <xref:System.Windows.Markup.ValueSerializer> 指定需要更多的狀態和內容的值序列化類別<xref:System.ComponentModel.TypeConverter>沒有。 <xref:System.Windows.Markup.ValueSerializer> 可以藉由套用可附加成員與相關聯<xref:System.Windows.Markup.ValueSerializerAttribute>上的靜態屬性`get`之可附加成員的存取子方法。 值序列化也適用於列舉、 介面和結構，但不適用於委派。  
  
### <a name="whitespacesignificantcollectionattribute"></a>WhitespaceSignificantCollectionAttribute  
 **參考文件：**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
 **適用於：** 類別，特別是裝載混合的內容，其中物件項目周圍的空白字元可能會造成很大 UI 表示法預期集合型別。  
  
 **引數：** 無。  
  
 <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> 表示集合型別應該處理為泛空白字元顯著，XAML 處理器，這會影響建構的 XAML 節點資料流的值集合中的節點。 如需詳細資訊，請參閱 <<c0> [ 泛空白字元處理中 XAML](whitespace-processing-in-xaml.md)。  
  
### <a name="xamldeferloadattribute"></a>XamlDeferLoadAttribute  
 **參考文件：**  <xref:System.Windows.Markup.XamlDeferLoadAttribute>  
  
 **適用於：** 類別屬性。  
  
 **引數：** 支援兩個屬性形成類型視為字串，或為<xref:System.Type>。 請參閱 <xref:System.Windows.Markup.XamlDeferLoadAttribute>。  
  
 表示類別或屬性具有 XAML 的延後的載入使用方式 （例如，範本行為），並報告啟用延後的行為和其目的地/內容型別類別。  
  
### <a name="xamlsetmarkupextensionattribute"></a>XamlSetMarkupExtensionAttribute  
 **參考文件：**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute>  
  
 **適用於：** 類別  
  
 **引數：** 命名的回呼。  
  
 表示類別可以使用標記延伸的一個或多個屬性，提供的值，以及參考的 XAML 寫入器應該呼叫在執行類別的任何屬性上的標記延伸設定作業之前的處理常式。  
  
### <a name="xamlsettypeconverterattribute"></a>XamlSetTypeConverterAttribute  
 **參考文件：**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute>  
  
 **適用於：** 類別  
  
 **引數：** 命名的回呼。  
  
 表示類別可以使用型別轉換子的一個或多個屬性，提供的值，以及參考的 XAML 寫入器應該呼叫在執行類別的任何屬性的型別轉換子設定作業之前的處理常式。  
  
### <a name="xmllangpropertyattribute"></a>XmlLangPropertyAttribute  
 **參考文件：**  <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
 **適用於：** 類別  
  
 **引數：** 字串，指定別名的屬性名稱`xml:lang`屬性化型別上。  
  
 <xref:System.Windows.Markup.XmlLangPropertyAttribute> 報告的屬性化型別對應至 XML 屬性`lang`指示詞。 屬性不是一定的型別<xref:System.String>，但必須可從字串 （這可藉由建立關聯型別轉換子，屬性的類型或特定的屬性）。 屬性必須是讀取/寫入。  
  
 對應的案例`xml:lang`會使執行階段物件模型而不需特別處理使用 XMLDOM 具有 XML 指定的語言資訊的存取權。  
  
 定義繼承可指派給定義類型的所有衍生類型。 您可以藉由套用覆寫特定的衍生型別上定義<xref:System.Windows.Markup.XmlLangPropertyAttribute>特定衍生型別，雖然這是常見的案例。  
  
## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a>組件層級的 XAML 相關 CLR 屬性  
 下列各節描述的 XAML 相關的屬性不會套用至類型或成員的定義，但會改為套用至組件。 這些屬性是與整體目標是要定義包含在 XAML 中使用的自訂型別程式庫相關。 有些屬性不一定影響 XAML 節點資料流直接，但會傳遞其他取用者使用的節點資料流中。 如需資訊的取用者包括設計環境或序列化程序，需要 XAML 命名空間的資訊和相關聯的前置詞資訊。 XAML 結構描述內容 （包括.NET Framework XAML 服務預設值） 也會使用這項資訊。  
  
### <a name="xmlnscompatiblewithattribute"></a>XmlnsCompatibleWithAttribute  
 **參考文件：**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
 **引數：**  
  
-   字串，指定要包含的 XAML 命名空間的識別項。  
  
-   字串，指定可以包含從先前的引數的 XAML 命名空間的 XAML 命名空間的識別碼。  
  
 <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute> 指定可以在另一個 XAML 命名空間建立小計的 XAML 命名空間。 一般會在預先定義的 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 中指出建立小計的 XAML 命名空間。 這種方式可用於版本控制 XAML 詞彙的文件庫中，並讓它與先前定義的標記，針對稍早的版本控制詞彙相容。  
  
### <a name="xmlnsdefinitionattribute"></a>XmlnsDefinitionAttribute  
 **參考文件：**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
 **引數：**  
  
-   字串，指定定義的 XAML 命名空間的識別碼。  
  
-   字串，可命名 CLR 命名空間。 CLR 命名空間應該在您的組件中定義公用型別，並至少一個 CLR 命名空間型別應該適合 XAML 用法。  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 指定 XAML 命名空間與 CLR 命名空間，然後用於類型解析的 XAML 物件寫入器或 XAML 結構描述內容之間以每個組件為基礎的對應。  
  
 多個<xref:System.Windows.Markup.XmlnsDefinitionAttribute>可以套用至組件。 達成此目的任何組合的原因如下：  
  
-   程式庫設計包含多個 CLR 命名空間，針對邏輯組織的執行階段 API 存取權限;不過，您會想要由 XAML 可參考相同的 XAML 命名空間在這些命名空間中的所有型別。 在此情況下，套用數個<xref:System.Windows.Markup.XmlnsDefinitionAttribute>屬性使用相同<xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A>值但不同<xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A>值。 這是特別有用，如果您要定義 framework 或應用程式想要預設 XAML 命名空間中常見的用法的 XAML 命名空間的對應。  
  
-   程式庫設計包含多個 CLR 命名空間，而且您想在審慎 XAML 命名空間之間的分隔的這些 CLR 命名空間中類型的使用方式。  
  
-   您定義的 CLR 命名空間的組件，而您希望它可透過一個以上的 XAML 命名空間。 若要支援具有相同的程式碼基底的多個詞彙，就會發生這種情況。  
  
-   您可以定義 XAML 語言支援一或多個 CLR 命名空間中。 對於這些<xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A>值應該是`http://schemas.microsoft.com/winfx/2006/xaml`。  
  
### <a name="xmlnsprefixattribute"></a>XmlnsPrefixAttribute  
 **參考文件：**  <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
 **引數：**  
  
-   字串，指定的 XAML 命名空間識別項。  
  
-   字串，指定建議的前置詞。  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 指定要用於 XAML 命名空間的建議前置詞。 寫入項目和屬性的 XAML 檔案中，序列化的.NET Framework XAML 服務時很有用的前置詞，是<xref:System.Xaml.XamlXmlWriter>，或當 XAML 實作的程式庫互動的設計環境具有 XAML 編輯功能。  
  
 多個<xref:System.Windows.Markup.XmlnsPrefixAttribute>可以套用至組件。 達成此目的任何組合的原因如下：  
  
-   您的組件會定義一個以上的 XAML 命名空間的類型。 在此情況下，您應該定義每個 XAML 命名空間的不同前置詞值。  
  
-   您要支援多個詞彙，而且您使用不同的前置詞為每個詞彙和 XAML 命名空間。  
  
-   您定義組件中的 XAML 語言支援，並讓<xref:System.Windows.Markup.XmlnsDefinitionAttribute>針對`http://schemas.microsoft.com/winfx/2006/xaml`。 在此情況下，您通常應該升級前置詞`x`。  
  
> [!NOTE]
>  .NET framework XAML 服務也會定義的 XAML 相關屬性<xref:System.Windows.Markup.RootNamespaceAttribute>。 這個屬性是專案系統支援的組件層級屬性，並不是與 XAML 自訂型別相關。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Attribute>
- [定義可搭配 .NET Framework XAML 服務使用的自訂類型](defining-custom-types-for-use-with-net-framework-xaml-services.md)
