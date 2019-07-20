---
title: 結構化巡覽概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- structured navigation [WPF]
ms.assetid: 025d30ef-fec5-436d-ad7a-5d5483331c26
ms.openlocfilehash: 8760c847d9e73fdff9f10f0dfa55a6c674021667
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364182"
---
# <a name="structured-navigation-overview"></a><span data-ttu-id="cd89d-102">結構化巡覽概觀</span><span class="sxs-lookup"><span data-stu-id="cd89d-102">Structured Navigation Overview</span></span>

<span data-ttu-id="cd89d-103">可由[!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] 、或所<xref:System.Windows.Navigation.NavigationWindow>裝載的內容是由可由套件識別並由超連結流覽至的頁面所組成。 <xref:System.Windows.Controls.Frame></span><span class="sxs-lookup"><span data-stu-id="cd89d-103">Content that can be hosted by an [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)], a <xref:System.Windows.Controls.Frame>, or a <xref:System.Windows.Navigation.NavigationWindow> is composed of pages that can be identified by pack [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] and navigated to by hyperlinks.</span></span> <span data-ttu-id="cd89d-104">頁面的結構及其可被巡覽的方式，如超連結所定義，稱之為巡覽拓撲。</span><span class="sxs-lookup"><span data-stu-id="cd89d-104">The structure of pages and the ways in which they can be navigated, as defined by hyperlinks, is known as a navigation topology.</span></span> <span data-ttu-id="cd89d-105">這種拓撲適合各種不同的應用程式類型，尤其是巡覽文件的應用程式。</span><span class="sxs-lookup"><span data-stu-id="cd89d-105">Such a topology suits a variety of application types, particularly those that navigate through documents.</span></span> <span data-ttu-id="cd89d-106">針對這類應用程式，使用者可以從一頁巡覽到另一頁，頁面彼此間不需要了解。</span><span class="sxs-lookup"><span data-stu-id="cd89d-106">For such applications, the user can navigate from one page to another page without either page needing to know anything about the other.</span></span>

<span data-ttu-id="cd89d-107">不過，其他類型的應用程式有需要知道被巡覽的頁面。</span><span class="sxs-lookup"><span data-stu-id="cd89d-107">However, other types of applications have pages that do need to know when they have been navigated between.</span></span> <span data-ttu-id="cd89d-108">例如，假設人力資源應用程式有列出組織中所有員工的頁面：「員工清單」頁面。</span><span class="sxs-lookup"><span data-stu-id="cd89d-108">For example, consider a human resources application that has one page to list all the employees in an organization—the "List Employees" page.</span></span> <span data-ttu-id="cd89d-109">此頁面也允許使用者按一下超連結新增新進員工。</span><span class="sxs-lookup"><span data-stu-id="cd89d-109">This page could also allow users to add a new employee by clicking a hyperlink.</span></span> <span data-ttu-id="cd89d-110">按一下時，頁面會巡覽至「新增員工」頁面，收集新進員工的詳細資料，並傳回「員工清單」頁面建立新的員工以及更新清單。</span><span class="sxs-lookup"><span data-stu-id="cd89d-110">When clicked, the page navigates to an "Add an Employee" page to gather the new employee's details and return them to the "List Employees" page to create the new employee and update the list.</span></span> <span data-ttu-id="cd89d-111">這種巡覽樣式類似於呼叫方法執行一些處理並傳回值，稱之為結構化程式設計。</span><span class="sxs-lookup"><span data-stu-id="cd89d-111">This style of navigation is similar to calling a method to perform some processing and return a value, which is known as structured programming.</span></span> <span data-ttu-id="cd89d-112">因此，這種巡覽稱之為「結構化巡覽」  。</span><span class="sxs-lookup"><span data-stu-id="cd89d-112">As such, this style of navigation is known as *structured navigation*.</span></span>

