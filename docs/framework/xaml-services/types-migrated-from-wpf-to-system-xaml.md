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
# <a name="types-migrated-from-wpf-to-systemxaml"></a><span data-ttu-id="3fd2c-102">從 WPF 移轉至 System.Xaml 的類型</span><span class="sxs-lookup"><span data-stu-id="3fd2c-102">Types Migrated from WPF to System.Xaml</span></span>
<span data-ttu-id="3fd2c-103">在 .NET Framework 3.5 和 .NET Framework 3.0 中, [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]和 Windows Workflow Foundation 都包含 XAML 語言執行。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-103">In .NET Framework 3.5 and .NET Framework 3.0, both [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] and Windows Workflow Foundation included a XAML language implementation.</span></span> <span data-ttu-id="3fd2c-104">有許多為 WPF XAML 實作提供擴充性的公用類型，存在於 WindowsBase、PresentationCore 和 PresentationFramework 組件中。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-104">Many of the public types that provided extensibility for the WPF XAML implementation existed in the WindowsBase, PresentationCore, and PresentationFramework assemblies.</span></span> <span data-ttu-id="3fd2c-105">同樣地, 為 Windows Workflow Foundation XAML 提供擴充性的公用類型也存在於 System.workflow.componentmodel.activity 元件中。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-105">Likewise, public types that provided extensibility for Windows Workflow Foundation XAML existed in the System.Workflow.ComponentModel assembly.</span></span> <span data-ttu-id="3fd2c-106">在 .NET Framework 4 中, 某些與 XAML 相關的類型會遷移至 system.string 元件。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-106">In the .NET Framework 4, some of the XAML-related types are migrated to the System.Xaml assembly.</span></span> <span data-ttu-id="3fd2c-107">XAML 語言服務的常見 .NET Framework 執行, 可讓許多 XAML 擴充性案例原本是由特定架構的 XAML 執行所定義, 但現在已成為整體 .NET Framework 4 個 XAML 語言支援的一部分。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-107">A common .NET Framework implementation of XAML language services enables many XAML extensibility scenarios that were originally defined by a specific framework's XAML implementation but are now part of overall .NET Framework 4 XAML language support.</span></span> <span data-ttu-id="3fd2c-108">本主題會列出移轉的類型，並討論與移轉相關的問題。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-108">This topic lists the types that are migrated and discusses issues related to the migration.</span></span>  
  
