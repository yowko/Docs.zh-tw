---
title: 從 WPF 移轉至 System.Xaml 的類型
ms.date: 03/30/2017
helpviewer_keywords:
- WPF XAML [XAML Services], migration to System.Xaml
- XAML [XAML Services], System.Xaml and WPF
- System.Xaml [XAML Services], types migrated from WPF
ms.assetid: d79dabf5-a2ec-4e8d-a37a-67c4ba8a2b91
ms.openlocfilehash: f967cf6b7957c36fd66ed5eafe695a850cf101e1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593348"
---
# <a name="types-migrated-from-wpf-to-systemxaml"></a>從 WPF 移轉至 System.Xaml 的類型
在 [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)]並[!INCLUDE[net_v30_long](../../../includes/net-v30-long-md.md)]，這兩個[!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]和 Windows Workflow Foundation 隨附 XAML 語言實作。 有許多為 WPF XAML 實作提供擴充性的公用類型，存在於 WindowsBase、PresentationCore 和 PresentationFramework 組件中。 同樣地，Windows Workflow Foundation XAML 提供擴充性的公用型別存在於 System.Workflow.ComponentModel 組件。 在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]中，某些與 XAML 相關的類型已移轉至 System.Xaml 組件。 .NET Framework 有一項常見的 XAML 語言服務實作，可用以執行許多 XAML 擴充性情節，這些情節原先由特定架構的 XAML 實作所定義，但現在已納入整體 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] XAML 語言支援中。 本主題會列出移轉的類型，並討論與移轉相關的問題。  
  
<a name="assemblies_and_namespaces"></a>   
## <a name="assemblies-and-namespaces"></a>組件和命名空間  
 在 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] 和 [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]中，WPF 為了支援 XAML 而實作的類型通常位於 <xref:System.Windows.Markup> 命名空間中。 這些類型大多數位於 WindowsBase 組件中。  
  
 在 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]中，則有新的 <xref:System.Xaml> 命名空間和新的 System.Xaml 組件。 許多原先針對 WPF XAML 實作的類型，現已提供為任何 XAML 實作的擴充點或服務。 為了可供更多一般情節使用，這些類型已從其原始 WPF 組件類型轉送至 System.Xaml 組件。 如此 XAML 擴充性案例而無須納入其他架構 （例如 WPF 和 Windows Workflow Foundation） 的組件。  
  
 大部分移轉後的類型仍會位於 <xref:System.Windows.Markup> 命名空間中。 部分原因是為了避免破壞個別檔案之現有實作中的 CLR 命名空間對應。 因此， <xref:System.Windows.Markup> 中的 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 命名空間會同時包含一般 XAML 語言支援類型 (來自 System.Xaml 組件) 和 WPF XAML 實作的特定類型 (來自 WindowsBase 和其他 WPF 組件)。 任何已移轉至 System.Xaml、但先前存在於 WPF 組件中的類型，在 WPF 組件第 4 版中都具有類型轉送支援。  
  
### <a name="workflow-xaml-support-types"></a>Workflow XAML 支援類型  
 Windows Workflow Foundation 也提供 XAML 支援類型，並在許多情況下，這些有相同的短檔名，用於對等 WPF。 以下是 Windows Workflow Foundation XAML 支援類型的清單：  
  
- <xref:System.Workflow.ComponentModel.Serialization.ContentPropertyAttribute>  
  
- <xref:System.Workflow.ComponentModel.Serialization.RuntimeNamePropertyAttribute>  
  
- <xref:System.Workflow.ComponentModel.Serialization.XmlnsPrefixAttribute>  
  
 這些支援類型仍存在於 Windows Workflow Foundation 組件中[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]和仍用於特定的 Windows Workflow Foundation 應用程式; 不過，它們不應參考的應用程式或不使用的架構Windows Workflow Foundation。  
  
