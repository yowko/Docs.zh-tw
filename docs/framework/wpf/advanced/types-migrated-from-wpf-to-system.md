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
# <a name="types-migrated-from-wpf-to-systemxaml"></a><span data-ttu-id="3a00b-102">從 WPF 遷移到 System.Xaml 的類型</span><span class="sxs-lookup"><span data-stu-id="3a00b-102">Types migrated from WPF to System.Xaml</span></span>

<span data-ttu-id="3a00b-103">在 .NET 框架 3.5 和 .NET 框架 3.0 中，Windows 演示基礎 （WPF） 和 Windows 工作流基礎都包含 XAML 語言實現。</span><span class="sxs-lookup"><span data-stu-id="3a00b-103">In .NET Framework 3.5 and .NET Framework 3.0, both Windows Presentation Foundation (WPF) and Windows Workflow Foundation included a XAML language implementation.</span></span> <span data-ttu-id="3a00b-104">有許多為 WPF XAML 實作提供擴充性的公用類型，存在於 WindowsBase、PresentationCore 和 PresentationFramework 組件中。</span><span class="sxs-lookup"><span data-stu-id="3a00b-104">Many of the public types that provided extensibility for the WPF XAML implementation existed in the WindowsBase, PresentationCore, and PresentationFramework assemblies.</span></span> <span data-ttu-id="3a00b-105">同樣，為 Windows 工作流基礎 XAML 提供擴充性的公共類型存在於 System.Workflow.元件模型程式集中。</span><span class="sxs-lookup"><span data-stu-id="3a00b-105">Likewise, public types that provided extensibility for Windows Workflow Foundation XAML existed in the System.Workflow.ComponentModel assembly.</span></span> <span data-ttu-id="3a00b-106">在 .NET 框架 4 中，一些與 XAML 相關的類型已遷移到 System.Xaml 程式集。</span><span class="sxs-lookup"><span data-stu-id="3a00b-106">In the .NET Framework 4, some of the XAML-related types were migrated to the System.Xaml assembly.</span></span> <span data-ttu-id="3a00b-107">XAML 語言服務的通用 .NET 框架實現支援許多 XAML 擴充性方案，這些方案最初由特定框架的 XAML 實現定義，但現在是整體 .NET 框架 4 XAML 語言支援的一部分。</span><span class="sxs-lookup"><span data-stu-id="3a00b-107">A common .NET Framework implementation of XAML language services enables many XAML extensibility scenarios that were originally defined by a specific framework's XAML implementation but are now part of overall .NET Framework 4 XAML language support.</span></span> <span data-ttu-id="3a00b-108">本文列出了遷移的類型，並討論了與遷移相關的問題。</span><span class="sxs-lookup"><span data-stu-id="3a00b-108">This article lists the types that were migrated and discusses issues related to the migration.</span></span>

## <a name="assemblies-and-namespaces"></a><span data-ttu-id="3a00b-109">組件和命名空間</span><span class="sxs-lookup"><span data-stu-id="3a00b-109">Assemblies and Namespaces</span></span>

<span data-ttu-id="3a00b-110">在 .NET 框架 3.5 和 .NET 框架 3.0 中，WPF 為支援 XAML 而實現的類型通常位於<xref:System.Windows.Markup>命名空間中。</span><span class="sxs-lookup"><span data-stu-id="3a00b-110">In .NET Framework 3.5 and .NET Framework 3.0, the types that WPF implemented to support XAML were generally in the <xref:System.Windows.Markup> namespace.</span></span> <span data-ttu-id="3a00b-111">這些類型大多數位於 WindowsBase 組件中。</span><span class="sxs-lookup"><span data-stu-id="3a00b-111">Most of these types were in the WindowsBase assembly.</span></span>

