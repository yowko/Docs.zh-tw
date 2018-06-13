---
title: 操作說明：定義畫筆
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pens [WPF], defining
- creating [WPF], pens
ms.assetid: 7a4f2900-cdf9-49de-84e0-ba5d0ded4d33
ms.openlocfilehash: 7c5be5eff06df55e465f3e34646ba1c34e8b7e07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559848"
---
# <a name="how-to-define-a-pen"></a><span data-ttu-id="29439-102">操作說明：定義畫筆</span><span class="sxs-lookup"><span data-stu-id="29439-102">How to: Define a Pen</span></span>
<span data-ttu-id="29439-103">這個範例示範如何使用<xref:System.Windows.Media.Pen>概述圖形。</span><span class="sxs-lookup"><span data-stu-id="29439-103">This example shows how use a <xref:System.Windows.Media.Pen> to outline a shape.</span></span> <span data-ttu-id="29439-104">若要建立簡單<xref:System.Windows.Media.Pen>，您只需要指定其<xref:System.Windows.Media.Pen.Thickness%2A>和<xref:System.Windows.Media.Pen.Brush%2A>。</span><span class="sxs-lookup"><span data-stu-id="29439-104">To create a simple <xref:System.Windows.Media.Pen>, you need only specify its <xref:System.Windows.Media.Pen.Thickness%2A> and <xref:System.Windows.Media.Pen.Brush%2A>.</span></span> <span data-ttu-id="29439-105">您可以藉由指定建立更複雜的畫筆<xref:System.Windows.Media.Pen.DashStyle%2A>， <xref:System.Windows.Media.Pen.DashCap%2A>， <xref:System.Windows.Media.Pen.LineJoin%2A>， <xref:System.Windows.Media.Pen.StartLineCap%2A>，和<xref:System.Windows.Media.Pen.EndLineCap%2A>。</span><span class="sxs-lookup"><span data-stu-id="29439-105">You can create more complex pen's by specifying a <xref:System.Windows.Media.Pen.DashStyle%2A>, <xref:System.Windows.Media.Pen.DashCap%2A>, <xref:System.Windows.Media.Pen.LineJoin%2A>, <xref:System.Windows.Media.Pen.StartLineCap%2A>, and <xref:System.Windows.Media.Pen.EndLineCap%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29439-106">範例</span><span class="sxs-lookup"><span data-stu-id="29439-106">Example</span></span>  
 <span data-ttu-id="29439-107">下列範例會使用<xref:System.Windows.Media.Pen>概述所定義的圖形<xref:System.Windows.Media.GeometryDrawing>。</span><span class="sxs-lookup"><span data-stu-id="29439-107">The following example uses a <xref:System.Windows.Media.Pen> to outline a shape defined by a <xref:System.Windows.Media.GeometryDrawing>.</span></span>  
  
 [!code-csharp[PenExamples_snip#PenExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PenExamples_snip/CSharp/PenExample.cs#penexamplewholepage)]
 [!code-vb[PenExamples_snip#PenExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PenExamples_snip/VisualBasic/PenExample.vb#penexamplewholepage)]  
  
 <span data-ttu-id="29439-108">![由 Pen 所描繪的外框會產生](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple-pen.jpg "graphicsmm_simple_pen")</span><span class="sxs-lookup"><span data-stu-id="29439-108">![Outlines produces by a Pen](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple-pen.jpg "graphicsmm_simple_pen")</span></span>  
<span data-ttu-id="29439-109">GeometryDrawing</span><span class="sxs-lookup"><span data-stu-id="29439-109">A GeometryDrawing</span></span>
