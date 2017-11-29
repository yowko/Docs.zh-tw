---
title: "使用畫筆繪製線條和形狀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pens
- examples [Windows Forms], drawing lines and shapes
- examples [Windows Forms], pens
- drawing
ms.assetid: 8a7542ab-3e9e-443f-8405-2d6053528e20
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0913dc2745e1b244e4b03c0e6b946441a401c5b1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="using-a-pen-to-draw-lines-and-shapes"></a><span data-ttu-id="e45ca-102">使用畫筆繪製線條和形狀</span><span class="sxs-lookup"><span data-stu-id="e45ca-102">Using a Pen to Draw Lines and Shapes</span></span>
<span data-ttu-id="e45ca-103">使用[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]`Pen`繪製直線線段、 曲線和形狀框線的物件。</span><span class="sxs-lookup"><span data-stu-id="e45ca-103">Use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] `Pen` objects to draw line segments, curves, and the outlines of shapes.</span></span> <span data-ttu-id="e45ca-104">在本節中，*列*指的是這些項目，除非另有指定，意指只直線線段。</span><span class="sxs-lookup"><span data-stu-id="e45ca-104">In this section, *line* refers to any of these, unless specified to mean only a line segment.</span></span> <span data-ttu-id="e45ca-105">設定的畫筆用來控制色彩、 寬度、 對齊方式和使用該畫筆繪製的直線樣式屬性。</span><span class="sxs-lookup"><span data-stu-id="e45ca-105">Set the properties of a pen to control the color, width, alignment, and style of lines drawn with that pen.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e45ca-106">本章節內容</span><span class="sxs-lookup"><span data-stu-id="e45ca-106">In This Section</span></span>  
 [<span data-ttu-id="e45ca-107">操作說明：使用畫筆繪製線條</span><span class="sxs-lookup"><span data-stu-id="e45ca-107">How to: Use a Pen to Draw Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-a-pen-to-draw-lines.md)  
 <span data-ttu-id="e45ca-108">說明如何繪製線條。</span><span class="sxs-lookup"><span data-stu-id="e45ca-108">Explains how to draw lines.</span></span>  
  
 [<span data-ttu-id="e45ca-109">操作說明：使用畫筆繪製矩形</span><span class="sxs-lookup"><span data-stu-id="e45ca-109">How to: Use a Pen to Draw Rectangles</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-a-pen-to-draw-rectangles.md)  
 <span data-ttu-id="e45ca-110">描述如何繪製矩形。</span><span class="sxs-lookup"><span data-stu-id="e45ca-110">Describes how to draw rectangles.</span></span>  
  
 [<span data-ttu-id="e45ca-111">操作說明：設定畫筆寬度和對齊</span><span class="sxs-lookup"><span data-stu-id="e45ca-111">How to: Set Pen Width and Alignment</span></span>](../../../../docs/framework/winforms/advanced/how-to-set-pen-width-and-alignment.md)  
 <span data-ttu-id="e45ca-112">說明如何變更的寬度和對齊`Pen`物件。</span><span class="sxs-lookup"><span data-stu-id="e45ca-112">Explains how to change the width and alignment of a `Pen` object.</span></span>  
  
 [<span data-ttu-id="e45ca-113">操作說明：繪製包含線條形式的線條</span><span class="sxs-lookup"><span data-stu-id="e45ca-113">How to: Draw a Line with Line Caps</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-with-line-caps.md)  
 <span data-ttu-id="e45ca-114">描述如何繪製一條線時加入端點。</span><span class="sxs-lookup"><span data-stu-id="e45ca-114">Describes how to add end caps when drawing a line.</span></span>  
  
 [<span data-ttu-id="e45ca-115">操作說明：聯結線條</span><span class="sxs-lookup"><span data-stu-id="e45ca-115">How to: Join Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-join-lines.md)  
 <span data-ttu-id="e45ca-116">示範如何聯結兩個線條。</span><span class="sxs-lookup"><span data-stu-id="e45ca-116">Shows how to join two lines.</span></span>  
  
 [<span data-ttu-id="e45ca-117">操作說明：繪製自訂短折線</span><span class="sxs-lookup"><span data-stu-id="e45ca-117">How to: Draw a Custom Dashed Line</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-custom-dashed-line.md)  
 <span data-ttu-id="e45ca-118">描述如何繪製虛線。</span><span class="sxs-lookup"><span data-stu-id="e45ca-118">Describes how to draw a dashed line.</span></span>  
  
 [<span data-ttu-id="e45ca-119">操作說明：繪製填滿材質的線條</span><span class="sxs-lookup"><span data-stu-id="e45ca-119">How to: Draw a Line Filled with a Texture</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-filled-with-a-texture.md)  
 <span data-ttu-id="e45ca-120">說明如何繪製填滿材質的線條。</span><span class="sxs-lookup"><span data-stu-id="e45ca-120">Explains how to draw a texture-filled line.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e45ca-121">參考資料</span><span class="sxs-lookup"><span data-stu-id="e45ca-121">Reference</span></span>  
 <xref:System.Drawing.Pen>  
 <span data-ttu-id="e45ca-122">說明這個類別，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="e45ca-122">Describes this class and has links to all its members.</span></span>
