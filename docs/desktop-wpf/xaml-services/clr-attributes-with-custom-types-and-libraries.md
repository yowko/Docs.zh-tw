---
title: 自訂類型和程式庫的 XAML 相關 CLR 屬性
ms.date: 03/30/2017
helpviewer_keywords:
- CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
ms.openlocfilehash: 5481d02e4d393312fa0f0dd13b45c54acc567e13
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071763"
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a>自訂型態與函式庫的與 XAML 相關的 CLR 屬性

本主題介紹由 .NET XAML 服務定義的通用語言運行時 (CLR) 屬性。 它還描述了在 .NET 中定義的其他 CLR 屬性,這些屬性具有與 XAML 相關的方案,用於應用程式到程式集或類型。 將這些 CLR 屬性的程式集、類型或成員歸為具有 XAML 類型系統資訊,這些資訊與您的類型相關。 資訊提供給使用 .NET XAML 服務直接或透過專用 XAML 讀取器和 XAML 編寫器處理 XAML 節點串流的任何 XAML 消費者。

## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a>自訂型態與自訂成員的 XAML 相關 CLR 屬性

使用 CLR 屬性意味著您使用整個 CLR 來定義類型,否則此類屬性不可用。 如果使用 CLR 定義類型備份,則 .NET XAML 服務 XAML 編寫器使用的預設 XAML 架構上下文可以通過反射來讀取 CLR 歸因。

以下各節介紹可應用於自定義類型或自定義成員的與 XAML 相關的屬性。 每個 CLR 屬性都傳達與 XAML 類型系統相關的資訊。 在載入路徑中,屬性化資訊要麼説明 XAML 讀取器形成有效的 XAML 節點流,要麼説明 XAML 編寫器生成有效的物件圖。 在保存路徑中,屬性化資訊要麼説明 XAML 讀取器形成有效的 XAML 節點流,從而重新構成 XAML 類型系統資訊;或者聲明 XAML 編寫器或其他 XAML 消費者的序列化提示或要求。

### <a name="ambientattribute"></a>環境屬性

**參考文件:**<xref:System.Windows.Markup.AmbientAttribute>

**適用於:** 支援可附加屬性的`get`類、屬性或訪問器成員。

**參數:** 沒有

<xref:System.Windows.Markup.AmbientAttribute>指示屬性或採用屬性類型的所有屬性應在 XAML 中的環境屬性概念下解釋。 環境概念與 XAML 處理器如何判斷成員類別擁有者有關。 環境屬性是一個屬性,在創建物件圖時,該值在解析器上下文中可用,但在創建的直接 XAML 節點集時暫停典型的類型成員查找的屬性。

環境概念可以應用於可附加成員,這些成員在 CLR 屬性定義方面不表示<xref:System.AttributeTargets>為屬性 。 方法歸因用應僅適用於支援 XAML 可附加用`get`法的 訪問者。

### <a name="constructorargumentattribute"></a>建構函數參數屬性

**參考文件:**  <xref:System.Windows.Markup.ConstructorArgumentAttribute>

**適用於:** 類別

**參數:** 指定與單個建構函數參數匹配的屬性名稱的字串。

<xref:System.Windows.Markup.ConstructorArgumentAttribute>指定可以使用非參數建構函數語法初始化物件,並且指定名稱的屬性提供構造資訊。 這項資訊主要供 XAML 序列化之用。 如需詳細資訊，請參閱 <xref:System.Windows.Markup.ConstructorArgumentAttribute>。

### <a name="contentpropertyattribute"></a>內容屬性屬性

**參考文件:**  <xref:System.Windows.Markup.ContentPropertyAttribute>

**適用於:** 類別

**參數:** 指定屬性類型成員名稱的字串。

<xref:System.Windows.Markup.ContentPropertyAttribute>指示參數命名的屬性應用作該類型的 XAML 內容屬性。 XAML 內容屬性定義將繼承到可分配給定義類型的所有派生類型。 可以通過應用<xref:System.Windows.Markup.ContentPropertyAttribute>於 特定派生類型來覆蓋特定派生類型上的定義。

