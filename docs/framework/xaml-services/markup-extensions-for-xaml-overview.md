---
title: "Markup Extensions for XAML Overview | Microsoft Docs"
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
  - "markup extensions [XAML Services], custom"
  - "XAML [XAML Services], markup extensions"
ms.assetid: 261b2b11-2dc0-462f-8c66-55b8c9c6e436
caps.latest.revision: 14
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 14
---
# Markup Extensions for XAML Overview
標記延伸是一種 XAML 技巧，用於取得不是基本類型和特定 XAML 類型的值。 對於屬性使用方式，標記延伸使用左大括號 `{` 的已知字元序列進入標記延伸範圍，並使用右大括號 `}` 結束。 使用 .NET Framework XAML 服務時，您可以使用 System.Xaml 組件中的一些預先定義 XAML 語言標記延伸。 您也可以從 <xref:System.Windows.Markup.MarkupExtension> 類別產生子類別 \(定義於 System.Xaml 中\)，以及定義您自己的標記延伸。 或者，您可以使用特定架構所定義的標記延伸 \(如果已參考該架構\)。  
  
 存取標記延伸使用方式時，XAML 物件寫入器可以透過 <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A?displayProperty=fullName> 覆寫中的服務連接點，將服務提供給自訂 <xref:System.Windows.Markup.MarkupExtension> 類別。 服務可以用來取得有關使用方式、物件寫入器之特定功能、XAML 結構描述內容等的內容。  
  
<a name="XAML_Defined_Markup_Extensions"></a>   
## 已定義 XAML 的標記延伸  
 .NET Framework XAML 服務會針對 XAML 語言支援實作數個標記延伸。 這些標記延伸對應至 XAML 規格的各部分，做為語言。 這些通常可透過常見使用方式中所見語法的 `x:` 前置詞予以識別。 這些 XAML 語言項目的 .NET Framework XAML 服務實作都是衍生自 <xref:System.Windows.Markup.MarkupExtension> 基底類別。  
  
> [!NOTE]
>  `x:` 前置詞用於 XAML 生產的根項目中 XAML 語言命名空間的一般 XAML 命名空間對應。 例如，各種特定架構的 [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] 專案和頁面樣板會使用此 `x:` 對應來起始 XAML 檔案。 您可以選擇專屬 XAML 命名空間對應中的不同前置詞語彙基元，但是這份文件將假設使用預設 `x:` 對應來識別這些是 XAML 語言 XAML 命名空間之定義部分的實體，而非特定 Framework 的預設 XAML 命名空間或其他任意 CLR 或 XML 命名空間。  
  
### x:Type  
 `x:Type` 提供具名類型的 <xref:System.Type> 物件。 這項功能最常用於延遲機制，而延遲機制使用基礎 CLR 類型和類型衍生做為群組 Moniker 或識別碼。 WPF 樣式和樣板 \(以及其 `TargetType` 屬性使用方式\) 是特定範例。 如需詳細資訊，請參閱[x:Type Markup Extension](../../../docs/framework/xaml-services/x-type-markup-extension.md)。  
  
### x:Static  
 `x:Static` 會從實值類型程式碼實體 \(非直接是屬性值的類型\) 產生靜態值，但可評估為該類型。 這適用於指定已存在做為類型定義中已知常數的值。 如需詳細資訊，請參閱[x:Static Markup Extension](../../../docs/framework/xaml-services/x-static-markup-extension.md)。  
  
### x:Null  
 `x:Null` 指定 `null` 做為 XAML 成員的值。 根據特定類型的設計或更大的架構概念，`null` 不一定是屬性的預設值或空字串屬性的隱含值。 如需詳細資訊，請參閱[x:Null Markup Extension](../../../docs/framework/xaml-services/x-null-markup-extension.md)。  
  
### x:Array  
 如果故意不使用基底項目和控制模型所提供的集合支援，則 `x:Array` 支援使用 XAML 語法建立一般陣列。 如需詳細資訊，請參閱[x:Array Markup Extension](../../../docs/framework/xaml-services/x-array-markup-extension.md)。 具體來說，在 XAML 2009 中，陣列會存取為語言基本類型，而不是延伸。 如需詳細資訊，請參閱[XAML 2009 Language Features](../../../docs/framework/xaml-services/xaml-2009-language-features.md)。  
  
