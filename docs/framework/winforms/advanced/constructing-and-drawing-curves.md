---
title: 建構和繪製曲線
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [Windows Forms], curves
- examples [Windows Forms], drawing curves
- curves [Windows Forms], drawing
ms.assetid: 76e92623-4130-4644-b867-faca58bdb3a2
ms.openlocfilehash: 92e7b1e8b4ce37db633b5dafe212a252b854d1af
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935443"
---
# <a name="constructing-and-drawing-curves"></a><span data-ttu-id="d3c9a-102">建構和繪製曲線</span><span class="sxs-lookup"><span data-stu-id="d3c9a-102">Constructing and Drawing Curves</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="d3c9a-103">支援數種類型的曲線： 省略符號，弧線、 基線曲線和貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="d3c9a-103">supports several types of curves: ellipses, arcs, cardinal splines, and Bézier splines.</span></span> <span data-ttu-id="d3c9a-104">橢圓形是由其周框; 定義弧形，是橢圓形的由開始角度和掃掠角度所定義的一部分。</span><span class="sxs-lookup"><span data-stu-id="d3c9a-104">An ellipse is defined by its bounding rectangle; an arc is a portion of an ellipse defined by a starting angle and a sweep angle.</span></span> <span data-ttu-id="d3c9a-105">基線曲線的點和張力參數陣列所定義，陣列中的每個點順利通過曲線和張力參數會影響曲線的彎曲的方式。</span><span class="sxs-lookup"><span data-stu-id="d3c9a-105">A cardinal spline is defined by an array of points and a tension parameter — the curve passes smoothly through each point in the array, and the tension parameter influences the way the curve bends.</span></span> <span data-ttu-id="d3c9a-106">貝茲曲線由兩個端點和定義曲線的控制點，透過未通過的兩個控制點，但控制點影響方向，並當曲線會在各個端點之間彎曲。</span><span class="sxs-lookup"><span data-stu-id="d3c9a-106">A Bézier spline is defined by two endpoints and two control points  the curve does not pass through the control points, but the control points influence the direction and bend as the curve goes from one endpoint to the other.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d3c9a-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="d3c9a-107">In This Section</span></span>  
 [<span data-ttu-id="d3c9a-108">如何：繪製基本曲線</span><span class="sxs-lookup"><span data-stu-id="d3c9a-108">How to: Draw Cardinal Splines</span></span>](how-to-draw-cardinal-splines.md)  
 <span data-ttu-id="d3c9a-109">描述基本曲線，以及如何進行繪製。</span><span class="sxs-lookup"><span data-stu-id="d3c9a-109">Describes cardinal splines and how to draw them.</span></span>  
  
 [<span data-ttu-id="d3c9a-110">如何：繪製單一貝茲曲線</span><span class="sxs-lookup"><span data-stu-id="d3c9a-110">How to: Draw a Single Bézier Spline</span></span>](how-to-draw-a-single-bezier-spline.md)  
 <span data-ttu-id="d3c9a-111">描述的貝茲曲線，以及如何發一張牌。</span><span class="sxs-lookup"><span data-stu-id="d3c9a-111">Describes a Bézier spline and how to draw one.</span></span>  
  
 [<span data-ttu-id="d3c9a-112">如何：繪製一連串的貝茲曲線</span><span class="sxs-lookup"><span data-stu-id="d3c9a-112">How to: Draw a Sequence of Bézier Splines</span></span>](how-to-draw-a-sequence-of-bezier-splines.md)  
 <span data-ttu-id="d3c9a-113">說明如何繪製順序中的數個貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="d3c9a-113">Explains how to draw several Bézier splines in sequence.</span></span>
