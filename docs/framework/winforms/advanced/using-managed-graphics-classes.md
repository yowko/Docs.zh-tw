---
title: "使用 Managed 圖形類別"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GDI+, managed classes
- graphics [Windows Forms], using in Windows Forms
- graphics [Windows Forms], managed classes
ms.assetid: e6d1a42d-2100-46aa-97e6-a5ddc0baaae5
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2a34e2726182c194882d94fe4b8d1164993d8284
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="using-managed-graphics-classes"></a><span data-ttu-id="bf8cd-102">使用 Managed 圖形類別</span><span class="sxs-lookup"><span data-stu-id="bf8cd-102">Using Managed Graphics Classes</span></span>
<span data-ttu-id="bf8cd-103">下列主題描述如何使用[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]managed 的類別 framework 中的應用程式開發介面。</span><span class="sxs-lookup"><span data-stu-id="bf8cd-103">The following topics describe how to use the [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] API in the managed class framework.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bf8cd-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="bf8cd-104">In This Section</span></span>  
 [<span data-ttu-id="bf8cd-105">圖形程式設計入門</span><span class="sxs-lookup"><span data-stu-id="bf8cd-105">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 <span data-ttu-id="bf8cd-106">描述如何完成基本工作，與[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bf8cd-106">Describes how to accomplish basic tasks with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span>  
  
 [<span data-ttu-id="bf8cd-107">使用畫筆繪製線條和形狀</span><span class="sxs-lookup"><span data-stu-id="bf8cd-107">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 <span data-ttu-id="bf8cd-108">示範如何建構畫筆，並用來繪製各種線條和形狀。</span><span class="sxs-lookup"><span data-stu-id="bf8cd-108">Demonstrates how to construct a pen and use it to draw a variety of lines and shapes.</span></span>  
  
 [<span data-ttu-id="bf8cd-109">使用筆刷填滿形狀</span><span class="sxs-lookup"><span data-stu-id="bf8cd-109">Using a Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)  
 <span data-ttu-id="bf8cd-110">示範如何建構效果的各種不同的筆刷和填滿圖案。</span><span class="sxs-lookup"><span data-stu-id="bf8cd-110">Demonstrates how to construct a brush and fill shapes with a variety of effects.</span></span>  
  
 [<span data-ttu-id="bf8cd-111">使用漸層筆刷填滿形狀</span><span class="sxs-lookup"><span data-stu-id="bf8cd-111">Using a Gradient Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)  
 <span data-ttu-id="bf8cd-112">示範如何建立及使用不同類型的漸層筆刷。</span><span class="sxs-lookup"><span data-stu-id="bf8cd-112">Shows how to create and use different types of gradient brushes.</span></span>  
  
 [<span data-ttu-id="bf8cd-113">使用影像、點陣圖、圖示和中繼檔</span><span class="sxs-lookup"><span data-stu-id="bf8cd-113">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)  
 <span data-ttu-id="bf8cd-114">示範如何建構及操控映像。</span><span class="sxs-lookup"><span data-stu-id="bf8cd-114">Demonstrates how to construct and manipulate images.</span></span>  
  
 [<span data-ttu-id="bf8cd-115">Alpha 混色線條和填色</span><span class="sxs-lookup"><span data-stu-id="bf8cd-115">Alpha Blending Lines and Fills</span></span>](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)  
 <span data-ttu-id="bf8cd-116">示範如何達到圖案和線條的透明度。</span><span class="sxs-lookup"><span data-stu-id="bf8cd-116">Demonstrates how to achieve transparency for shapes and lines.</span></span>  
  
 [<span data-ttu-id="bf8cd-117">使用字型和文字</span><span class="sxs-lookup"><span data-stu-id="bf8cd-117">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 <span data-ttu-id="bf8cd-118">示範如何繪製文字，並使用字型和字型家族。</span><span class="sxs-lookup"><span data-stu-id="bf8cd-118">Shows how to draw text and use fonts and font families.</span></span>  
  
 [<span data-ttu-id="bf8cd-119">建構和繪製曲線</span><span class="sxs-lookup"><span data-stu-id="bf8cd-119">Constructing and Drawing Curves</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)  
 <span data-ttu-id="bf8cd-120">顯示如何畫基線和貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="bf8cd-120">Shows how to draw Cardinal and Bezier splines.</span></span>  
  
 [<span data-ttu-id="bf8cd-121">建構和繪製路徑</span><span class="sxs-lookup"><span data-stu-id="bf8cd-121">Constructing and Drawing Paths</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)  
 <span data-ttu-id="bf8cd-122">示範如何使用路徑建立圖形。</span><span class="sxs-lookup"><span data-stu-id="bf8cd-122">Shows how to create figures using paths.</span></span>  
  
 [<span data-ttu-id="bf8cd-123">使用 Managed GDI+ 中的轉換</span><span class="sxs-lookup"><span data-stu-id="bf8cd-123">Using Transformations in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)  
 <span data-ttu-id="bf8cd-124">示範矩陣轉換。</span><span class="sxs-lookup"><span data-stu-id="bf8cd-124">Demonstrates matrix transformations.</span></span>  
  
 [<span data-ttu-id="bf8cd-125">使用圖形容器</span><span class="sxs-lookup"><span data-stu-id="bf8cd-125">Using Graphics Containers</span></span>](../../../../docs/framework/winforms/advanced/using-graphics-containers.md)  
 <span data-ttu-id="bf8cd-126">示範如何管理圖形物件狀態和巢狀圖形容器。</span><span class="sxs-lookup"><span data-stu-id="bf8cd-126">Shows how to manage graphics object state and nested graphics containers.</span></span>  
  
 [<span data-ttu-id="bf8cd-127">使用區域</span><span class="sxs-lookup"><span data-stu-id="bf8cd-127">Using Regions</span></span>](../../../../docs/framework/winforms/advanced/using-regions.md)  
 <span data-ttu-id="bf8cd-128">示範叫用的測試和裁剪區域。</span><span class="sxs-lookup"><span data-stu-id="bf8cd-128">Demonstrates hit testing and clipping with regions.</span></span>  
  
 [<span data-ttu-id="bf8cd-129">為影像重新著色</span><span class="sxs-lookup"><span data-stu-id="bf8cd-129">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)  
 <span data-ttu-id="bf8cd-130">示範色彩管理的各個層面。</span><span class="sxs-lookup"><span data-stu-id="bf8cd-130">Demonstrates various aspects of manipulating colors.</span></span>  
  
 [<span data-ttu-id="bf8cd-131">使用 Managed GDI+ 中的影像編碼器和解碼器</span><span class="sxs-lookup"><span data-stu-id="bf8cd-131">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)  
 <span data-ttu-id="bf8cd-132">示範如何使用操作影像的影像編碼器和解碼器。</span><span class="sxs-lookup"><span data-stu-id="bf8cd-132">Show how to use image encoders and decoders to manipulate images.</span></span>  
  
 [<span data-ttu-id="bf8cd-133">雙重緩衝的圖形</span><span class="sxs-lookup"><span data-stu-id="bf8cd-133">Double Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 <span data-ttu-id="bf8cd-134">示範如何減少重繪閃動使用雙重緩衝。</span><span class="sxs-lookup"><span data-stu-id="bf8cd-134">Demonstrates how to reduce flicker with double buffering.</span></span>