<span data-ttu-id="cd89d-113"><xref:System.Windows.Controls.Page>類別不會執行結構化導覽的支援。</span><span class="sxs-lookup"><span data-stu-id="cd89d-113">The <xref:System.Windows.Controls.Page> class doesn't implement support for structured navigation.</span></span> <span data-ttu-id="cd89d-114">相反地, <xref:System.Windows.Navigation.PageFunction%601>類別衍生自<xref:System.Windows.Controls.Page> , 並以結構化導覽所需的基本結構來擴充它。</span><span class="sxs-lookup"><span data-stu-id="cd89d-114">Instead, the <xref:System.Windows.Navigation.PageFunction%601> class derives from <xref:System.Windows.Controls.Page> and extends it with the basic constructs required for structured navigation.</span></span> <span data-ttu-id="cd89d-115">本主題說明如何使用<xref:System.Windows.Navigation.PageFunction%601>來建立結構化導覽。</span><span class="sxs-lookup"><span data-stu-id="cd89d-115">This topic shows how to establish structured navigation using <xref:System.Windows.Navigation.PageFunction%601>.</span></span>

<a name="Structured_Navigation"></a>

## <a name="structured-navigation"></a><span data-ttu-id="cd89d-116">結構化巡覽</span><span class="sxs-lookup"><span data-stu-id="cd89d-116">Structured Navigation</span></span>

<span data-ttu-id="cd89d-117">當一個頁面在結構化巡覽中呼叫另一個頁面時，需要下列部分或全部行為︰</span><span class="sxs-lookup"><span data-stu-id="cd89d-117">When one page calls another page in a structured navigation, some or all of the following behaviors are required:</span></span>

- <span data-ttu-id="cd89d-118">呼叫端頁面會巡覽至呼叫的頁面，並選擇性地傳遞被呼叫頁面所需的參數。</span><span class="sxs-lookup"><span data-stu-id="cd89d-118">The calling page navigates to the called page, optionally passing parameters required by the called page.</span></span>

- <span data-ttu-id="cd89d-119">當使用者用完呼叫端頁面時，呼叫的頁面會選擇性特別傳回給呼叫端頁面︰</span><span class="sxs-lookup"><span data-stu-id="cd89d-119">The called page, when a user has completed using the calling page, returns specifically to the calling page, optionally:</span></span>

  - <span data-ttu-id="cd89d-120">傳回狀態資訊，說明如何完成呼叫端頁面 (例如，使用者按下 [確定] 按鈕或 [取消] 按鈕)。</span><span class="sxs-lookup"><span data-stu-id="cd89d-120">Returning state information that describes how the calling page was completed (for example, whether a user pressed an OK button or a Cancel button).</span></span>

  - <span data-ttu-id="cd89d-121">傳回收集的使用者資料 (例如，新進員工的詳細資料)。</span><span class="sxs-lookup"><span data-stu-id="cd89d-121">Returning that data that was collected from the user (for example, new employee details).</span></span>

- <span data-ttu-id="cd89d-122">當呼叫端頁面傳回被呼叫的頁面時，巡覽記錄會移除呼叫的頁面，隔離呼叫頁面中的各個執行個體。</span><span class="sxs-lookup"><span data-stu-id="cd89d-122">When the calling page returns to the called page, the called page is removed from navigation history to isolate one instance of a called page from another.</span></span>

<span data-ttu-id="cd89d-123">下圖說明這些行為:</span><span class="sxs-lookup"><span data-stu-id="cd89d-123">These behaviors are illustrated by the following figure:</span></span>

![螢幕擷取畫面顯示呼叫頁面和呼叫頁面之間的流程。](./media/structured-navigation-overview/flow-between-calling-page-called-page.png)

<span data-ttu-id="cd89d-125">您可以使用<xref:System.Windows.Navigation.PageFunction%601>做為所呼叫的頁面, 來執行這些行為。</span><span class="sxs-lookup"><span data-stu-id="cd89d-125">You can implement these behaviors by using a <xref:System.Windows.Navigation.PageFunction%601> as the called page.</span></span>

<a name="Structured_Navigation_with_PageFunction"></a>

## <a name="structured-navigation-with-pagefunction"></a><span data-ttu-id="cd89d-126">有 PageFunction 的結構化巡覽</span><span class="sxs-lookup"><span data-stu-id="cd89d-126">Structured Navigation with PageFunction</span></span>

