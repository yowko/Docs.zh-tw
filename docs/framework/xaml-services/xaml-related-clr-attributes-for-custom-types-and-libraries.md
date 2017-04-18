---
title: "XAML-Related CLR Attributes for Custom Types and Libraries | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CLR attributes for custom types [XAML Services]"
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
caps.latest.revision: 8
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 8
---
# XAML-Related CLR Attributes for Custom Types and Libraries
本主題說明 .NET Framework XAML 服務所定義的 Common Language Runtime \(CLR\) 屬性。  同時也說明 .NET Framework 中所定義的其他 CLR 屬性，這些 CLR 屬性在 XAML 相關案例中可套用至組件或型別。  使用這些 CLR 屬性將組件、型別或成員屬性化，可提供您型別的相關資訊給 XAML 型別系統。  這些資訊可提供給任何使用 .NET Framework XAML 服務直接處理 XAML 節點資料流，或透過專用 XAML 讀取器與 XAML 寫入器進行處理的 XAML 消費者。  
  
## 自訂型別與自訂成員的 XAML 相關 CLR 屬性  
 若要使用 CLR 屬性，您必須使用整體的 CLR 定義您的型別，否則這些屬性將無法使用。  如果您使用 CLR 定義型別支援，.NET Framework XAML 服務的 XAML 寫入器所使用的預設 XAML 結構描述內容，即可透過對支援組件的反映來讀取 CLR 屬性。  
  
 以下幾節將說明可套用至自訂型別或自訂成員的 XAML 相關屬性。  每個 CLR 屬性都傳達了對 XAML 型別系統而言重要的資訊。  在載入路徑中，屬性化資訊可協助 XAML 讀取器構成有效的 XAML 節點資料流，或協助 XAML 寫入器產生有效的物件圖形。  在儲存路徑中，屬性化資訊可協助 XAML 讀取器構成能夠重新組成 XAML 型別系統資訊的有效 XAML 節點資料流，或宣告 XAML 寫入器或其他 XAML 消費者的序列化提示或需求。  
  
### AmbientAttribute  
 **參考文件：** <xref:System.Windows.Markup.AmbientAttribute>  
  
 **套用至**：類別、屬性、或支援可附加屬性的 `get` 存取子成員。  
  
 **引數**：無  
  
 <xref:System.Windows.Markup.AmbientAttribute> 表示屬性或所有採用屬性化型別的屬性均應以 XAML 中的環境屬性概念解譯。  環境概念與 XAML 處理器判斷成員之型別擁有者的方式有關聯。  環境屬性是指在建立物件圖形時預期應可在剖析器內容中使用其值，但為了要立即建立 XAML 節點集因而暫止一般型別成員查閱的屬性。  
  
 環境概念可套用至可附加成員，而這些成員就 CLR 屬性定義 <xref:System.AttributeTargets> 的方式而言，並不會以屬性的形式出現。  只有在使用支援 XAML 之可附加用法的 `get` 存取子時，才能套用方法屬性用法。  
  
### ConstructorArgumentAttribute  
 **參考文件**：<xref:System.Windows.Markup.ConstructorArgumentAttribute>  
  
 **套用至**：類別  
  
 **引數**：一個字串，用以指定符合單一建構函式引數的屬性名稱。  
  
 <xref:System.Windows.Markup.ConstructorArgumentAttribute> 會指定物件可透過非預設建構函式語法進行初始化，並指定具有指定名稱的屬性會提供建構資訊。  這個資訊主要用於 XAML 序列化。  如需詳細資訊，請參閱 <xref:System.Windows.Markup.ConstructorArgumentAttribute>。  
  
