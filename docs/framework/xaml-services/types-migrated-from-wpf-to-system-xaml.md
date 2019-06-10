---
title: 從 WPF 移轉至 System.Xaml 的類型
ms.date: 03/30/2017
helpviewer_keywords:
- WPF XAML [XAML Services], migration to System.Xaml
- XAML [XAML Services], System.Xaml and WPF
- System.Xaml [XAML Services], types migrated from WPF
ms.assetid: d79dabf5-a2ec-4e8d-a37a-67c4ba8a2b91
ms.openlocfilehash: 37433768c1bca3c013fb1e505d55bd7295f34933
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758023"
---
# <a name="types-migrated-from-wpf-to-systemxaml"></a><span data-ttu-id="e7cb1-102">從 WPF 移轉至 System.Xaml 的類型</span><span class="sxs-lookup"><span data-stu-id="e7cb1-102">Types Migrated from WPF to System.Xaml</span></span>
<span data-ttu-id="e7cb1-103">在.NET Framework 3.5 和.NET Framework 3.0，同時[!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]和 Windows Workflow Foundation 隨附 XAML 語言實作。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-103">In .NET Framework 3.5 and .NET Framework 3.0, both [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] and Windows Workflow Foundation included a XAML language implementation.</span></span> <span data-ttu-id="e7cb1-104">有許多為 WPF XAML 實作提供擴充性的公用類型，存在於 WindowsBase、PresentationCore 和 PresentationFramework 組件中。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-104">Many of the public types that provided extensibility for the WPF XAML implementation existed in the WindowsBase, PresentationCore, and PresentationFramework assemblies.</span></span> <span data-ttu-id="e7cb1-105">同樣地，Windows Workflow Foundation XAML 提供擴充性的公用型別存在於 System.Workflow.ComponentModel 組件。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-105">Likewise, public types that provided extensibility for Windows Workflow Foundation XAML existed in the System.Workflow.ComponentModel assembly.</span></span> <span data-ttu-id="e7cb1-106">在.NET Framework 4 中，某些與 XAML 相關型別會移轉至 System.Xaml 組件。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-106">In the .NET Framework 4, some of the XAML-related types are migrated to the System.Xaml assembly.</span></span> <span data-ttu-id="e7cb1-107">常見的.NET Framework 實作的 XAML 語言服務可讓許多 XAML 擴充性情節原先由特定架構的 XAML 實作所定義，但現在是整體的.NET Framework 4 的 XAML 語言支援的一部分。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-107">A common .NET Framework implementation of XAML language services enables many XAML extensibility scenarios that were originally defined by a specific framework's XAML implementation but are now part of overall .NET Framework 4 XAML language support.</span></span> <span data-ttu-id="e7cb1-108">本主題會列出移轉的類型，並討論與移轉相關的問題。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-108">This topic lists the types that are migrated and discusses issues related to the migration.</span></span>  
  