<span data-ttu-id="3a00b-112">在 .NET 框架 4 中<xref:System.Xaml>，有一個新的命名空間和一個新的 System.Xaml 程式集。</span><span class="sxs-lookup"><span data-stu-id="3a00b-112">In .NET Framework 4, there is a new <xref:System.Xaml> namespace and a new System.Xaml assembly.</span></span> <span data-ttu-id="3a00b-113">許多原先針對 WPF XAML 實作的類型，現已提供為任何 XAML 實作的擴充點或服務。</span><span class="sxs-lookup"><span data-stu-id="3a00b-113">Many of the types that were originally implemented for WPF XAML are now provided as extensibility points or services for any implementation of XAML.</span></span> <span data-ttu-id="3a00b-114">為了可供更多一般情節使用，這些類型已從其原始 WPF 組件類型轉送至 System.Xaml 組件。</span><span class="sxs-lookup"><span data-stu-id="3a00b-114">As part of making them available for more general scenarios, the types are type-forwarded from their original WPF assembly to the System.Xaml assembly.</span></span> <span data-ttu-id="3a00b-115">這支援 XAML 擴充性方案，而無需包括其他框架（如 WPF 和 Windows 工作流基礎）的程式集。</span><span class="sxs-lookup"><span data-stu-id="3a00b-115">This enables XAML extensibility scenarios without having to include the assemblies of other frameworks (such as WPF and Windows Workflow Foundation).</span></span>

<span data-ttu-id="3a00b-116">大部分移轉後的類型仍會位於 <xref:System.Windows.Markup> 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="3a00b-116">For migrated types, most of the types remain in the <xref:System.Windows.Markup> namespace.</span></span> <span data-ttu-id="3a00b-117">部分原因是為了避免破壞個別檔案之現有實作中的 CLR 命名空間對應。</span><span class="sxs-lookup"><span data-stu-id="3a00b-117">This was partially to avoid breaking CLR namespace mappings in existing implementations on a per-file basis.</span></span> <span data-ttu-id="3a00b-118">因此，.NET<xref:System.Windows.Markup>框架 4 中的命名空間包含一般 XAML 語言支援類型（來自 System.Xaml 程式集）和特定于 WPF XAML 實現的類型（來自 WindowsBase 和其他 WPF 程式集）的混合。</span><span class="sxs-lookup"><span data-stu-id="3a00b-118">As a result, the <xref:System.Windows.Markup> namespace in .NET Framework 4 contains a mixture of general XAML language support types (from the System.Xaml assembly) and types that are specific to the WPF XAML implementation (from WindowsBase and other WPF assemblies).</span></span> <span data-ttu-id="3a00b-119">任何已移轉至 System.Xaml、但先前存在於 WPF 組件中的類型，在 WPF 組件第 4 版中都具有類型轉送支援。</span><span class="sxs-lookup"><span data-stu-id="3a00b-119">Any type that was migrated to System.Xaml, but existed previously in a WPF assembly, has type-forwarding support in version 4 of the WPF assembly.</span></span>

### <a name="workflow-xaml-support-types"></a><span data-ttu-id="3a00b-120">Workflow XAML 支援類型</span><span class="sxs-lookup"><span data-stu-id="3a00b-120">Workflow XAML Support Types</span></span>

<span data-ttu-id="3a00b-121">Windows 工作流基礎還提供 XAML 支援類型，在許多情況下，這些類型與 WPF 等效項具有相同的短名稱。</span><span class="sxs-lookup"><span data-stu-id="3a00b-121">Windows Workflow Foundation also provided XAML support types, and in many cases these had identical short names to a WPF equivalent.</span></span> <span data-ttu-id="3a00b-122">以下是 Windows 工作流基礎 XAML 支援類型的清單：</span><span class="sxs-lookup"><span data-stu-id="3a00b-122">The following is a list of Windows Workflow Foundation XAML support types:</span></span>

- <xref:System.Workflow.ComponentModel.Serialization.ContentPropertyAttribute>

- <xref:System.Workflow.ComponentModel.Serialization.RuntimeNamePropertyAttribute>

- <xref:System.Workflow.ComponentModel.Serialization.XmlnsPrefixAttribute>

<span data-ttu-id="3a00b-123">這些支援類型仍然存在於 .NET 框架 4 的 Windows 工作流基礎程式集中，但仍可用於特定的 Windows 工作流基礎應用程式;但是，它們不應被不使用 Windows 工作流基礎的應用程式或框架引用。</span><span class="sxs-lookup"><span data-stu-id="3a00b-123">These support types still exist in the Windows Workflow Foundation assemblies for .NET Framework 4 and can still be used for specific Windows Workflow Foundation applications; however, they should not be referenced by applications or frameworks that do not use Windows Workflow Foundation.</span></span>

## <a name="markupextension"></a><span data-ttu-id="3a00b-124">MarkupExtension</span><span class="sxs-lookup"><span data-stu-id="3a00b-124">MarkupExtension</span></span>

