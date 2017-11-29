---
title: "如何：繪製線條"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing [WPF], lines
- graphics [WPF], lines
- lines [WPF], drawing
ms.assetid: 0513ee01-6b27-4bb3-85f3-3a3e6710d80e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4911aea91416fb84e9a18d54c145b494737ef9dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-line"></a><span data-ttu-id="3534c-102">如何：繪製線條</span><span class="sxs-lookup"><span data-stu-id="3534c-102">How to: Draw a Line</span></span>
<span data-ttu-id="3534c-103">此範例將示範如何使用的繪製線條<xref:System.Windows.Shapes.Line>項目。</span><span class="sxs-lookup"><span data-stu-id="3534c-103">This example shows you how to draw lines by using the <xref:System.Windows.Shapes.Line> element.</span></span>  
  
 <span data-ttu-id="3534c-104">若要繪製一條線，建立<xref:System.Windows.Shapes.Line>項目。</span><span class="sxs-lookup"><span data-stu-id="3534c-104">To draw a line, create a <xref:System.Windows.Shapes.Line> element.</span></span> <span data-ttu-id="3534c-105">使用其<xref:System.Windows.Shapes.Line.X1%2A>和<xref:System.Windows.Shapes.Line.Y1%2A>屬性來設定它的起點; 並使用其<xref:System.Windows.Shapes.Line.X2%2A>和<xref:System.Windows.Shapes.Line.Y2%2A>屬性可用來設定其結束點。</span><span class="sxs-lookup"><span data-stu-id="3534c-105">Use its <xref:System.Windows.Shapes.Line.X1%2A> and <xref:System.Windows.Shapes.Line.Y1%2A> properties to set its start point; and use its <xref:System.Windows.Shapes.Line.X2%2A> and <xref:System.Windows.Shapes.Line.Y2%2A> properties to set its end point.</span></span> <span data-ttu-id="3534c-106">最後，設定其<xref:System.Windows.Shapes.Shape.Stroke%2A>和<xref:System.Windows.Shapes.Shape.StrokeThickness%2A>因為沒有筆觸線條是不可見。</span><span class="sxs-lookup"><span data-stu-id="3534c-106">Finally, set its <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> because a line without a stroke is invisible.</span></span>  
  
 <span data-ttu-id="3534c-107">設定<xref:System.Windows.Shapes.Shape.Fill%2A>一條線的項目無效，因為列不有任何內部。</span><span class="sxs-lookup"><span data-stu-id="3534c-107">Setting the <xref:System.Windows.Shapes.Shape.Fill%2A> element for a line has no effect, because a line has no interior.</span></span>  
  
 <span data-ttu-id="3534c-108">下列範例會繪製內三行<xref:System.Windows.Controls.Canvas>項目。</span><span class="sxs-lookup"><span data-stu-id="3534c-108">The following example draws three lines inside a <xref:System.Windows.Controls.Canvas> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3534c-109">範例</span><span class="sxs-lookup"><span data-stu-id="3534c-109">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 <span data-ttu-id="3534c-110">這個範例是較大範例的一部分如需完整範例，請參閱[圖形項目範例](http://go.microsoft.com/fwlink/?LinkID=160037)。</span><span class="sxs-lookup"><span data-stu-id="3534c-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](http://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3534c-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3534c-111">See Also</span></span>  
 <xref:System.Windows.Shapes.Line>  
 [<span data-ttu-id="3534c-112">圖形項目範例</span><span class="sxs-lookup"><span data-stu-id="3534c-112">Shape Elements Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160037)