<a name="assemblies_and_namespaces"></a>   
## <a name="assemblies-and-namespaces"></a><span data-ttu-id="e7cb1-109">組件和命名空間</span><span class="sxs-lookup"><span data-stu-id="e7cb1-109">Assemblies and Namespaces</span></span>  
 <span data-ttu-id="e7cb1-110">在.NET Framework 3.5 和.NET Framework 3.0 中，WPF 實作以支援 XAML 的類型是通常在<xref:System.Windows.Markup>命名空間。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-110">In .NET Framework 3.5 and .NET Framework 3.0, the types that WPF implemented to support XAML were generally in the <xref:System.Windows.Markup> namespace.</span></span> <span data-ttu-id="e7cb1-111">這些類型大多數位於 WindowsBase 組件中。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-111">Most of these types were in the WindowsBase assembly.</span></span>  
  
 <span data-ttu-id="e7cb1-112">在.NET Framework 4 中，沒有新<xref:System.Xaml>命名空間和新的 System.Xaml 組件。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-112">In .NET Framework 4, there is a new <xref:System.Xaml> namespace and a new System.Xaml assembly.</span></span> <span data-ttu-id="e7cb1-113">許多原先針對 WPF XAML 實作的類型，現已提供為任何 XAML 實作的擴充點或服務。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-113">Many of the types that were originally implemented for WPF XAML are now provided as extensibility points or services for any implementation of XAML.</span></span> <span data-ttu-id="e7cb1-114">為了可供更多一般情節使用，這些類型已從其原始 WPF 組件類型轉送至 System.Xaml 組件。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-114">As part of making them available for more general scenarios, the types are type-forwarded from their original WPF assembly to the System.Xaml assembly.</span></span> <span data-ttu-id="e7cb1-115">如此 XAML 擴充性案例而無須納入其他架構 （例如 WPF 和 Windows Workflow Foundation） 的組件。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-115">This enables XAML extensibility scenarios without having to include the assemblies of other frameworks (such as WPF and Windows Workflow Foundation).</span></span>  
  
 <span data-ttu-id="e7cb1-116">大部分移轉後的類型仍會位於 <xref:System.Windows.Markup> 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-116">For migrated types, most of the types remain in the <xref:System.Windows.Markup> namespace.</span></span> <span data-ttu-id="e7cb1-117">部分原因是為了避免破壞個別檔案之現有實作中的 CLR 命名空間對應。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-117">This was partially to avoid breaking CLR namespace mappings in existing implementations on a per-file basis.</span></span> <span data-ttu-id="e7cb1-118">如此一來， <xref:System.Windows.Markup> .NET Framework 4 中的命名空間包含混合的一般 XAML 語言支援類型 （來自 System.Xaml 組件） 和類型的特定 WPF XAML 實作 （來自 WindowsBase 和其他 WPF 組件）。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-118">As a result, the <xref:System.Windows.Markup> namespace in .NET Framework 4 contains a mixture of general XAML language support types (from the System.Xaml assembly) and types that are specific to the WPF XAML implementation (from WindowsBase and other WPF assemblies).</span></span> <span data-ttu-id="e7cb1-119">任何已移轉至 System.Xaml、但先前存在於 WPF 組件中的類型，在 WPF 組件第 4 版中都具有類型轉送支援。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-119">Any type that was migrated to System.Xaml, but existed previously in a WPF assembly, has type-forwarding support in version 4 of the WPF assembly.</span></span>  
  
### <a name="workflow-xaml-support-types"></a><span data-ttu-id="e7cb1-120">Workflow XAML 支援類型</span><span class="sxs-lookup"><span data-stu-id="e7cb1-120">Workflow XAML Support Types</span></span>  
 <span data-ttu-id="e7cb1-121">Windows Workflow Foundation 也提供 XAML 支援類型，並在許多情況下，這些有相同的短檔名，用於對等 WPF。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-121">Windows Workflow Foundation also provided XAML support types, and in many cases these had identical short names to a WPF equivalent.</span></span> <span data-ttu-id="e7cb1-122">以下是 Windows Workflow Foundation XAML 支援類型的清單：</span><span class="sxs-lookup"><span data-stu-id="e7cb1-122">The following is a list of Windows Workflow Foundation XAML support types:</span></span>  
  
- <xref:System.Workflow.ComponentModel.Serialization.ContentPropertyAttribute>  
  
- <xref:System.Workflow.ComponentModel.Serialization.RuntimeNamePropertyAttribute>  
  
- <xref:System.Workflow.ComponentModel.Serialization.XmlnsPrefixAttribute>  
  
 <span data-ttu-id="e7cb1-123">這些支援類型仍存在於.NET Framework 4 的 Windows Workflow Foundation 組件，並且仍然可以用於特定的 Windows Workflow Foundation 應用程式;不過，它們不應參考的應用程式或不使用 Windows Workflow Foundation 的架構。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-123">These support types still exist in the Windows Workflow Foundation assemblies for .NET Framework 4 and can still be used for specific Windows Workflow Foundation applications; however, they should not be referenced by applications or frameworks that do not use Windows Workflow Foundation.</span></span>  
  