<span data-ttu-id="cd89d-127">本主題說明如何執行涉及單一<xref:System.Windows.Navigation.PageFunction%601>的結構化導覽的基本機制。</span><span class="sxs-lookup"><span data-stu-id="cd89d-127">This topic shows how to implement the basic mechanics of structured navigation involving a single <xref:System.Windows.Navigation.PageFunction%601>.</span></span> <span data-ttu-id="cd89d-128">在此範例中, <xref:System.Windows.Controls.Page>會<xref:System.Windows.Navigation.PageFunction%601>呼叫以從使用者<xref:System.String>取得值, 並將其傳回。</span><span class="sxs-lookup"><span data-stu-id="cd89d-128">In this sample, a <xref:System.Windows.Controls.Page> calls a <xref:System.Windows.Navigation.PageFunction%601> to get a <xref:System.String> value from the user and return it.</span></span>

### <a name="creating-a-calling-page"></a><span data-ttu-id="cd89d-129">建立呼叫端頁面</span><span class="sxs-lookup"><span data-stu-id="cd89d-129">Creating a Calling Page</span></span>

<span data-ttu-id="cd89d-130">呼叫<xref:System.Windows.Navigation.PageFunction%601>的頁面可以<xref:System.Windows.Controls.Page>是或<xref:System.Windows.Navigation.PageFunction%601>。</span><span class="sxs-lookup"><span data-stu-id="cd89d-130">The page that calls a <xref:System.Windows.Navigation.PageFunction%601> can be either a <xref:System.Windows.Controls.Page> or a <xref:System.Windows.Navigation.PageFunction%601>.</span></span> <span data-ttu-id="cd89d-131">在此範例中, 它是<xref:System.Windows.Controls.Page>, 如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="cd89d-131">In this example, it is a <xref:System.Windows.Controls.Page>, as shown in the following code.</span></span>

[!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup1)]
[!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup2)]

[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind1)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind1)]
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind2)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind2)]
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind3)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind3)]

### <a name="creating-a-page-function-to-call"></a><span data-ttu-id="cd89d-132">建立呼叫頁面函式</span><span class="sxs-lookup"><span data-stu-id="cd89d-132">Creating a Page Function to Call</span></span>

<span data-ttu-id="cd89d-133">因為呼叫的頁面可以使用呼叫的頁面來收集並傳回使用者的資料, 所以<xref:System.Windows.Navigation.PageFunction%601>會實作為泛型類別, 其型別引數會指定所呼叫的頁面將傳回的數值型別。</span><span class="sxs-lookup"><span data-stu-id="cd89d-133">Because the calling page can use the called page to collect and return data from the user, <xref:System.Windows.Navigation.PageFunction%601> is implemented as a generic class whose type argument specifies the type of the value that the called page will return.</span></span> <span data-ttu-id="cd89d-134">下列程式碼會使用<xref:System.Windows.Navigation.PageFunction%601>傳回的, <xref:System.String>以顯示呼叫的頁面的初始執行。</span><span class="sxs-lookup"><span data-stu-id="cd89d-134">The following code shows the initial implementation of the called page, using a <xref:System.Windows.Navigation.PageFunction%601>, which returns a <xref:System.String>.</span></span>

[!code-xaml[StructuredNavigationSample#CalledPageFunctionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml#calledpagefunctionmarkup)]

[!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind1)]
[!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind1)]
[!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind2)]
[!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind2)]

