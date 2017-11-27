---
title: "自訂類型和程式庫的 XAML 相關 CLR 屬性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 9a445d7e730ecb743d5e4086ec682b12a7bf3ff9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a>自訂類型和程式庫的 XAML 相關 CLR 屬性
本主題會描述通用語言執行階段 (CLR) 屬性所定義的.NET Framework XAML 服務。 它也會說明其他 CLR 具有的屬性定義在.NET Framework 組件或類型的應用程式的 XAML 相關案例。 屬性的組件、 類型或成員設定這些 CLR 屬性提供 XAML 類型系統資訊與您的型別。 任何直接處理 XAML 節點資料流，或透過專用的 XAML 讀取器和 XAML 寫入器會使用.NET Framework XAML 服務的 XAML 取用者會提供資訊。  
  
## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a>自訂型別和自訂成員的 XAML 相關 CLR 屬性  
 使用 CLR 屬性牽涉到您用來定義您的型別整體的 CLR，否則不可以使用這類屬性。 如果您使用 CLR 定義支援的型別時，.NET Framework XAML 服務 XAML 寫入器所使用的預設 XAML 結構描述內容可以讀取透過反映來針對備份組件的 CLR 屬性。  
  
 下列各節說明您可以套用至自訂類型或自訂成員的 XAML 相關屬性。 每個 CLR 屬性通訊與 XAML 類型系統有關的資訊。 在載入路徑中，屬性化的資訊可能有助於形成有效的 XAML 節點資料流，XAML 讀取器或它可協助產生有效的物件圖形的 XAML 寫入器。 在儲存路徑，是可幫助形成有效的 XAML 節點資料流，XAML 類型系統資訊，重新組成的 XAML 讀取器的屬性的資訊或其宣告序列化提示或 XAML 寫入器或其他 XAML 取用者的需求。  
  
### <a name="ambientattribute"></a>AmbientAttribute  
 **參考文件：**  <xref:System.Windows.Markup.AmbientAttribute>  
  
 **適用於：**類別屬性，或`get`支援可附加屬性的存取子成員。  
  
 **引數：**無  
  
 <xref:System.Windows.Markup.AmbientAttribute>表示屬性或使用屬性化型別的所有屬性，應在 XAML 中的環境屬性概念解譯。 環境概念與 XAML 處理器如何判斷成員類別擁有者有關。 環境的屬性是屬性預期的可供使用的剖析器的內容中建立物件圖形，但在暫止立即的 XAML 節點集所建立的一般型別成員查閱值。  
  
 環境概念可以套用到可附加成員，不會表示為 CLR 屬性會定義如何根據屬性<xref:System.AttributeTargets>。 方法屬性使用方式應該只是套用`get`xaml 支援可附加的使用方式的存取子。  
  
### <a name="constructorargumentattribute"></a>ConstructorArgumentAttribute  
 **參考文件：**  <xref:System.Windows.Markup.ConstructorArgumentAttribute>  
  
 **適用於：**類別  
  
 **引數：**指定比對單一建構函式引數的屬性名稱的字串。  
  
 <xref:System.Windows.Markup.ConstructorArgumentAttribute>指定可以使用非預設建構函式語法中初始化物件，並指定名稱的屬性提供建構資訊。 這項資訊主要供 XAML 序列化之用。 如需詳細資訊，請參閱<xref:System.Windows.Markup.ConstructorArgumentAttribute>。  
  
### <a name="contentpropertyattribute"></a>ContentPropertyAttribute  
 **參考文件：**  <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
 **適用於：**類別  
  
 **引數：**指定成員的屬性化型別名稱的字串。  
  
 <xref:System.Windows.Markup.ContentPropertyAttribute>表示引數所命名的屬性應該做為該類型的 XAML 內容屬性。 XAML 內容屬性定義會繼承所有可指派給定義類型的衍生型別。 您可以藉由套用覆寫特定衍生類型上的定義<xref:System.Windows.Markup.ContentPropertyAttribute>特定衍生型別。  
  
 做為 XAML 內容屬性的屬性，可以省略屬性標記的屬性項目中 XAML 用法。 一般而言，您會指定升級的內容和內含項目模型簡化的 XAML 標記的 XAML 內容屬性。 因為只有一個成員可以指定為 XAML 內容屬性中，您有時候必須設計選擇，可以讓數個容器的哪些類型的屬性應該指定為 XAML 內容屬性。 其他容器屬性必須使用具有明確的屬性項目。  
  
 在 XAML 節點資料流，XAML 內容屬性，仍可能產生`StartMember`和`EndMember`使用的屬性名稱的節點<xref:System.Xaml.XamlMember>。 若要判斷成員是否為 XAML 內容屬性，檢查<xref:System.Xaml.XamlType>值`StartObject`定位和取得的值， <xref:System.Xaml.XamlType.ContentProperty%2A>。  
  
