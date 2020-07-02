---
title: 巡覽概觀
description: 瞭解在 Windows Presentation Foundation （WPF）中用於獨立應用程式和 XAML 瀏覽器應用程式的瀏覽器樣式導覽支援。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- loose XAML files [WPF]
- windows [WPF]
- Start page [WPF]
- HTML files [WPF]
- structured navigation [WPF]
- fragment navigation [WPF]
- URIs (Uniform Resource Identifiers)
- custom objects [WPF]
- Uniform Resource Identifiers (URIs)
- pages [WPF]
- frames [WPF]
- navigation hosts [WPF]
- journals [WPF]
- lifetimes [WPF]
- retaining content state [WPF]
- content state [WPF]
- programmatic navigation [WPF]
- hyperlinks [WPF]
ms.assetid: 86ad2143-606a-4e34-bf7e-51a2594248b8
ms.openlocfilehash: 2aac1b3a38b6240bfba1b90983fd9cbd18b31b6f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621700"
---
# <a name="navigation-overview"></a><span data-ttu-id="ae875-103">巡覽概觀</span><span class="sxs-lookup"><span data-stu-id="ae875-103">Navigation Overview</span></span>

<span data-ttu-id="ae875-104">Windows Presentation Foundation （WPF）支援瀏覽器樣式的導覽，可用於兩種類型的應用程式：獨立應用程式和 XAML 瀏覽器應用程式（Xbap）。</span><span class="sxs-lookup"><span data-stu-id="ae875-104">Windows Presentation Foundation (WPF) supports browser-style navigation that can be used in two types of applications: standalone applications and XAML browser applications (XBAPs).</span></span> <span data-ttu-id="ae875-105">為了要封裝內容以進行導覽，WPF 提供了 <xref:System.Windows.Controls.Page> 類別。</span><span class="sxs-lookup"><span data-stu-id="ae875-105">To package content for navigation, WPF provides the <xref:System.Windows.Controls.Page> class.</span></span> <span data-ttu-id="ae875-106">您可以藉由使用 <xref:System.Windows.Controls.Page> <xref:System.Windows.Documents.Hyperlink> 或以程式設計方式，使用從一個流覽至另一個 <xref:System.Windows.Navigation.NavigationService> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-106">You can navigate from one <xref:System.Windows.Controls.Page> to another declaratively, by using a <xref:System.Windows.Documents.Hyperlink>, or programmatically, by using the <xref:System.Windows.Navigation.NavigationService>.</span></span> <span data-ttu-id="ae875-107">WPF 會使用日誌來記住已從流覽的頁面，並流覽回它們。</span><span class="sxs-lookup"><span data-stu-id="ae875-107">WPF uses the journal to remember pages that have been navigated from and to navigate back to them.</span></span>

<span data-ttu-id="ae875-108"><xref:System.Windows.Controls.Page>、 <xref:System.Windows.Documents.Hyperlink> 、 <xref:System.Windows.Navigation.NavigationService> 和日誌形成 WPF 所提供的導覽支援的核心。</span><span class="sxs-lookup"><span data-stu-id="ae875-108"><xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Navigation.NavigationService>, and the journal form the core of the navigation support offered by WPF.</span></span> <span data-ttu-id="ae875-109">本總覽會在涵蓋包含鬆散檔案、HTML 檔案和物件導覽的先進導覽支援之前，先深入探索這些功能 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ae875-109">This overview explores these features in detail before covering advanced navigation support that includes navigation to loose [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] files, HTML files, and objects.</span></span>

> [!NOTE]
> <span data-ttu-id="ae875-110">在本主題中，「瀏覽器」一詞只是指可以裝載 WPF 應用程式的瀏覽器，其中目前包含 Microsoft Internet Explorer 和 Firefox。</span><span class="sxs-lookup"><span data-stu-id="ae875-110">In this topic, the term "browser" refers only to browsers that can host WPF applications, which currently includes Microsoft Internet Explorer and Firefox.</span></span> <span data-ttu-id="ae875-111">只有特定的瀏覽器支援特定的 WPF 功能時，才會參考瀏覽器版本。</span><span class="sxs-lookup"><span data-stu-id="ae875-111">Where specific WPF features are supported only by a particular browser, the browser version is referred to.</span></span>

## <a name="navigation-in-wpf-applications"></a><span data-ttu-id="ae875-112">WPF 應用程式中的巡覽</span><span class="sxs-lookup"><span data-stu-id="ae875-112">Navigation in WPF Applications</span></span>

<span data-ttu-id="ae875-113">本主題提供 WPF 中主要導覽功能的總覽。</span><span class="sxs-lookup"><span data-stu-id="ae875-113">This topic provides an overview of the key navigation capabilities in WPF.</span></span> <span data-ttu-id="ae875-114">這些功能都可供獨立應用程式和 Xbap 使用，雖然本主題會在 XBAP 的內容中呈現它們。</span><span class="sxs-lookup"><span data-stu-id="ae875-114">These capabilities are available to both standalone applications and XBAPs, although this topic presents them within the context of an XBAP.</span></span>

> [!NOTE]
> <span data-ttu-id="ae875-115">本主題不會討論如何建立和部署 Xbap。</span><span class="sxs-lookup"><span data-stu-id="ae875-115">This topic doesn't discuss how to build and deploy XBAPs.</span></span> <span data-ttu-id="ae875-116">如需 Xbap 的詳細資訊，請參閱[WPF XAML 瀏覽器應用程式總覽](wpf-xaml-browser-applications-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="ae875-116">For more information on XBAPs, see [WPF XAML Browser Applications Overview](wpf-xaml-browser-applications-overview.md).</span></span>

<span data-ttu-id="ae875-117">本節說明並示範下列巡覽的各個面向︰</span><span class="sxs-lookup"><span data-stu-id="ae875-117">This section explains and demonstrates the following aspects of navigation:</span></span>