<span data-ttu-id="cd89d-135">的宣告類似于的<xref:System.Windows.Controls.Page>宣告, 並加入型別引數。 <xref:System.Windows.Navigation.PageFunction%601></span><span class="sxs-lookup"><span data-stu-id="cd89d-135">The declaration of a <xref:System.Windows.Navigation.PageFunction%601> is similar to the declaration of a <xref:System.Windows.Controls.Page> with the addition of the type arguments.</span></span> <span data-ttu-id="cd89d-136">如您在程式碼範例中所見，使用 `x:TypeArguments` 屬性的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記和使用標準泛型型別引數語法的程式碼後置，兩者都指定型別引數。</span><span class="sxs-lookup"><span data-stu-id="cd89d-136">As you can see from the code example, the type arguments are specified in both [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, using the `x:TypeArguments` attribute, and code-behind, using standard generic type argument syntax.</span></span>

<span data-ttu-id="cd89d-137">您不需要只使用 .NET Framework 類別做為型別引數。</span><span class="sxs-lookup"><span data-stu-id="cd89d-137">You don't have to use only .NET Framework classes as type arguments.</span></span> <span data-ttu-id="cd89d-138"><xref:System.Windows.Navigation.PageFunction%601>可以呼叫來收集抽象為自訂類型的定義域特定資料。</span><span class="sxs-lookup"><span data-stu-id="cd89d-138">A <xref:System.Windows.Navigation.PageFunction%601> could be called to gather domain-specific data that is abstracted as a custom type.</span></span> <span data-ttu-id="cd89d-139">下列程式碼示範如何使用自訂類型做為的型別引數<xref:System.Windows.Navigation.PageFunction%601>。</span><span class="sxs-lookup"><span data-stu-id="cd89d-139">The following code shows how to use a custom type as a type argument for a <xref:System.Windows.Navigation.PageFunction%601>.</span></span>

[!code-csharp[CustomTypePageFunctionSnippets#CustomTypeCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomType.cs#customtypecode1)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypeCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomType.vb#customtypecode1)]
[!code-csharp[CustomTypePageFunctionSnippets#CustomTypeCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomType.cs#customtypecode2)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypeCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomType.vb#customtypecode2)]

[!code-xaml[CustomTypePageFunctionSnippets#CustomTypePageFunctionMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml#customtypepagefunctionmarkup1)]
[!code-xaml[CustomTypePageFunctionSnippets#CustomTypePageFunctionMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml#customtypepagefunctionmarkup2)]

[!code-csharp[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml.cs#customtypepagefunctioncodebehind1)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomTypePageFunction.xaml.vb#customtypepagefunctioncodebehind1)]
[!code-csharp[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml.cs#customtypepagefunctioncodebehind2)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomTypePageFunction.xaml.vb#customtypepagefunctioncodebehind2)]

<span data-ttu-id="cd89d-140">的型別引數<xref:System.Windows.Navigation.PageFunction%601>提供呼叫頁面與所呼叫頁面之間通訊的基礎, 下列各節將討論這些程式。</span><span class="sxs-lookup"><span data-stu-id="cd89d-140">The type arguments for the <xref:System.Windows.Navigation.PageFunction%601> provide the foundation for the communication between a calling page and the called page, which are discussed in the following sections.</span></span>

<span data-ttu-id="cd89d-141">如您所見, 使用<xref:System.Windows.Navigation.PageFunction%601>宣告所識別的類型在將資料<xref:System.Windows.Navigation.PageFunction%601>從傳回至呼叫的頁面時, 扮演著重要的角色。</span><span class="sxs-lookup"><span data-stu-id="cd89d-141">As you'll see, the type that is identified with the declaration of a <xref:System.Windows.Navigation.PageFunction%601> plays an important role in returning data from a <xref:System.Windows.Navigation.PageFunction%601> to the calling page.</span></span>

### <a name="calling-a-pagefunction-and-passing-parameters"></a><span data-ttu-id="cd89d-142">呼叫 PageFunction 並傳遞參數</span><span class="sxs-lookup"><span data-stu-id="cd89d-142">Calling a PageFunction and Passing Parameters</span></span>

<span data-ttu-id="cd89d-143">若要呼叫頁面, 呼叫的頁面必須具現化所呼叫的頁面, 並使用<xref:System.Windows.Navigation.NavigationService.Navigate%2A>方法流覽至該網頁。</span><span class="sxs-lookup"><span data-stu-id="cd89d-143">To call a page, the calling page must instantiate the called page and navigate to it using the <xref:System.Windows.Navigation.NavigationService.Navigate%2A> method.</span></span> <span data-ttu-id="cd89d-144">這可讓呼叫端頁面將初始資料傳遞至呼叫的頁面，例如由呼叫的頁面所收集之資料的預設值。</span><span class="sxs-lookup"><span data-stu-id="cd89d-144">This allows the calling page to pass initial data to the called page, such as default values for the data being gathered by the called page.</span></span>

<span data-ttu-id="cd89d-145">下列程式碼顯示已呼叫的頁面, 其中包含非參數的函式, 可接受來自呼叫端頁面的參數。</span><span class="sxs-lookup"><span data-stu-id="cd89d-145">The following code shows the called page with a non-parameterless constructor to accept parameters from the calling page.</span></span>

[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind1)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind1)]
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind2)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind2)]
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind3)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind3)]
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind4)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind4)]

<span data-ttu-id="cd89d-146">下列程式碼顯示處理<xref:System.Windows.Documents.Hyperlink.Click>的事件<xref:System.Windows.Documents.Hyperlink>的呼叫頁面, 以具現化呼叫的頁面, 並將初始字串值傳遞給它。</span><span class="sxs-lookup"><span data-stu-id="cd89d-146">The following code shows the calling page handling the <xref:System.Windows.Documents.Hyperlink.Click> event of the <xref:System.Windows.Documents.Hyperlink> to instantiate the called page and pass it an initial string value.</span></span>

[!code-xaml[StructuredNavigationSample#PassingDataMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#passingdatamarkup2)]
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind1)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind1)]
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind2)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind2)]
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind3)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind3)]