### x:Reference  
 `x:Reference` 是 XAML 2009 的一部分 \(原始 \(2006\) 語言集的延伸模組\)。`x:Reference` 代表物件圖形中另一個現有物件的參考。 該物件是透過其 `x:Name` 進行識別。 如需詳細資訊，請參閱[x:Reference Markup Extension](../../../docs/framework/xaml-services/x-reference-markup-extension.md)。  
  
### 其他 x: 建構  
 具有支援 XAML 語言功能的其他 `x:` 建構，但這些不會實作為標記延伸。 如需詳細資訊，請參閱[XAML Namespace \(x:\) Language Features](../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)。  
  
<a name="the_markupextension_base_class"></a>   
## MarkupExtension 基底類別  
 若要定義自訂標記延伸模組，以與 System.Xaml 中的預設 XAML 讀取器和 XAML 寫入器實作互動，請從抽象 <xref:System.Windows.Markup.MarkupExtension> 類別衍生類別。 該類別有一個覆寫的方法 \(即 <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>\)。 您可能也需要定義其他建構函式來支援標記延伸使用方式的引數，以及相符的可設定屬性。  
  
 透過 <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>，自訂標記延伸可以存取服務內容，而服務內容會報告 XAML 處理器在其中實際叫用標記延伸的環境。 在載入路徑中，這通常是 <xref:System.Xaml.XamlObjectWriter>。 在儲存路徑中，這通常是 <xref:System.Xaml.XamlXmlWriter>。 每個都會將服務內容報告為內部 XAML 服務提供者內容類別，以實作服務提供者模式。 如需可用服務和其代表項目的詳細資訊，請參閱 [Type Converters and Markup Extensions for XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)。  
  
 您的標記延伸類別必須使用公用存取層級；XAML 處理器必須一律可以具現化標記延伸的支援類別，才能使用其服務。  
  
<a name="naming_the_support_type"></a>   
## 定義自訂標記延伸的支援類型  
 如果使用 .NET Framework XAML 服務或是根據 .NET Framework XAML 服務所建置的架構，則有兩種命名標記延伸支援類型的選項。 類型名稱是與下列方式有關：XAML 物件寫入器在 XAML 中發現標記延伸使用方式時，嘗試存取和叫用標記延伸支援類型的方式。 使用下列其中一種命名策略：  
  
-   將類型名稱命名為與 XAML 標記使用方式語彙基元完全相符的名稱。 例如，若要支援 `{Collate ...}` 延伸使用方式，請將支援類型命名為 `Collate`。  
  
-   將類型名稱命名為使用方式字串語彙基元加上後置詞 `Extension`。 例如，若要支援 `{Collate ...}` 延伸使用方式，請將支援類型命名為 `CollateExtension`。  
  
 查閱順序是先尋找後面加上 `Extension` 的類別名稱，然後尋找沒有 `Extension` 後置詞的類別名稱。  
  
 從標記使用方式觀點來看，將 `Extension` 後置詞包括為使用方式的一部分是有效的。 不過，其行為就像 `Extension` 是類別名稱的真正部分，如果支援類別沒有 `Extension` 後置詞，則 XAML 物件寫入器無法解析這種使用方式的標記延伸支援類別。  
  
### 預設建構函式  
 所有標記延伸支援類型，您應該公開公用預設建構函式。 只要 XAML 物件寫入器從物件項目使用方式具現化標記延伸，就需要預設建構函式。 支援物件項目使用方式是標記延伸的合理預期，特別是針對序列化。 不過，如果您只想要支援標記延伸的屬性使用方式，則可以實作沒有公用建構函式的標記延伸。  
  
 如果您的標記延伸使用方式沒有任何引數，則需要預設建構函式，才能支援使用方式。  
  
<a name="constructor_patterns_and_positional_arguments_for_a_custom_markup_extension"></a>   
## 自訂標記延伸的建構函式模式和位置引數  
 對於具有預定引數使用方式的標記延伸，公用建構函式必須對應於預定使用方式的模式。 換句話說，如果標記延伸設計成需要一個位置引數做為有效使用方式，則應該支援具有一個接受位置引數之輸入參數的公用建構函式。  
  
 例如，假設 `Collate` 標記延伸僅支援有一個位置引數代表其模式的模式 \(指定為 `CollationMode` 列舉常數\)。 在此情況下，應該有下列形式的建構函式：  
  