對於用作 XAML 內容屬性的屬性,可以在 XAML 用法中省略該屬性的屬性元素標記。 通常,您指定 XAML 內容屬性,這些屬性可為您的內容和包含模型推廣簡化的 XAML 標記。 由於只能將一個成員指定為 XAML 內容屬性,因此您有時可以選擇將某種類型的多個容器屬性中的哪一個指定為 XAML 內容屬性。 其他容器屬性必須與顯式屬性元素一起使用。

在 XAML 節點串流中,XAML 內容`StartMember`屬性`EndMember`, 使用的屬性<xref:System.Xaml.XamlMember>的名稱產生和節點 。 要決定成員是否為 XAML 內容屬性,<xref:System.Xaml.XamlType>`StartObject`請從 位置檢查值並<xref:System.Xaml.XamlType.ContentProperty%2A>取得的值 。

### <a name="contentwrapperattribute"></a>內容包裝屬性

**參考文件:**  <xref:System.Windows.Markup.ContentWrapperAttribute>

**適用於:** 類,特別是集合類型。

**參數:** 指定<xref:System.Type>用作外國內容內容包裝類型的類型的類型。

<xref:System.Windows.Markup.ContentWrapperAttribute>指定將用於包裝外來內容的關聯集合類型的一個或多個類型。 外國內容是指內容屬性類型的類型系統約束未捕獲擁有類型的 XAML 使用的所有可能內容情形的情況。 例如,對特定類型內容的 XAML 支援可能支援強類型<xref:System.Collections.ObjectModel.Collection%601>泛型 中的字串。 內容包裝器可用於將預先存在的標記約定遷移到 XAML 的集合可分配值的概念中,例如遷移與文本相關的內容模型。

要指定多個內容包裝類型,請多次應用該屬性。

### <a name="dependsonattribute"></a>相依屬性

**參考文件:**  <xref:System.Windows.Markup.DependsOnAttribute>

**適用於:** 財產

**參數:** 指定屬性類型另一個成員名稱的字串。

<xref:System.Windows.Markup.DependsOnAttribute>指示屬性屬性取決於另一個屬性的值。 將此屬性應用於屬性定義可確保在 XAML 物件寫入中首先處理從屬屬性。 的<xref:System.Windows.Markup.DependsOnAttribute>用法指定屬性的特殊情況,這些類型對於有效物件創建必須遵循特定的分析順序。

您可以將多個<xref:System.Windows.Markup.DependsOnAttribute>案例應用於屬性定義。

### <a name="markupextensionreturntypeattribute"></a>標記延伸傳回類型屬性

**參考文件:**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>

**適用於:** 類,應為<xref:System.Windows.Markup.MarkupExtension>派生類型。

**參數:**<xref:System.Type>指定作為`ProvideValue`<xref:System.Windows.Markup.MarkupExtension>屬性的結果預期的最精確類型。

有關詳細資訊,請參閱[XAML 概述的標記延伸](markup-extensions-overview.md)。

### <a name="namescopepropertyattribute"></a>名稱範圍屬性

**參考文件:**  <xref:System.Windows.Markup.NameScopePropertyAttribute>

**適用於:** 類別

**參數:** 支援兩種歸因形式:

- 指定屬性類型上屬性名稱的字串。

- 指定屬性名稱的字串,以及定義命名屬性的類型的<xref:System.Type>字串。 此表單用於將可附加成員指定為 XAML 命名範圍屬性。

<xref:System.Windows.Markup.NameScopePropertyAttribute>指定為屬性類提供 XAML 命名範圍值的屬性。 XAML 命名範圍屬性應參考<xref:System.Windows.Markup.INameScope>實現 並保存實際 XAML 名稱範圍、其存儲及其行為的物件。

### <a name="runtimenamepropertyattribute"></a>執行時名稱屬性屬性

**參考文件:**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>

**適用於:** 類別

**參數:** 指定屬性化類型上的執行時名稱屬性名稱的字串。