<span data-ttu-id="cd89d-147">您不需要將參數傳遞給呼叫的頁面。</span><span class="sxs-lookup"><span data-stu-id="cd89d-147">You are not required to pass parameters to the called page.</span></span> <span data-ttu-id="cd89d-148">您反而可以執行下列作業︰</span><span class="sxs-lookup"><span data-stu-id="cd89d-148">Instead, you could do the following:</span></span>

- <span data-ttu-id="cd89d-149">從呼叫端頁面︰</span><span class="sxs-lookup"><span data-stu-id="cd89d-149">From the calling page:</span></span>

  1. <span data-ttu-id="cd89d-150">使用無參數<xref:System.Windows.Navigation.PageFunction%601>的函式將呼叫的具現化。</span><span class="sxs-lookup"><span data-stu-id="cd89d-150">Instantiate the called <xref:System.Windows.Navigation.PageFunction%601> using the parameterless constructor.</span></span>

  2. <span data-ttu-id="cd89d-151">將參數儲存在<xref:System.Windows.Application.Properties%2A>中。</span><span class="sxs-lookup"><span data-stu-id="cd89d-151">Store the parameters in <xref:System.Windows.Application.Properties%2A>.</span></span>

  3. <span data-ttu-id="cd89d-152">流覽至呼叫<xref:System.Windows.Navigation.PageFunction%601>的。</span><span class="sxs-lookup"><span data-stu-id="cd89d-152">Navigate to the called <xref:System.Windows.Navigation.PageFunction%601>.</span></span>

- <span data-ttu-id="cd89d-153">從呼叫<xref:System.Windows.Navigation.PageFunction%601>的:</span><span class="sxs-lookup"><span data-stu-id="cd89d-153">From the called <xref:System.Windows.Navigation.PageFunction%601>:</span></span>

  - <span data-ttu-id="cd89d-154">取出並使用中<xref:System.Windows.Application.Properties%2A>儲存的參數。</span><span class="sxs-lookup"><span data-stu-id="cd89d-154">Retrieve and use the parameters stored in <xref:System.Windows.Application.Properties%2A>.</span></span>

