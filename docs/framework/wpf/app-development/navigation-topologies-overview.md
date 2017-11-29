---
title: "巡覽拓撲概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- linear topology [WPF]
- fixed hierarchical topology [WPF]
- fixed linear topology [WPF]
- topologies [WPF]
- navigation topologies [WPF]
- dynamically-generated topology
ms.assetid: 5d5ee837-629a-4933-869a-186dc22ac43d
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d33eb42aded2ad9d6cd32ae5790470fa1b2dc935
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="navigation-topologies-overview"></a><span data-ttu-id="b9549-102">巡覽拓撲概觀</span><span class="sxs-lookup"><span data-stu-id="b9549-102">Navigation Topologies Overview</span></span>
<span data-ttu-id="b9549-103"><a name="introduction"></a>本概觀介紹中瀏覽拓撲[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b9549-103"><a name="introduction"></a> This overview provides an introduction to navigation topologies in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span> <span data-ttu-id="b9549-104">並接著說明三種常見的巡覽拓撲及其範例。</span><span class="sxs-lookup"><span data-stu-id="b9549-104">Three common navigation topologies, with samples, are subsequently discussed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9549-105">閱讀本主題之前，您應該熟悉在結構化之導覽的概念[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]頁面函式的使用。</span><span class="sxs-lookup"><span data-stu-id="b9549-105">Before reading this topic, you should be familiar with the concept of structured navigation in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] using page functions.</span></span> <span data-ttu-id="b9549-106">如需這兩個主題的詳細資訊，請參閱[結構化的巡覽概觀](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b9549-106">For more information on both of these topics, see [Structured Navigation Overview](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md).</span></span>  
  
 <span data-ttu-id="b9549-107">此主題包括下列章節：</span><span class="sxs-lookup"><span data-stu-id="b9549-107">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="b9549-108">巡覽拓撲</span><span class="sxs-lookup"><span data-stu-id="b9549-108">Navigation Topologies</span></span>](#Navigation_Topologies)  
  
-   [<span data-ttu-id="b9549-109">結構化巡覽拓撲</span><span class="sxs-lookup"><span data-stu-id="b9549-109">Structured Navigation Topologies</span></span>](#Structured_Navigation_Topologies)  
  
-   [<span data-ttu-id="b9549-110">透過固定線性拓撲進行巡覽</span><span class="sxs-lookup"><span data-stu-id="b9549-110">Navigation over a Fixed Linear Topology</span></span>](#Navigation_over_a_Fixed_Linear_Topology)  
  
-   [<span data-ttu-id="b9549-111">透過固定的階層式拓撲進行動態巡覽</span><span class="sxs-lookup"><span data-stu-id="b9549-111">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
-   [<span data-ttu-id="b9549-112">透過動態產生的拓撲進行巡覽</span><span class="sxs-lookup"><span data-stu-id="b9549-112">Navigation over a Dynamically Generated Topology</span></span>](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>   
## <a name="navigation-topologies"></a><span data-ttu-id="b9549-113">巡覽拓撲</span><span class="sxs-lookup"><span data-stu-id="b9549-113">Navigation Topologies</span></span>  
 <span data-ttu-id="b9549-114">在[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]，瀏覽通常包含的頁數 (<xref:System.Windows.Controls.Page>) 的超連結 (<xref:System.Windows.Documents.Hyperlink>)，瀏覽至其他頁面，按下時。</span><span class="sxs-lookup"><span data-stu-id="b9549-114">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], navigation typically consists of pages (<xref:System.Windows.Controls.Page>) with hyperlinks (<xref:System.Windows.Documents.Hyperlink>) that navigate to other pages when clicked.</span></span> <span data-ttu-id="b9549-115">瀏覽至的頁面所識別的[!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)](請參閱[WPF 中的組件 Uri](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md))。</span><span class="sxs-lookup"><span data-stu-id="b9549-115">Pages that are navigated to are identified by [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] (see [Pack URIs in WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)).</span></span> <span data-ttu-id="b9549-116">請考慮下列簡單的範例，其中顯示超連結的網頁和[!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="b9549-116">Consider the following simple example that shows pages, hyperlinks, and [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)]:</span></span>  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 <span data-ttu-id="b9549-117">這些頁面會排列在*瀏覽拓撲*其結構取決於如何您在頁面之間巡覽。</span><span class="sxs-lookup"><span data-stu-id="b9549-117">These pages are arranged in a *navigation topology* whose structure is determined by how you can navigate between the pages.</span></span> <span data-ttu-id="b9549-118">這種特定巡覽拓撲適合簡單的案例，不過巡覽可能需要更複雜的拓撲，其中有些只能在應用程式執行時定義。</span><span class="sxs-lookup"><span data-stu-id="b9549-118">This particular navigation topology is suitable in simple scenarios, although navigation can require more complex topologies, some of which can only be defined when an application is running.</span></span>  
  
 <span data-ttu-id="b9549-119">本主題涵蓋三種常見的巡覽拓撲：*固定線性*，*固定階層式*，和*動態產生*。</span><span class="sxs-lookup"><span data-stu-id="b9549-119">This topic covers three common navigation topologies: *fixed linear*, *fixed hierarchical*, and *dynamically generated*.</span></span> <span data-ttu-id="b9549-120">以具有範例示範每個瀏覽拓撲[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]類似下圖所示：</span><span class="sxs-lookup"><span data-stu-id="b9549-120">Each navigation topology is demonstrated with a sample that has a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] like the one that is shown in the following figure:</span></span>  
  
 <span data-ttu-id="b9549-121">![具有資料項目的工作頁面](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure6.png "NavigationTopologyFigure6")</span><span class="sxs-lookup"><span data-stu-id="b9549-121">![Task pages with data items](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure6.png "NavigationTopologyFigure6")</span></span>  
  
<a name="Structured_Navigation_Topologies"></a>   
## <a name="structured-navigation-topologies"></a><span data-ttu-id="b9549-122">結構化巡覽拓撲</span><span class="sxs-lookup"><span data-stu-id="b9549-122">Structured Navigation Topologies</span></span>  
 <span data-ttu-id="b9549-123">巡覽拓撲有下列兩種廣泛的類型：</span><span class="sxs-lookup"><span data-stu-id="b9549-123">There are two broad types of navigation topologies:</span></span>  
  
-   <span data-ttu-id="b9549-124">**固定拓撲**：在編譯時期定義，且不會在執行階段變更。</span><span class="sxs-lookup"><span data-stu-id="b9549-124">**Fixed Topology**: defined at compile time and does not change at run time.</span></span> <span data-ttu-id="b9549-125">固定拓撲適用於以線性或階層式順序的固定順序來瀏覽頁面。</span><span class="sxs-lookup"><span data-stu-id="b9549-125">Fixed topologies are useful for navigation through a fixed sequence of pages in either a linear or hierarchical order.</span></span>  
  
-   <span data-ttu-id="b9549-126">**動態拓撲**：根據從使用者、應用程式，或系統收集而得的輸入，在執行階段定義。</span><span class="sxs-lookup"><span data-stu-id="b9549-126">**Dynamic Topology**: defined at run time based on input that is collected from the user, the application, or the system.</span></span> <span data-ttu-id="b9549-127">如果要以不同的順序瀏覽頁面，動態拓撲就十分實用。</span><span class="sxs-lookup"><span data-stu-id="b9549-127">Dynamic topologies are useful when pages can be navigated in different sequences.</span></span>  
  
 <span data-ttu-id="b9549-128">雖然您可以使用頁面來建立巡覽拓撲，但本範例會使用頁面函式來提供額外的支援，藉此簡化透過拓撲頁面傳遞和傳回資料的支援。</span><span class="sxs-lookup"><span data-stu-id="b9549-128">Although it is possible to create navigation topologies using pages, the samples use page functions because they provide additional support that simplifies support for passing and returning data through the pages of a topology.</span></span>  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>   
## <a name="navigation-over-a-fixed-linear-topology"></a><span data-ttu-id="b9549-129">透過固定線性拓撲進行巡覽</span><span class="sxs-lookup"><span data-stu-id="b9549-129">Navigation over a Fixed Linear Topology</span></span>  
 <span data-ttu-id="b9549-130">固定線性拓撲類似於含有一個或多個精靈頁面，並以固定順序巡覽的精靈結構。</span><span class="sxs-lookup"><span data-stu-id="b9549-130">A fixed linear topology is analogous to the structure of a wizard that has one or more wizard pages that are navigated in a fixed sequence.</span></span> <span data-ttu-id="b9549-131">下圖顯示具有固定線性拓撲的精靈的高階結構與流程。</span><span class="sxs-lookup"><span data-stu-id="b9549-131">The following figure shows the high-level structure and flow of a wizard with a fixed linear topology.</span></span>  
  
 <span data-ttu-id="b9549-132">![巡覽拓撲圖表](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure1.png "NavigationTopologyFigure1")</span><span class="sxs-lookup"><span data-stu-id="b9549-132">![Navigation topology diagram](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure1.png "NavigationTopologyFigure1")</span></span>  
  
 <span data-ttu-id="b9549-133">透過固定線性拓撲進行巡覽的一般行為包括以下：</span><span class="sxs-lookup"><span data-stu-id="b9549-133">The typical behaviors for navigating over a fixed linear topology include the following:</span></span>  
  
-   <span data-ttu-id="b9549-134">從呼叫頁面巡覽至啟動器頁面，其可初始化精靈，並巡覽至精靈的第一頁。</span><span class="sxs-lookup"><span data-stu-id="b9549-134">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="b9549-135">啟動器頁面 ( [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-小於<xref:System.Windows.Navigation.PageFunction%601>) 不是必要項目，因為呼叫頁面可以直接呼叫第一個精靈頁面。</span><span class="sxs-lookup"><span data-stu-id="b9549-135">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="b9549-136">不過，如果精靈的初始化作業特別複雜，則可以使用啟動程式頁面來簡化這項作業。</span><span class="sxs-lookup"><span data-stu-id="b9549-136">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
-   <span data-ttu-id="b9549-137">使用者可以利用 [向後] 和 [向前] 按鈕 (或超連結)，在頁面之間巡覽。</span><span class="sxs-lookup"><span data-stu-id="b9549-137">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
-   <span data-ttu-id="b9549-138">使用者可以利用日誌，在頁面之間巡覽。</span><span class="sxs-lookup"><span data-stu-id="b9549-138">Users can navigate between pages using the journal.</span></span>  
  
-   <span data-ttu-id="b9549-139">使用者可以按 [取消] 按鈕，取消任何精靈頁面中的精靈。</span><span class="sxs-lookup"><span data-stu-id="b9549-139">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
-   <span data-ttu-id="b9549-140">使用者可以按 [結束] 按鈕，接受最後一個精靈頁面中的精靈。</span><span class="sxs-lookup"><span data-stu-id="b9549-140">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
-   <span data-ttu-id="b9549-141">如果取消精靈，精靈會傳回適當的結果，但不會傳回任何資料。</span><span class="sxs-lookup"><span data-stu-id="b9549-141">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
-   <span data-ttu-id="b9549-142">如果使用者接受精靈，精靈會傳回適當的結果，並傳回它所收集的資料。</span><span class="sxs-lookup"><span data-stu-id="b9549-142">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
-   <span data-ttu-id="b9549-143">完成精靈時 (已接受或取消)，即會從日誌中移除精靈所含的頁面。</span><span class="sxs-lookup"><span data-stu-id="b9549-143">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="b9549-144">這可將精靈的每個執行個體隔離，以避免潛在的資料或狀態異常。</span><span class="sxs-lookup"><span data-stu-id="b9549-144">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>   
## <a name="dynamic-navigation-over-a-fixed-hierarchical-topology"></a><span data-ttu-id="b9549-145">透過固定的階層式拓撲進行動態巡覽</span><span class="sxs-lookup"><span data-stu-id="b9549-145">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>  
 <span data-ttu-id="b9549-146">在某些應用程式中，頁面可以巡覽至兩個以上的其他頁面，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="b9549-146">In some applications, pages allow navigation to two or more other pages, as shown in the following figure.</span></span>  
  
 <span data-ttu-id="b9549-147">![可巡覽至多個頁面的頁面](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure2.png "NavigationTopologyFigure2")</span><span class="sxs-lookup"><span data-stu-id="b9549-147">![A page that can navigate to multiple pages](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure2.png "NavigationTopologyFigure2")</span></span>  
  
 <span data-ttu-id="b9549-148">這個結構稱為固定的階層式拓撲，而周遊階層的順序通常是在執行階段由應用程式或使用者決定。</span><span class="sxs-lookup"><span data-stu-id="b9549-148">This structure is known as a fixed hierarchical topology, and the sequence in which the hierarchy is traversed is often determined at run time by either the application or the user.</span></span> <span data-ttu-id="b9549-149">階層中每個可巡覽至兩個以上其他頁面的頁面，皆會在執行階段收集必要資料以判斷可巡覽至哪些頁面。</span><span class="sxs-lookup"><span data-stu-id="b9549-149">At run time, each page in the hierarchy that allows navigation to two or more other pages gathers the data required to determine which page to navigate to.</span></span> <span data-ttu-id="b9549-150">下圖擇一說明上圖可能的巡覽順序。</span><span class="sxs-lookup"><span data-stu-id="b9549-150">The following figure illustrates one of several possible navigation sequences based on the previous figure.</span></span>  
  
 <span data-ttu-id="b9549-151">![巡覽拓撲圖表](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure3.png "NavigationTopologyFigure3")</span><span class="sxs-lookup"><span data-stu-id="b9549-151">![Navigation topology diagram](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure3.png "NavigationTopologyFigure3")</span></span>  
  
 <span data-ttu-id="b9549-152">雖然固定階層式結構中的頁面巡覽順序是在執行階段決定，但使用者體驗仍和固定線性拓撲的使用者體驗相同：</span><span class="sxs-lookup"><span data-stu-id="b9549-152">Even though the sequence in which pages in a fixed hierarchical structure are navigated is determined at run time, the user experience is the same as the user experience for a fixed linear topology:</span></span>  
  
-   <span data-ttu-id="b9549-153">從呼叫頁面巡覽至啟動器頁面，其可初始化精靈，並巡覽至精靈的第一頁。</span><span class="sxs-lookup"><span data-stu-id="b9549-153">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="b9549-154">啟動器頁面 ( [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-小於<xref:System.Windows.Navigation.PageFunction%601>) 不是必要項目，因為呼叫頁面可以直接呼叫第一個精靈頁面。</span><span class="sxs-lookup"><span data-stu-id="b9549-154">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="b9549-155">不過，如果精靈的初始化作業特別複雜，則可以使用啟動程式頁面來簡化這項作業。</span><span class="sxs-lookup"><span data-stu-id="b9549-155">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
-   <span data-ttu-id="b9549-156">使用者可以利用 [向後] 和 [向前] 按鈕 (或超連結)，在頁面之間巡覽。</span><span class="sxs-lookup"><span data-stu-id="b9549-156">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
-   <span data-ttu-id="b9549-157">使用者可以利用日誌，在頁面之間巡覽。</span><span class="sxs-lookup"><span data-stu-id="b9549-157">Users can navigate between pages using the journal.</span></span>  
  
-   <span data-ttu-id="b9549-158">如果使用者向後巡覽日誌，即可變更巡覽順序。</span><span class="sxs-lookup"><span data-stu-id="b9549-158">Users can change the navigation sequence if they navigate back through the journal.</span></span>  
  
-   <span data-ttu-id="b9549-159">使用者可以按 [取消] 按鈕，取消任何精靈頁面中的精靈。</span><span class="sxs-lookup"><span data-stu-id="b9549-159">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
-   <span data-ttu-id="b9549-160">使用者可以按 [結束] 按鈕，接受最後一個精靈頁面中的精靈。</span><span class="sxs-lookup"><span data-stu-id="b9549-160">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
-   <span data-ttu-id="b9549-161">如果取消精靈，精靈會傳回適當的結果，但不會傳回任何資料。</span><span class="sxs-lookup"><span data-stu-id="b9549-161">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
-   <span data-ttu-id="b9549-162">如果使用者接受精靈，精靈會傳回適當的結果，並傳回它所收集的資料。</span><span class="sxs-lookup"><span data-stu-id="b9549-162">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
-   <span data-ttu-id="b9549-163">完成精靈時 (已接受或取消)，即會從日誌中移除精靈所含的頁面。</span><span class="sxs-lookup"><span data-stu-id="b9549-163">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="b9549-164">這可將精靈的每個執行個體隔離，以避免潛在的資料或狀態異常。</span><span class="sxs-lookup"><span data-stu-id="b9549-164">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>   
## <a name="navigation-over-a-dynamically-generated-topology"></a><span data-ttu-id="b9549-165">透過動態產生的拓撲進行巡覽</span><span class="sxs-lookup"><span data-stu-id="b9549-165">Navigation over a Dynamically Generated Topology</span></span>  
 <span data-ttu-id="b9549-166">在某些應用程式中，兩個以上頁面的巡覽順序只能在執行階段由使用者、應用程式或外部資料決定。</span><span class="sxs-lookup"><span data-stu-id="b9549-166">In some applications, the sequence in which two or more pages are navigated can only be determined at run time, whether by the user, the application, or external data.</span></span> <span data-ttu-id="b9549-167">下圖說明尚未決定巡覽順序的一組頁面。</span><span class="sxs-lookup"><span data-stu-id="b9549-167">The following figure illustrates a set of pages with an undetermined navigation sequence.</span></span>  
  
 <span data-ttu-id="b9549-168">![巡覽拓撲圖表](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure4.png "NavigationTopologyFigure4")</span><span class="sxs-lookup"><span data-stu-id="b9549-168">![Navigation topology diagram](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure4.png "NavigationTopologyFigure4")</span></span>  
  
 <span data-ttu-id="b9549-169">下圖說明已在執行階段由使用者選擇的巡覽順序。</span><span class="sxs-lookup"><span data-stu-id="b9549-169">The next figure illustrates a navigation sequence that was chosen by the user at run time.</span></span>  
  
 <span data-ttu-id="b9549-170">![巡覽圖表](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure5.png "NavigationTopologyFigure5")</span><span class="sxs-lookup"><span data-stu-id="b9549-170">![Navigation diagram](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure5.png "NavigationTopologyFigure5")</span></span>  
  
 <span data-ttu-id="b9549-171">巡覽順序也稱為動態產生的拓撲。</span><span class="sxs-lookup"><span data-stu-id="b9549-171">The navigation sequence is known as a dynamically generated topology.</span></span> <span data-ttu-id="b9549-172">對使用者來說，即使使用另一種巡覽拓撲，其使用者體驗和上一個拓撲是一樣的：</span><span class="sxs-lookup"><span data-stu-id="b9549-172">For the user, as with the other navigation topologies, the user experience is the same as it is for the previous topologies:</span></span>  
  
-   <span data-ttu-id="b9549-173">從呼叫頁面巡覽至啟動器頁面，其可初始化精靈，並巡覽至精靈的第一頁。</span><span class="sxs-lookup"><span data-stu-id="b9549-173">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="b9549-174">啟動器頁面 ( [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-小於<xref:System.Windows.Navigation.PageFunction%601>) 不是必要項目，因為呼叫頁面可以直接呼叫第一個精靈頁面。</span><span class="sxs-lookup"><span data-stu-id="b9549-174">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="b9549-175">不過，如果精靈的初始化作業特別複雜，則可以使用啟動程式頁面來簡化這項作業。</span><span class="sxs-lookup"><span data-stu-id="b9549-175">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
-   <span data-ttu-id="b9549-176">使用者可以利用 [向後] 和 [向前] 按鈕 (或超連結)，在頁面之間巡覽。</span><span class="sxs-lookup"><span data-stu-id="b9549-176">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
-   <span data-ttu-id="b9549-177">使用者可以利用日誌，在頁面之間巡覽。</span><span class="sxs-lookup"><span data-stu-id="b9549-177">Users can navigate between pages using the journal.</span></span>  
  
-   <span data-ttu-id="b9549-178">使用者可以按 [取消] 按鈕，取消任何精靈頁面中的精靈。</span><span class="sxs-lookup"><span data-stu-id="b9549-178">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
-   <span data-ttu-id="b9549-179">使用者可以按 [結束] 按鈕，接受最後一個精靈頁面中的精靈。</span><span class="sxs-lookup"><span data-stu-id="b9549-179">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
-   <span data-ttu-id="b9549-180">如果取消精靈，精靈會傳回適當的結果，但不會傳回任何資料。</span><span class="sxs-lookup"><span data-stu-id="b9549-180">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
-   <span data-ttu-id="b9549-181">如果使用者接受精靈，精靈會傳回適當的結果，並傳回它所收集的資料。</span><span class="sxs-lookup"><span data-stu-id="b9549-181">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
-   <span data-ttu-id="b9549-182">完成精靈時 (已接受或取消)，即會從日誌中移除精靈所含的頁面。</span><span class="sxs-lookup"><span data-stu-id="b9549-182">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="b9549-183">這可將精靈的每個執行個體隔離，以避免潛在的資料或狀態異常。</span><span class="sxs-lookup"><span data-stu-id="b9549-183">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9549-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9549-184">See Also</span></span>  
 <xref:System.Windows.Controls.Page>  
 <xref:System.Windows.Navigation.PageFunction%601>  
 <xref:System.Windows.Navigation.NavigationService>  
 [<span data-ttu-id="b9549-185">結構化巡覽概觀</span><span class="sxs-lookup"><span data-stu-id="b9549-185">Structured Navigation Overview</span></span>](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md)
