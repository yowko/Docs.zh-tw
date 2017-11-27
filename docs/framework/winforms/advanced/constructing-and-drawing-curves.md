---
title: "建構和繪製曲線"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing [Windows Forms], curves
- examples [Windows Forms], drawing curves
- curves [Windows Forms], drawing
ms.assetid: 76e92623-4130-4644-b867-faca58bdb3a2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 801af10f7b9e5e7998fc061537977c5bced6bdb3
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="constructing-and-drawing-curves"></a><span data-ttu-id="f6d4b-102">建構和繪製曲線</span><span class="sxs-lookup"><span data-stu-id="f6d4b-102">Constructing and Drawing Curves</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="f6d4b-103">支援幾種類型的曲線： 省略符號、 弧線、 曲線和貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="f6d4b-103"> supports several types of curves: ellipses, arcs, cardinal splines, and Bézier splines.</span></span> <span data-ttu-id="f6d4b-104">橢圓形是由其周框; 定義弧線是橢圓形的開始角度和掃掠角度所定義的一部分。</span><span class="sxs-lookup"><span data-stu-id="f6d4b-104">An ellipse is defined by its bounding rectangle; an arc is a portion of an ellipse defined by a starting angle and a sweep angle.</span></span> <span data-ttu-id="f6d4b-105">基線曲線的點和張力參數陣列所定義： 曲線平滑通過陣列中每個點，而且張力參數會影響曲線彎曲的方式。</span><span class="sxs-lookup"><span data-stu-id="f6d4b-105">A cardinal spline is defined by an array of points and a tension parameter — the curve passes smoothly through each point in the array, and the tension parameter influences the way the curve bends.</span></span> <span data-ttu-id="f6d4b-106">兩個端點和兩個控制點曲線不會通過控制點，所定義的貝茲曲線，但控制點影響方向和彎曲，因為曲線會在各個端點之間。</span><span class="sxs-lookup"><span data-stu-id="f6d4b-106">A Bézier spline is defined by two endpoints and two control points  the curve does not pass through the control points, but the control points influence the direction and bend as the curve goes from one endpoint to the other.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f6d4b-107">本章節內容</span><span class="sxs-lookup"><span data-stu-id="f6d4b-107">In This Section</span></span>  
 [<span data-ttu-id="f6d4b-108">操作說明：繪製基本曲線</span><span class="sxs-lookup"><span data-stu-id="f6d4b-108">How to: Draw Cardinal Splines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-cardinal-splines.md)  
 <span data-ttu-id="f6d4b-109">描述基本曲線，以及如何進行繪製。</span><span class="sxs-lookup"><span data-stu-id="f6d4b-109">Describes cardinal splines and how to draw them.</span></span>  
  
 [<span data-ttu-id="f6d4b-110">操作說明：繪製單一貝茲曲線</span><span class="sxs-lookup"><span data-stu-id="f6d4b-110">How to: Draw a Single Bézier Spline</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-single-bezier-spline.md)  
 <span data-ttu-id="f6d4b-111">貝茲曲線，以及如何繪製一個描述。</span><span class="sxs-lookup"><span data-stu-id="f6d4b-111">Describes a Bézier spline and how to draw one.</span></span>  
  
 [<span data-ttu-id="f6d4b-112">操作說明：繪製一連串的貝茲曲線</span><span class="sxs-lookup"><span data-stu-id="f6d4b-112">How to: Draw a Sequence of Bézier Splines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-sequence-of-bezier-splines.md)  
 <span data-ttu-id="f6d4b-113">說明如何繪製順序中的數個貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="f6d4b-113">Explains how to draw several Bézier splines in sequence.</span></span>