### ContentPropertyAttribute  
 **參考文件**：<xref:System.Windows.Markup.ContentPropertyAttribute>  
  
 **套用至**：類別  
  
 **引數**：一個字串，用以指定屬性化型別的成員名稱。  
  
 <xref:System.Windows.Markup.ContentPropertyAttribute> 表示引數所命名的屬性應做為該型別的 XAML 內容屬性。  XAML 內容屬性定義會繼承給所有可指派給定義型別的衍生型別。  您可以套用特定衍生型別的 <xref:System.Windows.Markup.ContentPropertyAttribute>，以覆寫特定衍生型別的定義。  
  
 就做為 XAML 內容屬性的屬性而言，在使用 XAML 時，可以省略該屬性的屬性項目標記。  一般而言，您會指定 XAML 內容屬性，為您的內容與內含項目模型提升有效率的 XAML 標記。  由於只有一個成員可指定為 XAML 內容屬性，因此您在設計時，有時必須選擇應將型別的哪幾個容器屬性指定為 XAML 內容屬性。  其他容器屬性則必須與明確的屬性項目一起使用。  
  
 在 XAML 節點資料流中，XAML 內容屬性仍會以 <xref:System.Xaml.XamlMember> 的屬性名稱產生 `StartMember` 與 `EndMember` 節點。  若要判斷成員是否為 XAML 內容屬性，請查看 `StartObject` 位置上的 <xref:System.Xaml.XamlType> 值，以及取得 <xref:System.Xaml.XamlType.ContentProperty%2A> 的值。  
  
### ContentWrapperAttribute  
 **參考文件**：<xref:System.Windows.Markup.ContentWrapperAttribute>  
  
 **套用至**：類別，尤其是集合型別。  
  
 **引數**：一個 <xref:System.Type>，用以指定要做為外部內容之內容包裝函式型別的型別。  
  
 <xref:System.Windows.Markup.ContentWrapperAttribute> 會在相關聯的集合型別上指定一個或多個要用以包裝外部內容的型別。  外部內容是指內容屬性型別的型別系統條件約束，無法擷取擁有者型別的 XAML 用法所將支援的所有可能內容類型。  例如，特定型別之內容的 XAML 支援，可能支援強型別泛型 <xref:System.Collections.ObjectModel.Collection%601> 中的字串。  將既有的標記慣例移轉至 XAML 可指派的集合值概念時，內容包裝函式將有所幫助；例如移轉與文字相關的內容模型時。  
  
 若要指定多個內容包裝函式型別，請套用此屬性多次。  
  
### DependsOnAttribute  
 **參考文件**：<xref:System.Windows.Markup.DependsOnAttribute>  
  
 **套用至**：屬性  
  
 **引數**：一個字串，用以指定屬性化型別之其他成員的名稱。  
  
 <xref:System.Windows.Markup.DependsOnAttribute> 表示屬性化屬性 \(Attributed Property\) 相依於其他屬性 \(Property\) 的值。  將此屬性 \(Attribute\) 套用至屬性 \(Property\) 定義，可確保相依屬性 \(Property\) 在 XAML 物件寫入作業中會優先處理。  使用 <xref:System.Windows.Markup.DependsOnAttribute>，可對型別的屬性 \(Property\) 指定必須遵循特定剖析順序以建立有效物件的例外情況。  
  
 您可以對一個屬性 \(Property\) 定義套用多個 <xref:System.Windows.Markup.DependsOnAttribute>。  
  
### MarkupExtensionReturnTypeAttribute  
 **參考文件**：<xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
 **套用至**：類別，此類別預期應為 <xref:System.Windows.Markup.MarkupExtension> 衍生型別。  
  
 **引數**：一個 <xref:System.Type>，用以指定最精準的型別，做為屬性化 <xref:System.Windows.Markup.MarkupExtension> 預期應有的 `ProvideValue` 結果。  
  
 如需詳細資訊，請參閱 [Markup Extensions for XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md)。  
  
### NameScopePropertyAttribute  
 **參考文件**：<xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
 **套用至**：類別  
  
 **引數**：支援兩種形式的屬性：  
  
-   一個字串，用以指定屬性化 \(Attributed\) 型別的屬性 \(Property\) 名稱。  
  
-   一個字串，用以指定屬性的名稱，以及為型別指定用以定義具名屬性的 <xref:System.Type>。  此形式可用來將可附加成員指定為 XAML 名稱範圍屬性。  
  
 <xref:System.Windows.Markup.NameScopePropertyAttribute> 會指定為屬性化 \(Attributed\) 類別提供 XAML 名稱範圍值的屬性 \(Property\)。  XAML 名稱範圍屬性依預期會參考實作 <xref:System.Windows.Markup.INameScope>，且包含實際 XAML 名稱範圍及其存放區與行為的物件。  
  