<span data-ttu-id="3a00b-125">在 .NET 框架 3.5 和 .NET 框架<xref:System.Windows.Markup.MarkupExtension>3.0 中，WPF 的類位於 WindowsBase 程式集中。</span><span class="sxs-lookup"><span data-stu-id="3a00b-125">In the .NET Framework 3.5 and .NET Framework 3.0, the <xref:System.Windows.Markup.MarkupExtension> class for WPF was in the WindowsBase assembly.</span></span> <span data-ttu-id="3a00b-126">Windows 工作流基礎<xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>的並行類存在於 System.Workflow.元件模型程式集中。</span><span class="sxs-lookup"><span data-stu-id="3a00b-126">A parallel class for Windows Workflow Foundation, <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>, existed in the System.Workflow.ComponentModel assembly.</span></span> <span data-ttu-id="3a00b-127">在 .NET 框架 4<xref:System.Windows.Markup.MarkupExtension>中，類將遷移到 System.Xaml 程式集。</span><span class="sxs-lookup"><span data-stu-id="3a00b-127">In the .NET Framework 4, the <xref:System.Windows.Markup.MarkupExtension> class is migrated to the System.Xaml assembly.</span></span> <span data-ttu-id="3a00b-128">在 .NET 框架<xref:System.Windows.Markup.MarkupExtension>4 中，適用于使用 .NET XAML 服務的任何 XAML 擴充性方案，而不僅僅是基於特定框架的服務。</span><span class="sxs-lookup"><span data-stu-id="3a00b-128">In the .NET Framework 4, <xref:System.Windows.Markup.MarkupExtension> is intended for any XAML extensibility scenario that uses .NET XAML Services, not just for those that build on specific frameworks.</span></span> <span data-ttu-id="3a00b-129">進行 XAML 擴充時，也應盡可能將特定架構或架構中的使用者程式碼建置在 <xref:System.Windows.Markup.MarkupExtension> 類別上。</span><span class="sxs-lookup"><span data-stu-id="3a00b-129">When possible, specific frameworks or user code in the framework should also build on the <xref:System.Windows.Markup.MarkupExtension> class for XAML extension.</span></span>

## <a name="markupextension-supporting-service-classes"></a><span data-ttu-id="3a00b-130">支援服務類別的 MarkupExtension</span><span class="sxs-lookup"><span data-stu-id="3a00b-130">MarkupExtension Supporting Service Classes</span></span>

<span data-ttu-id="3a00b-131">WPF 的 .NET 框架 3.5 和 .NET 框架 3.0 提供了一些服務，這些服務可用於<xref:System.Windows.Markup.MarkupExtension>實施者和<xref:System.ComponentModel.TypeConverter>實現，以支援 XAML 中的類型/屬性使用。</span><span class="sxs-lookup"><span data-stu-id="3a00b-131">.NET Framework 3.5 and .NET Framework 3.0 for WPF provided several services that were available to <xref:System.Windows.Markup.MarkupExtension> implementers and <xref:System.ComponentModel.TypeConverter> implementations to support type/property usage in XAML.</span></span> <span data-ttu-id="3a00b-132">這些服務包括：</span><span class="sxs-lookup"><span data-stu-id="3a00b-132">These services are the following:</span></span>

- <xref:System.Windows.Markup.IProvideValueTarget>

- <xref:System.Windows.Markup.IUriContext>

- <xref:System.Windows.Markup.IXamlTypeResolver>

> [!NOTE]
> <span data-ttu-id="3a00b-133">.NET Framework 3.5 中與標記擴展相關的另一個服務是<xref:System.Windows.Markup.IReceiveMarkupExtension>介面。</span><span class="sxs-lookup"><span data-stu-id="3a00b-133">Another service from .NET Framework 3.5 that is related to markup extensions is the <xref:System.Windows.Markup.IReceiveMarkupExtension> interface.</span></span> <span data-ttu-id="3a00b-134"><xref:System.Windows.Markup.IReceiveMarkupExtension>未遷移，標記為`[Obsolete]`.NET 框架 4。</span><span class="sxs-lookup"><span data-stu-id="3a00b-134"><xref:System.Windows.Markup.IReceiveMarkupExtension> was not migrated and is marked `[Obsolete]` for .NET Framework 4.</span></span> <span data-ttu-id="3a00b-135">先前使用 <xref:System.Windows.Markup.IReceiveMarkupExtension> 的情節應改用 <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> 屬性化回呼。</span><span class="sxs-lookup"><span data-stu-id="3a00b-135">Scenarios that previously used <xref:System.Windows.Markup.IReceiveMarkupExtension> should instead use <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> attributed callbacks.</span></span> <span data-ttu-id="3a00b-136"><xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute> 也已標記為 `[Obsolete]`。</span><span class="sxs-lookup"><span data-stu-id="3a00b-136"><xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute> is also marked `[Obsolete]`.</span></span>

