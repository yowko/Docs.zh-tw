---
title: 從 WPF 移轉至 System.Xaml 的類型
ms.date: 03/30/2017
helpviewer_keywords:
- WPF XAML [XAML Services], migration to System.Xaml
- XAML [XAML Services], System.Xaml and WPF
- System.Xaml [XAML Services], types migrated from WPF
ms.assetid: d79dabf5-a2ec-4e8d-a37a-67c4ba8a2b91
ms.openlocfilehash: 943cdb2a21cbf2f95ef7fe2feefe6c0e71f57be4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939674"
---
# <a name="types-migrated-from-wpf-to-systemxaml"></a>從 WPF 移轉至 System.Xaml 的類型
在 .NET Framework 3.5 和 .NET Framework 3.0 中, [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]和 Windows Workflow Foundation 都包含 XAML 語言執行。 有許多為 WPF XAML 實作提供擴充性的公用類型，存在於 WindowsBase、PresentationCore 和 PresentationFramework 組件中。 同樣地, 為 Windows Workflow Foundation XAML 提供擴充性的公用類型也存在於 System.workflow.componentmodel.activity 元件中。 在 .NET Framework 4 中, 某些與 XAML 相關的類型會遷移至 system.string 元件。 XAML 語言服務的常見 .NET Framework 執行, 可讓許多 XAML 擴充性案例原本是由特定架構的 XAML 執行所定義, 但現在已成為整體 .NET Framework 4 個 XAML 語言支援的一部分。 本主題會列出移轉的類型，並討論與移轉相關的問題。  
  
<a name="assemblies_and_namespaces"></a>   
## <a name="assemblies-and-namespaces"></a>組件和命名空間  
 在 .NET Framework 3.5 和 .NET Framework 3.0 中, WPF 實作為支援 XAML 的類型通常是在<xref:System.Windows.Markup>命名空間中。 這些類型大多數位於 WindowsBase 組件中。  
  
 在 .NET Framework 4 中, 有一個新<xref:System.Xaml>的命名空間和一個新的 system.object 元件。 許多原先針對 WPF XAML 實作的類型，現已提供為任何 XAML 實作的擴充點或服務。 為了可供更多一般情節使用，這些類型已從其原始 WPF 組件類型轉送至 System.Xaml 組件。 這會啟用 XAML 擴充性案例, 而不需要包含其他架構的元件 (例如 WPF 和 Windows Workflow Foundation)。  
  
 大部分移轉後的類型仍會位於 <xref:System.Windows.Markup> 命名空間中。 部分原因是為了避免破壞個別檔案之現有實作中的 CLR 命名空間對應。 因此, .NET Framework 4 中<xref:System.Windows.Markup>的命名空間包含一般 XAML 語言支援類型的混合 (來自 system.string 元件), 以及 WPF XAML 實作為特定的類型 (來自 WindowsBase 和其他 wpf 元件)。 任何已移轉至 System.Xaml、但先前存在於 WPF 組件中的類型，在 WPF 組件第 4 版中都具有類型轉送支援。  
  
### <a name="workflow-xaml-support-types"></a>Workflow XAML 支援類型  
 Windows Workflow Foundation 也提供 XAML 支援型別, 而且在許多情況下, 這些都有與 WPF 對等的簡短名稱。 以下是 Windows Workflow Foundation XAML 支援類型的清單:  
  
- <xref:System.Workflow.ComponentModel.Serialization.ContentPropertyAttribute>  
  
- <xref:System.Workflow.ComponentModel.Serialization.RuntimeNamePropertyAttribute>  
  
- <xref:System.Workflow.ComponentModel.Serialization.XmlnsPrefixAttribute>  
  
 這些支援類型仍存在於 .NET Framework 4 的 Windows Workflow Foundation 元件中, 而且仍然可以用於特定的 Windows Workflow Foundation 應用程式;不過, 不應由不使用 Windows Workflow Foundation 的應用程式或架構參考。  
  
<a name="markupextension"></a>   
## <a name="markupextension"></a>MarkupExtension  
 在 .NET Framework 3.5 和 .NET Framework 3.0 中, WPF <xref:System.Windows.Markup.MarkupExtension>的類別是在 WindowsBase 元件中。 System.workflow.componentmodel.activity 元件中已存在 Windows Workflow Foundation <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>的平行類別。 在 .NET Framework 4 中, <xref:System.Windows.Markup.MarkupExtension>類別會遷移至 system.object 元件。 在 .NET Framework 4 中, <xref:System.Windows.Markup.MarkupExtension>適用于任何使用 .NET Framework xaml 服務的 xaml 擴充性情節, 而不只是針對特定架構所建立的物件。 進行 XAML 擴充時，也應盡可能將特定架構或架構中的使用者程式碼建置在 <xref:System.Windows.Markup.MarkupExtension> 類別上。  
  
