---
title: 巡覽拓撲概觀
ms.date: 03/30/2017
helpviewer_keywords:
- linear topology [WPF]
- fixed hierarchical topology [WPF]
- fixed linear topology [WPF]
- topologies [WPF]
- navigation topologies [WPF]
- dynamically-generated topology
ms.assetid: 5d5ee837-629a-4933-869a-186dc22ac43d
ms.openlocfilehash: 08f6342095706e5ffe9479f5236457d21474152a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174195"
---
# <a name="navigation-topologies-overview"></a><span data-ttu-id="c1e21-102">巡覽拓撲概觀</span><span class="sxs-lookup"><span data-stu-id="c1e21-102">Navigation Topologies Overview</span></span>
<a name="introduction"></a><span data-ttu-id="c1e21-103">本概述介紹了 WPF 中的導航拓撲。</span><span class="sxs-lookup"><span data-stu-id="c1e21-103">This overview provides an introduction to navigation topologies in WPF.</span></span> <span data-ttu-id="c1e21-104">並接著說明三種常見的巡覽拓撲及其範例。</span><span class="sxs-lookup"><span data-stu-id="c1e21-104">Three common navigation topologies, with samples, are subsequently discussed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c1e21-105">在閱讀本主題之前，您應該熟悉使用頁面函數在 WPF 中進行結構化導航的概念。</span><span class="sxs-lookup"><span data-stu-id="c1e21-105">Before reading this topic, you should be familiar with the concept of structured navigation in WPF using page functions.</span></span> <span data-ttu-id="c1e21-106">有關這兩個主題的詳細資訊，請參閱[結構化導航概述](structured-navigation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="c1e21-106">For more information on both of these topics, see [Structured Navigation Overview](structured-navigation-overview.md).</span></span>  
  
 <span data-ttu-id="c1e21-107">本主題包含下列幾節：</span><span class="sxs-lookup"><span data-stu-id="c1e21-107">This topic contains the following sections:</span></span>  
  