<a name="assemblies_and_namespaces"></a>   
## <a name="assemblies-and-namespaces"></a><span data-ttu-id="3fd2c-109">組件和命名空間</span><span class="sxs-lookup"><span data-stu-id="3fd2c-109">Assemblies and Namespaces</span></span>  
 <span data-ttu-id="3fd2c-110">在 .NET Framework 3.5 和 .NET Framework 3.0 中, WPF 實作為支援 XAML 的類型通常是在<xref:System.Windows.Markup>命名空間中。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-110">In .NET Framework 3.5 and .NET Framework 3.0, the types that WPF implemented to support XAML were generally in the <xref:System.Windows.Markup> namespace.</span></span> <span data-ttu-id="3fd2c-111">這些類型大多數位於 WindowsBase 組件中。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-111">Most of these types were in the WindowsBase assembly.</span></span>  
  
 <span data-ttu-id="3fd2c-112">在 .NET Framework 4 中, 有一個新<xref:System.Xaml>的命名空間和一個新的 system.object 元件。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-112">In .NET Framework 4, there is a new <xref:System.Xaml> namespace and a new System.Xaml assembly.</span></span> <span data-ttu-id="3fd2c-113">許多原先針對 WPF XAML 實作的類型，現已提供為任何 XAML 實作的擴充點或服務。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-113">Many of the types that were originally implemented for WPF XAML are now provided as extensibility points or services for any implementation of XAML.</span></span> <span data-ttu-id="3fd2c-114">為了可供更多一般情節使用，這些類型已從其原始 WPF 組件類型轉送至 System.Xaml 組件。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-114">As part of making them available for more general scenarios, the types are type-forwarded from their original WPF assembly to the System.Xaml assembly.</span></span> <span data-ttu-id="3fd2c-115">這會啟用 XAML 擴充性案例, 而不需要包含其他架構的元件 (例如 WPF 和 Windows Workflow Foundation)。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-115">This enables XAML extensibility scenarios without having to include the assemblies of other frameworks (such as WPF and Windows Workflow Foundation).</span></span>  
  
 <span data-ttu-id="3fd2c-116">大部分移轉後的類型仍會位於 <xref:System.Windows.Markup> 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-116">For migrated types, most of the types remain in the <xref:System.Windows.Markup> namespace.</span></span> <span data-ttu-id="3fd2c-117">部分原因是為了避免破壞個別檔案之現有實作中的 CLR 命名空間對應。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-117">This was partially to avoid breaking CLR namespace mappings in existing implementations on a per-file basis.</span></span> <span data-ttu-id="3fd2c-118">因此, .NET Framework 4 中<xref:System.Windows.Markup>的命名空間包含一般 XAML 語言支援類型的混合 (來自 system.string 元件), 以及 WPF XAML 實作為特定的類型 (來自 WindowsBase 和其他 wpf 元件)。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-118">As a result, the <xref:System.Windows.Markup> namespace in .NET Framework 4 contains a mixture of general XAML language support types (from the System.Xaml assembly) and types that are specific to the WPF XAML implementation (from WindowsBase and other WPF assemblies).</span></span> <span data-ttu-id="3fd2c-119">任何已移轉至 System.Xaml、但先前存在於 WPF 組件中的類型，在 WPF 組件第 4 版中都具有類型轉送支援。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-119">Any type that was migrated to System.Xaml, but existed previously in a WPF assembly, has type-forwarding support in version 4 of the WPF assembly.</span></span>  
  
### <a name="workflow-xaml-support-types"></a><span data-ttu-id="3fd2c-120">Workflow XAML 支援類型</span><span class="sxs-lookup"><span data-stu-id="3fd2c-120">Workflow XAML Support Types</span></span>  
 <span data-ttu-id="3fd2c-121">Windows Workflow Foundation 也提供 XAML 支援型別, 而且在許多情況下, 這些都有與 WPF 對等的簡短名稱。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-121">Windows Workflow Foundation also provided XAML support types, and in many cases these had identical short names to a WPF equivalent.</span></span> <span data-ttu-id="3fd2c-122">以下是 Windows Workflow Foundation XAML 支援類型的清單:</span><span class="sxs-lookup"><span data-stu-id="3fd2c-122">The following is a list of Windows Workflow Foundation XAML support types:</span></span>  
  
- <xref:System.Workflow.ComponentModel.Serialization.ContentPropertyAttribute>  
  
- <xref:System.Workflow.ComponentModel.Serialization.RuntimeNamePropertyAttribute>  
  
- <xref:System.Workflow.ComponentModel.Serialization.XmlnsPrefixAttribute>  
  
 <span data-ttu-id="3fd2c-123">這些支援類型仍存在於 .NET Framework 4 的 Windows Workflow Foundation 元件中, 而且仍然可以用於特定的 Windows Workflow Foundation 應用程式;不過, 不應由不使用 Windows Workflow Foundation 的應用程式或架構參考。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-123">These support types still exist in the Windows Workflow Foundation assemblies for .NET Framework 4 and can still be used for specific Windows Workflow Foundation applications; however, they should not be referenced by applications or frameworks that do not use Windows Workflow Foundation.</span></span>  
  