<a name="markupextension"></a>   
## <a name="markupextension"></a><span data-ttu-id="e7cb1-124">MarkupExtension</span><span class="sxs-lookup"><span data-stu-id="e7cb1-124">MarkupExtension</span></span>  
 <span data-ttu-id="e7cb1-125">在.NET Framework 3.5 和.NET Framework 3.0，<xref:System.Windows.Markup.MarkupExtension>類別 WPF 是位於 WindowsBase 組件。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-125">In the .NET Framework 3.5 and .NET Framework 3.0, the <xref:System.Windows.Markup.MarkupExtension> class for WPF was in the WindowsBase assembly.</span></span> <span data-ttu-id="e7cb1-126">Windows Workflow Foundation 的平行類別<xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>System.Workflow.ComponentModel 組件中。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-126">A parallel class for Windows Workflow Foundation, <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>, existed in the System.Workflow.ComponentModel assembly.</span></span> <span data-ttu-id="e7cb1-127">在.NET Framework 4<xref:System.Windows.Markup.MarkupExtension>類別已移轉至 System.Xaml 組件。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-127">In the .NET Framework 4, the <xref:System.Windows.Markup.MarkupExtension> class is migrated to the System.Xaml assembly.</span></span> <span data-ttu-id="e7cb1-128">在.NET Framework 4<xref:System.Windows.Markup.MarkupExtension>適用於使用.NET Framework XAML 服務，不只是用於建置在特定架構上的任何 XAML 擴充性案例。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-128">In the .NET Framework 4, <xref:System.Windows.Markup.MarkupExtension> is intended for any XAML extensibility scenario that uses .NET Framework XAML Services, not just for those that build on specific frameworks.</span></span> <span data-ttu-id="e7cb1-129">進行 XAML 擴充時，也應盡可能將特定架構或架構中的使用者程式碼建置在 <xref:System.Windows.Markup.MarkupExtension> 類別上。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-129">When possible, specific frameworks or user code in the framework should also build on the <xref:System.Windows.Markup.MarkupExtension> class for XAML extension.</span></span>  
  
<a name="markupextension_supporting_service_classes"></a>   
## <a name="markupextension-supporting-service-classes"></a><span data-ttu-id="e7cb1-130">支援服務類別的 MarkupExtension</span><span class="sxs-lookup"><span data-stu-id="e7cb1-130">MarkupExtension Supporting Service Classes</span></span>  
 <span data-ttu-id="e7cb1-131">.NET framework 3.5 和.NET Framework 3.0，wpf 提供數個服務，可用於<xref:System.Windows.Markup.MarkupExtension>實作者和<xref:System.ComponentModel.TypeConverter>實作以在 XAML 支援類型/屬性使用。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-131">.NET Framework 3.5 and .NET Framework 3.0 for WPF provided several services that were available to <xref:System.Windows.Markup.MarkupExtension> implementers and <xref:System.ComponentModel.TypeConverter> implementations to support type/property usage in XAML.</span></span> <span data-ttu-id="e7cb1-132">這些服務包括：</span><span class="sxs-lookup"><span data-stu-id="e7cb1-132">These services are the following:</span></span>  
  
- <xref:System.Windows.Markup.IProvideValueTarget>  
  
- <xref:System.Windows.Markup.IUriContext>  
  
- <xref:System.Windows.Markup.IXamlTypeResolver>  
  
> [!NOTE]
>  <span data-ttu-id="e7cb1-133">另一項服務與標記延伸相關的.NET Framework 3.5 是<xref:System.Windows.Markup.IReceiveMarkupExtension>介面。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-133">Another service from .NET Framework 3.5 that is related to markup extensions is the <xref:System.Windows.Markup.IReceiveMarkupExtension> interface.</span></span> <span data-ttu-id="e7cb1-134"><xref:System.Windows.Markup.IReceiveMarkupExtension> 並未移轉，而且標示為`[Obsolete]`適用於.NET Framework 4。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-134"><xref:System.Windows.Markup.IReceiveMarkupExtension> was not migrated and is marked `[Obsolete]` for .NET Framework 4.</span></span> <span data-ttu-id="e7cb1-135">先前使用 <xref:System.Windows.Markup.IReceiveMarkupExtension> 的情節應改用 <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> 屬性化回呼。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-135">Scenarios that previously used <xref:System.Windows.Markup.IReceiveMarkupExtension> should instead use <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> attributed callbacks.</span></span> <span data-ttu-id="e7cb1-136"><xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute> 也已標記為 `[Obsolete]`。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-136"><xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute> is also marked `[Obsolete]`.</span></span>  
  