## <a name="xaml-language-features"></a><span data-ttu-id="3a00b-137">XAML 語言功能</span><span class="sxs-lookup"><span data-stu-id="3a00b-137">XAML Language Features</span></span>

<span data-ttu-id="3a00b-138">有數項 WPF 適用的 XAML 語言功能和元件先前存在於 PresentationFramework 組件中。</span><span class="sxs-lookup"><span data-stu-id="3a00b-138">Several XAML language features and components for WPF previously existed in the PresentationFramework assembly.</span></span> <span data-ttu-id="3a00b-139">這些項目會以 <xref:System.Windows.Markup.MarkupExtension> 子類別的形式實作，以在 XAML 標記中公開標記延伸使用。</span><span class="sxs-lookup"><span data-stu-id="3a00b-139">These were implemented as a <xref:System.Windows.Markup.MarkupExtension> subclass to expose markup extension usages in XAML markup.</span></span> <span data-ttu-id="3a00b-140">在 .NET 框架 4 中，這些功能存在於 System.Xaml 程式集中，以便不包含 WPF 程式集的專案可以使用這些 XAML 語言級功能。</span><span class="sxs-lookup"><span data-stu-id="3a00b-140">In .NET Framework 4, these exist in the System.Xaml assembly so that projects that do not include WPF assemblies can use these XAML language-level features.</span></span> <span data-ttu-id="3a00b-141">WPF 對 .NET 框架 4 應用程式使用相同的實現。</span><span class="sxs-lookup"><span data-stu-id="3a00b-141">WPF uses these same implementations for .NET Framework 4 applications.</span></span> <span data-ttu-id="3a00b-142">如本主題所列的其他情況，支援類型會繼續存在於 <xref:System.Windows.Markup> 命名空間中，以避免破壞先前的參考。</span><span class="sxs-lookup"><span data-stu-id="3a00b-142">As with the other cases that are listed in this topic, the supporting types continue to exist in the <xref:System.Windows.Markup> namespace to avoid breaking previous references.</span></span>

<span data-ttu-id="3a00b-143">下表包含 System.Xaml 中定義的 XAML 功能支援類別清單。</span><span class="sxs-lookup"><span data-stu-id="3a00b-143">The following table contains a list of the XAML feature-support classes that are defined in System.Xaml.</span></span>

|<span data-ttu-id="3a00b-144">XAML 語言功能</span><span class="sxs-lookup"><span data-stu-id="3a00b-144">XAML Language Feature</span></span>|<span data-ttu-id="3a00b-145">使用量</span><span class="sxs-lookup"><span data-stu-id="3a00b-145">Usage</span></span>|
|---------------------------|-----------|
|<xref:System.Windows.Markup.ArrayExtension>|`<x:Array ...>`|
|<xref:System.Windows.Markup.NullExtension>|`{x:Null}`|
|<xref:System.Windows.Markup.StaticExtension>|`{x:Static ...}`|
|<xref:System.Windows.Markup.TypeExtension>|`{x:Type ...}`|

<span data-ttu-id="3a00b-146">雖然 System.Xaml 可能沒有特定支援類別，但處理 XAML 語言的語言功能時所需的一般邏輯，現已常駐於 System.Xaml 以及其實作的 XAML 讀取器和 XAML 寫入器中。</span><span class="sxs-lookup"><span data-stu-id="3a00b-146">Although System.Xaml may not have specific support classes, the general logic for processing language features for the XAML language now resides in System.Xaml and its implemented XAML readers and XAML writers.</span></span> <span data-ttu-id="3a00b-147">例如， `x:TypeArguments` 是由 XAML 讀取器和 XAML 寫入器透過 System.Xaml 實作處理的屬性。該屬性可在 XAML 節點資料流中標註、在預設 (CLR 型) XAML 結構描述內容中有處理邏輯、具有 XAML 類型系統表示等。</span><span class="sxs-lookup"><span data-stu-id="3a00b-147">For example, `x:TypeArguments` is an attribute that is processed by XAML readers and XAML writers from System.Xaml implementations; it can be noted in the XAML node stream, has handling in the default (CLR-based) XAML schema context, has a XAML type-system representation, and so on.</span></span> <span data-ttu-id="3a00b-148">因此，所有 XAML 語言級別功能的參考文檔是[Windows 演示基礎 （WPF） 桌面指南](../../../desktop-wpf/overview/index.md)中[XAML 服務的](../../../desktop-wpf/xaml-services/index.md)子主題。</span><span class="sxs-lookup"><span data-stu-id="3a00b-148">As a result, the reference documentation for all XAML language-level features is a subtopic for [XAML Services](../../../desktop-wpf/xaml-services/index.md) in the [Desktop Guide for Windows Presentation Foundation (WPF)](../../../desktop-wpf/overview/index.md).</span></span>