### RuntimeNamePropertyAttribute  
 **參考文件**：<xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
 **套用至**：類別  
  
 **引數**：一個字串，用以指定屬性化 \(Attributed\) 型別之執行階段名稱屬性 \(Property\) 的名稱。  
  
 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> 會報告屬性化型別對應至 XAML [x:Name Directive](../../../docs/framework/xaml-services/x-name-directive.md)的屬性。  此屬性的型別必須是 <xref:System.String>，且必須可讀取\/寫入。  
  
 其定義會繼承給所有可指派給定義型別的衍生型別。  您可以套用特定衍生型別的 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>，以覆寫特定衍生型別的定義。  
  
### TrimSurroundingWhitespaceAttribute  
 **參考文件**：<xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
 **套用至**：型別  
  
 **引數**：無。  
  
 <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> 會套用至可能在空白字元具有重要意義的內容 \(具有 <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> 的集合所包含的內容\) 中以子項目的形式出現的特定型別。  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> 主要與儲存路徑有關，但也可以載入路徑中的 XAML 型別系統中加以使用，只要查看 <xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=fullName> 即可。  如需詳細資訊，請參閱 [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)。  
  
### TypeConverterAttribute  
 **參考文件**：<xref:System.ComponentModel.TypeConverterAttribute>  
  
 **套用至**：類別、屬性、方法 \(只有在使用支援可附加成員的 `get` 存取子時，才可套用 XAML 方法\)。  
  
 **引數**：<xref:System.ComponentModel.TypeConverter> 的 <xref:System.Type>。  
  
 XAML 內容中的 <xref:System.ComponentModel.TypeConverterAttribute> 會參考自訂 <xref:System.ComponentModel.TypeConverter>。  此 <xref:System.ComponentModel.TypeConverter> 會為自訂型別或該型別的成員提供型別轉換行為。  
  
 您可以將 <xref:System.ComponentModel.TypeConverterAttribute> 屬性套用至您的型別，以參考您的型別轉換器實作。  您可以對類別、結構或介面定義 XAML 的型別轉換器。  您無須為列舉提供型別轉換，該轉換原本即已啟用。  
  
 您的型別轉換器應能夠從標記中的屬性或初始化文字所使用的字串，轉換成您所需的目的型別。  如需詳細資訊，請參閱 [TypeConverter 和 XAML](../../../ocs/framework/wpf/advanced/typeconverters-and-xaml.md)。  
  
 除了套用至型別的所有值以外，XAML 的型別轉換器行為也可以建立於特定屬性上。  在此情況下，您會將 <xref:System.ComponentModel.TypeConverterAttribute> 套用至屬性定義 \(外部定義，而非特定的 `get` 與 `set` 定義\)。  
  
 若要指派自訂可附加成員使用 XAML 時的型別轉換器行為，可以將 <xref:System.ComponentModel.TypeConverterAttribute> 套用至支援 XAML 用法的 `get` 方法存取子。  
  
 與 <xref:System.ComponentModel.TypeConverter> 類似，在 XAML 出現之前，<xref:System.ComponentModel.TypeConverterAttribute> 也存在於 .NET Framework 中，型別轉換子模型則供作其他用途。  若要參考及使用 <xref:System.ComponentModel.TypeConverterAttribute>，您必須加以完整限定，或為 <xref:System.ComponentModel> 提供 `using` 陳述式。  您也必須在專案中加入系統組件。  
  
### UidPropertyAttribute  
 **參考文件**：<xref:System.Windows.Markup.UidPropertyAttribute>  
  
 **套用至**：類別  
  
 **引數**：依名稱參考相關屬性的字串。  
  
 指定會為 [x:Uid Directive](../../../docs/framework/xaml-services/x-uid-directive.md) 設定別名之類別的 CLR 屬性。  
  
### UsableDuringInitializationAttribute  
 **參考文件**：<xref:System.Windows.Markup.UsableDuringInitializationAttribute>  
  
 **套用至**：類別  
  
 **引數**：布林值。  用於屬性的預定用途時，應一律指定為 `true`。  
  
 表示這個型別是否在建立 XAML 物件圖形期間由上往下建立。  此為進階概念，可能與您程式設計模型的定義有密切的關連。  如需詳細資訊，請參閱 <xref:System.Windows.Markup.UsableDuringInitializationAttribute>。  
  