```  
public Collate(CollationMode collationMode) {...}  
```  
  
 在基本層級，傳遞給標記延伸的引數是字串，因為正在從標記的屬性值轉送引數。 您可以將所有引數都設為字串，並使用該層級的輸入。 不過，您確實可以存取將標記延伸引數傳遞至支援類別之前所發生的特定處理。  
  
 處理的運作在概念上如同標記延伸是要建立的物件，然後設定其成員值。 每個要設定之指定屬性的評估方式，類似剖析 XAML 時，如何在已建立物件上設定指定成員。 有兩個重大差異：  
  
-   如前所述，標記延伸支援類型不需要有預設建構函式，就可以在 XAML 中具現化。 除非它在文字語法中的可能引數語彙基元化並評估為位置或具名引數，以及在該時間呼叫適當的建構函式，否則會延後其物件建構。  
  
-   標記延伸使用方式可以是巢狀的。 會先評估最內層的標記延伸。 因此，您可以假設使用這類使用方式，並將一個建構參數宣告為需要值轉換器 \(例如標記延伸\) 的類型。  
  
 在先前範例中，顯示與這類處理的依賴性。 .NET Framework XAML 服務 XAML 物件寫入器會將列舉常數名稱處理為原生層級的列舉值。  
  
 處理標記延伸位置參數的文字語法也可以仰賴與建構引數中類型相關聯的類型轉換器。  
  
 引數稱為位置引數，因為使用方式中的語彙基元順序對應至指派給語彙基元之建構函式參數的位置順序。 例如，請考慮下列建構函式簽章：  
  
```  
public Collate(CollationMode collationMode, object collateThis) {...}  
```  
  
 XAML 處理器預期此標記延伸會有兩個位置引數。 如果有使用方式 `{Collate AlphaUp,{x:Reference circularFile}}`，則會將 `AlphaUp` 權杖傳送至第一個參數，並評估為 `CollationMode` 列舉具名常數。 內部 `x:Reference` 的結果會傳送至第二個參數，並評估為物件。  
  
 在標記延伸語法和處理的 XAML 指定規則中，不論引數是位置引數還是具名引數，逗號都是這些引數之間的分隔符號。  
  
### 位置引數的 Arity 重複  
 如果 XAML 物件寫入器遇到具有位置引數的標記延伸使用方式，而且有接受該數目之引數 \(重複 Arity\) 的多個建構函式引數，則這不一定是錯誤。 行為取決於可自訂 XAML 結構描述內容設定 \(<xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A>\)。 如果 <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> 是 `true`，XAML 物件寫入器應該不會僅針對重複 Arity 原因擲回例外狀況。 該點的行為並未嚴格進行定義。 基本設計假設是結構描述內容具有可用於特定參數的類型資訊，而且可以嘗試比對重複候選項的明確轉換，以查看哪些簽章可能是最佳相符項。 如果沒有簽章可以通過 XAML 物件寫入器上執行的特定結構描述內容所進行的測試，則可能還是會擲回例外狀況。  
  
 根據預設，<xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> 是 .NET Framework XAML 服務之 CLR <xref:System.Xaml.XamlSchemaContext> 中的 `false`。 因此，如果遇到支援類型建構函式中有重複 Arity 的標記延伸使用方式，則預設 <xref:System.Xaml.XamlObjectWriter> 會擲回例外狀況。  
  
<a name="named_arguments_for_a_custom_markup_extension"></a>   
## 自訂標記延伸的具名引數  
 XAML 所指定的標記延伸也可以使用使用方式的具名引數形式。 在第一個語彙基元化層級，文字語法會分成數個引數。 任何引數內有等號 \(\=\) 會將引數識別為具名引數。 這類引數也會語彙基元化成名稱\/值組。 在此情況下，名稱會指定標記延伸支援類型的公用可設定屬性。 如果您想要支援具名引數使用方式，則應該提供這些公用可設定屬性。 屬性只要保持公用，就可以是繼承屬性。  
  
<a name="accessing_service_provider_context_from_a_markup_extension_implementation"></a>   
## 從標記延伸實作存取服務提供者內容  
 任何值轉換器的可用服務都相同。 差異在於每個值轉換器如何接收服務內容。 存取服務和可用服務記載於 [Type Converters and Markup Extensions for XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md) 主題中。  
  