<span data-ttu-id="cd89d-155">但是，您很快就會發現，您還是需要使用程式碼來具現化並巡覽至呼叫的頁面，才能收集呼叫的頁面所傳回的資料。</span><span class="sxs-lookup"><span data-stu-id="cd89d-155">But, as you'll see shortly, you'll still need use code to instantiate and navigate to the called page to collect the data returned by the called page.</span></span> <span data-ttu-id="cd89d-156"><xref:System.Windows.Navigation.PageFunction%601>基於這個理由, 必須保持運作, 否則當您下次流覽<xref:System.Windows.Navigation.PageFunction%601>至時, 會<xref:System.Windows.Navigation.PageFunction%601>使用無參數的[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]函式來具現化。</span><span class="sxs-lookup"><span data-stu-id="cd89d-156">For this reason, the <xref:System.Windows.Navigation.PageFunction%601> needs to be kept alive; otherwise, the next time you navigate to the <xref:System.Windows.Navigation.PageFunction%601>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] instantiates the <xref:System.Windows.Navigation.PageFunction%601> using the parameterless constructor.</span></span>

<span data-ttu-id="cd89d-157">但在呼叫的頁面傳回之前，它需要傳回呼叫端頁面可擷取的資料。</span><span class="sxs-lookup"><span data-stu-id="cd89d-157">Before the called page can return, however, it needs to return data that can be retrieved by the calling page.</span></span>

### <a name="returning-task-result-and-task-data-from-a-task-to-a-calling-page"></a><span data-ttu-id="cd89d-158">將工作的工作結果和工作資料傳回給呼叫端頁面</span><span class="sxs-lookup"><span data-stu-id="cd89d-158">Returning Task Result and Task Data from a Task to a Calling Page</span></span>

<span data-ttu-id="cd89d-159">使用者用完呼叫的頁面時，如本例所示，按 [確定] 或 [取消] 按鈕，必須傳回呼叫的頁面。</span><span class="sxs-lookup"><span data-stu-id="cd89d-159">Once the user has finished using the called page, signified in this example by pressing either the OK or Cancel buttons, the called page needs to return.</span></span> <span data-ttu-id="cd89d-160">因為呼叫端頁面使用了被呼叫頁面來收集使用者資料，所以呼叫端頁面需要兩種類型的資訊︰</span><span class="sxs-lookup"><span data-stu-id="cd89d-160">Since the calling page used the called page to collect data from the user, the calling page requires two types of information:</span></span>

1. <span data-ttu-id="cd89d-161">使用者是否取消了呼叫的頁面 (本例中為按下 [確定] 按鈕或 [取消] 按鈕)。</span><span class="sxs-lookup"><span data-stu-id="cd89d-161">Whether the user canceled the called page (by pressing either the OK button or the Cancel button in this example).</span></span> <span data-ttu-id="cd89d-162">這可讓呼叫端頁面決定是否要處理呼叫端頁面收集的使用者資料。</span><span class="sxs-lookup"><span data-stu-id="cd89d-162">This allows the calling page to determine whether to process the data that the calling page gathered from the user.</span></span>

2. <span data-ttu-id="cd89d-163">使用者提供的資料。</span><span class="sxs-lookup"><span data-stu-id="cd89d-163">The data that was provided by the user.</span></span>

<span data-ttu-id="cd89d-164">若要傳回信息<xref:System.Windows.Navigation.PageFunction%601> , 請<xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>執行方法。</span><span class="sxs-lookup"><span data-stu-id="cd89d-164">To return information, <xref:System.Windows.Navigation.PageFunction%601> implements the <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> method.</span></span> <span data-ttu-id="cd89d-165">下列程式碼示範如何呼叫它。</span><span class="sxs-lookup"><span data-stu-id="cd89d-165">The following code shows how to call it.</span></span>