<xref:System.Windows.Markup.RuntimeNamePropertyAttribute>報告對應到 XAML [x:Name 指令](xname-directive.md)的屬性類型。 屬性必須為類型<xref:System.String>,並且必須讀取/寫入。

定義將繼承到可分配給定義類型的所有派生類型。 可以通過應用<xref:System.Windows.Markup.RuntimeNamePropertyAttribute>於 特定派生類型來覆蓋特定派生類型上的定義。

### <a name="trimsurroundingwhitespaceattribute"></a>修剪包圍空白屬性

**參考文件:**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>

**適用於:** 類型

**參數:** 沒有。

<xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>應用於可能顯示為空白重要內容中的子元素的特定類型(由<xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>具有的集合持有的內容)。 <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>主要與保存路徑相關,但通過檢查<xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType>在負載路徑中的 XAML 類型系統中可用。 有關詳細資訊,請參閱[XAML 中的空白處理](white-space-processing.md)。

### <a name="typeconverterattribute"></a>TypeConverterAttribute

**參考文件:**  <xref:System.ComponentModel.TypeConverterAttribute>

**適用於:** 類、屬性、方法(唯一`get`的 XAML 有效方法大小寫是支援可連接成員的存取器)。

**參數:** 的<xref:System.Type><xref:System.ComponentModel.TypeConverter>。

<xref:System.ComponentModel.TypeConverterAttribute>在 XAML 內文中引用<xref:System.ComponentModel.TypeConverter>自訂 。 這為<xref:System.ComponentModel.TypeConverter>自定義類型或該類型的成員提供類型轉換行為。

將<xref:System.ComponentModel.TypeConverterAttribute>該屬性應用於類型,引用類型轉換器實現。 您可以在類、結構或介面上為 XAML 定義類型轉換器。 您無需為枚舉提供類型轉換,該轉換是本機啟用的。

類型轉換器應該能夠從用於標記中的屬性或初始化文本的字串轉換為預期的目標類型。 有關詳細資訊,請參考[類型轉換器與 XAML](../../framework/wpf/advanced/typeconverters-and-xaml.md)。

也可以在特定屬性上建立 XAML 的類型轉換器行為,而不是應用於類型的所有值。 在這種情況下,您將應用於<xref:System.ComponentModel.TypeConverterAttribute>屬性定義(外部定義,而不是`get`特定定義`set`和定義)。

可以通過應用<xref:System.ComponentModel.TypeConverterAttribute>於支援 XAML`get`用法 的方法存取器來分配自訂可連接成員的 XAML 使用的類型轉換器行為。

與<xref:System.ComponentModel.TypeConverter>類似<xref:System.ComponentModel.TypeConverterAttribute>,在 XAML 存在之前存在於 .NET 中,類型轉換器模型具有其他用途。 為了引用和使用<xref:System.ComponentModel.TypeConverterAttribute>,您必須完全限定它或`using`提供 語<xref:System.ComponentModel>句。 還在專案中包括系統程式集。

### <a name="uidpropertyattribute"></a>烏德屬性

**參考文件:**  <xref:System.Windows.Markup.UidPropertyAttribute>

**適用於:** 類別

**參數:** 依名稱引用相關屬性的字串。

指示別名[x:Uid 指令](xuid-directive.md)的類的 CLR 屬性。

### <a name="usableduringinitializationattribute"></a>初始化期間可用屬性

**參考文件:**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute>

**適用於:** 類別

**參數:** 一個布爾。 如果用於屬性的預期用途,則該值應設定為`true`。

指示類型在 XAML 物件圖形創建期間是否自上而下生成。 這是一個高級概念,可能與程式設計模型的定義密切相關。 如需詳細資訊，請參閱 <xref:System.Windows.Markup.UsableDuringInitializationAttribute>。

### <a name="valueserializerattribute"></a>值序列器屬性

**參考文件:**  <xref:System.Windows.Markup.ValueSerializerAttribute>

**適用於:** 類、屬性、方法(唯一`get`的 XAML 有效方法大小寫是支援可連接成員的存取器)。

