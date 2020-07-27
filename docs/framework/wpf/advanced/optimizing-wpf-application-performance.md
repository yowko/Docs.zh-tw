---
title: 優化應用程式效能
description: 使用這些資源可改善 Windows Presentation Foundation 應用程式的效能，例如規劃效能和利用硬體。
ms.date: 03/30/2017
helpviewer_keywords:
- application rendering [WPF], performance
- application optimization [WPF]
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: ac8c6aa3-3c68-4a24-9827-3b6c829c1ebf
ms.openlocfilehash: 165caaf102a66988db0254839a947b8e262a386d
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166328"
---
# <a name="optimizing-wpf-application-performance"></a><span data-ttu-id="a462c-103">最佳化 WPF 應用程式效能</span><span class="sxs-lookup"><span data-stu-id="a462c-103">Optimizing WPF Application Performance</span></span>
<span data-ttu-id="a462c-104">本節旨在做為 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式開發人員的參考，以尋找改善其應用程式效能的方法。</span><span class="sxs-lookup"><span data-stu-id="a462c-104">This section is intended as a reference for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application developers who are looking for ways to improve the performance of their applications.</span></span> <span data-ttu-id="a462c-105">如果您是 Microsoft .NET Framework 和的新手開發人員 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ，您應該先熟悉這兩個平臺。</span><span class="sxs-lookup"><span data-stu-id="a462c-105">If you are a developer who is new to the Microsoft .NET Framework and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], you should first familiarize yourself with both platforms.</span></span> <span data-ttu-id="a462c-106">本章節假設您對兩者都有了解，而且是針對已經知道要讓應用程式啟動並執行的程式設計人員所撰寫的。</span><span class="sxs-lookup"><span data-stu-id="a462c-106">This section assumes working knowledge of both, and is written for programmers who already know enough to get their applications up and running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a462c-107">本節所提供的效能資料是以 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 2.8 GHZ 電腦上執行的應用程式為基礎，其中包含 512 RAM 和一個 ATI Radeon 9700 圖形配接器。</span><span class="sxs-lookup"><span data-stu-id="a462c-107">The performance data provided in this section are based on [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications running on a 2.8 GHz PC with 512 RAM and an ATI Radeon 9700 graphics card.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a462c-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="a462c-108">In This Section</span></span>  
 [<span data-ttu-id="a462c-109">應用程式效能規劃</span><span class="sxs-lookup"><span data-stu-id="a462c-109">Planning for Application Performance</span></span>](planning-for-application-performance.md)  
  
 [<span data-ttu-id="a462c-110">運用硬體</span><span class="sxs-lookup"><span data-stu-id="a462c-110">Taking Advantage of Hardware</span></span>](optimizing-performance-taking-advantage-of-hardware.md)  
  
 [<span data-ttu-id="a462c-111">版面配置與設計</span><span class="sxs-lookup"><span data-stu-id="a462c-111">Layout and Design</span></span>](optimizing-performance-layout-and-design.md)  
  
 [<span data-ttu-id="a462c-112">2D 圖形和影像處理</span><span class="sxs-lookup"><span data-stu-id="a462c-112">2D Graphics and Imaging</span></span>](optimizing-performance-2d-graphics-and-imaging.md)  
  
 [<span data-ttu-id="a462c-113">物件行為</span><span class="sxs-lookup"><span data-stu-id="a462c-113">Object Behavior</span></span>](optimizing-performance-object-behavior.md)  
  
 [<span data-ttu-id="a462c-114">應用程式資源</span><span class="sxs-lookup"><span data-stu-id="a462c-114">Application Resources</span></span>](optimizing-performance-application-resources.md)  
  
 [<span data-ttu-id="a462c-115">Text</span><span class="sxs-lookup"><span data-stu-id="a462c-115">Text</span></span>](optimizing-performance-text.md)  
  
 [<span data-ttu-id="a462c-116">資料系結</span><span class="sxs-lookup"><span data-stu-id="a462c-116">Data Binding</span></span>](optimizing-performance-data-binding.md)  
  
 [<span data-ttu-id="a462c-117">控制項</span><span class="sxs-lookup"><span data-stu-id="a462c-117">Controls</span></span>](optimizing-performance-controls.md)  
  
 [<span data-ttu-id="a462c-118">其他效能建議</span><span class="sxs-lookup"><span data-stu-id="a462c-118">Other Performance Recommendations</span></span>](optimizing-performance-other-recommendations.md)  
  
 [<span data-ttu-id="a462c-119">應用程式啟動時間</span><span class="sxs-lookup"><span data-stu-id="a462c-119">Application Startup Time</span></span>](application-startup-time.md)  
  
## <a name="see-also"></a><span data-ttu-id="a462c-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a462c-120">See also</span></span>

- <xref:System.Windows.Media.RenderOptions>
- <xref:System.Windows.Media.RenderCapability>
- [<span data-ttu-id="a462c-121">圖形轉譯層</span><span class="sxs-lookup"><span data-stu-id="a462c-121">Graphics Rendering Tiers</span></span>](graphics-rendering-tiers.md)
- [<span data-ttu-id="a462c-122">WPF 圖形轉譯概觀</span><span class="sxs-lookup"><span data-stu-id="a462c-122">WPF Graphics Rendering Overview</span></span>](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [<span data-ttu-id="a462c-123">版面配置</span><span class="sxs-lookup"><span data-stu-id="a462c-123">Layout</span></span>](layout.md)
- [<span data-ttu-id="a462c-124">WPF 中的樹狀結構</span><span class="sxs-lookup"><span data-stu-id="a462c-124">Trees in WPF</span></span>](trees-in-wpf.md)
- [<span data-ttu-id="a462c-125">繪圖物件概觀</span><span class="sxs-lookup"><span data-stu-id="a462c-125">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="a462c-126">使用 DrawingVisual 物件</span><span class="sxs-lookup"><span data-stu-id="a462c-126">Using DrawingVisual Objects</span></span>](../graphics-multimedia/using-drawingvisual-objects.md)
- [<span data-ttu-id="a462c-127">相依性屬性總覽</span><span class="sxs-lookup"><span data-stu-id="a462c-127">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="a462c-128">Freezable 物件概觀</span><span class="sxs-lookup"><span data-stu-id="a462c-128">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="a462c-129">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="a462c-129">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="a462c-130">WPF 中的文件</span><span class="sxs-lookup"><span data-stu-id="a462c-130">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="a462c-131">繪製格式化的文字</span><span class="sxs-lookup"><span data-stu-id="a462c-131">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
- [<span data-ttu-id="a462c-132">WPF 中的印刷樣式</span><span class="sxs-lookup"><span data-stu-id="a462c-132">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="a462c-133">資料系結總覽</span><span class="sxs-lookup"><span data-stu-id="a462c-133">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="a462c-134">巡覽概觀</span><span class="sxs-lookup"><span data-stu-id="a462c-134">Navigation Overview</span></span>](../app-development/navigation-overview.md)
- [<span data-ttu-id="a462c-135">動畫秘訣和訣竅</span><span class="sxs-lookup"><span data-stu-id="a462c-135">Animation Tips and Tricks</span></span>](../graphics-multimedia/animation-tips-and-tricks.md)
- [<span data-ttu-id="a462c-136">逐步解說：在 WPF 應用程式中快取應用程式資料</span><span class="sxs-lookup"><span data-stu-id="a462c-136">Walkthrough: Caching Application Data in a WPF Application</span></span>](walkthrough-caching-application-data-in-a-wpf-application.md)