<a name="property_element_usage_of_a_markup_extension"></a>   
## 標記延伸的屬性項目使用方式  
 通常是在屬性使用方式中使用標記延伸來設定標記延伸使用方式的案例。 不過，也可能可以定義支援類別，以支援屬性項目使用方式。  
  
 若要支援標記延伸的屬性項目使用方式，請定義公用預設建構函式。 這應該是執行個體建構函式，而不是靜態建構函式。 這是必要的，因為 XAML 處理器通常必須對它從標記所處理的任何物件項目叫用預設建構函式，而且這包括做為物件項目的標記延伸類別。 在進階案例中，您可以定義類別的非預設建構路徑。 \(如需詳細資訊，請參閱 [x:FactoryMethod Directive](../../../docs/framework/xaml-services/x-factorymethod-directive.md)\)。 不過，您不應該基於標記延伸用途使用這些模式，因為這樣會讓使用方式模式探索更為困難 \(針對設計人員與原始標記的使用者\)。  
  
<a name="attributing_for_a_custom_markup_extension"></a>   
## 自訂標記延伸的屬性設定  
 為了支援設計環境和特定 XAML 物件寫入器案例，您應該設定具有數個 CLR 屬性之標記延伸支援類型的屬性。 這些屬性會報告預定標記延伸使用方式。  
  
 <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute> 會報告 <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> 所傳回之物件類型的 <xref:System.Type> 資訊。 透過其純正簽章，<xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> 會傳回 <xref:System.Object>。 但是，各種消費者可能想要更精確的傳回類型資訊。 包括：  
  
-   設計人員和 IDE，可能可以提供標記延伸使用方式的類型感知支援。  
  
-   目標類別上 `SetMarkupExtension` 處理常式的進階實作，可能依賴反映來判斷標記延伸的傳回類型，而不是依名稱對特定已知 <xref:System.Windows.Markup.MarkupExtension> 實作進行分支處理。  
  
<a name="serialization_of_markup_extension_usages"></a>   
## 標記延伸使用方式的序列化  
 XAML 物件寫入器處理標記延伸使用方式並呼叫 <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> 時，先前為標記延伸使用方式的內容存在於 XAML 節點資料流中，但不在物件圖形中。 在物件圖形中，只會保留值。 如果您有設計案例或將原始標記延伸使用方式持續保存至序列化輸出的其他原因，則必須設計您自己的基礎結構，以從載入路徑 XAML 節點資料流追蹤標記延伸使用方式。 您可以實作行為以從載入路徑重新建立節點資料流的項目，並將它們播放回 XAML 寫入器以在儲存路徑中進行序列化，但需替換節點資料流適當位置中的值。  
  
<a name="markup_extensions_in_the_xaml_node_stream"></a>   
## XAML 節點資料流中的標記延伸  
 如果您是在載入路徑上使用 XAML 節點資料流，則標記延伸使用方式會以物件形式出現在節點資料流中。  
  
 如果標記延伸使用方式使用位置引數，則會呈現為具有初始化值的啟動物件。 節點資料流是以粗略的文字表示，看起來如下：  
  
 `StartObject` \(<xref:System.Xaml.XamlType> 是標記延伸的定義類型，而不是它的傳回類型\)  
  
 `StartMember` \(<xref:System.Xaml.XamlMember> 的名稱是 `_InitializationText`\)  
  
 `Value` \(值是字串形式的位置引數，包括中間分隔符號\)  
  
 `EndMember`  
  
 `EndObject`  
  
 具有具名引數的標記延伸使用方式會呈現為具有相關名稱之成員的物件，且成員各設定文字字串值。  
  
 實際叫用標記延伸的 `ProvideValue` 實作需要 XAML 結構描述內容，因為這需要類型對應以及建立標記延伸支援類型執行個體。 這是使用這種方式將標記延伸使用方式保留在預設 .NET Framework XAML 服務節點資料流中的一個原因：載入路徑的讀取器部分通常沒有可用的必要 XAML 結構描述內容。  
  
 如果您是在儲存路徑上使用 XAML 節點資料流，則物件圖形呈現中通常不會有任何項目可通知您：要序列化的物件一開始是由標記延伸使用方式和 `ProvideValue` 結果所提供。 如果案例需要針對來回處理保存標記延伸使用方式，同時擷取物件圖形中的其他變更，則必須設計自己的技術來保留原始 XAML 輸入中的標記延伸使用方式知識。 例如，若要還原標記延伸使用方式，您可能需要在儲存路徑上使用節點資料流才能還原標記延伸使用方式，或在原始 XAML 與往返 XAML 之間執行某種類型的合併。 一些實作 XAML 的架構 \(例如 WPF\) 使用中繼類型 \(運算式\)，協助代表標記延伸使用方式提供值的情況。  
  
## 請參閱  
 <xref:System.Windows.Markup.MarkupExtension>   
 [Type Converters and Markup Extensions for XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)   
 [標記延伸和 WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)