### <a name="contentwrapperattribute"></a>ContentWrapperAttribute  
 **參考文件：**  <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
 **適用於：**類別，尤其是集合型別。  
  
 **引數：** A <xref:System.Type> ，指定要使用的內容包裝函式類型做為外部內容類型。  
  
 <xref:System.Windows.Markup.ContentWrapperAttribute>將用來包裝外部內容的相關聯的集合型別上指定一個或多個類型。 外部內容是指其中內容屬性的型別上的型別系統條件約束沒有擷取所有可能的擁有者類型的 XAML 用法原本支援的內容案例的情況下。 比方說，XAML 支援特定類型的內容可能會支援字串中的強型別的泛型<xref:System.Collections.ObjectModel.Collection%601>。 內容包裝函式可用於為 XAML 的概念，可指派值的集合，例如移轉相關的文字內容模型的移轉預先存在的標記慣例。  
  
 若要指定多個內容包裝函式類型，將屬性套用多次。  
  
### <a name="dependsonattribute"></a>DependsOnAttribute  
 **參考文件：**  <xref:System.Windows.Markup.DependsOnAttribute>  
  
 **適用於：**屬性  
  
 **引數：**字串，指定的屬性化類型的另一個成員的名稱。  
  
 <xref:System.Windows.Markup.DependsOnAttribute>表示屬性化的屬性，取決於另一個屬性的值。 將此屬性套用至屬性定義，可確保相依的屬性，會先處理 XAML 物件寫入。 使用方式的<xref:System.Windows.Markup.DependsOnAttribute>建立有效的物件必須遵循剖析特定順序的型別上指定例外的情況下的屬性。  
  
 您可以套用多個<xref:System.Windows.Markup.DependsOnAttribute>至屬性定義的情況。  
  
### <a name="markupextensionreturntypeattribute"></a>MarkupExtensionReturnTypeAttribute  
 **參考文件：**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
 **適用於：**類別，應該是<xref:System.Windows.Markup.MarkupExtension>衍生型別。  
  
 **引數：** A <xref:System.Type> ，指定最精確的類型，預期為`ProvideValue`結果的屬性化<xref:System.Windows.Markup.MarkupExtension>。  
  
 如需詳細資訊，請參閱[標記延伸 XAML 概觀](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md)。  
  
### <a name="namescopepropertyattribute"></a>NameScopePropertyAttribute  
 **參考文件：**  <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
 **適用於：**類別  
  
 **引數：**支援兩種屬性：  
  
-   屬性化型別指定的屬性名稱的字串。  
  
-   字串，指定屬性的名稱，以及<xref:System.Type>所定義之具名的屬性的類型。 這種形式是為 XAML namescope 屬性指定可附加的成員。  
  
 <xref:System.Windows.Markup.NameScopePropertyAttribute>指定提供 XAML namescope 值屬性化類別的屬性。 XAML namescope 屬性應參考該物件會實作<xref:System.Windows.Markup.INameScope>和保存實際的 XAML 名稱範圍，其存放區，其行為。  
  
### <a name="runtimenamepropertyattribute"></a>RuntimeNamePropertyAttribute  
 **參考文件：**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
 **適用於：**類別  
  
 **引數：**屬性化型別指定執行階段名稱屬性名稱的字串。  
  
 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>報告的屬性化類型對應至 XAML 屬性[X:name 指示詞](../../../docs/framework/xaml-services/x-name-directive.md)。 屬性必須是型別<xref:System.String>，而且必須是讀取/寫入。  
  
 定義繼承所有可指派給定義類型的衍生型別。 您可以藉由套用覆寫特定衍生類型上的定義<xref:System.Windows.Markup.RuntimeNamePropertyAttribute>特定衍生型別。  
  