<a name="xaml_language_features"></a>   
## <a name="xaml-language-features"></a><span data-ttu-id="e7cb1-137">XAML 語言功能</span><span class="sxs-lookup"><span data-stu-id="e7cb1-137">XAML Language Features</span></span>  
 <span data-ttu-id="e7cb1-138">有數項 WPF 適用的 XAML 語言功能和元件先前存在於 PresentationFramework 組件中。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-138">Several XAML language features and components for WPF previously existed in the PresentationFramework assembly.</span></span> <span data-ttu-id="e7cb1-139">這些項目會以 <xref:System.Windows.Markup.MarkupExtension> 子類別的形式實作，以在 XAML 標記中公開標記延伸使用。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-139">These were implemented as a <xref:System.Windows.Markup.MarkupExtension> subclass to expose markup extension usages in XAML markup.</span></span> <span data-ttu-id="e7cb1-140">在.NET Framework 4 中，這些存在於 System.Xaml 組件，讓不含 WPF 組件的專案可以使用這些 XAML 語言層級功能。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-140">In .NET Framework 4, these exist in the System.Xaml assembly so that projects that do not include WPF assemblies can use these XAML language-level features.</span></span> <span data-ttu-id="e7cb1-141">WPF 會使用這些相同的實作，.NET Framework 4 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-141">WPF uses these same implementations for .NET Framework 4 applications.</span></span> <span data-ttu-id="e7cb1-142">如本主題所列的其他情況，支援類型會繼續存在於 <xref:System.Windows.Markup> 命名空間中，以避免破壞先前的參考。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-142">As with the other cases that are listed in this topic, the supporting types continue to exist in the <xref:System.Windows.Markup> namespace to avoid breaking previous references.</span></span>  
  
 <span data-ttu-id="e7cb1-143">下表包含 System.Xaml 中定義的 XAML 功能支援類別清單。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-143">The following table contains a list of the XAML feature-support classes that are defined in System.Xaml.</span></span>  
  
|<span data-ttu-id="e7cb1-144">XAML 語言功能</span><span class="sxs-lookup"><span data-stu-id="e7cb1-144">XAML Language Feature</span></span>|<span data-ttu-id="e7cb1-145">使用量</span><span class="sxs-lookup"><span data-stu-id="e7cb1-145">Usage</span></span>|  
|---------------------------|-----------|  
|<xref:System.Windows.Markup.ArrayExtension>|`<x:Array ...>`|  
|<xref:System.Windows.Markup.NullExtension>|`{x:Null}`|  
|<xref:System.Windows.Markup.StaticExtension>|`{x:Static ...}`|  
|<xref:System.Windows.Markup.TypeExtension>|`{x:Type ...}`|  
  
 <span data-ttu-id="e7cb1-146">雖然 System.Xaml 可能沒有特定支援類別，但處理 XAML 語言的語言功能時所需的一般邏輯，現已常駐於 System.Xaml 以及其實作的 XAML 讀取器和 XAML 寫入器中。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-146">Although System.Xaml may not have specific support classes, the general logic for processing language features for the XAML language now resides in System.Xaml and its implemented XAML readers and XAML writers.</span></span> <span data-ttu-id="e7cb1-147">例如， `x:TypeArguments` 是由 XAML 讀取器和 XAML 寫入器透過 System.Xaml 實作處理的屬性。該屬性可在 XAML 節點資料流中標註、在預設 (CLR 型) XAML 結構描述內容中有處理邏輯、具有 XAML 類型系統表示等。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-147">For example, `x:TypeArguments` is an attribute that is processed by XAML readers and XAML writers from System.Xaml implementations; it can be noted in the XAML node stream, has handling in the default (CLR-based) XAML schema context, has a XAML type-system representation, and so on.</span></span> <span data-ttu-id="e7cb1-148">因此，所有 XAML 語言層級功能的參考文件，都會是 [XAML Services](index.md) 和 .NET Framework 文件集該一般區域的子主題，而不會是 WPF 文件集中 [進階 (Windows Presentation Foundation)](../wpf/advanced/index.md) 的子主題 (在 3.5 文件集中仍為如此)。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-148">As a result, the reference documentation for all XAML language-level features is a subtopic for [XAML Services](index.md) and that general area of the .NET Framework documentation set, instead of being part of the WPF documentation set as a subtopic of [Advanced (Windows Presentation Foundation)](../wpf/advanced/index.md) (as is still the case in 3.5 documentation sets).</span></span>  
  
