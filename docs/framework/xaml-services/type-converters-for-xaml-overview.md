---
title: XAML 類型轉換子概觀
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converters
- XAML [XAML Services], TypeConverter
- type conversion for XAML [XAML Services]
ms.assetid: 51a65860-efcb-4fe0-95a0-1c679cde66b7
ms.openlocfilehash: df6b7f212a60d8d51bb684891055de7e285ddf4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="type-converters-for-xaml-overview"></a>XAML 類型轉換子概觀
物件寫入器的類型轉換器供應邏輯，可將 XAML 標記中的字串轉換為物件圖形中的特定物件。 在 .NET Framework XAML 服務中，類型轉換器必須是衍生自 <xref:System.ComponentModel.TypeConverter>的類別。 有些轉換器也支援 XAML 儲存路徑，而且可用來將序列化標記中的物件序列化成字串格式。 本主題描述如何以及何時叫用 XAML 中的類型轉換器，並提供 <xref:System.ComponentModel.TypeConverter>之方法覆寫的實作建議。  
  
<a name="type_conversion_concepts"></a>   
## <a name="type-conversion-concepts"></a>類型轉換概念  
 下列各節說明下列作業的基本概念：XAML 如何使用字串，以及 .NET Framework XAML 服務中的物件寫入器如何使用類型轉換器來處理在 XAML 原始碼中發現的一些字串值。  
  
### <a name="xaml-and-string-values"></a>XAML 和字串值  
 在 XAML 檔案中設定屬性值時，該值的初始類型是一般感應器中的字串，以及 XML 感應器中的字串屬性值。 甚至，其他基本類型 (例如 <xref:System.Double> ) 一開始是 XAML 處理器的字串。  
  
 在大部分情況下，XAML 處理器需要兩項資訊才能處理屬性值。 第一項資訊是正在設定之屬性的實值類型。 任何定義屬性值並在 XAML 中處理的字串最後必須轉換或解析成該類型的值。 如果值是 XAML 剖析器可理解的基本類型 (例如數值)，則會嘗試直接轉換字串。 如果屬性的值參考列舉，則會檢查提供的字串是否有該列舉中具名常數的名稱相符項。 如果值不是剖析器理解的基本類型也不是列舉中的常數名稱，則適用的類型必須可以提供以已轉換字串為基礎的值或參考。  
  
> [!NOTE]
>  XAML 語言指示詞不會使用類型轉換器。  
  
### <a name="type-converters-and-markup-extensions"></a>類型轉換器和標記延伸  
 XAML 處理器必須先處理標記延伸使用方式，才會檢查屬性類型和其他考量。 例如，如果設為屬性 (Attribute) 的屬性 (Property) 通常具有類型轉換，但在特定情況下是由標記延伸使用方式所設定，則會先處理標記延伸行為。 需要有標記延伸的一個常見情況是參考現有的物件。 在此案例中，無狀態類型轉換器只能產生新的執行個體，但這可能不是令人滿意的情況。 如需標記延伸的詳細資訊，請參閱 [Markup Extensions for XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md)。  
  
### <a name="native-type-converters"></a>原生類型轉換器  
 在 WPF 和.NET XAML 服務實作中，有原生類型轉換處理某些 CLR 類型，不過，這些 CLR 型別會不依照慣例視為基本類型。 這類類型的範例是 <xref:System.DateTime>。 其中一個原因是 .NET Framework 架構的運作方式：類型 <xref:System.DateTime> 定義於 mscorlib (.NET 中的最基本程式庫)。 <xref:System.DateTime> 不允許使用來自另一個引進相依性的組件進行屬性設定 (<xref:System.ComponentModel.TypeConverterAttribute> 來自系統)；因此，無法支援透過屬性設定的一般類型轉換器探索機制。 而是，XAML 剖析器都有一份需要原生處理的類型清單，而且這些類型的處理方式與 true 基本類型的處理方式類似。 如果是 <xref:System.DateTime>則此處理包含 <xref:System.DateTime.Parse%2A>呼叫。  
  
<a name="Implementing_a_Type_Converter"></a>   
## <a name="implementing-a-type-converter"></a>實作類型轉換器  
 下列章節討論 <xref:System.ComponentModel.TypeConverter> 類別的 API。  
  