### <a name="trimsurroundingwhitespaceattribute"></a>TrimSurroundingWhitespaceAttribute  
 **參考文件：**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
 **適用於：**類型  
  
 **引數：** None。  
  
 <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>會套用至可能會以空白字元重要內容中的子項目出現的特定類型 (內容持有的集合，其中具有<xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>)。 <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>大致上是相關的儲存路徑，但卻是在載入路徑 XAML 類型系統所提供藉由檢查<xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType>。 如需詳細資訊，請參閱[XAML 中的空白字元處理](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)。  
  
### <a name="typeconverterattribute"></a>TypeConverterAttribute  
 **參考文件：**  <xref:System.ComponentModel.TypeConverterAttribute>  
  
 **適用於：**類別、 屬性、 方法 (唯一 XAML 有效的方法則是`get`存取子，支援可附加的成員)。  
  
 **引數：** <xref:System.Type>的<xref:System.ComponentModel.TypeConverter>。  
  
 <xref:System.ComponentModel.TypeConverterAttribute>在 XAML 內容參考自訂<xref:System.ComponentModel.TypeConverter>。 這<xref:System.ComponentModel.TypeConverter>提供自訂型別或該類型的成員的類型轉換行為。  
  
 您套用<xref:System.ComponentModel.TypeConverterAttribute>屬性設定為您的型別，請參考您的型別轉換子實作。 您可以定義 XAML 的類型轉換器類別、 結構或介面。 您不需要提供型別轉換為列舉型別轉換已啟用原生。  
  
 類型轉換器應該能夠從字串用於屬性或在標記中，初始文字轉換預定的目的地類型轉換。 如需詳細資訊，請參閱[TypeConverters 和 XAML](../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md)。  
  
 而不是套用至所有值的類型，xaml 的類型轉換器行為可建立在特定的屬性。 在此情況下，您將套用<xref:System.ComponentModel.TypeConverterAttribute>至 property 定義 (外部定義、 非特有`get`和`set`定義)。  
  
 自訂的可附加成員的 XAML 用法的類型轉換器行為可以藉由套用指派<xref:System.ComponentModel.TypeConverterAttribute>至`get`支援 XAML 用法的方法存取子。  
  
 類似於<xref:System.ComponentModel.TypeConverter>，<xref:System.ComponentModel.TypeConverterAttribute>存在於 XAML，面市之前的.NET Framework 中，而類型轉換器模型提供的其他用途。 若要參考及使用<xref:System.ComponentModel.TypeConverterAttribute>，您必須完整限定它，或提供`using`陳述式<xref:System.ComponentModel>。 您也必須包含在專案中的系統組件。  
  
### <a name="uidpropertyattribute"></a>UidPropertyAttribute  
 **參考文件：**  <xref:System.Windows.Markup.UidPropertyAttribute>  
  
 **適用於：**類別  
  
 **引數：**參考相關的屬性名稱的字串。  
  
 表示的 CLR 屬性的類別別名[X:uid 指示詞](../../../docs/framework/xaml-services/x-uid-directive.md)。  
  
### <a name="usableduringinitializationattribute"></a>UsableDuringInitializationAttribute  
 **參考文件：**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute>  
  
 **適用於：**類別  
  
 **引數：**布林值。 如果用於屬性的使用目的，這應該一律指定為`true`。  
  
 表示這個類型是否在 XAML 物件圖形建立期間由上而下建置。 這是進階的概念，與您的程式設計模型的定義可能密切相關。 如需詳細資訊，請參閱<xref:System.Windows.Markup.UsableDuringInitializationAttribute>。  
  
