---
title: "建構和繪製路徑"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- paths [Windows Forms], drawing
- drawing paths [Windows Forms]
- graphics paths [Windows Forms], creating
- graphics paths [Windows Forms], drawing
- examples [Windows Forms], drawing paths
ms.assetid: f16ec921-56cf-46d1-9741-d7316ad06b23
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e6cec2356159b59e58ac6785a2988df7b2fac0e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="constructing-and-drawing-paths"></a><span data-ttu-id="1e3e5-102">建構和繪製路徑</span><span class="sxs-lookup"><span data-stu-id="1e3e5-102">Constructing and Drawing Paths</span></span>
<span data-ttu-id="1e3e5-103">路徑是一系列基本圖形 （線條、 矩形、 曲線、 文字和 like），可操作並繪製為單一單位。</span><span class="sxs-lookup"><span data-stu-id="1e3e5-103">A path is a sequence of graphics primitives (lines, rectangles, curves, text, and the like) that can be manipulated and drawn as a single unit.</span></span> <span data-ttu-id="1e3e5-104">路徑可以分割成*圖表*為開啟或關閉。</span><span class="sxs-lookup"><span data-stu-id="1e3e5-104">A path can be divided into *figures* that are either open or closed.</span></span> <span data-ttu-id="1e3e5-105">圖形可以包含數個基本項目。</span><span class="sxs-lookup"><span data-stu-id="1e3e5-105">A figure can contain several primitives.</span></span>  
  
 <span data-ttu-id="1e3e5-106">您可以藉由呼叫來繪製路徑<xref:System.Drawing.Graphics.DrawPath%2A>方法<xref:System.Drawing.Graphics>類別，而您可以藉由呼叫填入路徑<xref:System.Drawing.Graphics.FillPath%2A>方法<xref:System.Drawing.Graphics>類別。</span><span class="sxs-lookup"><span data-stu-id="1e3e5-106">You can draw a path by calling the <xref:System.Drawing.Graphics.DrawPath%2A> method of the <xref:System.Drawing.Graphics> class, and you can fill a path by calling the <xref:System.Drawing.Graphics.FillPath%2A> method of the <xref:System.Drawing.Graphics> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1e3e5-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="1e3e5-107">In This Section</span></span>  
 [<span data-ttu-id="1e3e5-108">操作說明：從線條、曲線和形狀建立圖形</span><span class="sxs-lookup"><span data-stu-id="1e3e5-108">How to: Create Figures from Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-figures-from-lines-curves-and-shapes.md)  
 <span data-ttu-id="1e3e5-109">示範如何使用<xref:System.Drawing.Drawing2D.GraphicsPath>建立數字。</span><span class="sxs-lookup"><span data-stu-id="1e3e5-109">Shows how to use a <xref:System.Drawing.Drawing2D.GraphicsPath> to create figures.</span></span>  
  
 [<span data-ttu-id="1e3e5-110">操作說明：填滿開放圖形</span><span class="sxs-lookup"><span data-stu-id="1e3e5-110">How to: Fill Open Figures</span></span>](../../../../docs/framework/winforms/advanced/how-to-fill-open-figures.md)  
 <span data-ttu-id="1e3e5-111">說明如何填滿<xref:System.Drawing.Drawing2D.GraphicsPath>。</span><span class="sxs-lookup"><span data-stu-id="1e3e5-111">Explains how to fill a <xref:System.Drawing.Drawing2D.GraphicsPath>.</span></span>  
  
 [<span data-ttu-id="1e3e5-112">操作說明：將曲線路徑簡維為線條</span><span class="sxs-lookup"><span data-stu-id="1e3e5-112">How to: Flatten a Curved Path into a Line</span></span>](../../../../docs/framework/winforms/advanced/how-to-flatten-a-curved-path-into-a-line.md)  
 <span data-ttu-id="1e3e5-113">示範如何壓平合併<xref:System.Drawing.Drawing2D.GraphicsPath>。</span><span class="sxs-lookup"><span data-stu-id="1e3e5-113">Shows how to flatten a <xref:System.Drawing.Drawing2D.GraphicsPath>.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1e3e5-114">參考資料</span><span class="sxs-lookup"><span data-stu-id="1e3e5-114">Reference</span></span>  
 <xref:System.Drawing.Drawing2D.GraphicsPath>  
 <span data-ttu-id="1e3e5-115">描述這個類別，並包含其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="1e3e5-115">Describes this class and contains links to all of its members.</span></span>