**參數:** 指定<xref:System.Type>在序列化屬性類型或特定屬性屬性的所有屬性時要使用的值序列化器支援類。

<xref:System.Windows.Markup.ValueSerializer>指定值序列化類,該類需要比 更多的<xref:System.ComponentModel.TypeConverter>狀態和上下文。 <xref:System.Windows.Markup.ValueSerializer>通過將屬性應用於可附加成員的靜態<xref:System.Windows.Markup.ValueSerializerAttribute>`get`訪問器方法,可以與可連接成員關聯。 值序列化也適用於枚舉、介面和結構,但不適用於委託。

### <a name="whitespacesignificantcollectionattribute"></a>空白顯著集合屬性

**參考文件:**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>

**適用於:** 類,特別是預期承載混合內容的集合類型,其中物件元素周圍的空白對於UI表示可能很重要。

**參數:** 沒有。

<xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>指示集合類型應被 XAML 處理器處理為具有顯著意義的空格,這會影響集合中 XAML 節點流的值節點的構造。 有關詳細資訊,請參閱[XAML 中的空白處理](white-space-processing.md)。

### <a name="xamldeferloadattribute"></a>XamlDeferLoad 屬性

**參考文件:**  <xref:System.Windows.Markup.XamlDeferLoadAttribute>

**適用於:** 類,屬性。

**參數:** 支援兩個歸因表單型態為字串,或<xref:System.Type>類型為 。 請參閱＜<xref:System.Windows.Markup.XamlDeferLoadAttribute>＞。

表示類別或屬性具有 XAML 的延後載入使用方式 (例如，範本行為)，並報告啟用延後行為的類別及其目的型別/內容型別。

### <a name="xamlsetmarkupextensionattribute"></a>XamlSetMarkup 擴充屬性

**參考文件:**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute>

**適用於:** 類別

**參數:** 命名回調。

指示類可以使用標記擴展為一個或多個屬性提供值,並引用 XAML 編寫器在對類的任何屬性執行標記擴展集操作之前應調用的處理程式。

### <a name="xamlsettypeconverterattribute"></a>XamlSet 類型轉換器屬性

**參考文件:**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute>

**適用於:** 類別

**參數:** 命名回調。

指示類可以使用類型轉換器為其一個或多個屬性提供值,並引用 XAML 編寫器在對類的任何屬性執行類型轉換器集操作之前應調用的處理程式。

### <a name="xmllangpropertyattribute"></a>XmlLang屬性

**參考文件:**  <xref:System.Windows.Markup.XmlLangPropertyAttribute>

**適用於:** 類別

**參數:** 一個字串,用於在屬性類型上指定屬性的名稱`xml:lang`到別名。

<xref:System.Windows.Markup.XmlLangPropertyAttribute>報告對應到 XML`lang`指令屬性類型的屬性。 屬性不一定是類型<xref:System.String>,但必須從字串中分配(可以通過將類型轉換器與屬性的類型或特定屬性相關聯來實現)。 屬性必須讀/寫。

映射`xml:lang`方案是,執行時物件模型可以訪問 XML 指定的語言資訊,而無需專門使用 XMLDOM 進行處理。

定義將繼承到可分配給定義類型的所有派生類型。 可以通過應用<xref:System.Windows.Markup.XmlLangPropertyAttribute>於 特定派生類型來覆蓋特定派生類型上的定義,儘管這種情況並不常見。

## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a>裝配層級的 XAML 相關 CLR 屬性

以下各節介紹不應用於類型或成員定義但應用於程式集的與 XAML 相關的屬性。 這些屬性與定義包含要在 XAML 中使用的自定義類型的庫的總體目標相關。 某些屬性不一定直接影響 XAML 節點流,而是在節點流中傳遞,供其他消費者使用。 資訊的消費者包括需要 XAML 命名空間資訊和關聯的前置資訊的設計環境或序列化過程。 XAML 架構上下文(包括 .NET XAML 服務預設值)也使用此資訊。