### <a name="valueserializerattribute"></a>ValueSerializerAttribute  
 **參考文件：**  <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
 **適用於：**類別、 屬性、 方法 (唯一 XAML 有效的方法則是`get`存取子，支援可附加的成員)。  
  
 **引數：** A<xref:System.Type>指定值序列化程式支援類別，用於在序列化的屬性化類型中，所有屬性，或是特定屬性的屬性。  
  
 <xref:System.Windows.Markup.ValueSerializer>指定需要更多的狀態和內容的值序列化類別<xref:System.ComponentModel.TypeConverter>沒有。 <xref:System.Windows.Markup.ValueSerializer>可以藉由套用可附加成員與相關聯<xref:System.Windows.Markup.ValueSerializerAttribute>上靜態屬性`get`可附加成員的存取子方法。 值序列化也適用於列舉型別、 介面和結構，但不適用於委派。  
  
### <a name="whitespacesignificantcollectionattribute"></a>WhitespaceSignificantCollectionAttribute  
 **參考文件：**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
 **適用於：**類別，特別是預期的混合的內容，裝載在物件項目周圍的空白字元可能會顯著 UI 表示法的集合型別。  
  
 **引數：** None。  
  
 <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>表示集合型別應該處理為空白字元，XAML 處理器，會影響集合內的 XAML 節點資料流值節點建構。 如需詳細資訊，請參閱[XAML 中的空白字元處理](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)。  
  
### <a name="xamldeferloadattribute"></a>XamlDeferLoadAttribute  
 **參考文件：**  <xref:System.Windows.Markup.XamlDeferLoadAttribute>  
  
 **適用於：**類別屬性。  
  
 **引數：**支援兩個屬性會形成類型為字串，或類型為<xref:System.Type>。 請參閱 <xref:System.Windows.Markup.XamlDeferLoadAttribute>。  
  
 表示類別或屬性具有 XAML 延後的載入使用量 （例如範本行為），並報告類別，可讓延後的行為和目的地/內容型別。  
  
### <a name="xamlsetmarkupextensionattribute"></a>XamlSetMarkupExtensionAttribute  
 **參考文件：**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute>  
  
 **適用於：**類別  
  
 **引數：**命名回呼。  
  
 表示類別可以使用標記延伸的一個或多個屬性，提供的值，而且參考的 XAML 寫入器應該在之前執行任何屬性的類別上的標記延伸模組組作業呼叫的處理常式。  
  
### <a name="xamlsettypeconverterattribute"></a>XamlSetTypeConverterAttribute  
 **參考文件：**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute>  
  
 **適用於：**類別  
  
 **引數：**命名回呼。  
  
 表示類別可以使用類型轉換器，來提供值的一個或多個屬性，而且參考的 XAML 寫入器應該在之前執行上類別的任何屬性的型別轉換子組作業呼叫的處理常式。  
  
### <a name="xmllangpropertyattribute"></a>XmlLangPropertyAttribute  
 **參考文件：**  <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
 **適用於：**類別  
  
 **引數：**指定別名的屬性名稱的字串`xml:lang`屬性化型別上。  
  
 <xref:System.Windows.Markup.XmlLangPropertyAttribute>報告的屬性化類型對應至 XML 屬性`lang`指示詞。 屬性不是一定的型別<xref:System.String>，但必須是可從 （做到這一點無法關聯型別轉換子，屬性的型別，或特定的屬性） 的字串。 屬性必須是讀取/寫入。  
  
 對應的實例`xml:lang`會使執行階段物件模型而不需特別處理 XMLDOM 與已指定 XML 語言資訊的存取權。  
  
 定義繼承所有可指派給定義類型的衍生型別。 您可以藉由套用覆寫特定衍生類型上的定義<xref:System.Windows.Markup.XmlLangPropertyAttribute>特定衍生型別，但不常見的案例。  
  
## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a>組件層級的 XAML 相關 CLR 屬性  
 下列章節說明的 XAML 相關的屬性不會套用至類型或成員定義中，但會改為套用至組件。 這些屬性所相關的定義包含在 XAML 中使用的自訂型別程式庫的整體目標。 有些屬性不一定影響 XAML 節點資料流直接，但是會傳遞為使用其他取用者在節點資料流。 取用者的資訊包括設計環境或序列化程序需要 XAML 命名空間資訊及相關聯的前置詞資訊。 XAML 結構描述內容 （包括.NET Framework XAML 服務預設值） 也會使用這項資訊。  
  