### <a name="typeconverter"></a>TypeConverter  
 在 .NET Framework XAML 服務下，用於 XAML 用途的所有類型轉換器是衍生自基底類別 <xref:System.ComponentModel.TypeConverter>的類別。 <xref:System.ComponentModel.TypeConverter> 類別要先存在於 .NET Framework 版本中，XAML 才會存在；其中一個原始 <xref:System.ComponentModel.TypeConverter> 案例是提供視覺化設計工具中屬性編輯器的字串轉換。  
  
 針對 XAML，會展開 <xref:System.ComponentModel.TypeConverter> 的角色。 基於 XAML， <xref:System.ComponentModel.TypeConverter> 是支援特定目標字串與來源字串轉換的基底類別。 來源字串會從 XAML 剖析字串屬性值。 目標字串可能會讓特定物件屬性的執行階段值處理回 XAML 中的屬性，以進行序列化。  
  
 <xref:System.ComponentModel.TypeConverter> 定義四個成員，而這些成員與基於 XAML 處理轉換目標字串和來源字串有關：  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 在這些成員中，最重要的方法是 <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>，可將輸入字串轉換成所需的物件類型。 <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> 方法可以實作以將更廣泛範圍的類型轉換為轉換器的預定目的地類型。 因此，它可以提供不僅 XAML 的用途，例如支援執行階段轉換。 不過，對於 XAML 使用，只有可處理 <xref:System.String> 輸入的程式碼路徑才重要。  
  
 第二個最重要的方法是 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> 如果應用程式轉換成標記呈現 (例如，如果儲存為 XAML 檔案)， <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> 會包含在 XAML 文字寫入器的較大案例中，而 XAML 文字寫入器會產生標記呈現。 在此情況下，XAML 的重要程式碼路徑是呼叫端通過 `destinationType` 的 <xref:System.String>時。  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> 和 <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> 是服務查詢 <xref:System.ComponentModel.TypeConverter> 實作之功能時所使用的支援方法。 您必須實作這些方法來傳回轉換器對等轉換方法所支援類型特有案例的 `true` 。 基於 XAML，這通常表示 <xref:System.String> 類型。  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>XAML 的文化特性資訊和類型轉換器  
 每個 <xref:System.ComponentModel.TypeConverter> 實作都可以唯一解譯轉換的有效字串，也可以使用或忽略傳遞為參數的類型描述。 文化特性和 XAML 類型轉換的重要考量如下：雖然 XAML 支援使用可當地語系化字串做為屬性值，但是您無法使用這些可當地語系化字串做為具有特定文化特性需求的類型轉換器輸入。 這項限制是因為 XAML 屬性值的類型轉換器包含使用 `en-US` 文化特性的必要固定語言 XAML 處理行為。 如需有關這項限制之設計原因的詳細資訊，請參閱 XAML 語言規格 ([\[MS-XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525)) 或[WPF 全球化和當地語系化概觀](../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md).  
  
 在文化特性可能是問題的範例中，某些文化特性會使用逗號 (而非句號) 做為字串形式中數字的小數點分隔符號。 這項使用與許多現有類型轉換器的行為衝突，後者是使用逗號做為分隔符號。 在周圍 XAML 中透過 `xml:lang` 傳遞文化特性並不能解決問題。  
  
### <a name="implementing-convertfrom"></a>實作 ConvertFrom  
 若要可做為支援 XAML 的 <xref:System.ComponentModel.TypeConverter> 實作來重複使用，該轉換器的 <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> 方法必須接受字串做為 `value` 參數。 如果字串的格式有效，而且可以透過 <xref:System.ComponentModel.TypeConverter> 實作進行轉換，則傳回的物件必須支援轉型為屬性所預期的類型。 否則， <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> 實作必須傳回 `null`。  
  
 每個 <xref:System.ComponentModel.TypeConverter> 實作都可以唯一解譯什麼可替代轉換的有效字串，也可以使用或忽略傳遞為參數的類型描述或文化特性內容。 不過，WPF XAML 處理可能不會在所有情況下都將值傳遞至類型描述內容，也可能不會根據 `xml:lang`來傳遞文化特性。  
  
> [!NOTE]
>  請勿使用大括號 ({})，特別是左括號 （{}），做為字串格式的項目。 這些字元保留做為標記延伸序列的進入及結束。  
  
 如果類型轉換器必須可以從 .NET Framework XAML 服務物件寫入器存取 XAML 服務，但針對內容進行的 <xref:System.IServiceProvider.GetService%2A> 呼叫未傳回該服務，則會適當地擲回例外狀況。  
  
### <a name="implementing-convertto"></a>實作 ConvertTo  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> 可能用於序列化支援。 透過自訂類型和其類型轉換器之 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> 的序列化支援不是絕對需求。 不過，如果您正在實作控制項，或使用功能某部分的序列化或類別設計，則應該實作 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>。  
  
 若要可做為支援 XAML 的 <xref:System.ComponentModel.TypeConverter> 實作來重複使用，該轉換器的 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> 方法必須接受所支援類型 (或值) 的執行個體做為 `value` 參數。 `destinationType` 參數的類型是 <xref:System.String>時，傳回的物件必須可以轉型為 <xref:System.String>。 傳回的字串必須代表 `value` 的序列化值。 理想上，您選擇的序列化格式應該可以產生相同的值，就像將該字串傳遞給相同轉換器的 <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> 實作，而不會明顯遺失資訊。  
  
 如果無法序列化值，或轉換器不支援序列化，則 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> 實作必須傳回 `null` 並可能會擲回例外狀況。 不過，如果您確實擲回例外狀況，則應該報告無法使用該轉換做為 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> 實作的一部分；因此，支援先使用 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> 檢查以避免例外狀況的最佳做法。  
  
 如果 `destinationType` 參數的類型不是 <xref:System.String>，則可以選擇專屬轉換器處理。 一般而言，您會回復成基底實作處理，而在基底 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> 中會引發特定例外狀況。  
  
 如果類型轉換器必須可以從 .NET Framework XAML 服務物件寫入器存取 XAML 服務，但針對內容進行的 <xref:System.IServiceProvider.GetService%2A> 呼叫未傳回該服務，則會適當地擲回例外狀況。  
  
### <a name="implementing-canconvertfrom"></a>實作 CanConvertFrom  
 您的 <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> 實作應該傳回類型 `true` 之 `sourceType` 的 <xref:System.String> ，否則會進行基底實作。 不會從 <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>擲回例外狀況。  
  
### <a name="implementing-canconvertto"></a>實作 CanConvertTo  
 您的 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> 實作應該傳回類型 `true` 之 `destinationType` 的 <xref:System.String>，否則會進行基底實作。 不會從 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>擲回例外狀況。  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## <a name="applying-the-typeconverterattribute"></a>套用 TypeConverterAttribute  
 對於 .NET Framework XAML 服務要用做自訂類別之目前類型轉換器的自訂類型轉換器，您必須將 [!INCLUDE[TLA#tla_netframewkattr](../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> 套用至類別定義。 您透過屬性指定的 <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> 必須是您自訂類型轉換器的類型名稱。 如果您套用這個屬性，則在 XAML 處理器處理屬性類型使用您自訂類別類型的值時，可以輸入字串，並傳回物件執行個體。  
  
 您也可以提供每個屬性的類型轉換器。 將 [!INCLUDE[TLA#tla_netframewkattr](../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> 套用至屬性定義 (主要定義，非其內的 `get`/`set` 實作)，而不是將它套用至類別定義。 屬性的類型必須符合您自訂類型轉換器所處理的類型。 如果已套用這個屬性，則在 XAML 處理器處理該屬性的值時，可以處理輸入字串，並傳回物件執行個體。 每個屬性的類型轉換器技術是特別有用，如果您選擇使用的屬性類型，從 Microsoft.NET Framework 或某個其他程式庫，您無法控制類別定義，就無法套用<xref:System.ComponentModel.TypeConverterAttribute>那里。  
  
 若要提供自訂附加成員的類型轉換行為，請將 <xref:System.ComponentModel.TypeConverterAttribute> 套用至附加成員之實作模式的 `Get` 存取子方法。  
  
<a name="accessing_service_provider_context_from_a_markup_extension_implementation"></a>   
## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>從標記延伸實作存取服務提供者內容  
 任何值轉換器的可用服務都會相同。 差異在於每個值轉換器如何接收服務內容。 存取服務和可用服務記載於 [Type Converters and Markup Extensions for XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)主題中。  
  
<a name="type_converters_in_the_xaml_node_stream"></a>   
## <a name="type-converters-in-the-xaml-node-stream"></a>XAML 節點資料流中的類型轉換器  
 如果您是使用 XAML 節點資料流，則尚未執行類型轉換器的動作或最終結果。 在載入路徑中，最後需要進行類型轉換才能載入的屬性字串仍然維持為開始成員和結束成員內的文字值。 使用 <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> 屬性可以判定這項作業最後需要的類型轉換器。 不過，從 <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> 取得有效值是依賴具有 XAML 結構描述內容 (可透過基礎成員存取這類資訊) 或成員所使用物件值的類型。 叫用類型轉換行為時也需要 XAML 結構描述內容，因為這需要類型對應以及建立轉換器執行個體。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ComponentModel.TypeConverterAttribute>  
 [XAML 的類型轉換子和標記延伸](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)  
 [XAML 概觀 (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
