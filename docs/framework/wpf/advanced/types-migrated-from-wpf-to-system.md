---
title: 從 WPF 移轉至 System.Xaml 的類型
ms.date: 03/30/2017
helpviewer_keywords:
- WPF XAML [XAML Services], migration to System.Xaml
- XAML [XAML Services], System.Xaml and WPF
- System.Xaml [XAML Services], types migrated from WPF
ms.assetid: d79dabf5-a2ec-4e8d-a37a-67c4ba8a2b91
ms.openlocfilehash: 5aa2d8a39be47d9affb97c3b60e53c4722c63cce
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249799"
---
# <a name="types-migrated-from-wpf-to-systemxaml"></a>從 WPF 遷移到 System.Xaml 的類型

在 .NET 框架 3.5 和 .NET 框架 3.0 中，Windows 演示基礎 （WPF） 和 Windows 工作流基礎都包含 XAML 語言實現。 有許多為 WPF XAML 實作提供擴充性的公用類型，存在於 WindowsBase、PresentationCore 和 PresentationFramework 組件中。 同樣，為 Windows 工作流基礎 XAML 提供擴充性的公共類型存在於 System.Workflow.元件模型程式集中。 在 .NET 框架 4 中，一些與 XAML 相關的類型已遷移到 System.Xaml 程式集。 XAML 語言服務的通用 .NET 框架實現支援許多 XAML 擴充性方案，這些方案最初由特定框架的 XAML 實現定義，但現在是整體 .NET 框架 4 XAML 語言支援的一部分。 本文列出了遷移的類型，並討論了與遷移相關的問題。

## <a name="assemblies-and-namespaces"></a>組件和命名空間

在 .NET 框架 3.5 和 .NET 框架 3.0 中，WPF 為支援 XAML 而實現的類型通常位於<xref:System.Windows.Markup>命名空間中。 這些類型大多數位於 WindowsBase 組件中。

在 .NET 框架 4 中<xref:System.Xaml>，有一個新的命名空間和一個新的 System.Xaml 程式集。 許多原先針對 WPF XAML 實作的類型，現已提供為任何 XAML 實作的擴充點或服務。 為了可供更多一般情節使用，這些類型已從其原始 WPF 組件類型轉送至 System.Xaml 組件。 這支援 XAML 擴充性方案，而無需包括其他框架（如 WPF 和 Windows 工作流基礎）的程式集。

大部分移轉後的類型仍會位於 <xref:System.Windows.Markup> 命名空間中。 部分原因是為了避免破壞個別檔案之現有實作中的 CLR 命名空間對應。 因此，.NET<xref:System.Windows.Markup>框架 4 中的命名空間包含一般 XAML 語言支援類型（來自 System.Xaml 程式集）和特定于 WPF XAML 實現的類型（來自 WindowsBase 和其他 WPF 程式集）的混合。 任何已移轉至 System.Xaml、但先前存在於 WPF 組件中的類型，在 WPF 組件第 4 版中都具有類型轉送支援。

### <a name="workflow-xaml-support-types"></a>Workflow XAML 支援類型

Windows 工作流基礎還提供 XAML 支援類型，在許多情況下，這些類型與 WPF 等效項具有相同的短名稱。 以下是 Windows 工作流基礎 XAML 支援類型的清單：

- <xref:System.Workflow.ComponentModel.Serialization.ContentPropertyAttribute>

- <xref:System.Workflow.ComponentModel.Serialization.RuntimeNamePropertyAttribute>

- <xref:System.Workflow.ComponentModel.Serialization.XmlnsPrefixAttribute>

這些支援類型仍然存在於 .NET 框架 4 的 Windows 工作流基礎程式集中，但仍可用於特定的 Windows 工作流基礎應用程式;但是，它們不應被不使用 Windows 工作流基礎的應用程式或框架引用。

## <a name="markupextension"></a>MarkupExtension

在 .NET 框架 3.5 和 .NET 框架<xref:System.Windows.Markup.MarkupExtension>3.0 中，WPF 的類位於 WindowsBase 程式集中。 Windows 工作流基礎<xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>的並行類存在於 System.Workflow.元件模型程式集中。 在 .NET 框架 4<xref:System.Windows.Markup.MarkupExtension>中，類將遷移到 System.Xaml 程式集。 在 .NET 框架<xref:System.Windows.Markup.MarkupExtension>4 中，適用于使用 .NET XAML 服務的任何 XAML 擴充性方案，而不僅僅是基於特定框架的服務。 進行 XAML 擴充時，也應盡可能將特定架構或架構中的使用者程式碼建置在 <xref:System.Windows.Markup.MarkupExtension> 類別上。

## <a name="markupextension-supporting-service-classes"></a>支援服務類別的 MarkupExtension

WPF 的 .NET 框架 3.5 和 .NET 框架 3.0 提供了一些服務，這些服務可用於<xref:System.Windows.Markup.MarkupExtension>實施者和<xref:System.ComponentModel.TypeConverter>實現，以支援 XAML 中的類型/屬性使用。 這些服務包括：

- <xref:System.Windows.Markup.IProvideValueTarget>

- <xref:System.Windows.Markup.IUriContext>

- <xref:System.Windows.Markup.IXamlTypeResolver>