## <a name="valueserializer-and-supporting-classes"></a><span data-ttu-id="3a00b-149">ValueSerializer 和支援類別</span><span class="sxs-lookup"><span data-stu-id="3a00b-149">ValueSerializer and Supporting Classes</span></span>

<span data-ttu-id="3a00b-150"><xref:System.Windows.Markup.ValueSerializer> 類別支援將類型轉換成字串，尤其是在 XAML 序列化需要輸出中有多個模式或節點時。</span><span class="sxs-lookup"><span data-stu-id="3a00b-150">The <xref:System.Windows.Markup.ValueSerializer> class supports type conversion to a string, particularly for XAML serialization cases where serialization may require multiple modes or nodes in the output.</span></span> <span data-ttu-id="3a00b-151">在 .NET 框架 3.5 和 .NET<xref:System.Windows.Markup.ValueSerializer>框架 3.0 中，WPF 的 是在 WindowsBase 程式集中。</span><span class="sxs-lookup"><span data-stu-id="3a00b-151">In .NET Framework 3.5 and .NET Framework 3.0, the <xref:System.Windows.Markup.ValueSerializer> for WPF was in the WindowsBase assembly.</span></span> <span data-ttu-id="3a00b-152">在 .NET 框架 4<xref:System.Windows.Markup.ValueSerializer>中，該類位於 System.Xaml 中，適用于任何 XAML 擴充性方案，而不僅僅是基於 WPF 構建的方案。</span><span class="sxs-lookup"><span data-stu-id="3a00b-152">In the .NET Framework 4, the <xref:System.Windows.Markup.ValueSerializer> class is in System.Xaml and is intended for any XAML extensibility scenario, not just for those that build on WPF.</span></span> <span data-ttu-id="3a00b-153"><xref:System.Windows.Markup.IValueSerializerContext> (支援服務) 和 <xref:System.Windows.Markup.DateTimeValueSerializer> (特定子類別) 也會移轉至 System.Xaml。</span><span class="sxs-lookup"><span data-stu-id="3a00b-153"><xref:System.Windows.Markup.IValueSerializerContext> (a supporting service) and <xref:System.Windows.Markup.DateTimeValueSerializer> (a specific subclass) are also migrated to System.Xaml.</span></span>

## <a name="xaml-related-attributes"></a><span data-ttu-id="3a00b-154">XAML 相關屬性</span><span class="sxs-lookup"><span data-stu-id="3a00b-154">XAML-Related Attributes</span></span>

<span data-ttu-id="3a00b-155">WPF XAML 隨附數個可套用至 CLR 類型的屬性，以針對其 XAML 行為表示相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3a00b-155">WPF XAML included several attributes that can be applied to CLR types to indicate something about their XAML behavior.</span></span> <span data-ttu-id="3a00b-156">以下是 .NET 框架 3.5 和 .NET 框架 3.0 中 WPF 程式集中存在的屬性的清單。</span><span class="sxs-lookup"><span data-stu-id="3a00b-156">The following is a list of the attributes that existed in WPF assemblies in .NET Framework 3.5 and .NET Framework 3.0.</span></span> <span data-ttu-id="3a00b-157">這些屬性將遷移到 .NET 框架 4 中的 System.Xaml。</span><span class="sxs-lookup"><span data-stu-id="3a00b-157">These attributes are migrated to System.Xaml in .NET Framework 4.</span></span>

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

## <a name="miscellaneous-classes"></a><span data-ttu-id="3a00b-158">其他類別</span><span class="sxs-lookup"><span data-stu-id="3a00b-158">Miscellaneous Classes</span></span>