<a name="markupextension"></a>   
## <a name="markupextension"></a><span data-ttu-id="3fd2c-124">MarkupExtension</span><span class="sxs-lookup"><span data-stu-id="3fd2c-124">MarkupExtension</span></span>  
 <span data-ttu-id="3fd2c-125">在 .NET Framework 3.5 和 .NET Framework 3.0 中, WPF <xref:System.Windows.Markup.MarkupExtension>的類別是在 WindowsBase 元件中。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-125">In the .NET Framework 3.5 and .NET Framework 3.0, the <xref:System.Windows.Markup.MarkupExtension> class for WPF was in the WindowsBase assembly.</span></span> <span data-ttu-id="3fd2c-126">System.workflow.componentmodel.activity 元件中已存在 Windows Workflow Foundation <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>的平行類別。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-126">A parallel class for Windows Workflow Foundation, <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>, existed in the System.Workflow.ComponentModel assembly.</span></span> <span data-ttu-id="3fd2c-127">在 .NET Framework 4 中, <xref:System.Windows.Markup.MarkupExtension>類別會遷移至 system.object 元件。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-127">In the .NET Framework 4, the <xref:System.Windows.Markup.MarkupExtension> class is migrated to the System.Xaml assembly.</span></span> <span data-ttu-id="3fd2c-128">在 .NET Framework 4 中, <xref:System.Windows.Markup.MarkupExtension>適用于任何使用 .NET Framework xaml 服務的 xaml 擴充性情節, 而不只是針對特定架構所建立的物件。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-128">In the .NET Framework 4, <xref:System.Windows.Markup.MarkupExtension> is intended for any XAML extensibility scenario that uses .NET Framework XAML Services, not just for those that build on specific frameworks.</span></span> <span data-ttu-id="3fd2c-129">進行 XAML 擴充時，也應盡可能將特定架構或架構中的使用者程式碼建置在 <xref:System.Windows.Markup.MarkupExtension> 類別上。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-129">When possible, specific frameworks or user code in the framework should also build on the <xref:System.Windows.Markup.MarkupExtension> class for XAML extension.</span></span>  
  
<a name="markupextension_supporting_service_classes"></a>   
## <a name="markupextension-supporting-service-classes"></a><span data-ttu-id="3fd2c-130">支援服務類別的 MarkupExtension</span><span class="sxs-lookup"><span data-stu-id="3fd2c-130">MarkupExtension Supporting Service Classes</span></span>  
 <span data-ttu-id="3fd2c-131">WPF 的 .NET Framework 3.5 和 .NET Framework 3.0 提供了<xref:System.Windows.Markup.MarkupExtension>數項服務, 可供實作者和<xref:System.ComponentModel.TypeConverter>實作為支援 XAML 中的類型/屬性使用。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-131">.NET Framework 3.5 and .NET Framework 3.0 for WPF provided several services that were available to <xref:System.Windows.Markup.MarkupExtension> implementers and <xref:System.ComponentModel.TypeConverter> implementations to support type/property usage in XAML.</span></span> <span data-ttu-id="3fd2c-132">這些服務包括：</span><span class="sxs-lookup"><span data-stu-id="3fd2c-132">These services are the following:</span></span>  
  
- <xref:System.Windows.Markup.IProvideValueTarget>  
  
- <xref:System.Windows.Markup.IUriContext>  
  
- <xref:System.Windows.Markup.IXamlTypeResolver>  
  
> [!NOTE]
> <span data-ttu-id="3fd2c-133">與標記延伸相關的 .NET Framework 3.5 的另一個服務是<xref:System.Windows.Markup.IReceiveMarkupExtension>介面。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-133">Another service from .NET Framework 3.5 that is related to markup extensions is the <xref:System.Windows.Markup.IReceiveMarkupExtension> interface.</span></span> <span data-ttu-id="3fd2c-134"><xref:System.Windows.Markup.IReceiveMarkupExtension>尚未遷移, 並標示`[Obsolete]`為 .NET Framework 4。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-134"><xref:System.Windows.Markup.IReceiveMarkupExtension> was not migrated and is marked `[Obsolete]` for .NET Framework 4.</span></span> <span data-ttu-id="3fd2c-135">先前使用 <xref:System.Windows.Markup.IReceiveMarkupExtension> 的情節應改用 <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> 屬性化回呼。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-135">Scenarios that previously used <xref:System.Windows.Markup.IReceiveMarkupExtension> should instead use <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> attributed callbacks.</span></span> <span data-ttu-id="3fd2c-136"><xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute> 也已標記為 `[Obsolete]`。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-136"><xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute> is also marked `[Obsolete]`.</span></span>  
  