<a name="markupextension_supporting_service_classes"></a>   
## <a name="markupextension-supporting-service-classes"></a>支援服務類別的 MarkupExtension  
 WPF 的 .NET Framework 3.5 和 .NET Framework 3.0 提供了<xref:System.Windows.Markup.MarkupExtension>數項服務, 可供實作者和<xref:System.ComponentModel.TypeConverter>實作為支援 XAML 中的類型/屬性使用。 這些服務包括：  
  
- <xref:System.Windows.Markup.IProvideValueTarget>  
  
- <xref:System.Windows.Markup.IUriContext>  
  
- <xref:System.Windows.Markup.IXamlTypeResolver>  
  
> [!NOTE]
> 與標記延伸相關的 .NET Framework 3.5 的另一個服務是<xref:System.Windows.Markup.IReceiveMarkupExtension>介面。 <xref:System.Windows.Markup.IReceiveMarkupExtension>尚未遷移, 並標示`[Obsolete]`為 .NET Framework 4。 先前使用 <xref:System.Windows.Markup.IReceiveMarkupExtension> 的情節應改用 <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> 屬性化回呼。 <xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute> 也已標記為 `[Obsolete]`。  
  
<a name="xaml_language_features"></a>   
## <a name="xaml-language-features"></a>XAML 語言功能  
 有數項 WPF 適用的 XAML 語言功能和元件先前存在於 PresentationFramework 組件中。 這些項目會以 <xref:System.Windows.Markup.MarkupExtension> 子類別的形式實作，以在 XAML 標記中公開標記延伸使用。 在 .NET Framework 4 中, 這些存在於 System.object 元件中, 因此不包含 WPF 元件的專案可以使用這些 XAML 語言層級功能。 WPF 會針對 .NET Framework 4 應用程式使用這些相同的執行。 如本主題所列的其他情況，支援類型會繼續存在於 <xref:System.Windows.Markup> 命名空間中，以避免破壞先前的參考。  
  
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
 <xref:System.Windows.Markup.ValueSerializer> 類別支援將類型轉換成字串，尤其是在 XAML 序列化需要輸出中有多個模式或節點時。 在 .NET Framework 3.5 和 .NET Framework 3.0 中, <xref:System.Windows.Markup.ValueSerializer> for WPF 的是在 WindowsBase 元件中。 在 .NET Framework 4 中, <xref:System.Windows.Markup.ValueSerializer>類別是在 system.string 中, 適用于任何 Xaml 擴充性情節, 而不只是在 WPF 上建立的實例。 <xref:System.Windows.Markup.IValueSerializerContext> (支援服務) 和 <xref:System.Windows.Markup.DateTimeValueSerializer> (特定子類別) 也會移轉至 System.Xaml。  
  
<a name="xamlrelated_attributes"></a>   
## <a name="xaml-related-attributes"></a>XAML 相關屬性  
 WPF XAML 隨附數個可套用至 CLR 類型的屬性，以針對其 XAML 行為表示相關資訊。 以下是在 .NET Framework 3.5 和 .NET Framework 3.0 中, 存在於 WPF 元件中的屬性清單。 這些屬性會遷移至 .NET Framework 4 中的 System.object。  
  
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
 <xref:System.Windows.Markup.IComponentConnector>介面存在於 .NET Framework 3.5 和 .NET Framework 3.0 中的 WindowsBase 中, 但存在於 .NET Framework 4 中的 system.object。 <xref:System.Windows.Markup.IComponentConnector> 主要用於工具支援和 XAML 標記編譯器。  
  
 <xref:System.Windows.Markup.INameScope>介面存在於 .NET Framework 3.5 和 .NET Framework 3.0 中的 WindowsBase 中, 但存在於 .NET Framework 4 中的 system.object。 <xref:System.Windows.Markup.INameScope> 為 XAML 名稱範圍定義基本作業。  
  
<a name="xamlrelated_classes_with_shared_names_that_exist_in_wpf_and_systemxaml"></a>   
## <a name="xaml-related-classes-with-shared-names-that-exist-in-wpf-and-systemxaml"></a>WPF 和 System.Xaml 中具有共用名稱的 XAML 相關類別  
 下列類別同時存在於 WPF 元件和 .NET Framework 4 中的 System.object 元件中:  
  
 `XamlReader`  
  
 `XamlWriter`  
  
 `XamlParseException`  
  
 WPF 實作位於 <xref:System.Windows.Markup> 命名空間和 PresentationFramework 組件中。 System.Xaml 實作位於 <xref:System.Xaml> 命名空間中。 如果您使用 WPF 類型或衍生自 WPF 類型，通常應使用 <xref:System.Windows.Markup.XamlReader> 和 <xref:System.Windows.Markup.XamlWriter> 的 WPF 實作，而不是 System.Xaml 實作。 如需詳細資訊，請參閱 <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> 和 <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>中的＜備註＞。  
  
 如果您同時納入 WPF 組件和 System.Xaml 的參考，並且同時對 `include` 和 <xref:System.Windows.Markup> 命名空間使用 <xref:System.Xaml> 陳述式，則您可能必須完整限定對這些 API 的呼叫，以明確解析類型。  
  
## <a name="see-also"></a>另請參閱

- [XAML Services](index.md)
