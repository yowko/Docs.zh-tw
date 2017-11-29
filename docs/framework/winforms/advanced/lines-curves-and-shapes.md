---
title: "線條、曲線和形狀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shapes [Windows Forms], filling
- splines [Windows Forms], drawing
- shapes. drawing
- lines [Windows Forms], drawing
- curves [Windows Forms], drawing
ms.assetid: ace6e8d4-4e94-486b-9681-758a6667dc7f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2caa77285ebe327adc690b26baeb58aa800627fb
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="lines-curves-and-shapes"></a><span data-ttu-id="7c057-102">線條、曲線和形狀</span><span class="sxs-lookup"><span data-stu-id="7c057-102">Lines, Curves, and Shapes</span></span>
<span data-ttu-id="7c057-103">向量圖形部分[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]用來繪製線條、 繪製曲線，以及繪製，並填滿圖案。</span><span class="sxs-lookup"><span data-stu-id="7c057-103">The vector graphics portion of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] is used to draw lines, draw curves, and to draw and fill shapes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7c057-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="7c057-104">In This Section</span></span>  
 [<span data-ttu-id="7c057-105">向量圖形概觀</span><span class="sxs-lookup"><span data-stu-id="7c057-105">Vector Graphics Overview</span></span>](../../../../docs/framework/winforms/advanced/vector-graphics-overview.md)  
 <span data-ttu-id="7c057-106">討論向量圖形。</span><span class="sxs-lookup"><span data-stu-id="7c057-106">Discusses vector graphics.</span></span>  
  
 [<span data-ttu-id="7c057-107">GDI+ 中的畫筆、線條和矩形</span><span class="sxs-lookup"><span data-stu-id="7c057-107">Pens, Lines, and Rectangles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)  
 <span data-ttu-id="7c057-108">說明繪製線條和矩形。</span><span class="sxs-lookup"><span data-stu-id="7c057-108">Discusses drawing lines and rectangles.</span></span>  
  
 [<span data-ttu-id="7c057-109">GDI+ 中的橢圓形和弧形</span><span class="sxs-lookup"><span data-stu-id="7c057-109">Ellipses and Arcs in GDI+</span></span>](../../../../docs/framework/winforms/advanced/ellipses-and-arcs-in-gdi.md)  
 <span data-ttu-id="7c057-110">定義弧形和省略符號和識別以進行繪製所需的類別。</span><span class="sxs-lookup"><span data-stu-id="7c057-110">Defines arcs and ellipses and identifies the classes needed to draw them.</span></span>  
  
 [<span data-ttu-id="7c057-111">GDI+ 中的多邊形</span><span class="sxs-lookup"><span data-stu-id="7c057-111">Polygons in GDI+</span></span>](../../../../docs/framework/winforms/advanced/polygons-in-gdi.md)  
 <span data-ttu-id="7c057-112">定義的多邊形，並指出它們繪製所需的類別。</span><span class="sxs-lookup"><span data-stu-id="7c057-112">Defines polygons and identifies the classes needed to draw them.</span></span>  
  
 [<span data-ttu-id="7c057-113">GDI+ 中的基本曲線</span><span class="sxs-lookup"><span data-stu-id="7c057-113">Cardinal Splines in GDI+</span></span>](../../../../docs/framework/winforms/advanced/cardinal-splines-in-gdi.md)  
 <span data-ttu-id="7c057-114">定義曲線，並指出它們繪製所需的類別。</span><span class="sxs-lookup"><span data-stu-id="7c057-114">Defines cardinal splines and identifies the classes needed to draw them.</span></span>  
  
 [<span data-ttu-id="7c057-115">GDI+ 中的貝茲曲線</span><span class="sxs-lookup"><span data-stu-id="7c057-115">Bézier Splines in GDI+</span></span>](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)  
 <span data-ttu-id="7c057-116">定義貝茲曲線，並指出它們繪製所需的類別。</span><span class="sxs-lookup"><span data-stu-id="7c057-116">Defines Bezier splines and identifies the classes needed to draw them.</span></span>  
  
 [<span data-ttu-id="7c057-117">GDI+ 中的圖形路徑</span><span class="sxs-lookup"><span data-stu-id="7c057-117">Graphics Paths in GDI+</span></span>](../../../../docs/framework/winforms/advanced/graphics-paths-in-gdi.md)  
 <span data-ttu-id="7c057-118">描述路徑，以及如何建立和繪製。</span><span class="sxs-lookup"><span data-stu-id="7c057-118">Describes paths and how to create and draw them.</span></span>  
  
 [<span data-ttu-id="7c057-119">GDI+ 中的筆刷和填滿的形狀</span><span class="sxs-lookup"><span data-stu-id="7c057-119">Brushes and Filled Shapes in GDI+</span></span>](../../../../docs/framework/winforms/advanced/brushes-and-filled-shapes-in-gdi.md)  
 <span data-ttu-id="7c057-120">描述筆刷類型和使用方式。</span><span class="sxs-lookup"><span data-stu-id="7c057-120">Describes brush types and how to use them.</span></span>  
  
 [<span data-ttu-id="7c057-121">GDI+ 中的開放型和封閉型曲線</span><span class="sxs-lookup"><span data-stu-id="7c057-121">Open and Closed Curves in GDI+</span></span>](../../../../docs/framework/winforms/advanced/open-and-closed-curves-in-gdi.md)  
 <span data-ttu-id="7c057-122">開啟和封閉型曲線，以及如何繪製及填滿其定義。</span><span class="sxs-lookup"><span data-stu-id="7c057-122">Defines open and closed curves and how to draw and fill them.</span></span>  
  
 [<span data-ttu-id="7c057-123">GDI+ 中的區域</span><span class="sxs-lookup"><span data-stu-id="7c057-123">Regions in GDI+</span></span>](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)  
 <span data-ttu-id="7c057-124">描述與區域相關聯的方法。</span><span class="sxs-lookup"><span data-stu-id="7c057-124">Describes the methods associated with regions.</span></span>  
  
 [<span data-ttu-id="7c057-125">限制 GDI+ 中的繪圖介面</span><span class="sxs-lookup"><span data-stu-id="7c057-125">Restricting the Drawing Surface in GDI+</span></span>](../../../../docs/framework/winforms/advanced/restricting-the-drawing-surface-in-gdi.md)  
 <span data-ttu-id="7c057-126">描述裁剪及如何使用它。</span><span class="sxs-lookup"><span data-stu-id="7c057-126">Describes clipping and how to use it.</span></span>  
  
 [<span data-ttu-id="7c057-127">線條和曲線的反鋸齒功能</span><span class="sxs-lookup"><span data-stu-id="7c057-127">Antialiasing with Lines and Curves</span></span>](../../../../docs/framework/winforms/advanced/antialiasing-with-lines-and-curves.md)  
 <span data-ttu-id="7c057-128">定義反鋸齒功能以及如何使用反鋸齒功能時繪製線條和曲線。</span><span class="sxs-lookup"><span data-stu-id="7c057-128">Defines antialiasing and how use antialiasing when drawing lines and curves.</span></span>