[!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind1)]
[!code-vb[StructuredNavigationSample#ReturnCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind1)]
[!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind2)]
[!code-vb[StructuredNavigationSample#ReturnCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind2)]

<span data-ttu-id="cd89d-166">在本例中，如果使用者按下 [取消] 按鈕，`null` 值就會傳回呼叫端頁面。</span><span class="sxs-lookup"><span data-stu-id="cd89d-166">In this example, if a user presses the Cancel button, a value of `null` is returned to the calling page.</span></span> <span data-ttu-id="cd89d-167">如果改按下 [確定] 按鈕，則傳回使用者提供的字串值。</span><span class="sxs-lookup"><span data-stu-id="cd89d-167">If the OK button is pressed instead, the string value provided by the user is returned.</span></span> <span data-ttu-id="cd89d-168"><xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>是您呼叫的方法,可將您的資料傳回給呼叫的頁面。`protected virtual`</span><span class="sxs-lookup"><span data-stu-id="cd89d-168"><xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> is a `protected virtual` method that you call to return your data to the calling page.</span></span> <span data-ttu-id="cd89d-169">您的資料必須封裝在泛型<xref:System.Windows.Navigation.ReturnEventArgs%601>型別的實例中, 其型別引數會指定傳回<xref:System.Windows.Navigation.ReturnEventArgs%601.Result%2A>值的型別。</span><span class="sxs-lookup"><span data-stu-id="cd89d-169">Your data needs to be packaged in an instance of the generic <xref:System.Windows.Navigation.ReturnEventArgs%601> type, whose type argument specifies the type of value that <xref:System.Windows.Navigation.ReturnEventArgs%601.Result%2A> returns.</span></span> <span data-ttu-id="cd89d-170">如此一來, 當您宣告具有<xref:System.Windows.Navigation.PageFunction%601>特定類型引數的時, 您會指出<xref:System.Windows.Navigation.PageFunction%601>將會傳回類型引數所指定之類型的實例。</span><span class="sxs-lookup"><span data-stu-id="cd89d-170">In this way, when you declare a <xref:System.Windows.Navigation.PageFunction%601> with a particular type argument, you are stating that a <xref:System.Windows.Navigation.PageFunction%601> will return an instance of the type that is specified by the type argument.</span></span> <span data-ttu-id="cd89d-171">在此範例中, 類型引數和, 因此傳回值的類型<xref:System.String>為。</span><span class="sxs-lookup"><span data-stu-id="cd89d-171">In this example, the type argument and, consequently, the return value is of type <xref:System.String>.</span></span>

<span data-ttu-id="cd89d-172">呼叫<xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>時, 呼叫端頁面需要某種方式來接收的傳回值<xref:System.Windows.Navigation.PageFunction%601>。</span><span class="sxs-lookup"><span data-stu-id="cd89d-172">When <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> is called, the calling page needs some way of receiving the return value of the <xref:System.Windows.Navigation.PageFunction%601>.</span></span> <span data-ttu-id="cd89d-173">基於這個理由, <xref:System.Windows.Navigation.PageFunction%601>會執行<xref:System.Windows.Navigation.PageFunction%601.Return>呼叫要處理之頁面的事件。</span><span class="sxs-lookup"><span data-stu-id="cd89d-173">For this reason, <xref:System.Windows.Navigation.PageFunction%601> implements the <xref:System.Windows.Navigation.PageFunction%601.Return> event for calling pages to handle.</span></span> <span data-ttu-id="cd89d-174">當<xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>呼叫時, <xref:System.Windows.Navigation.PageFunction%601.Return>會引發, 因此<xref:System.Windows.Navigation.PageFunction%601.Return>呼叫的頁面可以向註冊以接收通知。</span><span class="sxs-lookup"><span data-stu-id="cd89d-174">When <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> is called, <xref:System.Windows.Navigation.PageFunction%601.Return> is raised, so the calling page can register with <xref:System.Windows.Navigation.PageFunction%601.Return> to receive the notification.</span></span>

[!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind1)]
[!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind1)]
[!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind2)]
[!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind2)]

### <a name="removing-task-pages-when-a-task-completes"></a><span data-ttu-id="cd89d-175">工作完成時移除工作頁面</span><span class="sxs-lookup"><span data-stu-id="cd89d-175">Removing Task Pages When a Task Completes</span></span>

<span data-ttu-id="cd89d-176">當傳回呼叫的頁面，而使用者未取消呼叫的頁面時，呼叫端頁面會處理使用者提供以及呼叫的頁面所傳回的資料。</span><span class="sxs-lookup"><span data-stu-id="cd89d-176">When a called page returns, and the user didn't cancel the called page, the calling page will process the data that was provided by the user and also returned from the called page.</span></span> <span data-ttu-id="cd89d-177">以此方式擷取的資料通常是獨立的活動。當被呼叫頁面傳回時，呼叫端頁面需要建立並巡覽至新的呼叫端頁面，以擷取更多資料。</span><span class="sxs-lookup"><span data-stu-id="cd89d-177">Data acquisition in this way is usually an isolated activity; when the called page returns, the calling page needs to create and navigate to a new calling page to capture more data.</span></span>