<a name="valueserializer_and_supporting_classes"></a>   
## <a name="valueserializer-and-supporting-classes"></a><span data-ttu-id="e7cb1-149">ValueSerializer 和支援類別</span><span class="sxs-lookup"><span data-stu-id="e7cb1-149">ValueSerializer and Supporting Classes</span></span>  
 <span data-ttu-id="e7cb1-150"><xref:System.Windows.Markup.ValueSerializer> 類別支援將類型轉換成字串，尤其是在 XAML 序列化需要輸出中有多個模式或節點時。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-150">The <xref:System.Windows.Markup.ValueSerializer> class supports type conversion to a string, particularly for XAML serialization cases where serialization may require multiple modes or nodes in the output.</span></span> <span data-ttu-id="e7cb1-151">在.NET Framework 3.5 和.NET Framework 3.0， <xref:System.Windows.Markup.ValueSerializer> WPF 是位於 WindowsBase 組件。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-151">In .NET Framework 3.5 and .NET Framework 3.0, the <xref:System.Windows.Markup.ValueSerializer> for WPF was in the WindowsBase assembly.</span></span> <span data-ttu-id="e7cb1-152">在.NET Framework 4<xref:System.Windows.Markup.ValueSerializer>類別位於 System.Xaml，並用於任何 XAML 擴充性案例中，用不只是用於在 WPF 上建置。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-152">In the .NET Framework 4, the <xref:System.Windows.Markup.ValueSerializer> class is in System.Xaml and is intended for any XAML extensibility scenario, not just for those that build on WPF.</span></span> <span data-ttu-id="e7cb1-153"><xref:System.Windows.Markup.IValueSerializerContext> (支援服務) 和 <xref:System.Windows.Markup.DateTimeValueSerializer> (特定子類別) 也會移轉至 System.Xaml。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-153"><xref:System.Windows.Markup.IValueSerializerContext> (a supporting service) and <xref:System.Windows.Markup.DateTimeValueSerializer> (a specific subclass) are also migrated to System.Xaml.</span></span>  
  
<a name="xamlrelated_attributes"></a>   
## <a name="xaml-related-attributes"></a><span data-ttu-id="e7cb1-154">XAML 相關屬性</span><span class="sxs-lookup"><span data-stu-id="e7cb1-154">XAML-Related Attributes</span></span>  
 <span data-ttu-id="e7cb1-155">WPF XAML 隨附數個可套用至 CLR 類型的屬性，以針對其 XAML 行為表示相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-155">WPF XAML included several attributes that can be applied to CLR types to indicate something about their XAML behavior.</span></span> <span data-ttu-id="e7cb1-156">以下是存在於 WPF 組件中.NET Framework 3.5 和.NET Framework 3.0 中的屬性清單。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-156">The following is a list of the attributes that existed in WPF assemblies in .NET Framework 3.5 and .NET Framework 3.0.</span></span> <span data-ttu-id="e7cb1-157">這些屬性會移轉至 System.Xaml 中.NET Framework 4。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-157">These attributes are migrated to System.Xaml in .NET Framework 4.</span></span>  
  
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
## <a name="miscellaneous-classes"></a><span data-ttu-id="e7cb1-158">其他類別</span><span class="sxs-lookup"><span data-stu-id="e7cb1-158">Miscellaneous Classes</span></span>  
 <span data-ttu-id="e7cb1-159"><xref:System.Windows.Markup.IComponentConnector>介面存在於 WindowsBase 中的.NET Framework 3.5 和.NET Framework 3.0，但存在於 System.Xaml 中.NET Framework 4。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-159">The <xref:System.Windows.Markup.IComponentConnector> interface existed in WindowsBase in the .NET Framework 3.5 and .NET Framework 3.0, but exists in System.Xaml in .NET Framework 4.</span></span> <span data-ttu-id="e7cb1-160"><xref:System.Windows.Markup.IComponentConnector> 主要用於工具支援和 XAML 標記編譯器。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-160"><xref:System.Windows.Markup.IComponentConnector> is primarily intended for tooling support and XAML markup compilers.</span></span>  
  
 <span data-ttu-id="e7cb1-161"><xref:System.Windows.Markup.INameScope>介面存在於 WindowsBase 中的.NET Framework 3.5 和.NET Framework 3.0，但存在於 System.Xaml 中.NET Framework 4。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-161">The <xref:System.Windows.Markup.INameScope> interface existed in WindowsBase in the .NET Framework 3.5 and .NET Framework 3.0, but exists in System.Xaml in .NET Framework 4.</span></span> <span data-ttu-id="e7cb1-162"><xref:System.Windows.Markup.INameScope> 為 XAML 名稱範圍定義基本作業。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-162"><xref:System.Windows.Markup.INameScope> defines basic operations for a XAML namescope.</span></span>  
  