### ValueSerializerAttribute  
 **參考文件**：<xref:System.Windows.Markup.ValueSerializerAttribute>  
  
 **套用至**：類別、屬性、方法 \(只有在使用支援可附加成員的 `get` 存取子時，才可套用 XAML 方法\)。  
  
 **引數**：一個 <xref:System.Type>，用以指定在序列化屬性化型別的所有屬性 \(Property\)\) 或特定屬性化屬性 \(Attributed Property\) 時，所要使用的值序列化程式支援類別。  
  
 <xref:System.Windows.Markup.ValueSerializer> 會指定比 <xref:System.ComponentModel.TypeConverter> 需要更多狀態與內容的值序列化類別。  <xref:System.Windows.Markup.ValueSerializer> 可以與可附加成員產生關聯，方法是對可附加成員套用靜態 `get` 存取子方法的 <xref:System.Windows.Markup.ValueSerializerAttribute> 屬性。  值序列化程式也適用於列舉、介面與結構，但不適用於委派。  
  
### WhitespaceSignificantCollectionAttribute  
 **參考文件**：<xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
 **套用至**：類別，尤其是預期會包含混合內容的集合型別，在此類內容中，物件項目周圍的空白字元對於 UI 的呈現可能有重要影響。  
  
 **引數**：無。  
  
 <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> 表示 XAML 處理器應以空白字元具有重要性的形式處理集合型別，以影響集合內 XAML 節點資料流的值節點建構。  如需詳細資訊，請參閱 [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)。  
  
### XamlDeferLoadAttribute  
 **參考文件**：<xref:System.Windows.Markup.XamlDeferLoadAttribute>  
  
 **套用至**：類別、屬性。  
  
 **引數**：支援兩種形式的屬性，即字串型別或 <xref:System.Type> 型別。  請參閱 <xref:System.Windows.Markup.XamlDeferLoadAttribute>。  
  
 表示類別或屬性具有 XAML 的延後載入使用方式 \(例如，範本行為\)，並報告啟用延後行為的類別及其目的型別\/內容型別。  
  
### XamlSetMarkupExtensionAttribute  
 **參考文件**：<xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute>  
  
 **套用至**：類別  
  
 **引數**：回呼的名稱。  
  
 表示類別可使用標記延伸提供其一個或多個屬性的值，並且在對類別的任何屬性執行標記延伸設定作業之前，會參考 XAML 寫入器應呼叫的處理常式。  
  
### XamlSetTypeConverterAttribute  
 **參考文件**：<xref:System.Windows.Markup.XamlSetTypeConverterAttribute>  
  
 **套用至**：類別  
  
 **引數**：回呼的名稱。  
  
 表示類別可使用型別轉換器提供其一個或多個屬性的值，並且在對類別的任何屬性執行型別轉換器設定作業之前，會參考 XAML 寫入器應呼叫的處理常式。  
  
### XmlLangPropertyAttribute  
 **參考文件**：<xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
 **套用至**：類別  
  
 **引數**：一個字串，會將屬性化 \(Attributed\) 型別之別名屬性 \(Property\) 的名稱指定為 `xml:lang`。  
  
 <xref:System.Windows.Markup.XmlLangPropertyAttribute> 會報告屬性化型別對應至 XML `lang` 指示詞的屬性。  此屬性的型別不一定是 <xref:System.String>，但必須可從字串指派 \(建立型別轉換器與屬性型別或特定屬性之間的關聯，可達此目的\)。  此屬性必須是讀取\/寫入屬性。  
  
 對應 `xml:lang` 必須在此情節下，執行階段物件模型才可直接存取 XML 特定語言資訊，而無須明確地以 XMLDOM 處理。  
  
 其定義會繼承給所有可指派給定義型別的衍生型別。  您可以套用特定衍生型別的 <xref:System.Windows.Markup.XmlLangPropertyAttribute>，以覆寫特定衍生型別的定義，但這種情況並不多見。  
  
## 組件層級的 XAML 相關 CLR 屬性  
 以下幾節將說明未套用至型別或成員定義、而套用至組件的 XAML 相關屬性。  在定義程式庫，以存放要在 XAML 中使用的自訂型別時，這些屬性大體上可發揮不錯的功效。  有些屬性不一定可直接對 XAML 節點資料流產生影響，但可隨節點資料流傳遞給其他消費者使用。  這項資訊的消費者包括需要 XAML 命名空間資訊與相關前置詞資訊的設計環境或序列化流程。  XAML 結構描述內容 \(包括 .NET Framework XAML 服務的預設值\) 也會使用這項資訊。  
  
