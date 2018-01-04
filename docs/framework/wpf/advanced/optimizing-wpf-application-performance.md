---
title: "最佳化 WPF 應用程式效能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application rendering [WPF], performance
- application optimization [WPF]
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: ac8c6aa3-3c68-4a24-9827-3b6c829c1ebf
caps.latest.revision: "45"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 385bcb8678b11e1cb8f84ae509b1f1b6777665d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="optimizing-wpf-application-performance"></a><span data-ttu-id="0242c-102">最佳化 WPF 應用程式效能</span><span class="sxs-lookup"><span data-stu-id="0242c-102">Optimizing WPF Application Performance</span></span>
<span data-ttu-id="0242c-103">本節的目的在於為參考[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]應用程式開發人員所需的方式來改善其應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="0242c-103">This section is intended as a reference for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application developers who are looking for ways to improve the performance of their applications.</span></span> <span data-ttu-id="0242c-104">如果您是開發人員而言是新[!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)]和[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，您應該先熟悉這兩個平台。</span><span class="sxs-lookup"><span data-stu-id="0242c-104">If you are a developer who is new to the [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], you should first familiarize yourself with both platforms.</span></span> <span data-ttu-id="0242c-105">本節假設兩者的實用知識，並寫入的程式設計人員已經知道要取得其應用程式啟動且正在執行。</span><span class="sxs-lookup"><span data-stu-id="0242c-105">This section assumes working knowledge of both, and is written for programmers who already know enough to get their applications up and running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0242c-106">本章節中提供的效能資料會根據[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式上執行，2.8 GHz 電腦且 512 RAM 和 ATI Radeon 9700 圖形卡。</span><span class="sxs-lookup"><span data-stu-id="0242c-106">The performance data provided in this section are based on [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications running on a 2.8 GHz PC with 512 RAM and an ATI Radeon 9700 graphics card.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0242c-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="0242c-107">In This Section</span></span>  
 [<span data-ttu-id="0242c-108">應用程式效能規劃</span><span class="sxs-lookup"><span data-stu-id="0242c-108">Planning for Application Performance</span></span>](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
  
 [<span data-ttu-id="0242c-109">運用硬體</span><span class="sxs-lookup"><span data-stu-id="0242c-109">Taking Advantage of Hardware</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
  
 [<span data-ttu-id="0242c-110">版面配置與設計</span><span class="sxs-lookup"><span data-stu-id="0242c-110">Layout and Design</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
  
 [<span data-ttu-id="0242c-111">2D 圖形和影像處理</span><span class="sxs-lookup"><span data-stu-id="0242c-111">2D Graphics and Imaging</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
  
 [<span data-ttu-id="0242c-112">物件行為</span><span class="sxs-lookup"><span data-stu-id="0242c-112">Object Behavior</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
  
 [<span data-ttu-id="0242c-113">應用程式資源</span><span class="sxs-lookup"><span data-stu-id="0242c-113">Application Resources</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
  
 [<span data-ttu-id="0242c-114">Text</span><span class="sxs-lookup"><span data-stu-id="0242c-114">Text</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
  
 [<span data-ttu-id="0242c-115">資料繫結</span><span class="sxs-lookup"><span data-stu-id="0242c-115">Data Binding</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
  
 [<span data-ttu-id="0242c-116">控制項</span><span class="sxs-lookup"><span data-stu-id="0242c-116">Controls</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)  
  
 [<span data-ttu-id="0242c-117">其他效能建議</span><span class="sxs-lookup"><span data-stu-id="0242c-117">Other Performance Recommendations</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)  
  
 [<span data-ttu-id="0242c-118">應用程式啟動時間</span><span class="sxs-lookup"><span data-stu-id="0242c-118">Application Startup Time</span></span>](../../../../docs/framework/wpf/advanced/application-startup-time.md)  
  
## <a name="see-also"></a><span data-ttu-id="0242c-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="0242c-119">See Also</span></span>  
 <xref:System.Windows.Media.RenderOptions>  
 <xref:System.Windows.Media.RenderCapability>  
 [<span data-ttu-id="0242c-120">圖形轉譯層</span><span class="sxs-lookup"><span data-stu-id="0242c-120">Graphics Rendering Tiers</span></span>](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)  
 [<span data-ttu-id="0242c-121">WPF 圖形轉譯概觀</span><span class="sxs-lookup"><span data-stu-id="0242c-121">WPF Graphics Rendering Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [<span data-ttu-id="0242c-122">版面配置</span><span class="sxs-lookup"><span data-stu-id="0242c-122">Layout</span></span>](../../../../docs/framework/wpf/advanced/layout.md)  
 [<span data-ttu-id="0242c-123">WPF 中的樹狀結構</span><span class="sxs-lookup"><span data-stu-id="0242c-123">Trees in WPF</span></span>](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)  
 [<span data-ttu-id="0242c-124">繪圖物件概觀</span><span class="sxs-lookup"><span data-stu-id="0242c-124">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="0242c-125">使用 DrawingVisual 物件</span><span class="sxs-lookup"><span data-stu-id="0242c-125">Using DrawingVisual Objects</span></span>](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)  
 [<span data-ttu-id="0242c-126">相依性屬性概觀</span><span class="sxs-lookup"><span data-stu-id="0242c-126">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [<span data-ttu-id="0242c-127">Freezable 物件概觀</span><span class="sxs-lookup"><span data-stu-id="0242c-127">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="0242c-128">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="0242c-128">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="0242c-129">WPF 中的文件</span><span class="sxs-lookup"><span data-stu-id="0242c-129">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="0242c-130">繪製格式化的文字</span><span class="sxs-lookup"><span data-stu-id="0242c-130">Drawing Formatted Text</span></span>](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)  
 [<span data-ttu-id="0242c-131">WPF 中的印刷樣式</span><span class="sxs-lookup"><span data-stu-id="0242c-131">Typography in WPF</span></span>](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [<span data-ttu-id="0242c-132">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="0242c-132">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="0242c-133">瀏覽概觀</span><span class="sxs-lookup"><span data-stu-id="0242c-133">Navigation Overview</span></span>](../../../../docs/framework/wpf/app-development/navigation-overview.md)  
 [<span data-ttu-id="0242c-134">動畫祕訣和訣竅</span><span class="sxs-lookup"><span data-stu-id="0242c-134">Animation Tips and Tricks</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)  
 [<span data-ttu-id="0242c-135">逐步解說：在 WPF 應用程式中快取應用程式資料</span><span class="sxs-lookup"><span data-stu-id="0242c-135">Walkthrough: Caching Application Data in a WPF Application</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)