> [!NOTE]
> .NET Framework 3.5 中與標記擴展相關的另一個服務是<xref:System.Windows.Markup.IReceiveMarkupExtension>介面。 <xref:System.Windows.Markup.IReceiveMarkupExtension>未遷移，標記為`[Obsolete]`.NET 框架 4。 先前使用 <xref:System.Windows.Markup.IReceiveMarkupExtension> 的情節應改用 <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> 屬性化回呼。 <xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute> 也已標記為 `[Obsolete]`。

## <a name="xaml-language-features"></a>XAML 語言功能

有數項 WPF 適用的 XAML 語言功能和元件先前存在於 PresentationFramework 組件中。 這些項目會以 <xref:System.Windows.Markup.MarkupExtension> 子類別的形式實作，以在 XAML 標記中公開標記延伸使用。 在 .NET 框架 4 中，這些功能存在於 System.Xaml 程式集中，以便不包含 WPF 程式集的專案可以使用這些 XAML 語言級功能。 WPF 對 .NET 框架 4 應用程式使用相同的實現。 如本主題所列的其他情況，支援類型會繼續存在於 <xref:System.Windows.Markup> 命名空間中，以避免破壞先前的參考。

下表包含 System.Xaml 中定義的 XAML 功能支援類別清單。

|XAML 語言功能|使用量|
|---------------------------|-----------|
|<xref:System.Windows.Markup.ArrayExtension>|`<x:Array ...>`|
|<xref:System.Windows.Markup.NullExtension>|`{x:Null}`|
|<xref:System.Windows.Markup.StaticExtension>|`{x:Static ...}`|
|<xref:System.Windows.Markup.TypeExtension>|`{x:Type ...}`|

雖然 System.Xaml 可能沒有特定支援類別，但處理 XAML 語言的語言功能時所需的一般邏輯，現已常駐於 System.Xaml 以及其實作的 XAML 讀取器和 XAML 寫入器中。 例如， `x:TypeArguments` 是由 XAML 讀取器和 XAML 寫入器透過 System.Xaml 實作處理的屬性。該屬性可在 XAML 節點資料流中標註、在預設 (CLR 型) XAML 結構描述內容中有處理邏輯、具有 XAML 類型系統表示等。 因此，所有 XAML 語言級別功能的參考文檔是[Windows 演示基礎 （WPF） 桌面指南](../../../desktop-wpf/overview/index.md)中[XAML 服務的](../../../desktop-wpf/xaml-services/index.md)子主題。

## <a name="valueserializer-and-supporting-classes"></a>ValueSerializer 和支援類別

<xref:System.Windows.Markup.ValueSerializer> 類別支援將類型轉換成字串，尤其是在 XAML 序列化需要輸出中有多個模式或節點時。 在 .NET 框架 3.5 和 .NET<xref:System.Windows.Markup.ValueSerializer>框架 3.0 中，WPF 的 是在 WindowsBase 程式集中。 在 .NET 框架 4<xref:System.Windows.Markup.ValueSerializer>中，該類位於 System.Xaml 中，適用于任何 XAML 擴充性方案，而不僅僅是基於 WPF 構建的方案。 <xref:System.Windows.Markup.IValueSerializerContext> (支援服務) 和 <xref:System.Windows.Markup.DateTimeValueSerializer> (特定子類別) 也會移轉至 System.Xaml。

## <a name="xaml-related-attributes"></a>XAML 相關屬性

WPF XAML 隨附數個可套用至 CLR 類型的屬性，以針對其 XAML 行為表示相關資訊。 以下是 .NET 框架 3.5 和 .NET 框架 3.0 中 WPF 程式集中存在的屬性的清單。 這些屬性將遷移到 .NET 框架 4 中的 System.Xaml。

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

## <a name="miscellaneous-classes"></a>其他類別

該<xref:System.Windows.Markup.IComponentConnector>介面存在於 .NET 框架 3.5 和 .NET 框架 3.0 中的 WindowsBase 中，但存在於 .NET 框架 4 中的 System.Xaml 中。 <xref:System.Windows.Markup.IComponentConnector> 主要用於工具支援和 XAML 標記編譯器。

該<xref:System.Windows.Markup.INameScope>介面存在於 .NET 框架 3.5 和 .NET 框架 3.0 中的 WindowsBase 中，但存在於 .NET 框架 4 中的 System.Xaml 中。 <xref:System.Windows.Markup.INameScope> 為 XAML 名稱範圍定義基本作業。

## <a name="xaml-related-classes-with-shared-names-that-exist-in-wpf-and-systemxaml"></a>WPF 和 System.Xaml 中具有共用名稱的 XAML 相關類別

以下類存在於 .NET 框架 4 中的 WPF 程式集和 System.Xaml 程式集中：

`XamlReader`

`XamlWriter`

`XamlParseException`

WPF 實作位於 <xref:System.Windows.Markup> 命名空間和 PresentationFramework 組件中。 System.Xaml 實作位於 <xref:System.Xaml> 命名空間中。 如果您使用 WPF 類型或衍生自 WPF 類型，通常應使用 <xref:System.Windows.Markup.XamlReader> 和 <xref:System.Windows.Markup.XamlWriter> 的 WPF 實作，而不是 System.Xaml 實作。 如需詳細資訊，請參閱 <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> 和 <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>中的＜備註＞。

如果您同時納入 WPF 組件和 System.Xaml 的參考，並且同時對 `include` 和 <xref:System.Windows.Markup> 命名空間使用 <xref:System.Xaml> 陳述式，則您可能必須完整限定對這些 API 的呼叫，以明確解析類型。