### XmlnsCompatibleWithAttribute  
 **參考文件**：<xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
 **引數：**  
  
-   一個字串，用以指定要納入之 XAML 命名空間的識別項。  
  
-   一個字串，用以指定可從先前的引數納入 XAML 命名空間之 XAML 命名空間的識別項。  
  
 <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute> 會指定一個 XAML 命名空間可由另一個 XAML 命名空間納入。  一般而言，納入方的 XAML 命名空間會指定於先前定義的 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 中。  這項技術可來對程式庫中的 XAML 詞彙進行版本控制，使其符合先前根據舊版詞彙所定義的標記。  
  
### XmlnsDefinitionAttribute  
 **參考文件**：<xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
 **引數：**  
  
-   一個字串，用以指定要定義之 XAML 命名空間的識別項。  
  
-   為 CLR 命名空間命名的字串。  CLR 命名空間應定義您組件中的公用型別，且至少應有一個 CLR 命名空間型別用於 XAML。  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 以個別組件為基礎指定 XAML 命名空間與 CLR 命名空間之間的對應，這個對應之後會由 XAML 物件寫入器或 XAML 結構描述內容用來執行型別解析。  
  
 一個組件可以套用多個 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>。  採用此作法的原因可能包含下列一或多項：  
  
-   程式庫設計包含多個 CLR 命名空間可供執行階段 API 存取的邏輯組織使用，但是，您想讓所有來自這些命名空間的型別參考相同的 XAML 命名空間以適用於 XAML。  在此情況下，您會套用數個使用相同 <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> 值、但使用不同 <xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A> 值的 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 屬性。  當您為 XAML 命名空間定義對應時，若預定以您的架構或應用程式做為通用使用方式中的預設 XAML 命名空間，前述作法的功效更為顯著。  
  
-   程式庫設計包含多個 CLR 命名空間，而您想刻意區隔這些 CLR 命名空間中各個型別所使用的 XAML 命名空間。  
  
-   您在組件中定義了 CLR 命名空間，而您想讓此命名空間可透過多個 XAML 命名空間來存取。  此情節發生於您以相同程式碼基底支援多個詞彙時。  
  
-   您在一個或多個 CLR 命名空間中定義了 XAML 語言支援。  這些命名空間的 <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> 值應為 `http://schemas.microsoft.com/winfx/2006/xaml`。  
  
### XmlnsPrefixAttribute  
 **參考文件**：<xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
 **引數：**  
  
-   一個字串，用以指定 XAML 命名空間的識別項。  
  
-   一個字串，用以指定建議的前置詞。  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 會指定建議用於 XAML 命名空間的前置詞。  在會由 .NET Framework XAML 服務 <xref:System.Xaml.XamlXmlWriter> 進行序列化的 XAML 檔案中撰寫項目與屬性時，或者當實作 XAML 的程式庫會與具有 XAML 編輯功能的設計環境互動時，此前置詞很有用。  
  
 一個組件可以套用多個 <xref:System.Windows.Markup.XmlnsPrefixAttribute>。  採用此作法的原因可能包含下列一或多項：  
  
-   您的組建為多個 XAML 命名空間定義型別。  在此情況下，您應為每個 XAML 命名空間定義不同的前置詞值。  
  
-   您支援多個詞彙，並且對每個詞彙與 XAML 命名空間使用不同的前置詞。  
  
-   您在組件中定義了 XAML 語言支援，並且為 `http://schemas.microsoft.com/winfx/2006/xaml` 設定了 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>。  在此情況下，您通常應提升前置詞 `x`。  
  
> [!NOTE]
>  .NET Framework XAML 服務也會定義 XAML 相關屬性 <xref:System.Windows.Markup.RootNamespaceAttribute>。  此屬性是專案系統支援所需的組件層級屬性，與 XAML 自訂型別沒有關連。  
  
## 請參閱  
 <xref:System.Attribute>   
 [Defining Custom Types for Use with .NET Framework XAML Services](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)