### <a name="xmlnscompatiblewithattribute"></a>XmlnsCompatibleWithAttribute  
 **參考文件：**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
 **引數：**  
  
-   字串，指定而已 XAML 命名空間識別項。  
  
-   字串，指定可以而已 XAML 命名空間，從先前的引數的 XAML 命名空間識別項。  
  
 <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>指定可以在另一個 XAML 命名空間建立小計的 XAML 命名空間。 一般而言，會指出歸類 XAML 命名空間中預先定義<xref:System.Windows.Markup.XmlnsDefinitionAttribute>。 這項技術可用於 XAML 詞彙的文件庫中，並讓它與先前定義的標記，針對稍早的版本設定詞彙相容版本。  
  
### <a name="xmlnsdefinitionattribute"></a>XmlnsDefinitionAttribute  
 **參考文件：**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
 **引數：**  
  
-   字串，指定 XAML 命名空間定義的識別項。  
  
-   命名的 CLR 命名空間的字串。 CLR 命名空間應該組件中定義的公用型別，至少一個 CLR 命名空間類型應該用於 XAML 用法。  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>每個組件為基礎的 XAML 命名空間與 CLR 命名空間，然後使用型別解析 XAML 物件寫入器或 XAML 結構描述內容所指定的對應。  
  
 多個<xref:System.Windows.Markup.XmlnsDefinitionAttribute>可以套用至組件。 這可能會基於下列原因所造成的任何組合：  
  
-   程式庫設計包含多個 CLR 命名空間的執行階段應用程式開發介面存取; 的邏輯組織不過，您會想要由 XAML 可參考相同的 XAML 命名空間在這些命名空間中的所有型別。 在此情況下，套用數個<xref:System.Windows.Markup.XmlnsDefinitionAttribute>屬性使用相同<xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A>值但不同<xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A>值。 這是特別有用，如果您要定義 framework 或應用程式想要預設 XAML 命名空間中常見的用法的 XAML 命名空間的對應。  
  
-   程式庫設計包含多個 CLR 命名空間，而且您想刻意 XAML 命名空間的區隔這些 CLR 命名空間中類型的用法。  
  
-   您定義的 CLR 命名空間的組件，而且希望能夠透過一個以上的 XAML 命名空間。 若要支援具有相同的程式碼基底的多個詞彙，就會發生此情況。  
  
-   您可以定義 XAML 語言支援一或多個 CLR 命名空間中。 對於這些<xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A>值應該是`http://schemas.microsoft.com/winfx/2006/xaml`。  
  
### <a name="xmlnsprefixattribute"></a>XmlnsPrefixAttribute  
 **參考文件：**  <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
 **引數：**  
  
-   指定的 XAML 命名空間識別項的字串。  
  
-   指定的建議前置詞的字串。  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>指定要用於 XAML 命名空間的建議前置詞。 前置詞時，寫入序列化的.NET Framework XAML 服務 XAML 檔案中的項目和屬性<xref:System.Xaml.XamlXmlWriter>，或實作 XAML 的程式庫互動設計環境具有 XAML 編輯功能。  
  
 多個<xref:System.Windows.Markup.XmlnsPrefixAttribute>可以套用至組件。 這可能會基於下列原因所造成的任何組合：  
  
-   您的組件會定義一個以上的 XAML 命名空間的類型。 在此情況下，您應該定義每個 XAML 命名空間的不同前置詞值。  
  
-   您要支援多個詞彙，而且您使用不同的前置詞為每個詞彙和 XAML 命名空間。  
  
-   您的組件中定義 XAML 語言支援，且有<xref:System.Windows.Markup.XmlnsDefinitionAttribute>如`http://schemas.microsoft.com/winfx/2006/xaml`。 在此情況下，您通常應該將升級的前置詞`x`。  
  
> [!NOTE]
>  .NET framework XAML 服務也會定義 XAML 相關屬性<xref:System.Windows.Markup.RootNamespaceAttribute>。 這個屬性是專案系統支援，組件層級屬性，並不是與 XAML 自訂型別相關。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Attribute>  
 [定義可搭配 .NET Framework XAML 服務使用的自訂類型](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)