### <a name="xmlnscompatiblewithattribute"></a>與屬性相容的 Xmlns

**參考文件:**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>

**引數:**

- 指定要歸納的 XAML 命名空間的識別碼的字串。

- 指定 XAML 命名空間的識別碼的字串,該名稱空間可以從上一個參數中歸入 XAML 命名空間。

  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>指定 XAML 命名空間可以由另一個 XAML 命名空間進行歸用。 一般會在預先定義的 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 中指出建立小計的 XAML 命名空間。 此技術可用於在庫中對 XAML 詞彙進行版本控制,並使之與以前定義的標記(針對早期版本化的詞彙表)相容。

### <a name="xmlnsdefinitionattribute"></a>Xmlns 定義屬性

**參考文件:**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>

**引數:**

- 指定要定義的 XAML 命名空間的識別碼的字串。

- 命名 CLR 命名空間的字串。 CLR 命名空間應在程式集中定義公共類型,並且至少應使用一種 CLR 命名空間類型來使用 XAML。

  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>指定 XAML 命名空間和 CLR 命名空間之間的每個程式集映射,然後 XAML 物件編寫器或 XAML 架構上下文用於類型解析。

  可以有多個<xref:System.Windows.Markup.XmlnsDefinitionAttribute>元件。 這可能是出於以下任何原因的組合:

- 庫設計包含多個 CLR 命名空間,用於運行時 API 訪問的邏輯組織;但是,您希望這些命名空間中的所有類型都可用於 XAML,透過引用相同的 XAML 命名空間。 在這種情況下,使用相同的<xref:System.Windows.Markup.XmlnsDefinitionAttribute><xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A>值但不同的<xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A>值應用多個屬性。 如果要定義框架或應用程式打算成為常用的預設 XAML 命名空間的 XAML 命名空間的映射,則此功能尤其有用。

- 庫設計包含多個 CLR 命名空間,您希望在這些 CLR 命名空間中類型的用法之間進行深思熟慮的 XAML 命名空間分離。

- 在程式集中定義 CLR 命名空間,並希望它可以通過多個 XAML 命名空間進行訪問。 當您支援具有相同代碼庫的多個詞彙庫時,將發生此情況。

- 在一個或多個 CLR 命名空間中定義 XAML 語言支援。 在這種情況下,<xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A>值應`http://schemas.microsoft.com/winfx/2006/xaml`為 。

### <a name="xmlnsprefixattribute"></a>Xmlns前置字串屬性

**參考文件:**  <xref:System.Windows.Markup.XmlnsPrefixAttribute>

**引數:**

- 指定 XAML 命名空間識別碼的字串。

- 指定建議前置字串。

  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>指定用於 XAML 命名空間的建議前置碼。 在由 .NET XAML 服務<xref:System.Xaml.XamlXmlWriter>序列化的 XAML 檔中編寫元素和屬性時,或者當 XAML 實現庫與具有 XAML 編輯功能的設計環境互動時,前置碼非常有用。

  可以有多個<xref:System.Windows.Markup.XmlnsPrefixAttribute>元件。 這可能是出於以下任何原因的組合:

- 程式集定義多個 XAML 命名空間的類型。 在這種情況下,為每個 XAML 命名空間定義不同的前置值。

- 您支援多個詞彙,並且對每個詞彙表和 XAML 命名空間使用不同的前置碼。

- 在程式集中定義 XAML 語言支援,<xref:System.Windows.Markup.XmlnsDefinitionAttribute>`http://schemas.microsoft.com/winfx/2006/xaml`並為 在這種情況下,通常應升級前置字`x`串 。

> [!NOTE]
> .NET XAML 服務還定義了與<xref:System.Windows.Markup.RootNamespaceAttribute>XAML 相關的屬性 。 此屬性是專案系統支援的程式集級屬性,與 XAML 自定義類型無關。

## <a name="see-also"></a>另請參閱

- <xref:System.Attribute>
- [定義可搭配 .NET XAML 服務使用的自訂類型](define-custom-types.md)