<a name="xamlrelated_classes_with_shared_names_that_exist_in_wpf_and_systemxaml"></a>   
## <a name="xaml-related-classes-with-shared-names-that-exist-in-wpf-and-systemxaml"></a><span data-ttu-id="e7cb1-163">WPF 和 System.Xaml 中具有共用名稱的 XAML 相關類別</span><span class="sxs-lookup"><span data-stu-id="e7cb1-163">XAML-related Classes with Shared Names that Exist in WPF and System.Xaml</span></span>  
 <span data-ttu-id="e7cb1-164">下列類別存在於 WPF 組件和 System.Xaml 組件，在.NET Framework 4 中：</span><span class="sxs-lookup"><span data-stu-id="e7cb1-164">The following classes exist in both the WPF assemblies and the System.Xaml assembly in the .NET Framework 4:</span></span>  
  
 `XamlReader`  
  
 `XamlWriter`  
  
 `XamlParseException`  
  
 <span data-ttu-id="e7cb1-165">WPF 實作位於 <xref:System.Windows.Markup> 命名空間和 PresentationFramework 組件中。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-165">The WPF implementation is found in the <xref:System.Windows.Markup> namespace, and PresentationFramework assembly.</span></span> <span data-ttu-id="e7cb1-166">System.Xaml 實作位於 <xref:System.Xaml> 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-166">The System.Xaml implementation is found in the <xref:System.Xaml> namespace.</span></span> <span data-ttu-id="e7cb1-167">如果您使用 WPF 類型或衍生自 WPF 類型，通常應使用 <xref:System.Windows.Markup.XamlReader> 和 <xref:System.Windows.Markup.XamlWriter> 的 WPF 實作，而不是 System.Xaml 實作。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-167">If you are using WPF types or are deriving from WPF types, you should typically use the WPF implementations of <xref:System.Windows.Markup.XamlReader> and <xref:System.Windows.Markup.XamlWriter> instead of the System.Xaml implementations.</span></span> <span data-ttu-id="e7cb1-168">如需詳細資訊，請參閱 <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> 和 <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>中的＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-168">For more information, see Remarks in <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> and <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="e7cb1-169">如果您同時納入 WPF 組件和 System.Xaml 的參考，並且同時對 `include` 和 <xref:System.Windows.Markup> 命名空間使用 <xref:System.Xaml> 陳述式，則您可能必須完整限定對這些 API 的呼叫，以明確解析類型。</span><span class="sxs-lookup"><span data-stu-id="e7cb1-169">If you are including references to both WPF assemblies and System.Xaml, and you also are using `include` statements for both the <xref:System.Windows.Markup> and <xref:System.Xaml> namespaces, you may need to fully qualify the calls to these APIs in order to resolve the types without ambiguity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7cb1-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7cb1-170">See also</span></span>

- [<span data-ttu-id="e7cb1-171">XAML Services</span><span class="sxs-lookup"><span data-stu-id="e7cb1-171">XAML Services</span></span>](index.md)