<a name="xaml_language_features"></a>   
## <a name="xaml-language-features"></a><span data-ttu-id="3fd2c-137">XAML 語言功能</span><span class="sxs-lookup"><span data-stu-id="3fd2c-137">XAML Language Features</span></span>  
 <span data-ttu-id="3fd2c-138">有數項 WPF 適用的 XAML 語言功能和元件先前存在於 PresentationFramework 組件中。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-138">Several XAML language features and components for WPF previously existed in the PresentationFramework assembly.</span></span> <span data-ttu-id="3fd2c-139">這些項目會以 <xref:System.Windows.Markup.MarkupExtension> 子類別的形式實作，以在 XAML 標記中公開標記延伸使用。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-139">These were implemented as a <xref:System.Windows.Markup.MarkupExtension> subclass to expose markup extension usages in XAML markup.</span></span> <span data-ttu-id="3fd2c-140">在 .NET Framework 4 中, 這些存在於 System.object 元件中, 因此不包含 WPF 元件的專案可以使用這些 XAML 語言層級功能。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-140">In .NET Framework 4, these exist in the System.Xaml assembly so that projects that do not include WPF assemblies can use these XAML language-level features.</span></span> <span data-ttu-id="3fd2c-141">WPF 會針對 .NET Framework 4 應用程式使用這些相同的執行。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-141">WPF uses these same implementations for .NET Framework 4 applications.</span></span> <span data-ttu-id="3fd2c-142">如本主題所列的其他情況，支援類型會繼續存在於 <xref:System.Windows.Markup> 命名空間中，以避免破壞先前的參考。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-142">As with the other cases that are listed in this topic, the supporting types continue to exist in the <xref:System.Windows.Markup> namespace to avoid breaking previous references.</span></span>  
  
 <span data-ttu-id="3fd2c-143">下表包含 System.Xaml 中定義的 XAML 功能支援類別清單。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-143">The following table contains a list of the XAML feature-support classes that are defined in System.Xaml.</span></span>  
  
|<span data-ttu-id="3fd2c-144">XAML 語言功能</span><span class="sxs-lookup"><span data-stu-id="3fd2c-144">XAML Language Feature</span></span>|<span data-ttu-id="3fd2c-145">使用量</span><span class="sxs-lookup"><span data-stu-id="3fd2c-145">Usage</span></span>|  
|---------------------------|-----------|  
|<xref:System.Windows.Markup.ArrayExtension>|`<x:Array ...>`|  
|<xref:System.Windows.Markup.NullExtension>|`{x:Null}`|  
|<xref:System.Windows.Markup.StaticExtension>|`{x:Static ...}`|  
|<xref:System.Windows.Markup.TypeExtension>|`{x:Type ...}`|  
  
 <span data-ttu-id="3fd2c-146">雖然 System.Xaml 可能沒有特定支援類別，但處理 XAML 語言的語言功能時所需的一般邏輯，現已常駐於 System.Xaml 以及其實作的 XAML 讀取器和 XAML 寫入器中。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-146">Although System.Xaml may not have specific support classes, the general logic for processing language features for the XAML language now resides in System.Xaml and its implemented XAML readers and XAML writers.</span></span> <span data-ttu-id="3fd2c-147">例如， `x:TypeArguments` 是由 XAML 讀取器和 XAML 寫入器透過 System.Xaml 實作處理的屬性。該屬性可在 XAML 節點資料流中標註、在預設 (CLR 型) XAML 結構描述內容中有處理邏輯、具有 XAML 類型系統表示等。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-147">For example, `x:TypeArguments` is an attribute that is processed by XAML readers and XAML writers from System.Xaml implementations; it can be noted in the XAML node stream, has handling in the default (CLR-based) XAML schema context, has a XAML type-system representation, and so on.</span></span> <span data-ttu-id="3fd2c-148">因此，所有 XAML 語言層級功能的參考文件，都會是 [XAML Services](index.md) 和 .NET Framework 文件集該一般區域的子主題，而不會是 WPF 文件集中 [進階 (Windows Presentation Foundation)](../wpf/advanced/index.md) 的子主題 (在 3.5 文件集中仍為如此)。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-148">As a result, the reference documentation for all XAML language-level features is a subtopic for [XAML Services](index.md) and that general area of the .NET Framework documentation set, instead of being part of the WPF documentation set as a subtopic of [Advanced (Windows Presentation Foundation)](../wpf/advanced/index.md) (as is still the case in 3.5 documentation sets).</span></span>  
  