- [<span data-ttu-id="ae875-118">實作頁面</span><span class="sxs-lookup"><span data-stu-id="ae875-118">Implementing a Page</span></span>](#CreatingAXAMLPage)

- [<span data-ttu-id="ae875-119">設定起始頁</span><span class="sxs-lookup"><span data-stu-id="ae875-119">Configuring a Start Page</span></span>](#Configuring_a_Start_Page)

- [<span data-ttu-id="ae875-120">設定主機視窗的標題、寬度和高度</span><span class="sxs-lookup"><span data-stu-id="ae875-120">Configuring the Host Window's Title, Width, and Height</span></span>](#ConfiguringAXAMLPage)

- [<span data-ttu-id="ae875-121">超連結巡覽</span><span class="sxs-lookup"><span data-stu-id="ae875-121">Hyperlink Navigation</span></span>](#NavigatingBetweenXAMLPages)

- [<span data-ttu-id="ae875-122">片段巡覽</span><span class="sxs-lookup"><span data-stu-id="ae875-122">Fragment Navigation</span></span>](#FragmentNavigation)

- [<span data-ttu-id="ae875-123">巡覽服務</span><span class="sxs-lookup"><span data-stu-id="ae875-123">Navigation Service</span></span>](#NavigationService)

- [<span data-ttu-id="ae875-124">以程式設計的巡覽及巡覽服務</span><span class="sxs-lookup"><span data-stu-id="ae875-124">Programmatic Navigation with the Navigation Service</span></span>](#Programmatic_Navigation_with_the_Navigation_Service)

- [<span data-ttu-id="ae875-125">巡覽存留期</span><span class="sxs-lookup"><span data-stu-id="ae875-125">Navigation Lifetime</span></span>](#Navigation_Lifetime)

- [<span data-ttu-id="ae875-126">以日誌記憶巡覽</span><span class="sxs-lookup"><span data-stu-id="ae875-126">Remembering Navigation with the Journal</span></span>](#NavigationHistory)

- [<span data-ttu-id="ae875-127">網頁存留期和日誌</span><span class="sxs-lookup"><span data-stu-id="ae875-127">Page Lifetime and the Journal</span></span>](#PageLifetime)

- [<span data-ttu-id="ae875-128">以巡覽記錄保留內容狀態</span><span class="sxs-lookup"><span data-stu-id="ae875-128">Retaining Content State with Navigation History</span></span>](#RetainingContentStateWithNavigationHistory)

- [<span data-ttu-id="ae875-129">Cookie</span><span class="sxs-lookup"><span data-stu-id="ae875-129">Cookies</span></span>](#Cookies)

- [<span data-ttu-id="ae875-130">結構化巡覽</span><span class="sxs-lookup"><span data-stu-id="ae875-130">Structured Navigation</span></span>](#Structured_Navigation)

<a name="CreatingAXAMLPage"></a>

### <a name="implementing-a-page"></a><span data-ttu-id="ae875-131">實作頁面</span><span class="sxs-lookup"><span data-stu-id="ae875-131">Implementing a Page</span></span>

<span data-ttu-id="ae875-132">在 WPF 中，您可以導覽至數種內容類型，其中包括 .NET Framework 物件、自訂物件、列舉值、使用者控制項、檔案 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 和 HTML 檔案。</span><span class="sxs-lookup"><span data-stu-id="ae875-132">In WPF, you can navigate to several content types that include .NET Framework objects, custom objects, enumeration values, user controls, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files, and HTML files.</span></span> <span data-ttu-id="ae875-133">不過，您會發現封裝內容最常見且方便的方式是使用 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-133">However, you'll find that the most common and convenient way to package content is by using <xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="ae875-134">此外， <xref:System.Windows.Controls.Page> 也會執行導覽特有的功能，以增強其外觀並簡化開發。</span><span class="sxs-lookup"><span data-stu-id="ae875-134">Furthermore, <xref:System.Windows.Controls.Page> implements navigation-specific features to enhance their appearance and simplify development.</span></span>

<span data-ttu-id="ae875-135">使用 <xref:System.Windows.Controls.Page> ，您可以 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 使用如下所示的標記，以宣告方式執行可導覽的內容頁面。</span><span class="sxs-lookup"><span data-stu-id="ae875-135">Using <xref:System.Windows.Controls.Page>, you can declaratively implement a navigable page of [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content by using markup like the following.</span></span>

[!code-xaml[NavigationOverviewSnippets#Page1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page1.xaml#page1xaml)]

<span data-ttu-id="ae875-136"><xref:System.Windows.Controls.Page>在標記中實 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] `Page` 作為其根項目，而且需要 WPF XML 命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="ae875-136">A <xref:System.Windows.Controls.Page> that is implemented in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup has `Page` as its root element and requires the WPF XML namespace declaration.</span></span> <span data-ttu-id="ae875-137">專案 `Page` 包含您要流覽並顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="ae875-137">The `Page` element contains the content that you want to navigate to and display.</span></span> <span data-ttu-id="ae875-138">您可以藉由設定屬性元素來新增內容 `Page.Content` ，如下列標記所示。</span><span class="sxs-lookup"><span data-stu-id="ae875-138">You add content by setting the `Page.Content` property element, as shown in the following markup.</span></span>

[!code-xaml[NavigationOverviewSnippets#Page2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page2.xaml#page2xaml)]

<span data-ttu-id="ae875-139">`Page.Content` 只能包含一個子項目。在上例中，內容是單一字串 "Hello, Page!"</span><span class="sxs-lookup"><span data-stu-id="ae875-139">`Page.Content` can only contain one child element; in the preceding example, the content is a single string, "Hello, Page!"</span></span> <span data-ttu-id="ae875-140">在實務上，您通常會使用版面配置控制項做為子專案（請參閱[版面](../advanced/layout.md)配置）以包含及撰寫內容。</span><span class="sxs-lookup"><span data-stu-id="ae875-140">In practice, you will usually use a layout control as the child element (see [Layout](../advanced/layout.md)) to contain and compose your content.</span></span>

<span data-ttu-id="ae875-141">專案的子專案 `Page` 會被視為和的內容 <xref:System.Windows.Controls.Page> ，因此，您不需要使用明確宣告 `Page.Content` 。</span><span class="sxs-lookup"><span data-stu-id="ae875-141">The child elements of a `Page` element are considered to be the content of a <xref:System.Windows.Controls.Page> and, consequently, you don't need to use the explicit `Page.Content` declaration.</span></span> <span data-ttu-id="ae875-142">下列標記是前例的宣告式對等項目。</span><span class="sxs-lookup"><span data-stu-id="ae875-142">The following markup is the declarative equivalent to the preceding sample.</span></span>

[!code-xaml[NavigationOverviewSnippets#Page3XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page3.xaml#page3xaml)]

<span data-ttu-id="ae875-143">在此情況下， `Page.Content` 會自動使用專案的子項目進行設定 `Page` 。</span><span class="sxs-lookup"><span data-stu-id="ae875-143">In this case, `Page.Content` is automatically set with the child elements of the `Page` element.</span></span> <span data-ttu-id="ae875-144">如需詳細資訊，請參閱 [WPF 內容模型](../controls/wpf-content-model.md)。</span><span class="sxs-lookup"><span data-stu-id="ae875-144">For more information, see [WPF Content Model](../controls/wpf-content-model.md).</span></span>

<span data-ttu-id="ae875-145">僅限標記適用 <xref:System.Windows.Controls.Page> 于顯示內容。</span><span class="sxs-lookup"><span data-stu-id="ae875-145">A markup-only <xref:System.Windows.Controls.Page> is useful for displaying content.</span></span> <span data-ttu-id="ae875-146">不過， <xref:System.Windows.Controls.Page> 也可以顯示可讓使用者與頁面互動的控制項，而且它可以藉由處理事件和呼叫應用程式邏輯來回應使用者互動。</span><span class="sxs-lookup"><span data-stu-id="ae875-146">However, a <xref:System.Windows.Controls.Page> can also display controls that allow users to interact with the page, and it can respond to user interaction by handling events and calling application logic.</span></span> <span data-ttu-id="ae875-147">互動式 <xref:System.Windows.Controls.Page> 會使用標記和程式碼後置的組合來執行，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ae875-147">An interactive <xref:System.Windows.Controls.Page> is implemented by using a combination of markup and code-behind, as shown in the following example.</span></span>

[!code-xaml[XBAPAppDefSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml#homepagemarkup)]

[!code-csharp[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml.cs#homepagecodebehind)]
[!code-vb[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/HomePage.xaml.vb#homepagecodebehind)]

<span data-ttu-id="ae875-148">若要讓標記檔案和程式碼後置檔案一起工作，需要設定下列項目：</span><span class="sxs-lookup"><span data-stu-id="ae875-148">To allow a markup file and code-behind file to work together, the following configuration is required:</span></span>

- <span data-ttu-id="ae875-149">在標記中， `Page` 元素必須包含 `x:Class` 屬性。</span><span class="sxs-lookup"><span data-stu-id="ae875-149">In markup, the `Page` element must include the `x:Class` attribute.</span></span> <span data-ttu-id="ae875-150">建立應用程式時，標記檔案中的存在 `x:Class` 會導致 Microsoft build engine （MSBuild）建立 `partial` 衍生自的類別， <xref:System.Windows.Controls.Page> 並具有屬性所指定的名稱 `x:Class` 。</span><span class="sxs-lookup"><span data-stu-id="ae875-150">When the application is built, the existence of `x:Class` in the markup file causes Microsoft build engine (MSBuild) to create a `partial` class that derives from <xref:System.Windows.Controls.Page> and has the name that is specified by the `x:Class` attribute.</span></span> <span data-ttu-id="ae875-151">這需要新增架構的 XML 命名空間宣告 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] （ `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ）。</span><span class="sxs-lookup"><span data-stu-id="ae875-151">This requires the addition of an XML namespace declaration for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schema ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ).</span></span> <span data-ttu-id="ae875-152">產生的 `partial` 類別 `InitializeComponent` 會執行，它會呼叫來註冊事件，並設定在標記中實作為的屬性。</span><span class="sxs-lookup"><span data-stu-id="ae875-152">The generated `partial` class implements `InitializeComponent`, which is called to register the events and set the properties that are implemented in markup.</span></span>

- <span data-ttu-id="ae875-153">在程式碼後置中，類別必須是 `partial` 具有與標記中的屬性所指定相同名稱的類別 `x:Class` ，而且必須衍生自 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-153">In code-behind, the class must be a `partial` class with the same name that is specified by the `x:Class` attribute in markup, and it must derive from <xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="ae875-154">這可讓程式碼後置檔案與 `partial` 建立應用程式時為標記檔案產生的類別相關聯（請參閱[建立 WPF 應用程式](building-a-wpf-application-wpf.md)）。</span><span class="sxs-lookup"><span data-stu-id="ae875-154">This allows the code-behind file to be associated with the `partial` class that is generated for the markup file when the application is built (see [Building a WPF Application](building-a-wpf-application-wpf.md)).</span></span>

- <span data-ttu-id="ae875-155">在程式碼後置中， <xref:System.Windows.Controls.Page> 類別必須執行呼叫方法的函式 `InitializeComponent` 。</span><span class="sxs-lookup"><span data-stu-id="ae875-155">In code-behind, the <xref:System.Windows.Controls.Page> class must implement a constructor that calls the `InitializeComponent` method.</span></span> <span data-ttu-id="ae875-156">`InitializeComponent`會由標記檔案產生的 `partial` 類別來執行，以註冊事件並設定在標記中定義的屬性。</span><span class="sxs-lookup"><span data-stu-id="ae875-156">`InitializeComponent` is implemented by the markup file's generated `partial` class to register events and set properties that are defined in markup.</span></span>

> [!NOTE]
> <span data-ttu-id="ae875-157">當您使用 Visual Studio 將新的新增 <xref:System.Windows.Controls.Page> 至專案時， <xref:System.Windows.Controls.Page> 會使用標記和程式碼後置來實作為，並包含必要的設定來建立標記和程式碼後置檔案之間的關聯，如這裡所述。</span><span class="sxs-lookup"><span data-stu-id="ae875-157">When you add a new <xref:System.Windows.Controls.Page> to your project using Visual Studio, the <xref:System.Windows.Controls.Page> is implemented using both markup and code-behind, and it includes the necessary configuration to create the association between the markup and code-behind files as described here.</span></span>

<span data-ttu-id="ae875-158">一旦有 <xref:System.Windows.Controls.Page> ，您就可以流覽至該檔案。</span><span class="sxs-lookup"><span data-stu-id="ae875-158">Once you have a <xref:System.Windows.Controls.Page>, you can navigate to it.</span></span> <span data-ttu-id="ae875-159">若要指定 <xref:System.Windows.Controls.Page> 應用程式流覽的第一個，您必須設定 [啟動] <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-159">To specify the first <xref:System.Windows.Controls.Page> that an application navigates to, you need to configure the start <xref:System.Windows.Controls.Page>.</span></span>

<a name="Configuring_a_Start_Page"></a>

### <a name="configuring-a-start-page"></a><span data-ttu-id="ae875-160">設定起始頁</span><span class="sxs-lookup"><span data-stu-id="ae875-160">Configuring a Start Page</span></span>

<span data-ttu-id="ae875-161">Xbap 需要在瀏覽器中裝載一定數量的應用程式基礎結構。</span><span class="sxs-lookup"><span data-stu-id="ae875-161">XBAPs require a certain amount of application infrastructure to be hosted in a browser.</span></span> <span data-ttu-id="ae875-162">在 WPF 中， <xref:System.Windows.Application> 類別是應用程式定義的一部分，可建立必要的應用程式基礎結構（請參閱[應用程式管理總覽](application-management-overview.md)）。</span><span class="sxs-lookup"><span data-stu-id="ae875-162">In WPF, the <xref:System.Windows.Application> class is part of an application definition that establishes the required application infrastructure (see [Application Management Overview](application-management-overview.md)).</span></span>

<span data-ttu-id="ae875-163">應用程式定義通常會使用標記和程式碼後置來實作為，並將標記檔案設定為 MSBuild `ApplicationDefinition` 專案。</span><span class="sxs-lookup"><span data-stu-id="ae875-163">An application definition is usually implemented using both markup and code-behind, with the markup file configured as an MSBuild`ApplicationDefinition` item.</span></span> <span data-ttu-id="ae875-164">以下是 XBAP 的應用程式定義。</span><span class="sxs-lookup"><span data-stu-id="ae875-164">The following is an application definition for an XBAP.</span></span>

[!code-xaml[XBAPAppDefSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

[!code-csharp[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml.cs#xbapapplicationdefinitioncodebehind)]
[!code-vb[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/Application.xaml.vb#xbapapplicationdefinitioncodebehind)]

<span data-ttu-id="ae875-165">XBAP 可以使用其應用程式定義來指定 start <xref:System.Windows.Controls.Page> ，這是啟動 <xref:System.Windows.Controls.Page> XBAP 時自動載入的。</span><span class="sxs-lookup"><span data-stu-id="ae875-165">An XBAP can use its application definition to specify a start <xref:System.Windows.Controls.Page>, which is the <xref:System.Windows.Controls.Page> that is automatically loaded when the XBAP is launched.</span></span> <span data-ttu-id="ae875-166">若要這麼做，您可以 <xref:System.Windows.Application.StartupUri%2A> 為所需的統一資源識別項（URI）設定屬性 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-166">You do this by setting the <xref:System.Windows.Application.StartupUri%2A> property with the uniform resource identifier (URI) for the desired <xref:System.Windows.Controls.Page>.</span></span>

> [!NOTE]
> <span data-ttu-id="ae875-167">在大部分情況下， <xref:System.Windows.Controls.Page> 會編譯成或與應用程式一起部署。</span><span class="sxs-lookup"><span data-stu-id="ae875-167">In most cases, the <xref:System.Windows.Controls.Page> is either compiled into or deployed with an application.</span></span> <span data-ttu-id="ae875-168">在這些情況下，識別的 URI <xref:System.Windows.Controls.Page> 是一個 PACK uri，這是符合*套件*配置的 uri。</span><span class="sxs-lookup"><span data-stu-id="ae875-168">In these cases, the URI that identifies a <xref:System.Windows.Controls.Page> is a pack URI, which is a URI that conforms to the *pack* scheme.</span></span> <span data-ttu-id="ae875-169">套件 Uri 會[在 WPF 的 Pack uri](pack-uris-in-wpf.md)中進一步討論。</span><span class="sxs-lookup"><span data-stu-id="ae875-169">Pack URIs are discussed further in     [Pack URIs in WPF](pack-uris-in-wpf.md).</span></span> <span data-ttu-id="ae875-170">您也可以巡覽至使用 http 配置的內容，後文會討論。</span><span class="sxs-lookup"><span data-stu-id="ae875-170">You can also navigate to content using the http scheme, which is discussed below.</span></span>

<span data-ttu-id="ae875-171">您可以 <xref:System.Windows.Application.StartupUri%2A> 在標記中以宣告方式設定，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ae875-171">You can set <xref:System.Windows.Application.StartupUri%2A> declaratively in markup, as shown in the following example.</span></span>

[!code-xaml[NavigationOverviewSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

<span data-ttu-id="ae875-172">在此範例中， `StartupUri` 屬性是以識別首頁的相對 PACK URI 來設定。</span><span class="sxs-lookup"><span data-stu-id="ae875-172">In this example, the `StartupUri` attribute is set with a relative pack URI that identifies HomePage.xaml.</span></span> <span data-ttu-id="ae875-173">當 XBAP 啟動時，首頁. xaml 會自動流覽並顯示。</span><span class="sxs-lookup"><span data-stu-id="ae875-173">When the XBAP is launched, HomePage.xaml is automatically navigated to and displayed.</span></span> <span data-ttu-id="ae875-174">如下圖所示，它會顯示從 Web 服務器啟動的 XBAP。</span><span class="sxs-lookup"><span data-stu-id="ae875-174">This is demonstrated by the following figure, which shows an XBAP that was launched from a Web server.</span></span>

<span data-ttu-id="ae875-175">![XBAP 網頁](./media/navigation-overview/xbap-launched-from-a-web-server.png "這會顯示從 Web 服務器啟動的 XBAP。")</span><span class="sxs-lookup"><span data-stu-id="ae875-175">![XBAP page](./media/navigation-overview/xbap-launched-from-a-web-server.png "This shows an XBAP launched from a Web server.")</span></span>

> [!NOTE]
> <span data-ttu-id="ae875-176">如需有關開發和部署 Xbap 的詳細資訊，請參閱[WPF XAML 瀏覽器應用程式總覽](wpf-xaml-browser-applications-overview.md)和[部署 wpf 應用程式](deploying-a-wpf-application-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="ae875-176">For more information regarding the development and deployment of XBAPs, see [WPF XAML Browser Applications Overview](wpf-xaml-browser-applications-overview.md) and     [Deploying a WPF Application](deploying-a-wpf-application-wpf.md).</span></span>

<a name="ConfiguringAXAMLPage"></a>

### <a name="configuring-the-host-windows-title-width-and-height"></a><span data-ttu-id="ae875-177">設定主機視窗的標題、寬度和高度</span><span class="sxs-lookup"><span data-stu-id="ae875-177">Configuring the Host Window's Title, Width, and Height</span></span>

<span data-ttu-id="ae875-178">您在上圖中可能注意到的一件事，就是瀏覽器和索引標籤面板的標題都是 XBAP 的 URI。</span><span class="sxs-lookup"><span data-stu-id="ae875-178">One thing you may have noticed from the previous figure is that the title of both the browser and the tab panel is the URI for the XBAP.</span></span> <span data-ttu-id="ae875-179">除了長之外，標題既不吸引人，也不提供資訊。</span><span class="sxs-lookup"><span data-stu-id="ae875-179">Besides being long, the title is neither attractive nor informative.</span></span> <span data-ttu-id="ae875-180">基於這個理由， <xref:System.Windows.Controls.Page> 您可以藉由設定屬性來變更標題 <xref:System.Windows.Controls.Page.WindowTitle%2A> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-180">For this reason, <xref:System.Windows.Controls.Page> offers a way for you to change the title by setting the <xref:System.Windows.Controls.Page.WindowTitle%2A> property.</span></span> <span data-ttu-id="ae875-181">此外，您可以分別設定和，藉以設定瀏覽器視窗的寬度和高度 <xref:System.Windows.Controls.Page.WindowWidth%2A> <xref:System.Windows.Controls.Page.WindowHeight%2A> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-181">Furthermore, you can configure the width and height of the browser window by setting <xref:System.Windows.Controls.Page.WindowWidth%2A> and <xref:System.Windows.Controls.Page.WindowHeight%2A>, respectively.</span></span>

<span data-ttu-id="ae875-182"><xref:System.Windows.Controls.Page.WindowTitle%2A>、 <xref:System.Windows.Controls.Page.WindowWidth%2A> 和 <xref:System.Windows.Controls.Page.WindowHeight%2A> 可以在標記中以宣告方式設定，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ae875-182"><xref:System.Windows.Controls.Page.WindowTitle%2A>, <xref:System.Windows.Controls.Page.WindowWidth%2A>, and <xref:System.Windows.Controls.Page.WindowHeight%2A> can be set declaratively in markup, as shown in the following example.</span></span>

[!code-xaml[NavigationOverviewSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/HomePage.xaml#homepagemarkup)]

<span data-ttu-id="ae875-183">其結果如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="ae875-183">The result is shown in the following figure.</span></span>

<span data-ttu-id="ae875-184">![視窗標題、高度、寬度](./media/navigation-overview/window-title-width-height.png "這會顯示您可以設定的視窗標題、高度和寬度。")</span><span class="sxs-lookup"><span data-stu-id="ae875-184">![Window title, height, width](./media/navigation-overview/window-title-width-height.png "This shows the window title, height, and width you can configure.")</span></span>

<a name="NavigatingBetweenXAMLPages"></a>

### <a name="hyperlink-navigation"></a><span data-ttu-id="ae875-185">超連結巡覽</span><span class="sxs-lookup"><span data-stu-id="ae875-185">Hyperlink Navigation</span></span>

<span data-ttu-id="ae875-186">典型的 XBAP 包含數個頁面。</span><span class="sxs-lookup"><span data-stu-id="ae875-186">A typical XBAP comprises several pages.</span></span> <span data-ttu-id="ae875-187">從一頁流覽至另一個頁面的最簡單方式是使用 <xref:System.Windows.Documents.Hyperlink> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-187">The simplest way to navigate from one page to another is to use a <xref:System.Windows.Documents.Hyperlink>.</span></span> <span data-ttu-id="ae875-188">您可以 <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Controls.Page> 使用專案 `Hyperlink` （如下列標記所示），以宣告的方式將加入至。</span><span class="sxs-lookup"><span data-stu-id="ae875-188">You can declaratively add a <xref:System.Windows.Documents.Hyperlink> to a <xref:System.Windows.Controls.Page> by using the `Hyperlink` element, which is shown in the following markup.</span></span>

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

<span data-ttu-id="ae875-189">`Hyperlink`元素需要下列專案：</span><span class="sxs-lookup"><span data-stu-id="ae875-189">A `Hyperlink` element requires the following:</span></span>

- <span data-ttu-id="ae875-190">要導覽之的 pack URI <xref:System.Windows.Controls.Page> ，如屬性所指定 `NavigateUri` 。</span><span class="sxs-lookup"><span data-stu-id="ae875-190">The pack URI of the <xref:System.Windows.Controls.Page> to navigate to, as specified by the `NavigateUri` attribute.</span></span>

- <span data-ttu-id="ae875-191">使用者可以按一下以起始導覽的內容，例如文字和影像（針對 `Hyperlink` 元素可以包含的內容，請參閱 <xref:System.Windows.Documents.Hyperlink> ）。</span><span class="sxs-lookup"><span data-stu-id="ae875-191">Content that a user can click to initiate the navigation, such as text and images (for the content that the `Hyperlink` element can contain, see <xref:System.Windows.Documents.Hyperlink>).</span></span>

<span data-ttu-id="ae875-192">下圖顯示具有之的 XBAP <xref:System.Windows.Controls.Page> <xref:System.Windows.Documents.Hyperlink> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-192">The following figure shows an XBAP with a <xref:System.Windows.Controls.Page> that has a <xref:System.Windows.Documents.Hyperlink>.</span></span>

<span data-ttu-id="ae875-193">![具有超連結的頁面](./media/navigation-overview/xbap-with-a-page-with-a-hyperlink.png "這會顯示具有超連結之頁面的 XBAP。")</span><span class="sxs-lookup"><span data-stu-id="ae875-193">![Page with Hyperlink](./media/navigation-overview/xbap-with-a-page-with-a-hyperlink.png "This shows an XBAP with a page with a hyperlink.")</span></span>

<span data-ttu-id="ae875-194">如您所預期，按一下 <xref:System.Windows.Documents.Hyperlink> 會導致 XBAP 流覽至 <xref:System.Windows.Controls.Page> 屬性所識別的 `NavigateUri` 。</span><span class="sxs-lookup"><span data-stu-id="ae875-194">As you would expect, clicking the <xref:System.Windows.Documents.Hyperlink> causes the XBAP to navigate to the <xref:System.Windows.Controls.Page> that is identified by the `NavigateUri` attribute.</span></span> <span data-ttu-id="ae875-195">此外，XBAP 會 <xref:System.Windows.Controls.Page> 在 Internet Explorer 的 [最近使用的頁面] 清單中新增先前的專案。</span><span class="sxs-lookup"><span data-stu-id="ae875-195">Additionally, the XBAP adds an entry for the previous <xref:System.Windows.Controls.Page> to the Recent Pages list in Internet Explorer.</span></span> <span data-ttu-id="ae875-196">如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="ae875-196">This is shown in the following figure.</span></span>

<span data-ttu-id="ae875-197">![[上一頁] 和 [下一頁] 按鈕](./media/navigation-overview/back-and-forward-navigation.png "以 [上一頁] 和 [下一頁] 按鈕導覽。")</span><span class="sxs-lookup"><span data-stu-id="ae875-197">![Back and Forward buttons](./media/navigation-overview/back-and-forward-navigation.png "Navigate with the back and forward buttons.")</span></span>

<span data-ttu-id="ae875-198">除了支援從一個導覽 <xref:System.Windows.Controls.Page> 至另一個， <xref:System.Windows.Documents.Hyperlink> 也支援片段導覽。</span><span class="sxs-lookup"><span data-stu-id="ae875-198">As well as supporting navigation from one <xref:System.Windows.Controls.Page> to another, <xref:System.Windows.Documents.Hyperlink> also supports fragment navigation.</span></span>

<a name="FragmentNavigation"></a>

### <a name="fragment-navigation"></a><span data-ttu-id="ae875-199">片段巡覽</span><span class="sxs-lookup"><span data-stu-id="ae875-199">Fragment Navigation</span></span>

<span data-ttu-id="ae875-200">*片段導覽*是導覽至目前或另一個中的內容片段 <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-200">*Fragment navigation* is the navigation to a content fragment in either the current <xref:System.Windows.Controls.Page> or another <xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="ae875-201">在 WPF 中，內容片段是指已命名專案所包含的內容。</span><span class="sxs-lookup"><span data-stu-id="ae875-201">In WPF, a content fragment is the content that is contained by a named element.</span></span> <span data-ttu-id="ae875-202">已命名的元素是已設定其屬性的元素 `Name` 。</span><span class="sxs-lookup"><span data-stu-id="ae875-202">A named element is an element that has its `Name` attribute set.</span></span> <span data-ttu-id="ae875-203">下列標記顯示 `TextBlock` 包含內容片段的命名元素。</span><span class="sxs-lookup"><span data-stu-id="ae875-203">The following markup shows a named `TextBlock` element that contains a content fragment.</span></span>

[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup2)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup3)]

<span data-ttu-id="ae875-204"><xref:System.Windows.Documents.Hyperlink>若要讓流覽至內容片段， `NavigateUri` 屬性必須包含下列各項：</span><span class="sxs-lookup"><span data-stu-id="ae875-204">For a <xref:System.Windows.Documents.Hyperlink> to navigate to a content fragment, the `NavigateUri` attribute must include the following:</span></span>

- <span data-ttu-id="ae875-205"><xref:System.Windows.Controls.Page>具有要導覽之內容片段的 URI。</span><span class="sxs-lookup"><span data-stu-id="ae875-205">The URI of the <xref:System.Windows.Controls.Page> with the content fragment to navigate to.</span></span>

- <span data-ttu-id="ae875-206">"#" 字元。</span><span class="sxs-lookup"><span data-stu-id="ae875-206">A "#" character.</span></span>

- <span data-ttu-id="ae875-207">上包含內容片段之專案的名稱 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-207">The name of the element on the <xref:System.Windows.Controls.Page> that contains the content fragment.</span></span>

<span data-ttu-id="ae875-208">片段 URI 具有下列格式。</span><span class="sxs-lookup"><span data-stu-id="ae875-208">A fragment URI has the following format.</span></span>

<span data-ttu-id="ae875-209">*PageURI <項目名稱>* `#` \*\*</span><span class="sxs-lookup"><span data-stu-id="ae875-209">*PageURI* `#` *ElementName*</span></span>

<span data-ttu-id="ae875-210">以下顯示的範例 `Hyperlink` 是設定為流覽至內容片段。</span><span class="sxs-lookup"><span data-stu-id="ae875-210">The following shows an example of a `Hyperlink` that is configured to navigate to a content fragment.</span></span>

[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml1)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml2)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml3)]

> [!NOTE]
> <span data-ttu-id="ae875-211">本節說明 WPF 中的預設片段導覽執行。</span><span class="sxs-lookup"><span data-stu-id="ae875-211">This section describes the default fragment navigation implementation in WPF.</span></span> <span data-ttu-id="ae875-212">WPF 也可以讓您執行自己的片段導覽配置，而這種配置必須處理 <xref:System.Windows.Navigation.NavigationService.FragmentNavigation?displayProperty=nameWithType> 事件。</span><span class="sxs-lookup"><span data-stu-id="ae875-212">WPF also allows you to implement your own fragment navigation scheme which, in part, requires handling the <xref:System.Windows.Navigation.NavigationService.FragmentNavigation?displayProperty=nameWithType> event.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ae875-213">只有在可以透過 HTTP 流覽頁面時，您才可以流覽到鬆散分頁中的片段（僅限標記的檔案 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，以 `Page` 作為根項目）。</span><span class="sxs-lookup"><span data-stu-id="ae875-213">You can navigate to fragments in loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pages (markup-only [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files with `Page` as the root element) only if the pages can be browsed via HTTP.</span></span>
>
> <span data-ttu-id="ae875-214">不過，鬆散 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 分頁可以流覽至它自己的片段。</span><span class="sxs-lookup"><span data-stu-id="ae875-214">However, a loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page can navigate to its own fragments.</span></span>

<a name="NavigationService"></a>

### <a name="navigation-service"></a><span data-ttu-id="ae875-215">巡覽服務</span><span class="sxs-lookup"><span data-stu-id="ae875-215">Navigation Service</span></span>

<span data-ttu-id="ae875-216">雖然 <xref:System.Windows.Documents.Hyperlink> 可讓使用者起始特定的導覽，但 <xref:System.Windows.Controls.Page> 尋找和下載頁面的工作是由 <xref:System.Windows.Navigation.NavigationService> 類別執行。</span><span class="sxs-lookup"><span data-stu-id="ae875-216">While <xref:System.Windows.Documents.Hyperlink> allows a user to initiate navigation to a particular <xref:System.Windows.Controls.Page>, the work of locating and downloading the page is performed by the <xref:System.Windows.Navigation.NavigationService> class.</span></span> <span data-ttu-id="ae875-217">基本上， <xref:System.Windows.Navigation.NavigationService> 可讓您代表用戶端程式代碼（例如）來處理導覽要求 <xref:System.Windows.Documents.Hyperlink> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-217">Essentially, <xref:System.Windows.Navigation.NavigationService> provides the ability to process a navigation request on behalf of client code, such as the <xref:System.Windows.Documents.Hyperlink>.</span></span> <span data-ttu-id="ae875-218">此外， <xref:System.Windows.Navigation.NavigationService> 也會執行更高層級的追蹤和影響導覽要求支援。</span><span class="sxs-lookup"><span data-stu-id="ae875-218">Additionally, <xref:System.Windows.Navigation.NavigationService> implements higher-level support for tracking and influencing a navigation request.</span></span>

<span data-ttu-id="ae875-219">當您 <xref:System.Windows.Documents.Hyperlink> 按一下時，WPF 會呼叫 <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> 來尋找並下載 <xref:System.Windows.Controls.Page> 位於指定 pack URI 的。</span><span class="sxs-lookup"><span data-stu-id="ae875-219">When a <xref:System.Windows.Documents.Hyperlink> is clicked, WPF calls <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> to locate and download the <xref:System.Windows.Controls.Page> at the specified pack URI.</span></span> <span data-ttu-id="ae875-220">已下載的 <xref:System.Windows.Controls.Page> 會轉換成物件的樹狀結構，其根物件是已下載的實例 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-220">The downloaded <xref:System.Windows.Controls.Page> is converted to a tree of objects whose root object is an instance of the downloaded <xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="ae875-221">根物件的參考 <xref:System.Windows.Controls.Page> 會儲存在 <xref:System.Windows.Navigation.NavigationService.Content%2A?displayProperty=nameWithType> 屬性中。</span><span class="sxs-lookup"><span data-stu-id="ae875-221">A reference to the root <xref:System.Windows.Controls.Page> object is stored in the <xref:System.Windows.Navigation.NavigationService.Content%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="ae875-222">所流覽之內容的 pack URI 會儲存在 <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> 屬性中，而則會 <xref:System.Windows.Navigation.NavigationService.CurrentSource%2A?displayProperty=nameWithType> 儲存流覽至的最後一頁的 pack uri。</span><span class="sxs-lookup"><span data-stu-id="ae875-222">The pack URI for the content that was navigated to is stored in the <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> property, while the <xref:System.Windows.Navigation.NavigationService.CurrentSource%2A?displayProperty=nameWithType> stores the pack URI for the last page that was navigated to.</span></span>

> [!NOTE]
> <span data-ttu-id="ae875-223">WPF 應用程式可能會有一個以上的目前作用 <xref:System.Windows.Navigation.NavigationService> 中。</span><span class="sxs-lookup"><span data-stu-id="ae875-223">It is possible for a WPF application to have more than one currently active <xref:System.Windows.Navigation.NavigationService>.</span></span> <span data-ttu-id="ae875-224">如需詳細資訊，請參閱本主題稍後的[導覽主機](#Navigation_Hosts)。</span><span class="sxs-lookup"><span data-stu-id="ae875-224">For more information, see [Navigation Hosts](#Navigation_Hosts) later in this topic.</span></span>

<a name="Programmatic_Navigation_with_the_Navigation_Service"></a>

### <a name="programmatic-navigation-with-the-navigation-service"></a><span data-ttu-id="ae875-225">以程式設計的巡覽及巡覽服務</span><span class="sxs-lookup"><span data-stu-id="ae875-225">Programmatic Navigation with the Navigation Service</span></span>

<span data-ttu-id="ae875-226">您不需要知道是否使用來以宣告 <xref:System.Windows.Navigation.NavigationService> 方式在標記中執行導覽 <xref:System.Windows.Documents.Hyperlink> ，因為會 <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Navigation.NavigationService> 代表您使用。</span><span class="sxs-lookup"><span data-stu-id="ae875-226">You don't need to know about <xref:System.Windows.Navigation.NavigationService> if navigation is implemented declaratively in markup using <xref:System.Windows.Documents.Hyperlink>, because <xref:System.Windows.Documents.Hyperlink> uses the <xref:System.Windows.Navigation.NavigationService> on your behalf.</span></span> <span data-ttu-id="ae875-227">這表示，只要的直接或間接父系 <xref:System.Windows.Documents.Hyperlink> 是導覽主控制項（請參閱 [[導覽主機](#Navigation_Hosts)]）， <xref:System.Windows.Documents.Hyperlink> 就能夠尋找和使用導覽主機的導覽服務來處理導覽要求。</span><span class="sxs-lookup"><span data-stu-id="ae875-227">This means that, as long as either the direct or indirect parent of a <xref:System.Windows.Documents.Hyperlink> is a navigation host (see [Navigation Hosts](#Navigation_Hosts)), <xref:System.Windows.Documents.Hyperlink> will be able to find and use the navigation host's navigation service to process a navigation request.</span></span>

<span data-ttu-id="ae875-228">不過，在某些情況下，您需要 <xref:System.Windows.Navigation.NavigationService> 直接使用，包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="ae875-228">However, there are situations when you need to use <xref:System.Windows.Navigation.NavigationService> directly, including the following:</span></span>

- <span data-ttu-id="ae875-229">當您需要 <xref:System.Windows.Controls.Page> 使用非無參數的函式來具現化時。</span><span class="sxs-lookup"><span data-stu-id="ae875-229">When you need to instantiate a <xref:System.Windows.Controls.Page> using a non-parameterless constructor.</span></span>

- <span data-ttu-id="ae875-230">當您需要在流覽至之前設定上的屬性時 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-230">When you need to set properties on the <xref:System.Windows.Controls.Page> before you navigate to it.</span></span>

- <span data-ttu-id="ae875-231">當 <xref:System.Windows.Controls.Page> 需要流覽至的時，只能在執行時間決定。</span><span class="sxs-lookup"><span data-stu-id="ae875-231">When the <xref:System.Windows.Controls.Page> that needs to be navigated to can only be determined at run time.</span></span>

<span data-ttu-id="ae875-232">在這些情況下，您需要撰寫程式碼，藉由呼叫物件的方法，以程式設計方式起始導覽 <xref:System.Windows.Navigation.NavigationService.Navigate%2A> <xref:System.Windows.Navigation.NavigationService> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-232">In these situations, you need to write code to programmatically initiate navigation by calling the <xref:System.Windows.Navigation.NavigationService.Navigate%2A> method of the <xref:System.Windows.Navigation.NavigationService> object.</span></span> <span data-ttu-id="ae875-233">這需要取得的參考 <xref:System.Windows.Navigation.NavigationService> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-233">That requires getting a reference to a <xref:System.Windows.Navigation.NavigationService>.</span></span>

#### <a name="getting-a-reference-to-the-navigationservice"></a><span data-ttu-id="ae875-234">取得 NavigationService 的參考</span><span class="sxs-lookup"><span data-stu-id="ae875-234">Getting a Reference to the NavigationService</span></span>

<span data-ttu-id="ae875-235">針對 [[導覽主機](#Navigation_Hosts)] 區段中所涵蓋的原因，WPF 應用程式可以有一個以上的 <xref:System.Windows.Navigation.NavigationService> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-235">For reasons that are covered in the [Navigation Hosts](#Navigation_Hosts) section, a WPF application can have more than one <xref:System.Windows.Navigation.NavigationService>.</span></span> <span data-ttu-id="ae875-236">這表示您的程式碼需要一種方式來尋找 <xref:System.Windows.Navigation.NavigationService> ，這通常是 <xref:System.Windows.Navigation.NavigationService> 流覽至目前的 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-236">This means that your code needs a way to find a <xref:System.Windows.Navigation.NavigationService>, which is usually the <xref:System.Windows.Navigation.NavigationService> that navigated to the current <xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="ae875-237">您可以藉 <xref:System.Windows.Navigation.NavigationService> 由呼叫方法來取得的參考 `static` <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-237">You can get a reference to a <xref:System.Windows.Navigation.NavigationService> by calling the `static`<xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ae875-238">若要取得導覽 <xref:System.Windows.Navigation.NavigationService> 至特定的 <xref:System.Windows.Controls.Page> ，請將的參考傳遞至 <xref:System.Windows.Controls.Page> 做為方法的引數 <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-238">To get the <xref:System.Windows.Navigation.NavigationService> that navigated to a particular <xref:System.Windows.Controls.Page>, you pass a reference to the <xref:System.Windows.Controls.Page> as the argument of the <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A> method.</span></span> <span data-ttu-id="ae875-239">下列程式碼顯示如何取得目前的 <xref:System.Windows.Navigation.NavigationService> <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-239">The following code shows how to get the <xref:System.Windows.Navigation.NavigationService> for the current <xref:System.Windows.Controls.Page>.</span></span>

[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPage.xaml.vb#getnscodebehind2)]

<span data-ttu-id="ae875-240">若要尋找的快捷方式 <xref:System.Windows.Navigation.NavigationService> <xref:System.Windows.Controls.Page> ，請執行 <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page.NavigationService%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="ae875-240">As a shortcut for finding the <xref:System.Windows.Navigation.NavigationService> for a <xref:System.Windows.Controls.Page>, <xref:System.Windows.Controls.Page> implements the <xref:System.Windows.Controls.Page.NavigationService%2A> property.</span></span> <span data-ttu-id="ae875-241">下列範例會顯示這一點。</span><span class="sxs-lookup"><span data-stu-id="ae875-241">This is shown in the following example.</span></span>

[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPageShortCut.xaml.vb#getnsshortcutcodebehind2)]

> [!NOTE]
> <span data-ttu-id="ae875-242"><xref:System.Windows.Controls.Page> <xref:System.Windows.Navigation.NavigationService> 當引發事件時，只能取得其的參考 <xref:System.Windows.Controls.Page> <xref:System.Windows.FrameworkElement.Loaded> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-242">A <xref:System.Windows.Controls.Page> can only get a reference to its <xref:System.Windows.Navigation.NavigationService> when <xref:System.Windows.Controls.Page> raises the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

#### <a name="programmatic-navigation-to-a-page-object"></a><span data-ttu-id="ae875-243">以程式設計方式巡覽至頁面物件</span><span class="sxs-lookup"><span data-stu-id="ae875-243">Programmatic Navigation to a Page Object</span></span>

<span data-ttu-id="ae875-244">下列範例示範如何使用，以程式設計 <xref:System.Windows.Navigation.NavigationService> 方式流覽至 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-244">The following example shows how to use the <xref:System.Windows.Navigation.NavigationService> to programmatically navigate to a <xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="ae875-245">必須以程式設計方式導覽，因為所流覽的只能 <xref:System.Windows.Controls.Page> 使用單一、非參數的函式來具現化。</span><span class="sxs-lookup"><span data-stu-id="ae875-245">Programmatic navigation is required because the <xref:System.Windows.Controls.Page> that is being navigated to can only be instantiated using a single, non-parameterless constructor.</span></span> <span data-ttu-id="ae875-246"><xref:System.Windows.Controls.Page>具有非無參數的函式的會顯示在下列標記和程式碼中。</span><span class="sxs-lookup"><span data-stu-id="ae875-246">The <xref:System.Windows.Controls.Page> with the non-parameterless constructor is shown in the following markup and code.</span></span>

[!code-xaml[NavigationOverviewSnippets#PageWithNonDefaultConstructorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml#pagewithnondefaultconstructorxaml)]

[!code-csharp[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml.cs#pagewithnondefaultconstructorcodebehind)]
[!code-vb[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithNonDefaultConstructor.xaml.vb#pagewithnondefaultconstructorcodebehind)]

<span data-ttu-id="ae875-247"><xref:System.Windows.Controls.Page>使用非無參數的函式來流覽至的 <xref:System.Windows.Controls.Page> 會顯示在下列標記和程式碼中。</span><span class="sxs-lookup"><span data-stu-id="ae875-247">The <xref:System.Windows.Controls.Page> that navigates to the <xref:System.Windows.Controls.Page> with the non-parameterless constructor is shown in the following markup and code.</span></span>

[!code-xaml[NavigationOverviewSnippets#NSNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml#nsnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml.cs#nsnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSNavigationPage.xaml.vb#nsnavigationpagecodebehind)]

<span data-ttu-id="ae875-248">當按一下 [on] 時 <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Controls.Page> ，就會藉由具現化來起始導覽， <xref:System.Windows.Controls.Page> 以使用非無參數的函式並呼叫方法來流覽至 <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-248">When the <xref:System.Windows.Documents.Hyperlink> on this <xref:System.Windows.Controls.Page> is clicked, navigation is initiated by instantiating the <xref:System.Windows.Controls.Page> to navigate to using the non-parameterless constructor and calling the <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ae875-249"><xref:System.Windows.Navigation.NavigationService.Navigate%2A>接受將導覽至之物件的參考 <xref:System.Windows.Navigation.NavigationService> ，而不是 PACK URI。</span><span class="sxs-lookup"><span data-stu-id="ae875-249"><xref:System.Windows.Navigation.NavigationService.Navigate%2A> accepts a reference to the object that the <xref:System.Windows.Navigation.NavigationService> will navigate to, rather than a pack URI.</span></span>

#### <a name="programmatic-navigation-with-a-pack-uri"></a><span data-ttu-id="ae875-250">以程式設計的巡覽及 Pack URI</span><span class="sxs-lookup"><span data-stu-id="ae875-250">Programmatic Navigation with a Pack URI</span></span>

<span data-ttu-id="ae875-251">如果您需要以程式設計方式來建立 pack URI （例如，您只能在執行時間判斷 pack URI），可以使用 <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="ae875-251">If you need to construct a pack URI programmatically (when you can only determine the pack URI at run time, for example), you can use the <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ae875-252">下列範例會顯示這一點。</span><span class="sxs-lookup"><span data-stu-id="ae875-252">This is shown in the following example.</span></span>

[!code-xaml[NavigationOverviewSnippets#NSUriNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml#nsurinavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml.cs#nsurinavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSUriNavigationPage.xaml.vb#nsurinavigationpagecodebehind)]

#### <a name="refreshing-the-current-page"></a><span data-ttu-id="ae875-253">重新整理目前的頁面</span><span class="sxs-lookup"><span data-stu-id="ae875-253">Refreshing the Current Page</span></span>

<span data-ttu-id="ae875-254"><xref:System.Windows.Controls.Page>如果與儲存在屬性中的 PACK uri 具有相同的 pack uri，則不會下載。 <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ae875-254">A <xref:System.Windows.Controls.Page> is not downloaded if it has the same pack URI as the pack URI that is stored in the <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="ae875-255">若要強制 WPF 再次下載目前的頁面，您可以呼叫 <xref:System.Windows.Navigation.NavigationService.Refresh%2A?displayProperty=nameWithType> 方法，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ae875-255">To force WPF to download the current page again, you can call the <xref:System.Windows.Navigation.NavigationService.Refresh%2A?displayProperty=nameWithType> method, as shown in the following example.</span></span>

[!code-xaml[NavigationOverviewSnippets#NSRefreshNavigationPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml#nsrefreshnavigationpagexaml1)]

[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind1)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind2)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind2)]

<a name="Navigation_Lifetime"></a>

### <a name="navigation-lifetime"></a><span data-ttu-id="ae875-256">巡覽存留期</span><span class="sxs-lookup"><span data-stu-id="ae875-256">Navigation Lifetime</span></span>

<span data-ttu-id="ae875-257">如您所見，有多種方式可以初始化巡覽。</span><span class="sxs-lookup"><span data-stu-id="ae875-257">There are many ways to initiate navigation, as you've seen.</span></span> <span data-ttu-id="ae875-258">當導覽已起始，而且導覽正在進行時，您可以使用下列所實的事件來追蹤和影響導覽 <xref:System.Windows.Navigation.NavigationService> ：</span><span class="sxs-lookup"><span data-stu-id="ae875-258">When navigation is initiated, and while navigation is in progress, you can track and influence the navigation using the following events that are implemented by <xref:System.Windows.Navigation.NavigationService>:</span></span>

- <span data-ttu-id="ae875-259"><xref:System.Windows.Navigation.NavigationService.Navigating>.</span><span class="sxs-lookup"><span data-stu-id="ae875-259"><xref:System.Windows.Navigation.NavigationService.Navigating>.</span></span> <span data-ttu-id="ae875-260">要求新的巡覽時發生。</span><span class="sxs-lookup"><span data-stu-id="ae875-260">Occurs when a new navigation is requested.</span></span> <span data-ttu-id="ae875-261">可用於取消巡覽。</span><span class="sxs-lookup"><span data-stu-id="ae875-261">Can be used to cancel the navigation.</span></span>

- <span data-ttu-id="ae875-262"><xref:System.Windows.Navigation.NavigationService.NavigationProgress>.</span><span class="sxs-lookup"><span data-stu-id="ae875-262"><xref:System.Windows.Navigation.NavigationService.NavigationProgress>.</span></span> <span data-ttu-id="ae875-263">在下載期間定期發生以提供導覽進度資訊。</span><span class="sxs-lookup"><span data-stu-id="ae875-263">Occurs periodically during a download to provide navigation progress information.</span></span>

- <span data-ttu-id="ae875-264"><xref:System.Windows.Navigation.NavigationService.Navigated>.</span><span class="sxs-lookup"><span data-stu-id="ae875-264"><xref:System.Windows.Navigation.NavigationService.Navigated>.</span></span> <span data-ttu-id="ae875-265">找到並下載頁面時發生。</span><span class="sxs-lookup"><span data-stu-id="ae875-265">Occurs when the page has been located and downloaded.</span></span>

- <span data-ttu-id="ae875-266"><xref:System.Windows.Navigation.NavigationService.NavigationStopped>.</span><span class="sxs-lookup"><span data-stu-id="ae875-266"><xref:System.Windows.Navigation.NavigationService.NavigationStopped>.</span></span> <span data-ttu-id="ae875-267">當導覽已停止（藉由呼叫 <xref:System.Windows.Navigation.NavigationService.StopLoading%2A> ），或目前導覽正在進行中要求新的導覽時發生。</span><span class="sxs-lookup"><span data-stu-id="ae875-267">Occurs when the navigation is stopped (by calling <xref:System.Windows.Navigation.NavigationService.StopLoading%2A>), or when a new navigation is requested while a current navigation is in progress.</span></span>

- <span data-ttu-id="ae875-268"><xref:System.Windows.Navigation.NavigationService.NavigationFailed>.</span><span class="sxs-lookup"><span data-stu-id="ae875-268"><xref:System.Windows.Navigation.NavigationService.NavigationFailed>.</span></span> <span data-ttu-id="ae875-269">在廵覽至要求的內容引發錯誤時發生。</span><span class="sxs-lookup"><span data-stu-id="ae875-269">Occurs when an error is raised while navigating to the requested content.</span></span>

- <span data-ttu-id="ae875-270"><xref:System.Windows.Navigation.NavigationService.LoadCompleted>.</span><span class="sxs-lookup"><span data-stu-id="ae875-270"><xref:System.Windows.Navigation.NavigationService.LoadCompleted>.</span></span> <span data-ttu-id="ae875-271">當載入並剖析巡覽到的內容，且開始轉譯時發生。</span><span class="sxs-lookup"><span data-stu-id="ae875-271">Occurs when content that was navigated to is loaded and parsed, and has begun rendering.</span></span>

- <span data-ttu-id="ae875-272"><xref:System.Windows.Navigation.NavigationService.FragmentNavigation>.</span><span class="sxs-lookup"><span data-stu-id="ae875-272"><xref:System.Windows.Navigation.NavigationService.FragmentNavigation>.</span></span> <span data-ttu-id="ae875-273">當內容片段巡覽開始時發生，狀況為︰</span><span class="sxs-lookup"><span data-stu-id="ae875-273">Occurs when navigation to a content fragment begins, which happens:</span></span>

  - <span data-ttu-id="ae875-274">立即發生，如果所需片段位在目前的內容中。</span><span class="sxs-lookup"><span data-stu-id="ae875-274">Immediately, if the desired fragment is in the current content.</span></span>

  - <span data-ttu-id="ae875-275">載入來源內容之後，如果所需片段位在不同的內容中。</span><span class="sxs-lookup"><span data-stu-id="ae875-275">After the source content has been loaded, if the desired fragment is in different content.</span></span>

<span data-ttu-id="ae875-276">下圖顯示巡覽事件的引發順序。</span><span class="sxs-lookup"><span data-stu-id="ae875-276">The navigation events are raised in the order that is illustrated by the following figure.</span></span>

<span data-ttu-id="ae875-277">![頁面巡覽流程圖](./media/navigation-overview/order-of-navigation-events.png "頁面導覽事件流程圖表")</span><span class="sxs-lookup"><span data-stu-id="ae875-277">![Page navigation flow chart](./media/navigation-overview/order-of-navigation-events.png "Page navigation event flow chart")</span></span>

<span data-ttu-id="ae875-278">一般而言，不會 <xref:System.Windows.Controls.Page> 關心這些事件。</span><span class="sxs-lookup"><span data-stu-id="ae875-278">In general, a <xref:System.Windows.Controls.Page> isn't concerned about these events.</span></span> <span data-ttu-id="ae875-279">應用程式很有可能會擔心它們，因此，這些事件也會由 <xref:System.Windows.Application> 類別引發：</span><span class="sxs-lookup"><span data-stu-id="ae875-279">It is more likely that an application is concerned with them and, for that reason, these events are also raised by the <xref:System.Windows.Application> class:</span></span>

- <xref:System.Windows.Application.Navigating?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationProgress?displayProperty=nameWithType>

- <xref:System.Windows.Application.Navigated?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationFailed?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationStopped?displayProperty=nameWithType>

- <xref:System.Windows.Application.LoadCompleted?displayProperty=nameWithType>

- <xref:System.Windows.Application.FragmentNavigation?displayProperty=nameWithType>

<span data-ttu-id="ae875-280">每次 <xref:System.Windows.Navigation.NavigationService> 引發事件時， <xref:System.Windows.Application> 類別都會引發對應的事件。</span><span class="sxs-lookup"><span data-stu-id="ae875-280">Every time <xref:System.Windows.Navigation.NavigationService> raises an event, the <xref:System.Windows.Application> class raises the corresponding event.</span></span> <span data-ttu-id="ae875-281"><xref:System.Windows.Controls.Frame>和會 <xref:System.Windows.Navigation.NavigationWindow> 提供相同的事件，以偵測其各自範圍內的導覽。</span><span class="sxs-lookup"><span data-stu-id="ae875-281"><xref:System.Windows.Controls.Frame> and <xref:System.Windows.Navigation.NavigationWindow> offer the same events to detect navigation within their respective scopes.</span></span>

<span data-ttu-id="ae875-282">在某些情況下， <xref:System.Windows.Controls.Page> 可能會對這些事件感興趣。</span><span class="sxs-lookup"><span data-stu-id="ae875-282">In some cases, a <xref:System.Windows.Controls.Page> might be interested in these events.</span></span> <span data-ttu-id="ae875-283">例如， <xref:System.Windows.Controls.Page> 可能會處理事件， <xref:System.Windows.Navigation.NavigationService.Navigating?displayProperty=nameWithType> 以判斷是否要取消本身的導覽。</span><span class="sxs-lookup"><span data-stu-id="ae875-283">For example, a <xref:System.Windows.Controls.Page> might handle the <xref:System.Windows.Navigation.NavigationService.Navigating?displayProperty=nameWithType> event to determine whether or not to cancel navigation away from itself.</span></span> <span data-ttu-id="ae875-284">下列範例會顯示這一點。</span><span class="sxs-lookup"><span data-stu-id="ae875-284">This is shown in the following example.</span></span>

[!code-xaml[NavigationOverviewSnippets#CancelNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml#cancelnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml.cs#cancelnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/CancelNavigationPage.xaml.vb#cancelnavigationpagecodebehind)]

<span data-ttu-id="ae875-285">如果您從註冊具有導覽事件的處理常式 <xref:System.Windows.Controls.Page> ，如上述範例所示，您也必須取消註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="ae875-285">If you register a handler with a navigation event from a <xref:System.Windows.Controls.Page>, as the preceding example does, you must also unregister the event handler.</span></span> <span data-ttu-id="ae875-286">如果您沒有這麼做，可能會有關于 WPF 導覽如何使用日誌來記住導覽的副作用 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-286">If you don't, there may be side effects with respect to how WPF navigation remembers <xref:System.Windows.Controls.Page> navigation using the journal.</span></span>

<a name="NavigationHistory"></a>

### <a name="remembering-navigation-with-the-journal"></a><span data-ttu-id="ae875-287">以日誌記憶巡覽</span><span class="sxs-lookup"><span data-stu-id="ae875-287">Remembering Navigation with the Journal</span></span>

<span data-ttu-id="ae875-288">WPF 會使用兩個堆疊來記住您所流覽的頁面：後端堆疊和向前堆疊。</span><span class="sxs-lookup"><span data-stu-id="ae875-288">WPF uses two stacks to remember the pages that you have navigated from: a back stack and a forward stack.</span></span> <span data-ttu-id="ae875-289">當您從目前的流覽 <xref:System.Windows.Controls.Page> 至新的 <xref:System.Windows.Controls.Page> 或轉送到現有的時 <xref:System.Windows.Controls.Page> ，會將目前的 <xref:System.Windows.Controls.Page> 加入至*後端堆疊*。</span><span class="sxs-lookup"><span data-stu-id="ae875-289">When you navigate from the current <xref:System.Windows.Controls.Page> to a new <xref:System.Windows.Controls.Page> or forward to an existing <xref:System.Windows.Controls.Page>, the current <xref:System.Windows.Controls.Page> is added to the *back stack*.</span></span> <span data-ttu-id="ae875-290">當您從目前的 <xref:System.Windows.Controls.Page> 回到上一個時 <xref:System.Windows.Controls.Page> ，會將目前的 <xref:System.Windows.Controls.Page> 加入至*正向堆疊*中。</span><span class="sxs-lookup"><span data-stu-id="ae875-290">When you navigate from the current <xref:System.Windows.Controls.Page> back to the previous <xref:System.Windows.Controls.Page>, the current <xref:System.Windows.Controls.Page> is added to the *forward stack*.</span></span> <span data-ttu-id="ae875-291">上一頁堆疊、下一頁堆疊和管理它們的功能，統稱為日誌。</span><span class="sxs-lookup"><span data-stu-id="ae875-291">The back stack, the forward stack, and the functionality to manage them, are collectively referred to as the journal.</span></span> <span data-ttu-id="ae875-292">後端堆疊和轉寄堆疊中的每個專案都是類別的實例 <xref:System.Windows.Navigation.JournalEntry> ，而則稱為*日誌項目*。</span><span class="sxs-lookup"><span data-stu-id="ae875-292">Each item in the back stack and the forward stack is an instance of the <xref:System.Windows.Navigation.JournalEntry> class, and is referred to as a *journal entry*.</span></span>

#### <a name="navigating-the-journal-from-internet-explorer"></a><span data-ttu-id="ae875-293">從 Internet Explorer 巡覽日誌</span><span class="sxs-lookup"><span data-stu-id="ae875-293">Navigating the Journal from Internet Explorer</span></span>

<span data-ttu-id="ae875-294">就概念而言，日誌的運作方式與 Internet Explorer 中的 [**上一頁**] 和 [**下一頁**] 按鈕相同。</span><span class="sxs-lookup"><span data-stu-id="ae875-294">Conceptually, the journal operates the same way that the **Back** and **Forward** buttons in Internet Explorer do.</span></span> <span data-ttu-id="ae875-295">如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="ae875-295">These are shown in the following figure.</span></span>

<span data-ttu-id="ae875-296">![[上一頁] 和 [下一頁] 按鈕](./media/navigation-overview/back-and-forward-navigation.png "以 [上一頁] 和 [下一頁] 按鈕導覽。")</span><span class="sxs-lookup"><span data-stu-id="ae875-296">![Back and Forward buttons](./media/navigation-overview/back-and-forward-navigation.png "Navigate with the back and forward buttons.")</span></span>

<span data-ttu-id="ae875-297">若為 Internet Explorer 所裝載的 Xbap，WPF 會將日誌整合到 Internet Explorer 的導覽中 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ae875-297">For XBAPs that are hosted by Internet Explorer, WPF integrates the journal into the navigation [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] of Internet Explorer.</span></span> <span data-ttu-id="ae875-298">這可讓使用者使用 Internet Explorer 中的 [**上一頁**]、[**下一頁**] 和 [**最近使用的頁面**] 按鈕，流覽 XBAP 中的頁面。</span><span class="sxs-lookup"><span data-stu-id="ae875-298">This allows users to navigate pages in an XBAP by using the **Back**, **Forward**, and **Recent Pages** buttons in Internet Explorer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ae875-299">在 Internet Explorer 中，當使用者離開並回到 XBAP 時，只有未保持運作之頁面的記錄項目會保留在日誌中。</span><span class="sxs-lookup"><span data-stu-id="ae875-299">In Internet Explorer, when a user navigates away from and back to an XBAP, only the journal entries for pages that were not kept alive are retained in the journal.</span></span> <span data-ttu-id="ae875-300">如需讓頁面保持運作的討論，請參閱本主題稍後的[頁面存留期和日誌](#PageLifetime)。</span><span class="sxs-lookup"><span data-stu-id="ae875-300">For discussion on keeping pages alive, see [Page Lifetime and the Journal](#PageLifetime) later in this topic.</span></span>

<span data-ttu-id="ae875-301">根據預設， <xref:System.Windows.Controls.Page> Internet Explorer [**最近使用的頁面**] 清單中出現的每個文字，都是的 URI <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-301">By default, the text for each <xref:System.Windows.Controls.Page> that appears in the **Recent Pages** list of Internet Explorer is the URI for the <xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="ae875-302">在許多情況下，這對使用者都不是特別有意義。</span><span class="sxs-lookup"><span data-stu-id="ae875-302">In many cases, this is not particularly meaningful to the user.</span></span> <span data-ttu-id="ae875-303">幸運的是，您可以變更使用下列選項之一的文字︰</span><span class="sxs-lookup"><span data-stu-id="ae875-303">Fortunately, you can change the text using one the following options:</span></span>

1. <span data-ttu-id="ae875-304">附加的 `JournalEntry.Name` 屬性值。</span><span class="sxs-lookup"><span data-stu-id="ae875-304">The attached `JournalEntry.Name` attribute value.</span></span>

2. <span data-ttu-id="ae875-305">`Page.Title`屬性值。</span><span class="sxs-lookup"><span data-stu-id="ae875-305">The `Page.Title` attribute value.</span></span>

3. <span data-ttu-id="ae875-306">`Page.WindowTitle`屬性值和目前的 URI <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-306">The `Page.WindowTitle` attribute value and the URI for the current <xref:System.Windows.Controls.Page>.</span></span>

4. <span data-ttu-id="ae875-307">目前的 URI <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-307">The URI for the current <xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="ae875-308">(預設值)</span><span class="sxs-lookup"><span data-stu-id="ae875-308">(Default)</span></span>

<span data-ttu-id="ae875-309">選項列示順序符合尋找文字的優先順序。</span><span class="sxs-lookup"><span data-stu-id="ae875-309">The order in which the options are listed matches the order of precedence for finding the text.</span></span> <span data-ttu-id="ae875-310">例如，如果 `JournalEntry.Name` 設定，則會忽略其他值。</span><span class="sxs-lookup"><span data-stu-id="ae875-310">For example, if `JournalEntry.Name` is set, the other values are ignored.</span></span>

<span data-ttu-id="ae875-311">下列範例 `Page.Title` 會使用屬性來變更日誌項目所顯示的文字。</span><span class="sxs-lookup"><span data-stu-id="ae875-311">The following example uses the `Page.Title` attribute to change the text that appears for a journal entry.</span></span>

[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup2)]

[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind1)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind2)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind2)]

#### <a name="navigating-the-journal-using-wpf"></a><span data-ttu-id="ae875-312">巡覽使用 WPF 的日誌</span><span class="sxs-lookup"><span data-stu-id="ae875-312">Navigating the Journal Using WPF</span></span>

<span data-ttu-id="ae875-313">雖然使用者可以使用 Internet Explorer 中的 [**上一頁**]、[**下一頁**] 和 [**最近] 頁面**來流覽日誌，但是您也可以使用 WPF 所提供的宣告式和程式設計機制來流覽日誌。</span><span class="sxs-lookup"><span data-stu-id="ae875-313">Although a user can navigate the journal by using the **Back**, **Forward**, and **Recent Pages** in Internet Explorer, you can also navigate the journal using both declarative and programmatic mechanisms provided by WPF.</span></span> <span data-ttu-id="ae875-314">這麼做的其中一個原因是在您的頁面中提供自訂的導覽 Ui。</span><span class="sxs-lookup"><span data-stu-id="ae875-314">One reason to do this is to provide custom navigation UIs in your pages.</span></span>

<span data-ttu-id="ae875-315">您可以使用所公開的導覽命令，以宣告方式加入日誌流覽支援 <xref:System.Windows.Input.NavigationCommands> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-315">You can declaratively add journal navigation support by using the navigation commands exposed by <xref:System.Windows.Input.NavigationCommands>.</span></span> <span data-ttu-id="ae875-316">下列範例示範如何使用 `BrowseBack` 導覽命令。</span><span class="sxs-lookup"><span data-stu-id="ae875-316">The following example demonstrates how to use the `BrowseBack` navigation command.</span></span>

[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml1)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml2)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml3)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML4](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml4)]

<span data-ttu-id="ae875-317">您可以使用類別的下列其中一個成員，以程式設計方式流覽日誌 <xref:System.Windows.Navigation.NavigationService> ：</span><span class="sxs-lookup"><span data-stu-id="ae875-317">You can programmatically navigate the journal by using one of the following members of the <xref:System.Windows.Navigation.NavigationService> class:</span></span>

- <xref:System.Windows.Navigation.NavigationService.GoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.GoForward%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoForward%2A>

<span data-ttu-id="ae875-318">您也可以透過程式設計方式動作記錄，如本主題稍後的[保留內容狀態與導覽歷程記錄](#RetainingContentStateWithNavigationHistory)中所述。</span><span class="sxs-lookup"><span data-stu-id="ae875-318">The journal can also be manipulated programmatically, as discussed in [Retaining Content State with Navigation History](#RetainingContentStateWithNavigationHistory) later in this topic.</span></span>

<a name="PageLifetime"></a>

### <a name="page-lifetime-and-the-journal"></a><span data-ttu-id="ae875-319">網頁存留期和日誌</span><span class="sxs-lookup"><span data-stu-id="ae875-319">Page Lifetime and the Journal</span></span>

<span data-ttu-id="ae875-320">假設有多個頁面包含豐富內容的 XBAP，包括圖形、動畫和媒體。</span><span class="sxs-lookup"><span data-stu-id="ae875-320">Consider an XBAP with several pages that contain rich content, including graphics, animations, and media.</span></span> <span data-ttu-id="ae875-321">這類頁面的磁碟使用量可能相當大，尤其是使用視訊和音訊媒體的時候。</span><span class="sxs-lookup"><span data-stu-id="ae875-321">The memory footprint for pages like these could be quite large, particularly if video and audio media are used.</span></span> <span data-ttu-id="ae875-322">假設筆記本「記憶」已流覽過的頁面，這樣的 XBAP 可能很快就會耗用大量且明顯的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="ae875-322">Given that the journal "remembers" pages that have been navigated to, such an XBAP could quickly consume a large and noticeable amount of memory.</span></span>

<span data-ttu-id="ae875-323">基於這個理由，日誌的預設行為是將 <xref:System.Windows.Controls.Page> 中繼資料儲存在每個日誌項目中，而不是對 <xref:System.Windows.Controls.Page> 物件的參考。</span><span class="sxs-lookup"><span data-stu-id="ae875-323">For this reason, the default behavior of the journal is to store <xref:System.Windows.Controls.Page> metadata in each journal entry rather than a reference to a <xref:System.Windows.Controls.Page> object.</span></span> <span data-ttu-id="ae875-324">當流覽記錄項目時，其 <xref:System.Windows.Controls.Page> 中繼資料會用來建立指定的的新實例 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-324">When a journal entry is navigated to, its <xref:System.Windows.Controls.Page> metadata is used to create a new instance of the specified <xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="ae875-325">因此，流覽的每個都 <xref:System.Windows.Controls.Page> 具有下圖所說明的存留期。</span><span class="sxs-lookup"><span data-stu-id="ae875-325">As a consequence, each <xref:System.Windows.Controls.Page> that is navigated has the lifetime that is illustrated by the following figure.</span></span>

<span data-ttu-id="ae875-326">![網頁存留期](./media/navigation-overview/navigated-page-lifetime.png "這會顯示流覽頁面時的存留期。")</span><span class="sxs-lookup"><span data-stu-id="ae875-326">![Page lifetime](./media/navigation-overview/navigated-page-lifetime.png "This shows the lifetime when a page is navigated.")</span></span>

<span data-ttu-id="ae875-327">雖然使用預設日誌行為可以節省記憶體耗用量，但每頁轉譯的效能可能會降低;reinstantiating <xref:System.Windows.Controls.Page> 可能會耗費大量時間，特別是當它有許多內容時。</span><span class="sxs-lookup"><span data-stu-id="ae875-327">Although using the default journaling behavior can save on memory consumption, per-page rendering performance might be reduced; reinstantiating a <xref:System.Windows.Controls.Page> can be time-intensive, particularly if it has a lot of content.</span></span> <span data-ttu-id="ae875-328">如果您需要將實例保留 <xref:System.Windows.Controls.Page> 在日誌中，您可以使用兩種技術來進行繪製。</span><span class="sxs-lookup"><span data-stu-id="ae875-328">If you need to retain a <xref:System.Windows.Controls.Page> instance in the journal, you can draw on two techniques for doing so.</span></span> <span data-ttu-id="ae875-329">首先，您可以藉由呼叫方法，以程式設計方式流覽至 <xref:System.Windows.Controls.Page> 物件 <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-329">First, you can programmatically navigate to a <xref:System.Windows.Controls.Page> object by calling the <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="ae875-330">第二，您可以 <xref:System.Windows.Controls.Page> 將 <xref:System.Windows.Controls.Page.KeepAlive%2A> 屬性設定為 `true` （預設值為），藉以指定 WPF 在日誌中保留的實例 `false` 。</span><span class="sxs-lookup"><span data-stu-id="ae875-330">Second, you can specify that WPF retain an instance of a <xref:System.Windows.Controls.Page> in the journal by setting the <xref:System.Windows.Controls.Page.KeepAlive%2A> property to `true` (the default is `false`).</span></span> <span data-ttu-id="ae875-331">如下列範例所示，您可以 <xref:System.Windows.Controls.Page.KeepAlive%2A> 在標記中以宣告方式設定。</span><span class="sxs-lookup"><span data-stu-id="ae875-331">As shown in the following example, you can set <xref:System.Windows.Controls.Page.KeepAlive%2A> declaratively in markup.</span></span>

[!code-xaml[NavigationOverviewSnippets#KeepAlivePageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/KeepAlivePage.xaml#keepalivepagexaml)]

<span data-ttu-id="ae875-332">保持運作狀態的存留期與 <xref:System.Windows.Controls.Page> 不是一樣。</span><span class="sxs-lookup"><span data-stu-id="ae875-332">The lifetime of a <xref:System.Windows.Controls.Page> that is kept alive is subtly different from one that is not.</span></span> <span data-ttu-id="ae875-333">第一次保持運作的 <xref:System.Windows.Controls.Page> 狀態會被流覽至，它會具現化，就像 <xref:System.Windows.Controls.Page> 不會保持運作的一樣。</span><span class="sxs-lookup"><span data-stu-id="ae875-333">The first time a <xref:System.Windows.Controls.Page> that is kept alive is navigated to, it is instantiated just like a <xref:System.Windows.Controls.Page> that is not kept alive.</span></span> <span data-ttu-id="ae875-334">不過，因為的實例 <xref:System.Windows.Controls.Page> 會保留在日誌中，所以只要它保留在日誌中，就永遠不會再次具現化。</span><span class="sxs-lookup"><span data-stu-id="ae875-334">However, because an instance of the <xref:System.Windows.Controls.Page> is retained in the journal, it is never instantiated again for as long as it remains in the journal.</span></span> <span data-ttu-id="ae875-335">因此，如果 <xref:System.Windows.Controls.Page> 有必須在每次導覽時呼叫的初始化邏輯 <xref:System.Windows.Controls.Page> ，您就應該將它從函式移至事件的處理常式 <xref:System.Windows.FrameworkElement.Loaded> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-335">Consequently, if a <xref:System.Windows.Controls.Page> has initialization logic that needs to be called every time the <xref:System.Windows.Controls.Page> is navigated to, you should move it from the constructor into a handler for the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span> <span data-ttu-id="ae875-336">如下圖所示， <xref:System.Windows.FrameworkElement.Loaded> <xref:System.Windows.FrameworkElement.Unloaded> 每次流覽到和時，仍會引發和事件 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-336">As shown in the following figure, the <xref:System.Windows.FrameworkElement.Loaded> and <xref:System.Windows.FrameworkElement.Unloaded> events are still raised each time a <xref:System.Windows.Controls.Page> is navigated to and from, respectively.</span></span>

<span data-ttu-id="ae875-337">![引發 Loaded 和 Unloaded 事件時](./media/navigation-overview/loaded-and-unloaded-events.png "當頁面流覽至和時，會引發載入和卸載的事件。")</span><span class="sxs-lookup"><span data-stu-id="ae875-337">![When the Loaded and Unloaded events are raised](./media/navigation-overview/loaded-and-unloaded-events.png "Loaded and unloaded events are raised when a page is navigated to and from.")</span></span>

<span data-ttu-id="ae875-338">當未 <xref:System.Windows.Controls.Page> 保持運作時，您不應該執行下列其中一項動作：</span><span class="sxs-lookup"><span data-stu-id="ae875-338">When a <xref:System.Windows.Controls.Page> is not kept alive, you should not do either of the following:</span></span>

- <span data-ttu-id="ae875-339">儲存其參考或任何部分。</span><span class="sxs-lookup"><span data-stu-id="ae875-339">Store a reference to it, or any part of it.</span></span>

- <span data-ttu-id="ae875-340">使用它未實作的事件來登錄事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="ae875-340">Register event handlers with events that are not implemented by it.</span></span>

<span data-ttu-id="ae875-341">執行其中一項作業會建立參考，強制將 <xref:System.Windows.Controls.Page> 其保留在記憶體中，即使已從日誌中移除亦然。</span><span class="sxs-lookup"><span data-stu-id="ae875-341">Doing either of these will create references that force the <xref:System.Windows.Controls.Page> to be retained in memory, even after it has been removed from the journal.</span></span>

<span data-ttu-id="ae875-342">一般來說，您應該偏好不要保持運作的預設 <xref:System.Windows.Controls.Page> 行為 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-342">In general, you should prefer the default <xref:System.Windows.Controls.Page> behavior of not keeping a <xref:System.Windows.Controls.Page> alive.</span></span> <span data-ttu-id="ae875-343">不過，這有下一節要討論的隱含狀態。</span><span class="sxs-lookup"><span data-stu-id="ae875-343">However, this has state implications that are discussed in the next section.</span></span>

<a name="RetainingContentStateWithNavigationHistory"></a>

### <a name="retaining-content-state-with-navigation-history"></a><span data-ttu-id="ae875-344">以巡覽記錄保留內容狀態</span><span class="sxs-lookup"><span data-stu-id="ae875-344">Retaining Content State with Navigation History</span></span>

<span data-ttu-id="ae875-345">如果 <xref:System.Windows.Controls.Page> 不是保持運作狀態，而且它具有可從使用者收集資料的控制項，當使用者流覽離開並回到時，資料會發生什麼事 <xref:System.Windows.Controls.Page> ？</span><span class="sxs-lookup"><span data-stu-id="ae875-345">If a <xref:System.Windows.Controls.Page> is not kept alive, and it has controls that collect data from the user, what happens to the data if a user navigates away from and back to the <xref:System.Windows.Controls.Page>?</span></span> <span data-ttu-id="ae875-346">從使用者體驗的觀點而言，使用者應該會希望看到他們先前所輸入的資料。</span><span class="sxs-lookup"><span data-stu-id="ae875-346">From a user experience perspective, the user should expect to see the data they entered previously.</span></span> <span data-ttu-id="ae875-347">可惜的是，由於 <xref:System.Windows.Controls.Page> 會使用每個導覽來建立的新實例，因此會 reinstantiated 收集資料的控制項並遺失資料。</span><span class="sxs-lookup"><span data-stu-id="ae875-347">Unfortunately, because a new instance of the <xref:System.Windows.Controls.Page> is created with each navigation, the controls that collected the data are reinstantiated and the data is lost.</span></span>

<span data-ttu-id="ae875-348">幸運的是，日誌提供了跨導覽來記憶資料的支援 <xref:System.Windows.Controls.Page> ，包括控制資料。</span><span class="sxs-lookup"><span data-stu-id="ae875-348">Fortunately, the journal provides support for remembering data across <xref:System.Windows.Controls.Page> navigations, including control data.</span></span> <span data-ttu-id="ae875-349">具體而言，每個專案的日誌項目都會 <xref:System.Windows.Controls.Page> 作為相關聯狀態的暫存容器 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-349">Specifically, the journal entry for each <xref:System.Windows.Controls.Page> acts as a temporary container for the associated <xref:System.Windows.Controls.Page> state.</span></span> <span data-ttu-id="ae875-350">下列步驟概述當從流覽時，如何使用這項支援 <xref:System.Windows.Controls.Page> ：</span><span class="sxs-lookup"><span data-stu-id="ae875-350">The following steps outline how this support is used when a <xref:System.Windows.Controls.Page> is navigated from:</span></span>

1. <span data-ttu-id="ae875-351">目前的專案 <xref:System.Windows.Controls.Page> 會新增至日誌。</span><span class="sxs-lookup"><span data-stu-id="ae875-351">An entry for the current <xref:System.Windows.Controls.Page> is added to the journal.</span></span>

2. <span data-ttu-id="ae875-352">的狀態 <xref:System.Windows.Controls.Page> 會與該頁面的日誌項目一起儲存，這會新增至後端堆疊。</span><span class="sxs-lookup"><span data-stu-id="ae875-352">The state of the <xref:System.Windows.Controls.Page> is stored with the journal entry for that page, which is added to the back stack.</span></span>

3. <span data-ttu-id="ae875-353">新的 <xref:System.Windows.Controls.Page> 會被流覽至。</span><span class="sxs-lookup"><span data-stu-id="ae875-353">The new <xref:System.Windows.Controls.Page> is navigated to.</span></span>

<span data-ttu-id="ae875-354">當頁面 <xref:System.Windows.Controls.Page> 流覽回時，使用日誌，會進行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="ae875-354">When the page <xref:System.Windows.Controls.Page> is navigated back to, using the journal, the following steps take place:</span></span>

1. <span data-ttu-id="ae875-355"><xref:System.Windows.Controls.Page>已具現化（後端堆疊上的最上層記錄項目）。</span><span class="sxs-lookup"><span data-stu-id="ae875-355">The <xref:System.Windows.Controls.Page> (the top journal entry on the back stack) is instantiated.</span></span>

2. <span data-ttu-id="ae875-356"><xref:System.Windows.Controls.Page>會使用與的日誌項目一起儲存的狀態重新整理 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-356">The <xref:System.Windows.Controls.Page> is refreshed with the state that was stored with the journal entry for the <xref:System.Windows.Controls.Page>.</span></span>

3. <span data-ttu-id="ae875-357"><xref:System.Windows.Controls.Page>會流覽回。</span><span class="sxs-lookup"><span data-stu-id="ae875-357">The <xref:System.Windows.Controls.Page> is navigated back to.</span></span>

<span data-ttu-id="ae875-358">當下列控制項用於時，WPF 會自動使用這項支援 <xref:System.Windows.Controls.Page> ：</span><span class="sxs-lookup"><span data-stu-id="ae875-358">WPF automatically uses this support when the following controls are used on a <xref:System.Windows.Controls.Page>:</span></span>

- <xref:System.Windows.Controls.CheckBox>

- <xref:System.Windows.Controls.ComboBox>

- <xref:System.Windows.Controls.Expander>

- <xref:System.Windows.Controls.Frame>

- <xref:System.Windows.Controls.ListBox>

- <xref:System.Windows.Controls.ListBoxItem>

- <xref:System.Windows.Controls.MenuItem>

- <xref:System.Windows.Controls.ProgressBar>

- <xref:System.Windows.Controls.RadioButton>

- <xref:System.Windows.Controls.Slider>

- <xref:System.Windows.Controls.TabControl>

- <xref:System.Windows.Controls.TabItem>

- <xref:System.Windows.Controls.TextBox>

<span data-ttu-id="ae875-359">如果 <xref:System.Windows.Controls.Page> 使用這些控制項，則會在所有導覽中記住輸入的資料， <xref:System.Windows.Controls.Page> 如下圖中的我的**最愛色彩**所示 <xref:System.Windows.Controls.ListBox> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-359">If a <xref:System.Windows.Controls.Page> uses these controls, data entered into them is remembered across <xref:System.Windows.Controls.Page> navigations, as demonstrated by the **Favorite Color**<xref:System.Windows.Controls.ListBox> in the following figure.</span></span>

<span data-ttu-id="ae875-360">![具有可記憶狀態之控制項的頁面](./media/navigation-overview/data-remembered-across-page-navigations.png "在頁面導覽中，會記住輸入的資料。")</span><span class="sxs-lookup"><span data-stu-id="ae875-360">![Page with controls that remember state](./media/navigation-overview/data-remembered-across-page-navigations.png "Data entered is remembered across page navigations.")</span></span>

<span data-ttu-id="ae875-361">當 <xref:System.Windows.Controls.Page> 具有上述清單以外的控制項，或當狀態儲存在自訂物件中時，您必須撰寫程式碼，讓日誌記住跨導覽的狀態 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-361">When a <xref:System.Windows.Controls.Page> has controls other than those in the preceding list, or when state is stored in custom objects, you need to write code to cause the journal to remember state across <xref:System.Windows.Controls.Page> navigations.</span></span>

<span data-ttu-id="ae875-362">如果您需要記住跨導覽的小部分狀態 <xref:System.Windows.Controls.Page> ，您可以使用 <xref:System.Windows.DependencyProperty> 以中繼資料旗標設定的相依性屬性（請參閱） <xref:System.Windows.FrameworkPropertyMetadata.Journal%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-362">If you need to remember small pieces of state across <xref:System.Windows.Controls.Page> navigations, you can use dependency properties (see <xref:System.Windows.DependencyProperty>) that are configured with the <xref:System.Windows.FrameworkPropertyMetadata.Journal%2A?displayProperty=nameWithType> metadata flag.</span></span>

<span data-ttu-id="ae875-363">如果您 <xref:System.Windows.Controls.Page> 需要記住跨導覽的狀態包含多個資料片段，您可能會發現在單一類別中封裝您的狀態並執行介面的程式碼較少 <xref:System.Windows.Navigation.IProvideCustomContentState> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-363">If the state that your <xref:System.Windows.Controls.Page> needs to remember across navigations comprises multiple pieces of data, you may find it less code intensive to encapsulate your state in a single class and implement the <xref:System.Windows.Navigation.IProvideCustomContentState> interface.</span></span>

<span data-ttu-id="ae875-364">如果您需要流覽單一的各種狀態 <xref:System.Windows.Controls.Page> ，而不想從 <xref:System.Windows.Controls.Page> 本身導覽，則可以使用 <xref:System.Windows.Navigation.IProvideCustomContentState> 和 <xref:System.Windows.Navigation.NavigationService.AddBackEntry%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-364">If you need to navigate through various states of a single <xref:System.Windows.Controls.Page>, without navigating from the <xref:System.Windows.Controls.Page> itself, you can use <xref:System.Windows.Navigation.IProvideCustomContentState> and <xref:System.Windows.Navigation.NavigationService.AddBackEntry%2A?displayProperty=nameWithType>.</span></span>

<a name="Cookies"></a>

### <a name="cookies"></a><span data-ttu-id="ae875-365">Cookie</span><span class="sxs-lookup"><span data-stu-id="ae875-365">Cookies</span></span>

<span data-ttu-id="ae875-366">WPF 應用程式可以儲存資料的另一種方式是使用和方法來建立、更新和刪除 cookie <xref:System.Windows.Application.SetCookie%2A> <xref:System.Windows.Application.GetCookie%2A> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-366">Another way that WPF applications can store data is with cookies, which are created, updated, and deleted by using the <xref:System.Windows.Application.SetCookie%2A> and <xref:System.Windows.Application.GetCookie%2A> methods.</span></span> <span data-ttu-id="ae875-367">您可以在 WPF 中建立的 cookie 與其他類型的 Web 應用程式所使用的 cookie 相同。cookie 是應用程式在應用程式會話期間或之間儲存的任意資料片段。</span><span class="sxs-lookup"><span data-stu-id="ae875-367">The cookies that you can create in WPF are the same cookies that other types of Web applications use; cookies are arbitrary pieces of data that are stored by an application on a client machine either during or across application sessions.</span></span> <span data-ttu-id="ae875-368">Cookie 資料通常會採用下列格式的名稱/值組形式。</span><span class="sxs-lookup"><span data-stu-id="ae875-368">Cookie data typically takes the form of a name/value pair in the following format.</span></span>

<span data-ttu-id="ae875-369">*名稱* `=`*值*</span><span class="sxs-lookup"><span data-stu-id="ae875-369">*Name* `=` *Value*</span></span>

<span data-ttu-id="ae875-370">將資料傳遞至時，如果要 <xref:System.Windows.Application.SetCookie%2A> <xref:System.Uri> 設定 cookie 的位置，就會在記憶體中建立 cookie，而且僅適用于目前應用程式會話的持續時間。</span><span class="sxs-lookup"><span data-stu-id="ae875-370">When the data is passed to <xref:System.Windows.Application.SetCookie%2A>, along with the <xref:System.Uri> of the location for which the cookie should be set, a cookie is created in-memory, and it is only available for the duration of the current application session.</span></span> <span data-ttu-id="ae875-371">這種類型的 cookie 稱為*會話 cookie*。</span><span class="sxs-lookup"><span data-stu-id="ae875-371">This type of cookie is referred to as a *session cookie*.</span></span>

<span data-ttu-id="ae875-372">若要在應用程式工作階段之間儲存 Cookie，到期日必須使用下列格式新增至 Cookie。</span><span class="sxs-lookup"><span data-stu-id="ae875-372">To store a cookie across application sessions, an expiration date must be added to the cookie, using the following format.</span></span>

<span data-ttu-id="ae875-373">「名稱」*「值」* `=` \*\* `; expires=DAY, DD-MMM-YYYY HH:MM:SS GMT`</span><span class="sxs-lookup"><span data-stu-id="ae875-373">*NAME* `=` *VALUE* `; expires=DAY, DD-MMM-YYYY HH:MM:SS GMT`</span></span>

<span data-ttu-id="ae875-374">具有到期日的 cookie 會儲存在目前 Windows 安裝的 [Internet Files] 資料夾中，直到 cookie 到期為止。</span><span class="sxs-lookup"><span data-stu-id="ae875-374">A cookie with an expiration date is stored in the current Windows installation's Temporary Internet Files folder until the cookie expires.</span></span> <span data-ttu-id="ae875-375">這類 cookie 稱為*持續性 cookie* ，因為它會在應用程式會話之間持續保存。</span><span class="sxs-lookup"><span data-stu-id="ae875-375">Such a cookie is known as a *persistent cookie* because it persists across application sessions.</span></span>

<span data-ttu-id="ae875-376">您可以藉由呼叫方法來取得會話和持續性的 cookie <xref:System.Windows.Application.GetCookie%2A> ，傳遞 <xref:System.Uri> 使用方法設定 cookie 的位置 <xref:System.Windows.Application.SetCookie%2A> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-376">You retrieve both session and persistent cookies by calling the <xref:System.Windows.Application.GetCookie%2A> method, passing the <xref:System.Uri> of the location where the cookie was set with the <xref:System.Windows.Application.SetCookie%2A> method.</span></span>

<span data-ttu-id="ae875-377">以下是 WPF 支援 cookie 的一些方式：</span><span class="sxs-lookup"><span data-stu-id="ae875-377">The following are some of the ways that cookies are supported in WPF:</span></span>

- <span data-ttu-id="ae875-378">WPF 獨立應用程式和 Xbap 可以建立和管理 cookie。</span><span class="sxs-lookup"><span data-stu-id="ae875-378">WPF standalone applications and XBAPs can both create and manage cookies.</span></span>

- <span data-ttu-id="ae875-379">您可以從瀏覽器存取 XBAP 所建立的 cookie。</span><span class="sxs-lookup"><span data-stu-id="ae875-379">Cookies that are created by an XBAP can be accessed from the browser.</span></span>

- <span data-ttu-id="ae875-380">來自相同網域的 Xbap 可以建立和共用 cookie。</span><span class="sxs-lookup"><span data-stu-id="ae875-380">XBAPs from the same domain can create and share cookies.</span></span>

- <span data-ttu-id="ae875-381">來自相同網域的 Xbap 和 HTML 頁面可以建立和共用 cookie。</span><span class="sxs-lookup"><span data-stu-id="ae875-381">XBAPs and HTML pages from the same domain can create and share cookies.</span></span>

- <span data-ttu-id="ae875-382">當 Xbap 和鬆散 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 分頁提出 Web 要求時，會分派 cookie。</span><span class="sxs-lookup"><span data-stu-id="ae875-382">Cookies are dispatched when XBAPs and loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pages make Web requests.</span></span>

- <span data-ttu-id="ae875-383">在 IFRAME 中裝載的頂層 Xbap 和 Xbap 都可以存取 cookie。</span><span class="sxs-lookup"><span data-stu-id="ae875-383">Both top-level XBAPs and XBAPs hosted in IFRAMES can access cookies.</span></span>

- <span data-ttu-id="ae875-384">WPF 中的 Cookie 支援對所有支援的瀏覽器都是相同的。</span><span class="sxs-lookup"><span data-stu-id="ae875-384">Cookie support in WPF is the same for all supported browsers.</span></span>

- <span data-ttu-id="ae875-385">在 Internet Explorer 中，適用于 cookie 的 P3P 原則會由 WPF 接受，特別是關於第一方和協力廠商的 Xbap。</span><span class="sxs-lookup"><span data-stu-id="ae875-385">In Internet Explorer, P3P policy that pertains to cookies is honored by WPF, particularly with respect to first-party and third-party XBAPs.</span></span>

<a name="Structured_Navigation"></a>

### <a name="structured-navigation"></a><span data-ttu-id="ae875-386">結構化巡覽</span><span class="sxs-lookup"><span data-stu-id="ae875-386">Structured Navigation</span></span>

<span data-ttu-id="ae875-387">如果您需要將資料從一個傳送 <xref:System.Windows.Controls.Page> 到另一個，您可以將資料當做引數傳遞至的非無參數的函式 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-387">If you need to pass data from one <xref:System.Windows.Controls.Page> to another, you can pass the data as arguments to a non-parameterless constructor of the <xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="ae875-388">請注意，如果您使用這項技術，就必須維持運作的 <xref:System.Windows.Controls.Page> 狀態。如果不是，則當您下次流覽至時， <xref:System.Windows.Controls.Page> WPF 會 <xref:System.Windows.Controls.Page> 使用無參數的函式來 reinstantiates。</span><span class="sxs-lookup"><span data-stu-id="ae875-388">Note that if you use this technique, you must keep the <xref:System.Windows.Controls.Page> alive; if not, the next time you navigate to the <xref:System.Windows.Controls.Page>, WPF reinstantiates the <xref:System.Windows.Controls.Page> by using the parameterless constructor.</span></span>

<span data-ttu-id="ae875-389">或者，您 <xref:System.Windows.Controls.Page> 可以使用需要傳遞的資料來執行設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="ae875-389">Alternatively, your <xref:System.Windows.Controls.Page> can implement properties that are set with the data that needs to be passed.</span></span> <span data-ttu-id="ae875-390">不過，當 <xref:System.Windows.Controls.Page> 需要將資料傳回給導覽到它的時，會變得 <xref:System.Windows.Controls.Page> 很棘手。</span><span class="sxs-lookup"><span data-stu-id="ae875-390">Things become tricky, however, when a <xref:System.Windows.Controls.Page> needs to pass data back to the <xref:System.Windows.Controls.Page> that navigated to it.</span></span> <span data-ttu-id="ae875-391">問題在於，導覽原本並不支援機制，以確保在 <xref:System.Windows.Controls.Page> 流覽之後，將會傳回。</span><span class="sxs-lookup"><span data-stu-id="ae875-391">The problem is that navigation doesn't natively support mechanisms for guaranteeing that a <xref:System.Windows.Controls.Page> will be returned to after it is navigated from.</span></span> <span data-ttu-id="ae875-392">基本上，巡覽不支援呼叫/傳回語意。</span><span class="sxs-lookup"><span data-stu-id="ae875-392">Essentially, navigation doesn't support call/return semantics.</span></span> <span data-ttu-id="ae875-393">為了解決這個問題，WPF 提供了 <xref:System.Windows.Navigation.PageFunction%601> 類別，您可以用它來確保以 <xref:System.Windows.Controls.Page> 可預測且結構化的方式傳回。</span><span class="sxs-lookup"><span data-stu-id="ae875-393">To solve this problem, WPF provides the <xref:System.Windows.Navigation.PageFunction%601> class that you can use to ensure that a <xref:System.Windows.Controls.Page> is returned to in a predictable and structured fashion.</span></span> <span data-ttu-id="ae875-394">如需詳細資訊，請參閱[結構化導覽總覽](structured-navigation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="ae875-394">For more information, see [Structured Navigation Overview](structured-navigation-overview.md).</span></span>

<a name="The_NavigationWindow_Class"></a>

## <a name="the-navigationwindow-class"></a><span data-ttu-id="ae875-395">NavigationWindow 類別</span><span class="sxs-lookup"><span data-stu-id="ae875-395">The NavigationWindow Class</span></span>

<span data-ttu-id="ae875-396">至此，您已了解最可能用來建置有可巡覽內容之應用程式的巡覽服務範圍。</span><span class="sxs-lookup"><span data-stu-id="ae875-396">To this point, you've seen the gamut of navigation services that you are most likely to use to build applications with navigable content.</span></span> <span data-ttu-id="ae875-397">這些服務是在 Xbap 的內容中討論，雖然它們不限於 Xbap。</span><span class="sxs-lookup"><span data-stu-id="ae875-397">These services were discussed in the context of XBAPs, although they are not limited to XBAPs.</span></span> <span data-ttu-id="ae875-398">新式作業系統和 Windows 應用程式利用新式使用者的瀏覽器體驗，將瀏覽器樣式的導覽併入獨立應用程式中。</span><span class="sxs-lookup"><span data-stu-id="ae875-398">Modern operating systems and Windows applications take advantage of the browser experience of modern users to incorporate browser-style navigation into standalone applications.</span></span> <span data-ttu-id="ae875-399">常見範例包括：</span><span class="sxs-lookup"><span data-stu-id="ae875-399">Common examples include:</span></span>

- <span data-ttu-id="ae875-400">**文字同義字**︰巡覽文字選擇。</span><span class="sxs-lookup"><span data-stu-id="ae875-400">**Word Thesaurus**: Navigate word choices.</span></span>

- <span data-ttu-id="ae875-401">**檔案總管**︰巡覽檔案和資料夾。</span><span class="sxs-lookup"><span data-stu-id="ae875-401">**File Explorer**: Navigate files and folders.</span></span>

- <span data-ttu-id="ae875-402">**精靈**︰將複雜的工作細分成可往來巡覽的多個頁面。</span><span class="sxs-lookup"><span data-stu-id="ae875-402">**Wizards**: Breaking down a complex task into multiple pages that can be navigated between.</span></span> <span data-ttu-id="ae875-403">其中一個範例是處理新增和移除 Windows 功能的 Windows 元件 Wizard。</span><span class="sxs-lookup"><span data-stu-id="ae875-403">An example is the Windows Components Wizard that handles adding and removing Windows features.</span></span>

<span data-ttu-id="ae875-404">若要將瀏覽器樣式的導覽併入您的獨立應用程式，您可以使用 <xref:System.Windows.Navigation.NavigationWindow> 類別。</span><span class="sxs-lookup"><span data-stu-id="ae875-404">To incorporate browser-style navigation into your standalone applications, you can use the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="ae875-405"><xref:System.Windows.Navigation.NavigationWindow>衍生自 <xref:System.Windows.Window> ，並使用 xbap 所提供的相同導覽支援來加以擴充。</span><span class="sxs-lookup"><span data-stu-id="ae875-405"><xref:System.Windows.Navigation.NavigationWindow> derives from <xref:System.Windows.Window> and extends it with the same support for navigation that XBAPs provide.</span></span> <span data-ttu-id="ae875-406">您可以使用 <xref:System.Windows.Navigation.NavigationWindow> 做為獨立應用程式的主視窗，或當做對話方塊之類的次要視窗。</span><span class="sxs-lookup"><span data-stu-id="ae875-406">You can use <xref:System.Windows.Navigation.NavigationWindow> as either the main window of your standalone application or as a secondary window such as a dialog box.</span></span>

<span data-ttu-id="ae875-407">若要執行 <xref:System.Windows.Navigation.NavigationWindow> ，如同 WPF 中的大部分最上層類別（ <xref:System.Windows.Window> 、 <xref:System.Windows.Controls.Page> 等等），您可以使用標記和程式碼後置的組合。</span><span class="sxs-lookup"><span data-stu-id="ae875-407">To implement a <xref:System.Windows.Navigation.NavigationWindow>, as with most top-level classes in WPF (<xref:System.Windows.Window>, <xref:System.Windows.Controls.Page>, and so on), you use a combination of markup and code-behind.</span></span> <span data-ttu-id="ae875-408">下列範例會顯示這一點。</span><span class="sxs-lookup"><span data-stu-id="ae875-408">This is shown in the following example.</span></span>

[!code-xaml[IntroToNavNavigationWindowSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml#navigationwindowmarkup)]

[!code-csharp[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml.cs#navigationwindowcodebehind)]
[!code-vb[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/MainWindow.xaml.vb#navigationwindowcodebehind)]

<span data-ttu-id="ae875-409">此 <xref:System.Windows.Navigation.NavigationWindow> 程式碼會建立，它會在開啟時自動流覽至 <xref:System.Windows.Controls.Page> （首頁. xaml） <xref:System.Windows.Navigation.NavigationWindow> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-409">This code creates a <xref:System.Windows.Navigation.NavigationWindow> that automatically navigates to a <xref:System.Windows.Controls.Page> (HomePage.xaml) when the <xref:System.Windows.Navigation.NavigationWindow> is opened.</span></span> <span data-ttu-id="ae875-410">如果 <xref:System.Windows.Navigation.NavigationWindow> 是主應用程式視窗，您可以使用 `StartupUri` 屬性來啟動它。</span><span class="sxs-lookup"><span data-stu-id="ae875-410">If the <xref:System.Windows.Navigation.NavigationWindow> is the main application window, you can use the `StartupUri` attribute to launch it.</span></span> <span data-ttu-id="ae875-411">下列標記顯示此做法。</span><span class="sxs-lookup"><span data-stu-id="ae875-411">This is shown in the following markup.</span></span>

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchNavWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/App.xaml#applaunchnavwindow)]

<span data-ttu-id="ae875-412">下圖顯示 <xref:System.Windows.Navigation.NavigationWindow> 作為獨立應用程式的主要視窗。</span><span class="sxs-lookup"><span data-stu-id="ae875-412">The following figure shows the <xref:System.Windows.Navigation.NavigationWindow> as the main window of a standalone application.</span></span>

<span data-ttu-id="ae875-413">![主視窗](./media/navigation-overview/navigation-window-as-main-window.png "做為主視窗的導覽視窗")</span><span class="sxs-lookup"><span data-stu-id="ae875-413">![A main window](./media/navigation-overview/navigation-window-as-main-window.png "Navigation window as the main window")</span></span>

<span data-ttu-id="ae875-414">從圖中，您可以看到 <xref:System.Windows.Navigation.NavigationWindow> 有一個標題，即使它不是在上述範例的實程式碼中設定也一樣 <xref:System.Windows.Navigation.NavigationWindow> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-414">From the figure, you can see that the <xref:System.Windows.Navigation.NavigationWindow> has a title, even though it wasn't set in the <xref:System.Windows.Navigation.NavigationWindow> implementation code from the preceding example.</span></span> <span data-ttu-id="ae875-415">而是使用屬性來設定標題 <xref:System.Windows.Controls.Page.WindowTitle%2A> ，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="ae875-415">Instead, the title is set using the <xref:System.Windows.Controls.Page.WindowTitle%2A> property, which is shown in the following code.</span></span>

[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup1)]
[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup2)]

<span data-ttu-id="ae875-416">設定 <xref:System.Windows.Controls.Page.WindowWidth%2A> 和 <xref:System.Windows.Controls.Page.WindowHeight%2A> 屬性也會影響 <xref:System.Windows.Navigation.NavigationWindow> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-416">Setting the <xref:System.Windows.Controls.Page.WindowWidth%2A> and <xref:System.Windows.Controls.Page.WindowHeight%2A> properties also affects the <xref:System.Windows.Navigation.NavigationWindow>.</span></span>

<span data-ttu-id="ae875-417"><xref:System.Windows.Navigation.NavigationWindow>當您需要自訂其行為或其外觀時，通常會執行自己的工作。</span><span class="sxs-lookup"><span data-stu-id="ae875-417">Usually, you implement your own <xref:System.Windows.Navigation.NavigationWindow> when you need to customize either its behavior or its appearance.</span></span> <span data-ttu-id="ae875-418">如果兩樣都不做，您可以使用捷徑。</span><span class="sxs-lookup"><span data-stu-id="ae875-418">If you do neither, you can use a shortcut.</span></span> <span data-ttu-id="ae875-419">如果您在獨立應用程式中將的 pack URI 指定 <xref:System.Windows.Controls.Page> 為 <xref:System.Windows.Application.StartupUri%2A> ，則 <xref:System.Windows.Application> 會自動建立 <xref:System.Windows.Navigation.NavigationWindow> 來裝載 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-419">If you specify the pack URI of a <xref:System.Windows.Controls.Page> as the <xref:System.Windows.Application.StartupUri%2A> in a standalone application, <xref:System.Windows.Application> automatically creates a <xref:System.Windows.Navigation.NavigationWindow> to host the <xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="ae875-420">下列標記顯示如何啟用此功能。</span><span class="sxs-lookup"><span data-stu-id="ae875-420">The following markup shows how to enable this.</span></span>

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchPage](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/AnotherApp.xaml#applaunchpage)]

<span data-ttu-id="ae875-421">如果您想要讓次要應用程式視窗（例如對話方塊 <xref:System.Windows.Navigation.NavigationWindow> ）成為，您可以使用下列範例中的程式碼來開啟它。</span><span class="sxs-lookup"><span data-stu-id="ae875-421">If you want a secondary application window such as a dialog box to be a <xref:System.Windows.Navigation.NavigationWindow>, you can use the code in the following example to open it.</span></span>

[!code-csharp[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/DialogOwnerWindow.xaml.cs#createnwdialogbox)]
[!code-vb[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/DialogOwnerWindow.xaml.vb#createnwdialogbox)]

<span data-ttu-id="ae875-422">其結果如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="ae875-422">The following figure shows the result.</span></span>

<span data-ttu-id="ae875-423">![對話方塊](./media/navigation-overview/navigation-window-as-dialog-box.png "作為對話方塊的導覽視窗")</span><span class="sxs-lookup"><span data-stu-id="ae875-423">![A dialog box](./media/navigation-overview/navigation-window-as-dialog-box.png "Navigation window as a dialog box")</span></span>

<span data-ttu-id="ae875-424">如您所見，會 <xref:System.Windows.Navigation.NavigationWindow> 顯示 Internet Explorer 樣式的 [**上一頁**] 和 [**下一頁**] 按鈕，讓使用者可以流覽日誌。</span><span class="sxs-lookup"><span data-stu-id="ae875-424">As you can see, <xref:System.Windows.Navigation.NavigationWindow> displays Internet Explorer-style **Back** and **Forward** buttons that allow users to navigate the journal.</span></span> <span data-ttu-id="ae875-425">這些按鈕提供相同的使用者體驗，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="ae875-425">These buttons provide the same user experience, as shown in the following figure.</span></span>

<span data-ttu-id="ae875-426">![NavigationWindow 中的向後和向前按鈕](./media/navigation-overview/back-and-forward-buttons-in-navigation-window.png "導覽視窗中的 [上一頁] 和 [下一頁] 按鈕")</span><span class="sxs-lookup"><span data-stu-id="ae875-426">![Back and Forward buttons in a NavigationWindow](./media/navigation-overview/back-and-forward-buttons-in-navigation-window.png "Back and Forward buttons in a Navigation window")</span></span>

<span data-ttu-id="ae875-427">如果您的頁面提供自己的日誌流覽支援和 UI，您可以將屬性的值設定為，以隱藏顯示的 [**上一頁**] 和 [**下一頁**] 按鈕 <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Navigation.NavigationWindow.ShowsNavigationUI%2A> `false` 。</span><span class="sxs-lookup"><span data-stu-id="ae875-427">If your pages provide their own journal navigation support and UI, you can hide the **Back** and **Forward** buttons displayed by <xref:System.Windows.Navigation.NavigationWindow> by setting the value of the <xref:System.Windows.Navigation.NavigationWindow.ShowsNavigationUI%2A> property to `false`.</span></span>

<span data-ttu-id="ae875-428">或者，您可以使用 WPF 中的自訂支援來取代 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Navigation.NavigationWindow> 本身的。</span><span class="sxs-lookup"><span data-stu-id="ae875-428">Alternatively, you can use customization support in WPF to replace the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] of the <xref:System.Windows.Navigation.NavigationWindow> itself.</span></span>

<a name="Frame_in_Standalone_Applications"></a>

## <a name="the-frame-class"></a><span data-ttu-id="ae875-429">Frame 類別</span><span class="sxs-lookup"><span data-stu-id="ae875-429">The Frame Class</span></span>

<span data-ttu-id="ae875-430">瀏覽器和 <xref:System.Windows.Navigation.NavigationWindow> 都是裝載可流覽內容的視窗。</span><span class="sxs-lookup"><span data-stu-id="ae875-430">Both the browser and <xref:System.Windows.Navigation.NavigationWindow> are windows that host navigable content.</span></span> <span data-ttu-id="ae875-431">在某些情況下，應用程式會有不需要由整個視窗裝載的內容。</span><span class="sxs-lookup"><span data-stu-id="ae875-431">In some cases, applications have content that does not need to be hosted by an entire window.</span></span> <span data-ttu-id="ae875-432">這類內容反可以裝載於其他內容中。</span><span class="sxs-lookup"><span data-stu-id="ae875-432">Instead, such content be hosted inside other content.</span></span> <span data-ttu-id="ae875-433">您可以使用類別，將可流覽的內容插入至其他內容 <xref:System.Windows.Controls.Frame> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-433">You can insert navigable content into other content by using the <xref:System.Windows.Controls.Frame> class.</span></span> <span data-ttu-id="ae875-434"><xref:System.Windows.Controls.Frame>提供與和 Xbap 相同的支援 <xref:System.Windows.Navigation.NavigationWindow> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-434"><xref:System.Windows.Controls.Frame> provides the same support as <xref:System.Windows.Navigation.NavigationWindow> and XBAPs.</span></span>

<span data-ttu-id="ae875-435">下列範例顯示如何使用專案，以宣告方式將加入 <xref:System.Windows.Controls.Frame> 至 <xref:System.Windows.Controls.Page> `Frame` 。</span><span class="sxs-lookup"><span data-stu-id="ae875-435">The following example shows how to add a <xref:System.Windows.Controls.Frame> to a <xref:System.Windows.Controls.Page> declaratively by using the `Frame` element.</span></span>

[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml3)]

<span data-ttu-id="ae875-436">此標記 `Source` `Frame` <xref:System.Windows.Controls.Page> 會針對應該一開始流覽至的，使用的 pack URI 來設定專案的屬性 <xref:System.Windows.Controls.Frame> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-436">This markup sets the `Source` attribute of the `Frame` element with a pack URI for the <xref:System.Windows.Controls.Page> that the <xref:System.Windows.Controls.Frame> should initially navigate to.</span></span> <span data-ttu-id="ae875-437">下圖顯示的 XBAP 具有，其已 <xref:System.Windows.Controls.Page> 在 <xref:System.Windows.Controls.Frame> 數個頁面之間流覽。</span><span class="sxs-lookup"><span data-stu-id="ae875-437">The following figure shows an XBAP with a <xref:System.Windows.Controls.Page> that has a <xref:System.Windows.Controls.Frame> that has navigated between several pages.</span></span>

<span data-ttu-id="ae875-438">![已在多個頁面之間巡覽過的框架](./media/navigation-overview/frame-navigation-between-multiple-pages.png "這會顯示多個頁面之間的框架導覽。")</span><span class="sxs-lookup"><span data-stu-id="ae875-438">![A frame that has navigated between multiple pages](./media/navigation-overview/frame-navigation-between-multiple-pages.png "This shows a frame navigation between multiple pages.")</span></span>

<span data-ttu-id="ae875-439">您不只需要在的 <xref:System.Windows.Controls.Frame> 內容內使用 <xref:System.Windows.Controls.Page> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-439">You don't only have to use <xref:System.Windows.Controls.Frame> inside the content of a <xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="ae875-440">在的內容中裝載，也是很常見的情況 <xref:System.Windows.Controls.Frame> <xref:System.Windows.Window> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-440">It is also common to host a <xref:System.Windows.Controls.Frame> inside the content of a <xref:System.Windows.Window>.</span></span>

<span data-ttu-id="ae875-441">根據預設， <xref:System.Windows.Controls.Frame> 只有在沒有另一個日誌時，才會使用自己的日誌。</span><span class="sxs-lookup"><span data-stu-id="ae875-441">By default, <xref:System.Windows.Controls.Frame> only uses its own journal in the absence of another journal.</span></span> <span data-ttu-id="ae875-442">如果是裝載于 <xref:System.Windows.Controls.Frame> 或 xbap 內部之內容的一部分，則會 <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Controls.Frame> 使用屬於 <xref:System.Windows.Navigation.NavigationWindow> 或 xbap 的日誌。</span><span class="sxs-lookup"><span data-stu-id="ae875-442">If a <xref:System.Windows.Controls.Frame> is part of content that is hosted inside either a <xref:System.Windows.Navigation.NavigationWindow> or an XBAP, <xref:System.Windows.Controls.Frame> uses the journal that belongs to the <xref:System.Windows.Navigation.NavigationWindow> or XBAP.</span></span> <span data-ttu-id="ae875-443">不過，有時候 <xref:System.Windows.Controls.Frame> 可能需要負責自己的日誌。</span><span class="sxs-lookup"><span data-stu-id="ae875-443">Sometimes, though, a <xref:System.Windows.Controls.Frame> might need to be responsible for its own journal.</span></span> <span data-ttu-id="ae875-444">這麼做的其中一個原因是允許在所裝載的頁面內進行日誌導覽 <xref:System.Windows.Controls.Frame> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-444">One reason to do so is to allow journal navigation within the pages that are hosted by a <xref:System.Windows.Controls.Frame>.</span></span> <span data-ttu-id="ae875-445">如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="ae875-445">This is illustrated by the following figure.</span></span>

<span data-ttu-id="ae875-446">![框架和頁面圖表](./media/navigation-overview/journal-navigation-within-pages-hosted-by-a-frame.png "這會在框架所主控的頁面中顯示日誌導覽。")</span><span class="sxs-lookup"><span data-stu-id="ae875-446">![Frame and Page diagram](./media/navigation-overview/journal-navigation-within-pages-hosted-by-a-frame.png "This shows journal navigation within pages hosted by a frame.")</span></span>

<span data-ttu-id="ae875-447">在此情況下，您可以將的 <xref:System.Windows.Controls.Frame> 屬性設為，將設定為使用自己的日誌 <xref:System.Windows.Controls.Frame.JournalOwnership%2A> <xref:System.Windows.Controls.Frame> <xref:System.Windows.Navigation.JournalOwnership.OwnsJournal> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-447">In this case, you can configure the <xref:System.Windows.Controls.Frame> to use its own journal by setting the <xref:System.Windows.Controls.Frame.JournalOwnership%2A> property of the <xref:System.Windows.Controls.Frame> to <xref:System.Windows.Navigation.JournalOwnership.OwnsJournal>.</span></span> <span data-ttu-id="ae875-448">下列標記顯示此做法。</span><span class="sxs-lookup"><span data-stu-id="ae875-448">This is shown in the following markup.</span></span>

[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml3)]

<span data-ttu-id="ae875-449">下圖說明在使用自己的日誌的中流覽的效果 <xref:System.Windows.Controls.Frame> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-449">The following figure illustrates the effect of navigating within a <xref:System.Windows.Controls.Frame> that uses its own journal.</span></span>

<span data-ttu-id="ae875-450">![使用本身之日誌的框架](./media/navigation-overview/frame-uses-its-own-journal.png "這會顯示在使用自己的日誌的框架內流覽的效果。")</span><span class="sxs-lookup"><span data-stu-id="ae875-450">![A frame that uses its own journal](./media/navigation-overview/frame-uses-its-own-journal.png "This shows the effect of navigating within a frame that uses its own journal.")</span></span>

<span data-ttu-id="ae875-451">請注意，中的導覽會顯示日誌項目 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Controls.Frame> ，而不是 Internet Explorer。</span><span class="sxs-lookup"><span data-stu-id="ae875-451">Notice that the journal entries are shown by the navigation [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] in the <xref:System.Windows.Controls.Frame>, rather than by Internet Explorer.</span></span>

> [!NOTE]
> <span data-ttu-id="ae875-452">如果 <xref:System.Windows.Controls.Frame> 是裝載于中之內容的一部分，則 <xref:System.Windows.Window> 會 <xref:System.Windows.Controls.Frame> 使用自己的日誌，因此會顯示它自己的導覽 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ae875-452">If a <xref:System.Windows.Controls.Frame> is part of content that is hosted in a <xref:System.Windows.Window>, <xref:System.Windows.Controls.Frame> uses its own journal and, consequently, displays its own navigation [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span></span>

<span data-ttu-id="ae875-453">如果您的使用者體驗需要 <xref:System.Windows.Controls.Frame> 提供自己的日誌，而不顯示導覽 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ，您可以 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 將設定為來隱藏導覽 <xref:System.Windows.Controls.Frame.NavigationUIVisibility%2A> <xref:System.Windows.Visibility.Hidden> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-453">If your user experience requires a <xref:System.Windows.Controls.Frame> to provide its own journal without showing the navigation [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], you can hide the navigation [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] by setting the <xref:System.Windows.Controls.Frame.NavigationUIVisibility%2A> to <xref:System.Windows.Visibility.Hidden>.</span></span> <span data-ttu-id="ae875-454">下列標記顯示此做法。</span><span class="sxs-lookup"><span data-stu-id="ae875-454">This is shown in the following markup.</span></span>

[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml3)]

<a name="Navigation_Hosts"></a>

## <a name="navigation-hosts"></a><span data-ttu-id="ae875-455">巡覽裝載</span><span class="sxs-lookup"><span data-stu-id="ae875-455">Navigation Hosts</span></span>

<span data-ttu-id="ae875-456"><xref:System.Windows.Controls.Frame>和 <xref:System.Windows.Navigation.NavigationWindow> 是稱為「導覽主機」的類別。</span><span class="sxs-lookup"><span data-stu-id="ae875-456"><xref:System.Windows.Controls.Frame> and <xref:System.Windows.Navigation.NavigationWindow> are classes that are known as navigation hosts.</span></span> <span data-ttu-id="ae875-457">*導覽主機*是可流覽並顯示內容的類別。</span><span class="sxs-lookup"><span data-stu-id="ae875-457">A *navigation host* is a class that can navigate to and display content.</span></span> <span data-ttu-id="ae875-458">為了完成這項工作，每個導覽主機都會使用自己的 <xref:System.Windows.Navigation.NavigationService> 和日誌。</span><span class="sxs-lookup"><span data-stu-id="ae875-458">To accomplish this, each navigation host uses its own <xref:System.Windows.Navigation.NavigationService> and journal.</span></span> <span data-ttu-id="ae875-459">巡覽裝載的基本建構如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="ae875-459">The basic construction of a navigation host is shown in the following figure.</span></span>

<span data-ttu-id="ae875-460">![導覽器圖表](./media/navigation-overview/navigation-host-construction.png "導覽主控制項的基本結構")</span><span class="sxs-lookup"><span data-stu-id="ae875-460">![Navigator diagrams](./media/navigation-overview/navigation-host-construction.png "Basic construction of a navigation host")</span></span>

<span data-ttu-id="ae875-461">基本上，這可讓 <xref:System.Windows.Navigation.NavigationWindow> 和 <xref:System.Windows.Controls.Frame> 提供在瀏覽器中裝載時，XBAP 提供的相同導覽支援。</span><span class="sxs-lookup"><span data-stu-id="ae875-461">Essentially, this allows <xref:System.Windows.Navigation.NavigationWindow> and <xref:System.Windows.Controls.Frame> to provide the same navigation support that an XBAP provides when hosted in the browser.</span></span>

<span data-ttu-id="ae875-462">除了使用 <xref:System.Windows.Navigation.NavigationService> 和日誌以外，流覽主控制項還會執行相同的成員 <xref:System.Windows.Navigation.NavigationService> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-462">Besides using <xref:System.Windows.Navigation.NavigationService> and a journal, navigation hosts implement the same members that <xref:System.Windows.Navigation.NavigationService> implements.</span></span> <span data-ttu-id="ae875-463">如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="ae875-463">This is illustrated by the following figure.</span></span>

<span data-ttu-id="ae875-464">![在框架和 NavigationWindow 中的日誌](./media/navigation-overview/navigation-window-and-frame.png "導覽視窗和框架")</span><span class="sxs-lookup"><span data-stu-id="ae875-464">![A journal in a Frame and in a NavigationWindow](./media/navigation-overview/navigation-window-and-frame.png "Navigation Window and Frame")</span></span>

<span data-ttu-id="ae875-465">這可讓您針對它們直接設計巡覽支援程式。</span><span class="sxs-lookup"><span data-stu-id="ae875-465">This allows you to program navigation support directly against them.</span></span> <span data-ttu-id="ae875-466">如果您需要為裝載于的，提供自訂導覽，可以考慮這 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Controls.Frame> 一點 <xref:System.Windows.Window> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-466">You may consider this if you need to provide a custom navigation [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] for a <xref:System.Windows.Controls.Frame> that is hosted in a <xref:System.Windows.Window>.</span></span> <span data-ttu-id="ae875-467">此外，這兩種類型都會執行其他的導覽相關成員，包括 `BackStack` （ <xref:System.Windows.Navigation.NavigationWindow.BackStack%2A?displayProperty=nameWithType> ， <xref:System.Windows.Controls.Frame.BackStack%2A?displayProperty=nameWithType> ）和 `ForwardStack` （ <xref:System.Windows.Navigation.NavigationWindow.ForwardStack%2A?displayProperty=nameWithType> ， <xref:System.Windows.Controls.Frame.ForwardStack%2A?displayProperty=nameWithType> ），這可讓您分別列舉後端堆疊和轉送堆疊中的記錄項目。</span><span class="sxs-lookup"><span data-stu-id="ae875-467">Furthermore, both types implement additional, navigation-related members, including `BackStack` (<xref:System.Windows.Navigation.NavigationWindow.BackStack%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Frame.BackStack%2A?displayProperty=nameWithType>) and `ForwardStack` (<xref:System.Windows.Navigation.NavigationWindow.ForwardStack%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Frame.ForwardStack%2A?displayProperty=nameWithType>), which allow you to enumerate the journal entries in the back stack and forward stack, respectively.</span></span>

<span data-ttu-id="ae875-468">如前所述，應用程式中可有多個日誌。</span><span class="sxs-lookup"><span data-stu-id="ae875-468">As mentioned earlier, more than one journal can exist within an application.</span></span> <span data-ttu-id="ae875-469">下圖提供這種情況的範例。</span><span class="sxs-lookup"><span data-stu-id="ae875-469">The following figure provides an example of when this can happen.</span></span>

<span data-ttu-id="ae875-470">![一個應用程式中包含多個日誌](./media/navigation-overview/multiple-journals-in-one-application.png "這是應用程式中一個以上的日誌範例。")</span><span class="sxs-lookup"><span data-stu-id="ae875-470">![Multiple journals within one application](./media/navigation-overview/multiple-journals-in-one-application.png "This is an example of more than one journal in an application.")</span></span>

<a name="Navigating_to_Content_Other_than_Pages"></a>

## <a name="navigating-to-content-other-than-xaml-pages"></a><span data-ttu-id="ae875-471">巡覽至 XAML 頁面以外的內容</span><span class="sxs-lookup"><span data-stu-id="ae875-471">Navigating to Content Other than XAML Pages</span></span>

<span data-ttu-id="ae875-472">在本主題中， <xref:System.Windows.Controls.Page> 和 Pack xbap 已用來示範 WPF 的各種導覽功能。</span><span class="sxs-lookup"><span data-stu-id="ae875-472">Throughout this topic, <xref:System.Windows.Controls.Page> and pack XBAPs have been used to demonstrate the various navigation capabilities of WPF.</span></span> <span data-ttu-id="ae875-473">不過， <xref:System.Windows.Controls.Page> 編譯成應用程式的不是可流覽的唯一內容類型，而套件 xbap 則不是識別內容的唯一方法。</span><span class="sxs-lookup"><span data-stu-id="ae875-473">However, a <xref:System.Windows.Controls.Page> that is compiled into an application is not the only type of content that can be navigated to, and pack XBAPs aren't the only way to identify content.</span></span>

<span data-ttu-id="ae875-474">如本節所示，您也可以流覽至鬆散的檔案 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 、HTML 檔案和物件。</span><span class="sxs-lookup"><span data-stu-id="ae875-474">As this section demonstrates, you can also navigate to loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files, HTML files, and objects.</span></span>

<a name="Navigating_to_Loose_XAML_Files"></a>

### <a name="navigating-to-loose-xaml-files"></a><span data-ttu-id="ae875-475">巡覽至鬆散的 XAML 檔案</span><span class="sxs-lookup"><span data-stu-id="ae875-475">Navigating to Loose XAML Files</span></span>

<span data-ttu-id="ae875-476">鬆散檔案 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 是具有下列特性的檔案：</span><span class="sxs-lookup"><span data-stu-id="ae875-476">A loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file is a file with the following characteristics:</span></span>

- <span data-ttu-id="ae875-477">僅包含 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] （也就是沒有程式碼）。</span><span class="sxs-lookup"><span data-stu-id="ae875-477">Contains only [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (that is, no code).</span></span>

- <span data-ttu-id="ae875-478">具有適當的命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="ae875-478">Has an appropriate namespace declaration.</span></span>

- <span data-ttu-id="ae875-479">具有 .xaml 副檔名。</span><span class="sxs-lookup"><span data-stu-id="ae875-479">Has the .xaml file name extension.</span></span>

<span data-ttu-id="ae875-480">例如，請考慮將下列內容儲存為鬆散檔案 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，Person. xaml。</span><span class="sxs-lookup"><span data-stu-id="ae875-480">For example, consider the following content that is stored as a loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file, Person.xaml.</span></span>

[!code-xaml[NavigationOverviewSnippets#LooseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Person.xaml#loosexaml)]

<span data-ttu-id="ae875-481">當您按兩下檔案時，瀏覽器會開啟、巡覽至並顯示內容。</span><span class="sxs-lookup"><span data-stu-id="ae875-481">When you double-click the file, the browser opens and navigates to and displays the content.</span></span> <span data-ttu-id="ae875-482">如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="ae875-482">This is shown in the following figure.</span></span>

<span data-ttu-id="ae875-483">![顯示 Person.XAML 檔案中的內容](./media/navigation-overview/contents-of-person-xaml-file.png "顯示 Person. XAML 檔案的內容。")</span><span class="sxs-lookup"><span data-stu-id="ae875-483">![Display of the content in the Person.XAML file](./media/navigation-overview/contents-of-person-xaml-file.png "Shows the contents of the Person.XAML file.")</span></span>

<span data-ttu-id="ae875-484">您可以顯示 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 下列的鬆散檔案：</span><span class="sxs-lookup"><span data-stu-id="ae875-484">You can display a loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file from the following:</span></span>

- <span data-ttu-id="ae875-485">在本機電腦、內部網路或網際網路上的網站。</span><span class="sxs-lookup"><span data-stu-id="ae875-485">A Web site on the local machine, the intranet, or the Internet.</span></span>

- <span data-ttu-id="ae875-486">通用命名慣例（UNC）檔案共用。</span><span class="sxs-lookup"><span data-stu-id="ae875-486">A Universal Naming Convention (UNC) file share.</span></span>

- <span data-ttu-id="ae875-487">本機磁碟。</span><span class="sxs-lookup"><span data-stu-id="ae875-487">The local disk.</span></span>

<span data-ttu-id="ae875-488">鬆散檔案 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 可以新增至瀏覽器的 [我的最愛]，或作為瀏覽器的首頁。</span><span class="sxs-lookup"><span data-stu-id="ae875-488">A loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file can be added to the browser's favorites, or be the browser's home page.</span></span>

> [!NOTE]
> <span data-ttu-id="ae875-489">如需發佈和啟動鬆散頁面的詳細資訊 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，請參閱[部署 WPF 應用程式](deploying-a-wpf-application-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="ae875-489">For more information about publishing and launching loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pages, see [Deploying a WPF Application](deploying-a-wpf-application-wpf.md).</span></span>

<span data-ttu-id="ae875-490">鬆散的一項限制 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 是，您只能裝載可安全地在部分信任中執行的內容。</span><span class="sxs-lookup"><span data-stu-id="ae875-490">One limitation with respect to loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] is that you can only host content that is safe to run in partial trust.</span></span> <span data-ttu-id="ae875-491">例如， `Window` 不能是鬆散檔案的根項目 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ae875-491">For example, `Window` cannot be the root element of a loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="ae875-492">如需詳細資訊，請參閱 [WPF 部分信任安全性](../wpf-partial-trust-security.md)。</span><span class="sxs-lookup"><span data-stu-id="ae875-492">For more information, see [WPF Partial Trust Security](../wpf-partial-trust-security.md).</span></span>

<a name="Navigating_to_HTML_Files_Using_Frame"></a>

### <a name="navigating-to-html-files-by-using-frame"></a><span data-ttu-id="ae875-493">使用框架巡覽至 HTML 檔案</span><span class="sxs-lookup"><span data-stu-id="ae875-493">Navigating to HTML Files by Using Frame</span></span>

<span data-ttu-id="ae875-494">如您所預期，您也可以流覽至 HTML。</span><span class="sxs-lookup"><span data-stu-id="ae875-494">As you might expect, you can also navigate to HTML.</span></span> <span data-ttu-id="ae875-495">您只需要提供使用 HTTP 配置的 URI。</span><span class="sxs-lookup"><span data-stu-id="ae875-495">You simply need to provide a URI that uses the http scheme.</span></span> <span data-ttu-id="ae875-496">例如，以下 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 顯示 <xref:System.Windows.Controls.Frame> 流覽至 HTML 網頁的。</span><span class="sxs-lookup"><span data-stu-id="ae875-496">For example, the following [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] shows a <xref:System.Windows.Controls.Frame> that navigates to an HTML page.</span></span>

[!code-xaml[NavigationOverviewSnippets#FrameHtmlNavMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHTMLNavPage.xaml#framehtmlnavmarkup)]

<span data-ttu-id="ae875-497">流覽至 HTML 需要特殊許可權。</span><span class="sxs-lookup"><span data-stu-id="ae875-497">Navigating to HTML requires special permissions.</span></span> <span data-ttu-id="ae875-498">例如，您無法從在網際網路區域部分信任安全性沙箱中執行的 XBAP 進行流覽。</span><span class="sxs-lookup"><span data-stu-id="ae875-498">For example, you can't navigate from an XBAP that is running in the Internet zone partial trust security sandbox.</span></span> <span data-ttu-id="ae875-499">如需詳細資訊，請參閱 [WPF 部分信任安全性](../wpf-partial-trust-security.md)。</span><span class="sxs-lookup"><span data-stu-id="ae875-499">For more information, see [WPF Partial Trust Security](../wpf-partial-trust-security.md).</span></span>

<a name="Navigating_to_HTML_Files_Using_WebBrowser"></a>

### <a name="navigating-to-html-files-by-using-the-webbrowser-control"></a><span data-ttu-id="ae875-500">使用 WebBrowser 控制項巡覽至 HTML 檔案</span><span class="sxs-lookup"><span data-stu-id="ae875-500">Navigating to HTML Files by Using the WebBrowser Control</span></span>

<span data-ttu-id="ae875-501"><xref:System.Windows.Controls.WebBrowser>控制項支援 HTML 檔案裝載、導覽和腳本/managed 程式碼互通性。</span><span class="sxs-lookup"><span data-stu-id="ae875-501">The <xref:System.Windows.Controls.WebBrowser> control supports HTML document hosting, navigation and script/managed code interoperability.</span></span> <span data-ttu-id="ae875-502">如需有關控制項的詳細資訊 <xref:System.Windows.Controls.WebBrowser> ，請參閱 <xref:System.Windows.Controls.WebBrowser> 。</span><span class="sxs-lookup"><span data-stu-id="ae875-502">For detailed information regarding the <xref:System.Windows.Controls.WebBrowser> control, see <xref:System.Windows.Controls.WebBrowser>.</span></span>

<span data-ttu-id="ae875-503">如同 <xref:System.Windows.Controls.Frame> ，使用流覽至 HTML <xref:System.Windows.Controls.WebBrowser> 需要特殊許可權。</span><span class="sxs-lookup"><span data-stu-id="ae875-503">Like <xref:System.Windows.Controls.Frame>, navigating to HTML using <xref:System.Windows.Controls.WebBrowser> requires special permissions.</span></span> <span data-ttu-id="ae875-504">例如，您可以從部分信任的應用程式，只流覽至位於來源網站的 HTML。</span><span class="sxs-lookup"><span data-stu-id="ae875-504">For example, from a partial-trust application, you can navigate only to HTML located at the site of origin.</span></span> <span data-ttu-id="ae875-505">如需詳細資訊，請參閱 [WPF 部分信任安全性](../wpf-partial-trust-security.md)。</span><span class="sxs-lookup"><span data-stu-id="ae875-505">For more information, see [WPF Partial Trust Security](../wpf-partial-trust-security.md).</span></span>

<a name="Navigating_to_Objects"></a>

### <a name="navigating-to-custom-objects"></a><span data-ttu-id="ae875-506">巡覽至自訂物件</span><span class="sxs-lookup"><span data-stu-id="ae875-506">Navigating to Custom Objects</span></span>

<span data-ttu-id="ae875-507">如果您有儲存為自訂物件的資料，顯示該資料的一種方式是建立， <xref:System.Windows.Controls.Page> 並將內容系結至這些物件（請參閱[資料](../../../desktop-wpf/data/data-binding-overview.md)系結總覽）。</span><span class="sxs-lookup"><span data-stu-id="ae875-507">If you have data that is stored as custom objects, one way to display that data is to create a <xref:System.Windows.Controls.Page> with content that is bound to those objects (see [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md)).</span></span> <span data-ttu-id="ae875-508">如果您不需要建立整個頁面此額外負荷，而只要顯示物件，則您可以改為直接巡覽至它們。</span><span class="sxs-lookup"><span data-stu-id="ae875-508">If you don't need the overhead of creating an entire page just to display the objects, you can navigate directly to them instead.</span></span>

<span data-ttu-id="ae875-509">請考慮在 `Person` 下列程式碼中執行的類別。</span><span class="sxs-lookup"><span data-stu-id="ae875-509">Consider the `Person` class that is implemented in the following code.</span></span>

[!code-csharp[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/Person.cs#personclasscode)]
[!code-vb[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/Person.vb#personclasscode)]

<span data-ttu-id="ae875-510">若要流覽至它，您可以呼叫 <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A?displayProperty=nameWithType> 方法，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="ae875-510">To navigate to it, you call the <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A?displayProperty=nameWithType> method, as demonstrated by the following code.</span></span>

[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject1)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject2)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject3)]

[!code-csharp[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml.cs#pagethatnavstoobjectcodebehind)]
[!code-vb[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/HomePage.xaml.vb#pagethatnavstoobjectcodebehind)]

<span data-ttu-id="ae875-511">其結果如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="ae875-511">The following figure shows the result.</span></span>

<span data-ttu-id="ae875-512">![巡覽至類別的頁面](./media/navigation-overview/page-navigates-to-an-object.png "這是導覽至物件的頁面範例。")</span><span class="sxs-lookup"><span data-stu-id="ae875-512">![A page that navigates to a class](./media/navigation-overview/page-navigates-to-an-object.png "This is an example of a page that navigates to an object.")</span></span>

<span data-ttu-id="ae875-513">在此圖中，您看不到任何有用的內容。</span><span class="sxs-lookup"><span data-stu-id="ae875-513">From this figure, you can see that nothing useful is displayed.</span></span> <span data-ttu-id="ae875-514">事實上，顯示的值是 Person 物件之方法的傳回值 `ToString` ; 根據預設， **Person**這是 WPF 可用來代表物件的唯一值。</span><span class="sxs-lookup"><span data-stu-id="ae875-514">In fact, the value that is displayed is the return value of the `ToString` method for the **Person** object; by default, this is the only value that WPF can use to represent your object.</span></span> <span data-ttu-id="ae875-515">您可以覆寫 `ToString` 方法以傳回更有意義的資訊，但它仍然只是字串值。</span><span class="sxs-lookup"><span data-stu-id="ae875-515">You could override the `ToString` method to return more meaningful information, although it will still only be a string value.</span></span> <span data-ttu-id="ae875-516">您可以使用的一種技術，利用 WPF 的呈現功能，就是使用資料範本。</span><span class="sxs-lookup"><span data-stu-id="ae875-516">One technique you can use that takes advantage of the presentation capabilities of WPF is to use a data template.</span></span> <span data-ttu-id="ae875-517">您可以執行 WPF 可以與特定類型的物件產生關聯的資料範本。</span><span class="sxs-lookup"><span data-stu-id="ae875-517">You can implement a data template that WPF can associate with an object of a particular type.</span></span> <span data-ttu-id="ae875-518">下列程式碼顯示物件的資料範本 `Person` 。</span><span class="sxs-lookup"><span data-stu-id="ae875-518">The following code shows a data template for the `Person` object.</span></span>

[!code-xaml[NavigateToObjectSnippets#DataTemplateMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/App.xaml#datatemplatemarkup)]

<span data-ttu-id="ae875-519">在這裡，資料範本會 `Person` 使用 `x:Type` 屬性中的標記延伸，與類型相關聯 `DataType` 。</span><span class="sxs-lookup"><span data-stu-id="ae875-519">Here, the data template is associated with the `Person` type by using the `x:Type` markup extension in the `DataType` attribute.</span></span> <span data-ttu-id="ae875-520">然後，資料範本會將 `TextBlock` 元素（請參閱）系結 <xref:System.Windows.Controls.TextBlock> 至 `Person` 類別的屬性。</span><span class="sxs-lookup"><span data-stu-id="ae875-520">The data template then binds `TextBlock` elements (see <xref:System.Windows.Controls.TextBlock>) to the properties of the `Person` class.</span></span> <span data-ttu-id="ae875-521">下圖顯示物件的更新外觀 `Person` 。</span><span class="sxs-lookup"><span data-stu-id="ae875-521">The following figure shows the updated appearance of the `Person` object.</span></span>

<span data-ttu-id="ae875-522">![巡覽至具有資料範本的類別](./media/navigation-overview/navigating-to-a-class.png "流覽至具有資料範本的類別。")</span><span class="sxs-lookup"><span data-stu-id="ae875-522">![Navigating to a class that has a data template](./media/navigation-overview/navigating-to-a-class.png "Navigating to a class that has a data template.")</span></span>

<span data-ttu-id="ae875-523">這項技術的優點是可以取得一致性，因為能夠重複使用資料範本，所以應用程式任何位置都可顯示一致的物件。</span><span class="sxs-lookup"><span data-stu-id="ae875-523">An advantage of this technique is the consistency you gain by being able to reuse the data template to display your objects consistently anywhere in your application.</span></span>

<span data-ttu-id="ae875-524">如需資料範本的詳細資訊，請參閱[資料範本化總覽](../data/data-templating-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="ae875-524">For more information on data templates, see [Data Templating Overview](../data/data-templating-overview.md).</span></span>

<a name="Security"></a>

## <a name="security"></a><span data-ttu-id="ae875-525">安全性</span><span class="sxs-lookup"><span data-stu-id="ae875-525">Security</span></span>

<span data-ttu-id="ae875-526">WPF 導覽支援可讓您透過網際網路流覽 Xbap，並允許應用程式裝載協力廠商內容。</span><span class="sxs-lookup"><span data-stu-id="ae875-526">WPF navigation support allows XBAPs to be navigated to across the Internet, and it allows applications to host third-party content.</span></span> <span data-ttu-id="ae875-527">為了保護應用程式和使用者免于有害的行為，WPF 提供了[安全性](../security-wpf.md)和[WPF 部分信任安全性](../wpf-partial-trust-security.md)中所討論的各種安全性功能。</span><span class="sxs-lookup"><span data-stu-id="ae875-527">To protect both applications and users from harmful behavior, WPF provides a variety of security features that are discussed in [Security](../security-wpf.md) and [WPF Partial Trust Security](../wpf-partial-trust-security.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ae875-528">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae875-528">See also</span></span>

- <xref:System.Windows.Application.SetCookie%2A>
- <xref:System.Windows.Application.GetCookie%2A>
- [<span data-ttu-id="ae875-529">應用程式管理概觀</span><span class="sxs-lookup"><span data-stu-id="ae875-529">Application Management Overview</span></span>](application-management-overview.md)
- [<span data-ttu-id="ae875-530">WPF 中的 Pack URI</span><span class="sxs-lookup"><span data-stu-id="ae875-530">Pack URIs in WPF</span></span>](pack-uris-in-wpf.md)
- [<span data-ttu-id="ae875-531">結構化巡覽概觀</span><span class="sxs-lookup"><span data-stu-id="ae875-531">Structured Navigation Overview</span></span>](structured-navigation-overview.md)
- [<span data-ttu-id="ae875-532">巡覽拓撲概觀</span><span class="sxs-lookup"><span data-stu-id="ae875-532">Navigation Topologies Overview</span></span>](navigation-topologies-overview.md)
- [<span data-ttu-id="ae875-533">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="ae875-533">How-to Topics</span></span>](navigation-how-to-topics.md)
- [<span data-ttu-id="ae875-534">部署 WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="ae875-534">Deploying a WPF Application</span></span>](deploying-a-wpf-application-wpf.md)