<span data-ttu-id="3a00b-159">該<xref:System.Windows.Markup.IComponentConnector>介面存在於 .NET 框架 3.5 和 .NET 框架 3.0 中的 WindowsBase 中，但存在於 .NET 框架 4 中的 System.Xaml 中。</span><span class="sxs-lookup"><span data-stu-id="3a00b-159">The <xref:System.Windows.Markup.IComponentConnector> interface existed in WindowsBase in .NET Framework 3.5 and .NET Framework 3.0, but exists in System.Xaml in .NET Framework 4.</span></span> <span data-ttu-id="3a00b-160"><xref:System.Windows.Markup.IComponentConnector> 主要用於工具支援和 XAML 標記編譯器。</span><span class="sxs-lookup"><span data-stu-id="3a00b-160"><xref:System.Windows.Markup.IComponentConnector> is primarily intended for tooling support and XAML markup compilers.</span></span>

<span data-ttu-id="3a00b-161">該<xref:System.Windows.Markup.INameScope>介面存在於 .NET 框架 3.5 和 .NET 框架 3.0 中的 WindowsBase 中，但存在於 .NET 框架 4 中的 System.Xaml 中。</span><span class="sxs-lookup"><span data-stu-id="3a00b-161">The <xref:System.Windows.Markup.INameScope> interface existed in WindowsBase in .NET Framework 3.5 and .NET Framework 3.0, but exists in System.Xaml in .NET Framework 4.</span></span> <span data-ttu-id="3a00b-162"><xref:System.Windows.Markup.INameScope> 為 XAML 名稱範圍定義基本作業。</span><span class="sxs-lookup"><span data-stu-id="3a00b-162"><xref:System.Windows.Markup.INameScope> defines basic operations for a XAML namescope.</span></span>

## <a name="xaml-related-classes-with-shared-names-that-exist-in-wpf-and-systemxaml"></a><span data-ttu-id="3a00b-163">WPF 和 System.Xaml 中具有共用名稱的 XAML 相關類別</span><span class="sxs-lookup"><span data-stu-id="3a00b-163">XAML-related Classes with Shared Names that Exist in WPF and System.Xaml</span></span>

<span data-ttu-id="3a00b-164">以下類存在於 .NET 框架 4 中的 WPF 程式集和 System.Xaml 程式集中：</span><span class="sxs-lookup"><span data-stu-id="3a00b-164">The following classes exist in both the WPF assemblies and the System.Xaml assembly in .NET Framework 4:</span></span>

`XamlReader`

`XamlWriter`

`XamlParseException`

<span data-ttu-id="3a00b-165">WPF 實作位於 <xref:System.Windows.Markup> 命名空間和 PresentationFramework 組件中。</span><span class="sxs-lookup"><span data-stu-id="3a00b-165">The WPF implementation is found in the <xref:System.Windows.Markup> namespace, and PresentationFramework assembly.</span></span> <span data-ttu-id="3a00b-166">System.Xaml 實作位於 <xref:System.Xaml> 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="3a00b-166">The System.Xaml implementation is found in the <xref:System.Xaml> namespace.</span></span> <span data-ttu-id="3a00b-167">如果您使用 WPF 類型或衍生自 WPF 類型，通常應使用 <xref:System.Windows.Markup.XamlReader> 和 <xref:System.Windows.Markup.XamlWriter> 的 WPF 實作，而不是 System.Xaml 實作。</span><span class="sxs-lookup"><span data-stu-id="3a00b-167">If you are using WPF types or are deriving from WPF types, you should typically use the WPF implementations of <xref:System.Windows.Markup.XamlReader> and <xref:System.Windows.Markup.XamlWriter> instead of the System.Xaml implementations.</span></span> <span data-ttu-id="3a00b-168">如需詳細資訊，請參閱 <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> 和 <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>中的＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="3a00b-168">For more information, see Remarks in <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> and <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="3a00b-169">如果您同時納入 WPF 組件和 System.Xaml 的參考，並且同時對 `include` 和 <xref:System.Windows.Markup> 命名空間使用 <xref:System.Xaml> 陳述式，則您可能必須完整限定對這些 API 的呼叫，以明確解析類型。</span><span class="sxs-lookup"><span data-stu-id="3a00b-169">If you are including references to both WPF assemblies and System.Xaml, and you also are using `include` statements for both the <xref:System.Windows.Markup> and <xref:System.Xaml> namespaces, you may need to fully qualify the calls to these APIs in order to resolve the types without ambiguity.</span></span>