<a name="valueserializer_and_supporting_classes"></a>   
## <a name="valueserializer-and-supporting-classes"></a><span data-ttu-id="3fd2c-149">ValueSerializer 和支援類別</span><span class="sxs-lookup"><span data-stu-id="3fd2c-149">ValueSerializer and Supporting Classes</span></span>  
 <span data-ttu-id="3fd2c-150"><xref:System.Windows.Markup.ValueSerializer> 類別支援將類型轉換成字串，尤其是在 XAML 序列化需要輸出中有多個模式或節點時。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-150">The <xref:System.Windows.Markup.ValueSerializer> class supports type conversion to a string, particularly for XAML serialization cases where serialization may require multiple modes or nodes in the output.</span></span> <span data-ttu-id="3fd2c-151">在 .NET Framework 3.5 和 .NET Framework 3.0 中, <xref:System.Windows.Markup.ValueSerializer> for WPF 的是在 WindowsBase 元件中。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-151">In .NET Framework 3.5 and .NET Framework 3.0, the <xref:System.Windows.Markup.ValueSerializer> for WPF was in the WindowsBase assembly.</span></span> <span data-ttu-id="3fd2c-152">在 .NET Framework 4 中, <xref:System.Windows.Markup.ValueSerializer>類別是在 system.string 中, 適用于任何 Xaml 擴充性情節, 而不只是在 WPF 上建立的實例。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-152">In the .NET Framework 4, the <xref:System.Windows.Markup.ValueSerializer> class is in System.Xaml and is intended for any XAML extensibility scenario, not just for those that build on WPF.</span></span> <span data-ttu-id="3fd2c-153"><xref:System.Windows.Markup.IValueSerializerContext> (支援服務) 和 <xref:System.Windows.Markup.DateTimeValueSerializer> (特定子類別) 也會移轉至 System.Xaml。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-153"><xref:System.Windows.Markup.IValueSerializerContext> (a supporting service) and <xref:System.Windows.Markup.DateTimeValueSerializer> (a specific subclass) are also migrated to System.Xaml.</span></span>  
  
<a name="xamlrelated_attributes"></a>   
## <a name="xaml-related-attributes"></a><span data-ttu-id="3fd2c-154">XAML 相關屬性</span><span class="sxs-lookup"><span data-stu-id="3fd2c-154">XAML-Related Attributes</span></span>  
 <span data-ttu-id="3fd2c-155">WPF XAML 隨附數個可套用至 CLR 類型的屬性，以針對其 XAML 行為表示相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-155">WPF XAML included several attributes that can be applied to CLR types to indicate something about their XAML behavior.</span></span> <span data-ttu-id="3fd2c-156">以下是在 .NET Framework 3.5 和 .NET Framework 3.0 中, 存在於 WPF 元件中的屬性清單。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-156">The following is a list of the attributes that existed in WPF assemblies in .NET Framework 3.5 and .NET Framework 3.0.</span></span> <span data-ttu-id="3fd2c-157">這些屬性會遷移至 .NET Framework 4 中的 System.object。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-157">These attributes are migrated to System.Xaml in .NET Framework 4.</span></span>  
  
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
## <a name="miscellaneous-classes"></a><span data-ttu-id="3fd2c-158">其他類別</span><span class="sxs-lookup"><span data-stu-id="3fd2c-158">Miscellaneous Classes</span></span>  
 <span data-ttu-id="3fd2c-159"><xref:System.Windows.Markup.IComponentConnector>介面存在於 .NET Framework 3.5 和 .NET Framework 3.0 中的 WindowsBase 中, 但存在於 .NET Framework 4 中的 system.object。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-159">The <xref:System.Windows.Markup.IComponentConnector> interface existed in WindowsBase in the .NET Framework 3.5 and .NET Framework 3.0, but exists in System.Xaml in .NET Framework 4.</span></span> <span data-ttu-id="3fd2c-160"><xref:System.Windows.Markup.IComponentConnector> 主要用於工具支援和 XAML 標記編譯器。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-160"><xref:System.Windows.Markup.IComponentConnector> is primarily intended for tooling support and XAML markup compilers.</span></span>  
  
 <span data-ttu-id="3fd2c-161"><xref:System.Windows.Markup.INameScope>介面存在於 .NET Framework 3.5 和 .NET Framework 3.0 中的 WindowsBase 中, 但存在於 .NET Framework 4 中的 system.object。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-161">The <xref:System.Windows.Markup.INameScope> interface existed in WindowsBase in the .NET Framework 3.5 and .NET Framework 3.0, but exists in System.Xaml in .NET Framework 4.</span></span> <span data-ttu-id="3fd2c-162"><xref:System.Windows.Markup.INameScope> 為 XAML 名稱範圍定義基本作業。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-162"><xref:System.Windows.Markup.INameScope> defines basic operations for a XAML namescope.</span></span>  
  
