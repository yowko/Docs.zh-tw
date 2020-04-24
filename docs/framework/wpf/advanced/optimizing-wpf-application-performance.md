---
title: 優化應用效能
ms.date: 03/30/2017
helpviewer_keywords:
- application rendering [WPF], performance
- application optimization [WPF]
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: ac8c6aa3-3c68-4a24-9827-3b6c829c1ebf
ms.openlocfilehash: 54d69e87ef2a9c5318e394422e3bcfcabcc76210
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646254"
---
# <a name="optimizing-wpf-application-performance"></a><span data-ttu-id="1ef21-102">最佳化 WPF 應用程式效能</span><span class="sxs-lookup"><span data-stu-id="1ef21-102">Optimizing WPF Application Performance</span></span>
<span data-ttu-id="1ef21-103">本節旨在為[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]尋求提高應用程式性能的應用程式開發人員提供參考。</span><span class="sxs-lookup"><span data-stu-id="1ef21-103">This section is intended as a reference for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application developers who are looking for ways to improve the performance of their applications.</span></span> <span data-ttu-id="1ef21-104">如果您是 Microsoft .NET 框架的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]開發人員, 並且應首先熟悉這兩個平臺。</span><span class="sxs-lookup"><span data-stu-id="1ef21-104">If you are a developer who is new to the Microsoft .NET Framework and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], you should first familiarize yourself with both platforms.</span></span> <span data-ttu-id="1ef21-105">本節假定兩者的工作知識,並編寫給已經瞭解到足以啟動和運行其應用程式的程式師。</span><span class="sxs-lookup"><span data-stu-id="1ef21-105">This section assumes working knowledge of both, and is written for programmers who already know enough to get their applications up and running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1ef21-106">本節中提供的性能數據基於[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]在具有 512 RAM 的 2.8 GHz PC 和 ATI Radeon 9700 顯卡上運行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1ef21-106">The performance data provided in this section are based on [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications running on a 2.8 GHz PC with 512 RAM and an ATI Radeon 9700 graphics card.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1ef21-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="1ef21-107">In This Section</span></span>  
 [<span data-ttu-id="1ef21-108">應用程式效能規劃</span><span class="sxs-lookup"><span data-stu-id="1ef21-108">Planning for Application Performance</span></span>](planning-for-application-performance.md)  
  
 [<span data-ttu-id="1ef21-109">運用硬體</span><span class="sxs-lookup"><span data-stu-id="1ef21-109">Taking Advantage of Hardware</span></span>](optimizing-performance-taking-advantage-of-hardware.md)  
  
 [<span data-ttu-id="1ef21-110">版面配置與設計</span><span class="sxs-lookup"><span data-stu-id="1ef21-110">Layout and Design</span></span>](optimizing-performance-layout-and-design.md)  
  
 [<span data-ttu-id="1ef21-111">2D 圖形和影像處理</span><span class="sxs-lookup"><span data-stu-id="1ef21-111">2D Graphics and Imaging</span></span>](optimizing-performance-2d-graphics-and-imaging.md)  
  
 [<span data-ttu-id="1ef21-112">物件行為</span><span class="sxs-lookup"><span data-stu-id="1ef21-112">Object Behavior</span></span>](optimizing-performance-object-behavior.md)  
  
 [<span data-ttu-id="1ef21-113">應用程式資源</span><span class="sxs-lookup"><span data-stu-id="1ef21-113">Application Resources</span></span>](optimizing-performance-application-resources.md)  
  
 [<span data-ttu-id="1ef21-114">Text</span><span class="sxs-lookup"><span data-stu-id="1ef21-114">Text</span></span>](optimizing-performance-text.md)  
  
 [<span data-ttu-id="1ef21-115">資料繫結</span><span class="sxs-lookup"><span data-stu-id="1ef21-115">Data Binding</span></span>](optimizing-performance-data-binding.md)  
  
 [<span data-ttu-id="1ef21-116">控制項</span><span class="sxs-lookup"><span data-stu-id="1ef21-116">Controls</span></span>](optimizing-performance-controls.md)  
  
 [<span data-ttu-id="1ef21-117">其他效能建議</span><span class="sxs-lookup"><span data-stu-id="1ef21-117">Other Performance Recommendations</span></span>](optimizing-performance-other-recommendations.md)  
  
 [<span data-ttu-id="1ef21-118">應用程式啟動時間</span><span class="sxs-lookup"><span data-stu-id="1ef21-118">Application Startup Time</span></span>](application-startup-time.md)  
  
## <a name="see-also"></a><span data-ttu-id="1ef21-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ef21-119">See also</span></span>

- <xref:System.Windows.Media.RenderOptions>
- <xref:System.Windows.Media.RenderCapability>
- [<span data-ttu-id="1ef21-120">圖形轉譯層</span><span class="sxs-lookup"><span data-stu-id="1ef21-120">Graphics Rendering Tiers</span></span>](graphics-rendering-tiers.md)
- [<span data-ttu-id="1ef21-121">WPF 圖形轉譯概觀</span><span class="sxs-lookup"><span data-stu-id="1ef21-121">WPF Graphics Rendering Overview</span></span>](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [<span data-ttu-id="1ef21-122">配置</span><span class="sxs-lookup"><span data-stu-id="1ef21-122">Layout</span></span>](layout.md)
- [<span data-ttu-id="1ef21-123">WPF 中的樹狀結構</span><span class="sxs-lookup"><span data-stu-id="1ef21-123">Trees in WPF</span></span>](trees-in-wpf.md)
- [<span data-ttu-id="1ef21-124">繪圖物件概觀</span><span class="sxs-lookup"><span data-stu-id="1ef21-124">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="1ef21-125">使用 DrawingVisual 物件</span><span class="sxs-lookup"><span data-stu-id="1ef21-125">Using DrawingVisual Objects</span></span>](../graphics-multimedia/using-drawingvisual-objects.md)
- [<span data-ttu-id="1ef21-126">相依性屬性概觀</span><span class="sxs-lookup"><span data-stu-id="1ef21-126">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="1ef21-127">Freezable 物件概觀</span><span class="sxs-lookup"><span data-stu-id="1ef21-127">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="1ef21-128">XAML 資源</span><span class="sxs-lookup"><span data-stu-id="1ef21-128">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="1ef21-129">WPF 中的文件</span><span class="sxs-lookup"><span data-stu-id="1ef21-129">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="1ef21-130">繪製格式化的文字</span><span class="sxs-lookup"><span data-stu-id="1ef21-130">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
- [<span data-ttu-id="1ef21-131">WPF 中的印刷樣式</span><span class="sxs-lookup"><span data-stu-id="1ef21-131">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="1ef21-132">資料繫結概述</span><span class="sxs-lookup"><span data-stu-id="1ef21-132">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="1ef21-133">瀏覽概觀</span><span class="sxs-lookup"><span data-stu-id="1ef21-133">Navigation Overview</span></span>](../app-development/navigation-overview.md)
- [<span data-ttu-id="1ef21-134">動畫秘訣和訣竅</span><span class="sxs-lookup"><span data-stu-id="1ef21-134">Animation Tips and Tricks</span></span>](../graphics-multimedia/animation-tips-and-tricks.md)
- [<span data-ttu-id="1ef21-135">逐步解說：在 WPF 應用程式中快取應用程式資料</span><span class="sxs-lookup"><span data-stu-id="1ef21-135">Walkthrough: Caching Application Data in a WPF Application</span></span>](walkthrough-caching-application-data-in-a-wpf-application.md)