<span data-ttu-id="cd89d-178">不過，除非從日誌移除呼叫的頁面，否則使用者就能夠巡覽回到呼叫端頁面的上一個執行個體。</span><span class="sxs-lookup"><span data-stu-id="cd89d-178">However, unless a called page is removed from the journal, a user will be able to navigate back to a previous instance of the calling page.</span></span> <span data-ttu-id="cd89d-179">是否保留在日誌中是由<xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A>屬性所決定。 <xref:System.Windows.Navigation.PageFunction%601></span><span class="sxs-lookup"><span data-stu-id="cd89d-179">Whether a <xref:System.Windows.Navigation.PageFunction%601> is retained in the journal is determined by the <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> property.</span></span> <span data-ttu-id="cd89d-180">根據預設, 當呼叫時<xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> , 會自動移除頁面函式, 因為<xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A>設定`true`為。</span><span class="sxs-lookup"><span data-stu-id="cd89d-180">By default, a page function is automatically removed when <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> is called because <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> is set to `true`.</span></span> <span data-ttu-id="cd89d-181">若要在呼叫之後<xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> , 將頁面函式保留在導覽歷程記錄中, 請將設定<xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A>為`false`。</span><span class="sxs-lookup"><span data-stu-id="cd89d-181">To keep a page function in navigation history after <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> is called, set <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> to `false`.</span></span>

<a name="Other_Types_of_Structured_Navigation"></a>

## <a name="other-types-of-structured-navigation"></a><span data-ttu-id="cd89d-182">其他類型的結構化巡覽</span><span class="sxs-lookup"><span data-stu-id="cd89d-182">Other Types of Structured Navigation</span></span>

<span data-ttu-id="cd89d-183">本主題說明的最基本用法<xref:System.Windows.Navigation.PageFunction%601> , 以支援呼叫/傳回結構化導覽。</span><span class="sxs-lookup"><span data-stu-id="cd89d-183">This topic illustrates the most basic use of a <xref:System.Windows.Navigation.PageFunction%601> to support call/return structured navigation.</span></span> <span data-ttu-id="cd89d-184">此基礎讓您能夠建立更複雜的結構化巡覽類型。</span><span class="sxs-lookup"><span data-stu-id="cd89d-184">This foundation provides you with the ability to create more complex types of structured navigation.</span></span>

<span data-ttu-id="cd89d-185">例如，呼叫端頁面有時候需要多個頁面來收集足夠的使用者資料，或執行工作。</span><span class="sxs-lookup"><span data-stu-id="cd89d-185">For example, sometimes multiple pages are required by a calling page to gather enough data from a user or to perform a task.</span></span> <span data-ttu-id="cd89d-186">使用多個頁面稱之為「精靈」。</span><span class="sxs-lookup"><span data-stu-id="cd89d-186">The use of multiple pages is referred to as a "wizard".</span></span>

<span data-ttu-id="cd89d-187">在其他情況下，應用程式可能會令相依於結構化巡覽的複雜巡覽拓撲有效運作。</span><span class="sxs-lookup"><span data-stu-id="cd89d-187">In other cases, applications may have complex navigation topologies that depend on structured navigation to operate effectively.</span></span> <span data-ttu-id="cd89d-188">如需詳細資訊，請參閱[巡覽拓撲概觀](navigation-topologies-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="cd89d-188">For more information, see [Navigation Topologies Overview](navigation-topologies-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cd89d-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd89d-189">See also</span></span>

- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [<span data-ttu-id="cd89d-190">巡覽拓撲概觀</span><span class="sxs-lookup"><span data-stu-id="cd89d-190">Navigation Topologies Overview</span></span>](navigation-topologies-overview.md)