<a name="markupextension"></a>   
## <a name="markupextension"></a>MarkupExtension  
 在 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] 和 [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]中，WPF 的 <xref:System.Windows.Markup.MarkupExtension> 類別是位於 WindowsBase 組件中。 Windows Workflow Foundation 的平行類別<xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>System.Workflow.ComponentModel 組件中。 在 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]中， <xref:System.Windows.Markup.MarkupExtension> 類別已移轉至 System.Xaml 組件。 在 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]中， <xref:System.Windows.Markup.MarkupExtension> 可用於任何使用 .NET Framework XAML 服務的 XAML 擴充性情節，而不只是用於建置在特定架構上的情節。 進行 XAML 擴充時，也應盡可能將特定架構或架構中的使用者程式碼建置在 <xref:System.Windows.Markup.MarkupExtension> 類別上。  
  
<a name="markupextension_supporting_service_classes"></a>   
## <a name="markupextension-supporting-service-classes"></a>支援服務類別的 MarkupExtension  
 過去 WPF 適用的[!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] 和 [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)] 提供了數項服務，可供 <xref:System.Windows.Markup.MarkupExtension> implementers 和 <xref:System.ComponentModel.TypeConverter> 實作用來支援 XAML 中的類型/屬性使用。 這些服務包括：  
  
- <xref:System.Windows.Markup.IProvideValueTarget>  
  
- <xref:System.Windows.Markup.IUriContext>  
  
- <xref:System.Windows.Markup.IXamlTypeResolver>  
  
> [!NOTE]
>  [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] 介面是 <xref:System.Windows.Markup.IReceiveMarkupExtension> 中與標記延伸相關的另一項服務。 <xref:System.Windows.Markup.IReceiveMarkupExtension> 並未移轉，而且已對 `[Obsolete]` 標記為 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]。 先前使用 <xref:System.Windows.Markup.IReceiveMarkupExtension> 的情節應改用 <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> 屬性化回呼。 <xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute> 也已標記為 `[Obsolete]`。  
  
<a name="xaml_language_features"></a>   
## <a name="xaml-language-features"></a>XAML 語言功能  
 有數項 WPF 適用的 XAML 語言功能和元件先前存在於 PresentationFramework 組件中。 這些項目會以 <xref:System.Windows.Markup.MarkupExtension> 子類別的形式實作，以在 XAML 標記中公開標記延伸使用。 在 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]中，這些項目會存在於 System.Xaml 組件中，讓不含 WPF 組件的專案可以使用這些 XAML 語言層級功能。 WPF 針對 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 應用程式使用這些相同的實作。 如本主題所列的其他情況，支援類型會繼續存在於 <xref:System.Windows.Markup> 命名空間中，以避免破壞先前的參考。  
  
 下表包含 System.Xaml 中定義的 XAML 功能支援類別清單。  
  
|XAML 語言功能|使用量|  
|---------------------------|-----------|  
|<xref:System.Windows.Markup.ArrayExtension>|`<x:Array ...>`|  
|<xref:System.Windows.Markup.NullExtension>|`{x:Null}`|  
|<xref:System.Windows.Markup.StaticExtension>|`{x:Static ...}`|  
|<xref:System.Windows.Markup.TypeExtension>|`{x:Type ...}`|  
  
 雖然 System.Xaml 可能沒有特定支援類別，但處理 XAML 語言的語言功能時所需的一般邏輯，現已常駐於 System.Xaml 以及其實作的 XAML 讀取器和 XAML 寫入器中。 例如， `x:TypeArguments` 是由 XAML 讀取器和 XAML 寫入器透過 System.Xaml 實作處理的屬性。該屬性可在 XAML 節點資料流中標註、在預設 (CLR 型) XAML 結構描述內容中有處理邏輯、具有 XAML 類型系統表示等。 因此，所有 XAML 語言層級功能的參考文件，都會是 [XAML Services](index.md) 和 .NET Framework 文件集該一般區域的子主題，而不會是 WPF 文件集中 [進階 (Windows Presentation Foundation)](../wpf/advanced/index.md) 的子主題 (在 3.5 文件集中仍為如此)。  
  