- [<span data-ttu-id="c1e21-108">巡覽拓撲</span><span class="sxs-lookup"><span data-stu-id="c1e21-108">Navigation Topologies</span></span>](#Navigation_Topologies)  
  
- [<span data-ttu-id="c1e21-109">結構化巡覽拓撲</span><span class="sxs-lookup"><span data-stu-id="c1e21-109">Structured Navigation Topologies</span></span>](#Structured_Navigation_Topologies)  
  
- [<span data-ttu-id="c1e21-110">透過固定線性拓撲進行巡覽</span><span class="sxs-lookup"><span data-stu-id="c1e21-110">Navigation over a Fixed Linear Topology</span></span>](#Navigation_over_a_Fixed_Linear_Topology)  
  
- [<span data-ttu-id="c1e21-111">透過固定的階層式拓撲進行動態巡覽</span><span class="sxs-lookup"><span data-stu-id="c1e21-111">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
- [<span data-ttu-id="c1e21-112">透過動態產生的拓撲進行巡覽</span><span class="sxs-lookup"><span data-stu-id="c1e21-112">Navigation over a Dynamically Generated Topology</span></span>](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>
## <a name="navigation-topologies"></a><span data-ttu-id="c1e21-113">巡覽拓撲</span><span class="sxs-lookup"><span data-stu-id="c1e21-113">Navigation Topologies</span></span>  
 <span data-ttu-id="c1e21-114">在 WPF 中，導航通常由<xref:System.Windows.Controls.Page>具有超連結 （<xref:System.Windows.Documents.Hyperlink>） 的頁面組成，這些頁面在按一下時導航到其他頁面。</span><span class="sxs-lookup"><span data-stu-id="c1e21-114">In WPF, navigation typically consists of pages (<xref:System.Windows.Controls.Page>) with hyperlinks (<xref:System.Windows.Documents.Hyperlink>) that navigate to other pages when clicked.</span></span> <span data-ttu-id="c1e21-115">導航到的頁面由統一的資源識別碼 （URI） 標識（請參閱[WPF 中的 Pack URI）。](pack-uris-in-wpf.md)</span><span class="sxs-lookup"><span data-stu-id="c1e21-115">Pages that are navigated to are identified by uniform resource identifiers (URIs) (see [Pack URIs in WPF](pack-uris-in-wpf.md)).</span></span> <span data-ttu-id="c1e21-116">請考慮以下顯示頁面、超連結和統一資源識別項 （URI） 的簡單示例：</span><span class="sxs-lookup"><span data-stu-id="c1e21-116">Consider the following simple example that shows pages, hyperlinks, and uniform resource identifiers (URIs):</span></span>  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 <span data-ttu-id="c1e21-117">這些頁面排列在*導航拓撲*中，其結構取決於如何在頁面之間導航。</span><span class="sxs-lookup"><span data-stu-id="c1e21-117">These pages are arranged in a *navigation topology* whose structure is determined by how you can navigate between the pages.</span></span> <span data-ttu-id="c1e21-118">這種特定巡覽拓撲適合簡單的案例，不過巡覽可能需要更複雜的拓撲，其中有些只能在應用程式執行時定義。</span><span class="sxs-lookup"><span data-stu-id="c1e21-118">This particular navigation topology is suitable in simple scenarios, although navigation can require more complex topologies, some of which can only be defined when an application is running.</span></span>  
  
 <span data-ttu-id="c1e21-119">本主題涵蓋三種常見的導航拓撲：*固定線性*、*固定分層*和*動態生成*。</span><span class="sxs-lookup"><span data-stu-id="c1e21-119">This topic covers three common navigation topologies: *fixed linear*, *fixed hierarchical*, and *dynamically generated*.</span></span> <span data-ttu-id="c1e21-120">每個導航拓撲都使用示例進行演示，該示例具有[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]下圖所示的示例：</span><span class="sxs-lookup"><span data-stu-id="c1e21-120">Each navigation topology is demonstrated with a sample that has a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] like the one that is shown in the following figure:</span></span>  
  
 ![包含資料項目和導覽按鈕的任務頁。](./media/navigation-topologies-overview/navigation-topology-data-items.png)  
  
<a name="Structured_Navigation_Topologies"></a>
## <a name="structured-navigation-topologies"></a><span data-ttu-id="c1e21-122">結構化巡覽拓撲</span><span class="sxs-lookup"><span data-stu-id="c1e21-122">Structured Navigation Topologies</span></span>  
 <span data-ttu-id="c1e21-123">巡覽拓撲有下列兩種廣泛的類型：</span><span class="sxs-lookup"><span data-stu-id="c1e21-123">There are two broad types of navigation topologies:</span></span>  
  
- <span data-ttu-id="c1e21-124">**固定拓撲**：在編譯時期定義，且不會在執行階段變更。</span><span class="sxs-lookup"><span data-stu-id="c1e21-124">**Fixed Topology**: defined at compile time and does not change at run time.</span></span> <span data-ttu-id="c1e21-125">固定拓撲適用於以線性或階層式順序的固定順序來瀏覽頁面。</span><span class="sxs-lookup"><span data-stu-id="c1e21-125">Fixed topologies are useful for navigation through a fixed sequence of pages in either a linear or hierarchical order.</span></span>  
  
- <span data-ttu-id="c1e21-126">**動態拓撲**：根據從使用者、應用程式，或系統收集而得的輸入，在執行階段定義。</span><span class="sxs-lookup"><span data-stu-id="c1e21-126">**Dynamic Topology**: defined at run time based on input that is collected from the user, the application, or the system.</span></span> <span data-ttu-id="c1e21-127">如果要以不同的順序瀏覽頁面，動態拓撲就十分實用。</span><span class="sxs-lookup"><span data-stu-id="c1e21-127">Dynamic topologies are useful when pages can be navigated in different sequences.</span></span>  
  
 <span data-ttu-id="c1e21-128">雖然您可以使用頁面來建立巡覽拓撲，但本範例會使用頁面函式來提供額外的支援，藉此簡化透過拓撲頁面傳遞和傳回資料的支援。</span><span class="sxs-lookup"><span data-stu-id="c1e21-128">Although it is possible to create navigation topologies using pages, the samples use page functions because they provide additional support that simplifies support for passing and returning data through the pages of a topology.</span></span>  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>
## <a name="navigation-over-a-fixed-linear-topology"></a><span data-ttu-id="c1e21-129">透過固定線性拓撲進行巡覽</span><span class="sxs-lookup"><span data-stu-id="c1e21-129">Navigation over a Fixed Linear Topology</span></span>  
 <span data-ttu-id="c1e21-130">固定線性拓撲類似於含有一個或多個精靈頁面，並以固定順序巡覽的精靈結構。</span><span class="sxs-lookup"><span data-stu-id="c1e21-130">A fixed linear topology is analogous to the structure of a wizard that has one or more wizard pages that are navigated in a fixed sequence.</span></span> <span data-ttu-id="c1e21-131">下圖顯示了具有固定線性拓撲的嚮導的高級結構和流程：</span><span class="sxs-lookup"><span data-stu-id="c1e21-131">The following figure shows the high-level structure and flow of a wizard with a fixed linear topology:</span></span>  
  
 ![顯示固定線性拓撲的圖表。](./media/navigation-topologies-overview/navigation-topology-fixed-linear.png)  
  
 <span data-ttu-id="c1e21-133">透過固定線性拓撲進行巡覽的一般行為包括以下：</span><span class="sxs-lookup"><span data-stu-id="c1e21-133">The typical behaviors for navigating over a fixed linear topology include the following:</span></span>  
  
- <span data-ttu-id="c1e21-134">從呼叫頁面巡覽至啟動器頁面，其可初始化精靈，並巡覽至精靈的第一頁。</span><span class="sxs-lookup"><span data-stu-id="c1e21-134">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="c1e21-135">啟動器頁 （[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]無<xref:System.Windows.Navigation.PageFunction%601>-） 不是必需的，因為調用頁可以直接調用第一個嚮導頁。</span><span class="sxs-lookup"><span data-stu-id="c1e21-135">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="c1e21-136">不過，如果精靈的初始化作業特別複雜，則可以使用啟動程式頁面來簡化這項作業。</span><span class="sxs-lookup"><span data-stu-id="c1e21-136">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
- <span data-ttu-id="c1e21-137">使用者可以利用 [向後] 和 [向前] 按鈕 (或超連結)，在頁面之間巡覽。</span><span class="sxs-lookup"><span data-stu-id="c1e21-137">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
- <span data-ttu-id="c1e21-138">使用者可以利用日誌，在頁面之間巡覽。</span><span class="sxs-lookup"><span data-stu-id="c1e21-138">Users can navigate between pages using the journal.</span></span>  
  
- <span data-ttu-id="c1e21-139">使用者可以按 [取消] 按鈕，取消任何精靈頁面中的精靈。</span><span class="sxs-lookup"><span data-stu-id="c1e21-139">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
- <span data-ttu-id="c1e21-140">使用者可以按 [結束] 按鈕，接受最後一個精靈頁面中的精靈。</span><span class="sxs-lookup"><span data-stu-id="c1e21-140">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
- <span data-ttu-id="c1e21-141">如果取消精靈，精靈會傳回適當的結果，但不會傳回任何資料。</span><span class="sxs-lookup"><span data-stu-id="c1e21-141">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
- <span data-ttu-id="c1e21-142">如果使用者接受精靈，精靈會傳回適當的結果，並傳回它所收集的資料。</span><span class="sxs-lookup"><span data-stu-id="c1e21-142">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
- <span data-ttu-id="c1e21-143">完成精靈時 (已接受或取消)，即會從日誌中移除精靈所含的頁面。</span><span class="sxs-lookup"><span data-stu-id="c1e21-143">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="c1e21-144">這可將精靈的每個執行個體隔離，以避免潛在的資料或狀態異常。</span><span class="sxs-lookup"><span data-stu-id="c1e21-144">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>
## <a name="dynamic-navigation-over-a-fixed-hierarchical-topology"></a><span data-ttu-id="c1e21-145">透過固定的階層式拓撲進行動態巡覽</span><span class="sxs-lookup"><span data-stu-id="c1e21-145">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>  
 <span data-ttu-id="c1e21-146">在某些應用程式中，頁面允許導航到兩個或多個其他頁面，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="c1e21-146">In some applications, pages allow navigation to two or more other pages, as shown in the following figure:</span></span>
  
 ![顯示可導航到多個頁面的頁面的圖表。](./media/navigation-topologies-overview/navigation-topology-multiple-pages.png)  
  
 <span data-ttu-id="c1e21-148">這個結構稱為固定的階層式拓撲，而周遊階層的順序通常是在執行階段由應用程式或使用者決定。</span><span class="sxs-lookup"><span data-stu-id="c1e21-148">This structure is known as a fixed hierarchical topology, and the sequence in which the hierarchy is traversed is often determined at run time by either the application or the user.</span></span> <span data-ttu-id="c1e21-149">階層中每個可巡覽至兩個以上其他頁面的頁面，皆會在執行階段收集必要資料以判斷可巡覽至哪些頁面。</span><span class="sxs-lookup"><span data-stu-id="c1e21-149">At run time, each page in the hierarchy that allows navigation to two or more other pages gathers the data required to determine which page to navigate to.</span></span> <span data-ttu-id="c1e21-150">下圖說明瞭基於上圖的幾種可能的導航序列之一：</span><span class="sxs-lookup"><span data-stu-id="c1e21-150">The following figure illustrates one of several possible navigation sequences based on the previous figure:</span></span>  
  
 ![顯示可能的導航序列的圖表。](./media/navigation-topologies-overview/navigation-topology-fixed-hierarchical.png)  
  
 <span data-ttu-id="c1e21-152">雖然固定階層式結構中的頁面巡覽順序是在執行階段決定，但使用者體驗仍和固定線性拓撲的使用者體驗相同：</span><span class="sxs-lookup"><span data-stu-id="c1e21-152">Even though the sequence in which pages in a fixed hierarchical structure are navigated is determined at run time, the user experience is the same as the user experience for a fixed linear topology:</span></span>  
  
- <span data-ttu-id="c1e21-153">從呼叫頁面巡覽至啟動器頁面，其可初始化精靈，並巡覽至精靈的第一頁。</span><span class="sxs-lookup"><span data-stu-id="c1e21-153">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="c1e21-154">啟動器頁 （[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]無<xref:System.Windows.Navigation.PageFunction%601>-） 不是必需的，因為調用頁可以直接調用第一個嚮導頁。</span><span class="sxs-lookup"><span data-stu-id="c1e21-154">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="c1e21-155">不過，如果精靈的初始化作業特別複雜，則可以使用啟動程式頁面來簡化這項作業。</span><span class="sxs-lookup"><span data-stu-id="c1e21-155">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
- <span data-ttu-id="c1e21-156">使用者可以利用 [向後] 和 [向前] 按鈕 (或超連結)，在頁面之間巡覽。</span><span class="sxs-lookup"><span data-stu-id="c1e21-156">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
- <span data-ttu-id="c1e21-157">使用者可以利用日誌，在頁面之間巡覽。</span><span class="sxs-lookup"><span data-stu-id="c1e21-157">Users can navigate between pages using the journal.</span></span>  
  
- <span data-ttu-id="c1e21-158">如果使用者向後巡覽日誌，即可變更巡覽順序。</span><span class="sxs-lookup"><span data-stu-id="c1e21-158">Users can change the navigation sequence if they navigate back through the journal.</span></span>  
  
- <span data-ttu-id="c1e21-159">使用者可以按 [取消] 按鈕，取消任何精靈頁面中的精靈。</span><span class="sxs-lookup"><span data-stu-id="c1e21-159">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
- <span data-ttu-id="c1e21-160">使用者可以按 [結束] 按鈕，接受最後一個精靈頁面中的精靈。</span><span class="sxs-lookup"><span data-stu-id="c1e21-160">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
- <span data-ttu-id="c1e21-161">如果取消精靈，精靈會傳回適當的結果，但不會傳回任何資料。</span><span class="sxs-lookup"><span data-stu-id="c1e21-161">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
- <span data-ttu-id="c1e21-162">如果使用者接受精靈，精靈會傳回適當的結果，並傳回它所收集的資料。</span><span class="sxs-lookup"><span data-stu-id="c1e21-162">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
- <span data-ttu-id="c1e21-163">完成精靈時 (已接受或取消)，即會從日誌中移除精靈所含的頁面。</span><span class="sxs-lookup"><span data-stu-id="c1e21-163">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="c1e21-164">這可將精靈的每個執行個體隔離，以避免潛在的資料或狀態異常。</span><span class="sxs-lookup"><span data-stu-id="c1e21-164">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>
## <a name="navigation-over-a-dynamically-generated-topology"></a><span data-ttu-id="c1e21-165">透過動態產生的拓撲進行巡覽</span><span class="sxs-lookup"><span data-stu-id="c1e21-165">Navigation over a Dynamically Generated Topology</span></span>  
 <span data-ttu-id="c1e21-166">在某些應用程式中，兩個以上頁面的巡覽順序只能在執行階段由使用者、應用程式或外部資料決定。</span><span class="sxs-lookup"><span data-stu-id="c1e21-166">In some applications, the sequence in which two or more pages are navigated can only be determined at run time, whether by the user, the application, or external data.</span></span> <span data-ttu-id="c1e21-167">下圖說明瞭一組具有不確定導航序列的頁面：</span><span class="sxs-lookup"><span data-stu-id="c1e21-167">The following figure illustrates a set of pages with an undetermined navigation sequence:</span></span>  
  
 ![具有不確定導航序列的一組頁面。](./media/navigation-topologies-overview/navigation-topology-dynamically-generated.png)  
  
 <span data-ttu-id="c1e21-169">下圖顯示了使用者在運行時選擇的導航序列：</span><span class="sxs-lookup"><span data-stu-id="c1e21-169">The next figure illustrates a navigation sequence that was chosen by the user at run time:</span></span>  
  
 ![顯示運行時選擇的導航序列的圖表。](./media/navigation-topologies-overview/navigation-topology-sequence-chosen-run-time.png)  
  
 <span data-ttu-id="c1e21-171">巡覽順序也稱為動態產生的拓撲。</span><span class="sxs-lookup"><span data-stu-id="c1e21-171">The navigation sequence is known as a dynamically generated topology.</span></span> <span data-ttu-id="c1e21-172">對使用者來說，即使使用另一種巡覽拓撲，其使用者體驗和上一個拓撲是一樣的：</span><span class="sxs-lookup"><span data-stu-id="c1e21-172">For the user, as with the other navigation topologies, the user experience is the same as it is for the previous topologies:</span></span>  
  
- <span data-ttu-id="c1e21-173">從呼叫頁面巡覽至啟動器頁面，其可初始化精靈，並巡覽至精靈的第一頁。</span><span class="sxs-lookup"><span data-stu-id="c1e21-173">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="c1e21-174">啟動器頁 （[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]無<xref:System.Windows.Navigation.PageFunction%601>-） 不是必需的，因為調用頁可以直接調用第一個嚮導頁。</span><span class="sxs-lookup"><span data-stu-id="c1e21-174">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="c1e21-175">不過，如果精靈的初始化作業特別複雜，則可以使用啟動程式頁面來簡化這項作業。</span><span class="sxs-lookup"><span data-stu-id="c1e21-175">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
- <span data-ttu-id="c1e21-176">使用者可以利用 [向後] 和 [向前] 按鈕 (或超連結)，在頁面之間巡覽。</span><span class="sxs-lookup"><span data-stu-id="c1e21-176">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
- <span data-ttu-id="c1e21-177">使用者可以利用日誌，在頁面之間巡覽。</span><span class="sxs-lookup"><span data-stu-id="c1e21-177">Users can navigate between pages using the journal.</span></span>  
  
- <span data-ttu-id="c1e21-178">使用者可以按 [取消] 按鈕，取消任何精靈頁面中的精靈。</span><span class="sxs-lookup"><span data-stu-id="c1e21-178">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
- <span data-ttu-id="c1e21-179">使用者可以按 [結束] 按鈕，接受最後一個精靈頁面中的精靈。</span><span class="sxs-lookup"><span data-stu-id="c1e21-179">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
- <span data-ttu-id="c1e21-180">如果取消精靈，精靈會傳回適當的結果，但不會傳回任何資料。</span><span class="sxs-lookup"><span data-stu-id="c1e21-180">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
- <span data-ttu-id="c1e21-181">如果使用者接受精靈，精靈會傳回適當的結果，並傳回它所收集的資料。</span><span class="sxs-lookup"><span data-stu-id="c1e21-181">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
- <span data-ttu-id="c1e21-182">完成精靈時 (已接受或取消)，即會從日誌中移除精靈所含的頁面。</span><span class="sxs-lookup"><span data-stu-id="c1e21-182">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="c1e21-183">這可將精靈的每個執行個體隔離，以避免潛在的資料或狀態異常。</span><span class="sxs-lookup"><span data-stu-id="c1e21-183">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1e21-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1e21-184">See also</span></span>

- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [<span data-ttu-id="c1e21-185">結構化巡覽概觀</span><span class="sxs-lookup"><span data-stu-id="c1e21-185">Structured Navigation Overview</span></span>](structured-navigation-overview.md)