<a name="xamlrelated_classes_with_shared_names_that_exist_in_wpf_and_systemxaml"></a>   
## <a name="xaml-related-classes-with-shared-names-that-exist-in-wpf-and-systemxaml"></a><span data-ttu-id="3fd2c-163">WPF 和 System.Xaml 中具有共用名稱的 XAML 相關類別</span><span class="sxs-lookup"><span data-stu-id="3fd2c-163">XAML-related Classes with Shared Names that Exist in WPF and System.Xaml</span></span>  
 <span data-ttu-id="3fd2c-164">下列類別同時存在於 WPF 元件和 .NET Framework 4 中的 System.object 元件中:</span><span class="sxs-lookup"><span data-stu-id="3fd2c-164">The following classes exist in both the WPF assemblies and the System.Xaml assembly in the .NET Framework 4:</span></span>  
  
 `XamlReader`  
  
 `XamlWriter`  
  
 `XamlParseException`  
  
 <span data-ttu-id="3fd2c-165">WPF 實作位於 <xref:System.Windows.Markup> 命名空間和 PresentationFramework 組件中。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-165">The WPF implementation is found in the <xref:System.Windows.Markup> namespace, and PresentationFramework assembly.</span></span> <span data-ttu-id="3fd2c-166">System.Xaml 實作位於 <xref:System.Xaml> 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-166">The System.Xaml implementation is found in the <xref:System.Xaml> namespace.</span></span> <span data-ttu-id="3fd2c-167">如果您使用 WPF 類型或衍生自 WPF 類型，通常應使用 <xref:System.Windows.Markup.XamlReader> 和 <xref:System.Windows.Markup.XamlWriter> 的 WPF 實作，而不是 System.Xaml 實作。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-167">If you are using WPF types or are deriving from WPF types, you should typically use the WPF implementations of <xref:System.Windows.Markup.XamlReader> and <xref:System.Windows.Markup.XamlWriter> instead of the System.Xaml implementations.</span></span> <span data-ttu-id="3fd2c-168">如需詳細資訊，請參閱 <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> 和 <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>中的＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-168">For more information, see Remarks in <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> and <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="3fd2c-169">如果您同時納入 WPF 組件和 System.Xaml 的參考，並且同時對 `include` 和 <xref:System.Windows.Markup> 命名空間使用 <xref:System.Xaml> 陳述式，則您可能必須完整限定對這些 API 的呼叫，以明確解析類型。</span><span class="sxs-lookup"><span data-stu-id="3fd2c-169">If you are including references to both WPF assemblies and System.Xaml, and you also are using `include` statements for both the <xref:System.Windows.Markup> and <xref:System.Xaml> namespaces, you may need to fully qualify the calls to these APIs in order to resolve the types without ambiguity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fd2c-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3fd2c-170">See also</span></span>

- [<span data-ttu-id="3fd2c-171">XAML Services</span><span class="sxs-lookup"><span data-stu-id="3fd2c-171">XAML Services</span></span>](index.md)