<a name="valueserializer_and_supporting_classes"></a>   
## <a name="valueserializer-and-supporting-classes"></a>ValueSerializer 和支援類別  
 <xref:System.Windows.Markup.ValueSerializer> 類別支援將類型轉換成字串，尤其是在 XAML 序列化需要輸出中有多個模式或節點時。 在 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] 和 [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]中，WPF 的 <xref:System.Windows.Markup.ValueSerializer> 是位於 WindowsBase 組件中。 在 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]中， <xref:System.Windows.Markup.ValueSerializer> 類別位於 System.Xaml，並可用於任何 XAML 擴充性情節，而不只是用於在 WPF 上建置的情節。 <xref:System.Windows.Markup.IValueSerializerContext> (支援服務) 和 <xref:System.Windows.Markup.DateTimeValueSerializer> (特定子類別) 也會移轉至 System.Xaml。  
  
<a name="xamlrelated_attributes"></a>   
## <a name="xaml-related-attributes"></a>XAML 相關屬性  
 WPF XAML 隨附數個可套用至 CLR 類型的屬性，以針對其 XAML 行為表示相關資訊。 以下是 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] 和 [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]的 WPF 組件中已有的屬性清單。 這些屬性在 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]中已移轉至 System.Xaml。  
  
- <xref:System.Windows.Markup.AmbientAttribute>  
  
- <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
- <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
- <xref:System.Windows.Markup.DependsOnAttribute>  
  
- <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
- <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
- <xref:System.Windows.Markup.RootNamespaceAttribute>  
  
- <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
- <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
- <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
- <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
- <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
- <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
- <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
- <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
<a name="miscellaneous_classes"></a>   
## <a name="miscellaneous-classes"></a>其他類別  
 <xref:System.Windows.Markup.IComponentConnector> 介面在 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] 和 [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]存在於 WindowsBase 中，但到了 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]則存在於 System.Xaml 中。 <xref:System.Windows.Markup.IComponentConnector> 主要用於工具支援和 XAML 標記編譯器。  
  
 <xref:System.Windows.Markup.INameScope> 介面在 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] 和 [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]存在於 WindowsBase 中，但到了 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]則存在於 System.Xaml 中。 <xref:System.Windows.Markup.INameScope> 為 XAML 名稱範圍定義基本作業。  
  
<a name="xamlrelated_classes_with_shared_names_that_exist_in_wpf_and_systemxaml"></a>   
## <a name="xaml-related-classes-with-shared-names-that-exist-in-wpf-and-systemxaml"></a>WPF 和 System.Xaml 中具有共用名稱的 XAML 相關類別  
 在 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]中，下列類別同時存在於 WPF 組件和 System.Xaml 組件中：  
  
 `XamlReader`  
  
 `XamlWriter`  
  
 `XamlParseException`  
  
 WPF 實作位於 <xref:System.Windows.Markup> 命名空間和 PresentationFramework 組件中。 System.Xaml 實作位於 <xref:System.Xaml> 命名空間中。 如果您使用 WPF 類型或衍生自 WPF 類型，通常應使用 <xref:System.Windows.Markup.XamlReader> 和 <xref:System.Windows.Markup.XamlWriter> 的 WPF 實作，而不是 System.Xaml 實作。 如需詳細資訊，請參閱 <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> 和 <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>中的＜備註＞。  
  
 如果您同時納入 WPF 組件和 System.Xaml 的參考，並且同時對 `include` 和 <xref:System.Windows.Markup> 命名空間使用 <xref:System.Xaml> 陳述式，則您可能必須完整限定對這些 API 的呼叫，以明確解析類型。  
  
## <a name="see-also"></a>另請參閱

- [XAML Services](index.md)
