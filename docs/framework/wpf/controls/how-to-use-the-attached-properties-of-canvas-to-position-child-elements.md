---
title: "操作說明：使用 Canvas 的附加屬性置放子元素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- attached properties [WPF Designer]
- Canvas control [WPF], attached properties
ms.assetid: 48f1d25d-3820-4107-a4cc-d6c1e5664a44
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 85ee852c868f26937494d5d340d2db4210224754
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-attached-properties-of-canvas-to-position-child-elements"></a><span data-ttu-id="ac868-102">操作說明：使用 Canvas 的附加屬性置放子元素</span><span class="sxs-lookup"><span data-stu-id="ac868-102">How to: Use the Attached Properties of Canvas to Position Child Elements</span></span>
<span data-ttu-id="ac868-103">這個範例示範如何使用附加的屬性<xref:System.Windows.Controls.Canvas>来放置子項目。</span><span class="sxs-lookup"><span data-stu-id="ac868-103">This example shows how to use the attached properties of <xref:System.Windows.Controls.Canvas> to position child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac868-104">範例</span><span class="sxs-lookup"><span data-stu-id="ac868-104">Example</span></span>  
 <span data-ttu-id="ac868-105">下列範例會將四個<xref:System.Windows.Controls.Button>為父系的子元素的項目<xref:System.Windows.Controls.Canvas>。</span><span class="sxs-lookup"><span data-stu-id="ac868-105">The following example adds four <xref:System.Windows.Controls.Button> elements as child elements of a parent <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="ac868-106">每個子項目代表相異的附加的屬性的<xref:System.Windows.Controls.Canvas>: <xref:System.Windows.Controls.Canvas.Bottom%2A>， <xref:System.Windows.Controls.Canvas.Left%2A>， <xref:System.Windows.Controls.Canvas.Right%2A>，和<xref:System.Windows.Controls.Canvas.Top%2A>。</span><span class="sxs-lookup"><span data-stu-id="ac868-106">Each child element represents a distinct attached property of <xref:System.Windows.Controls.Canvas>: <xref:System.Windows.Controls.Canvas.Bottom%2A>, <xref:System.Windows.Controls.Canvas.Left%2A>, <xref:System.Windows.Controls.Canvas.Right%2A>, and <xref:System.Windows.Controls.Canvas.Top%2A>.</span></span> <span data-ttu-id="ac868-107">每個<xref:System.Windows.Controls.Button>相對於父<xref:System.Windows.Controls.Canvas>並根據其指派的屬性值。</span><span class="sxs-lookup"><span data-stu-id="ac868-107">Each <xref:System.Windows.Controls.Button> is positioned relative to the parent <xref:System.Windows.Controls.Canvas> and according to its assigned property value.</span></span>  
  
 [!code-cpp[CanvasAttachedProperties#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/CanvasAttachedProperties/CPP/CanvasAttachedProps.cpp#1)]
 [!code-csharp[CanvasAttachedProperties#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasAttachedProperties/CSharp/CanvasAttachedProps.cs#1)]
 [!code-vb[CanvasAttachedProperties#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasAttachedProperties/VisualBasic/CanvasAttachedProps.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ac868-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac868-108">See Also</span></span>  
 <xref:System.Windows.Controls.Canvas>  
 <xref:System.Windows.Controls.Canvas.Bottom%2A>  
 <xref:System.Windows.Controls.Canvas.Left%2A>  
 <xref:System.Windows.Controls.Canvas.Right%2A>  
 <xref:System.Windows.Controls.Canvas.Top%2A>  
 <xref:System.Windows.Controls.Button>  
 [<span data-ttu-id="ac868-109">面板概觀</span><span class="sxs-lookup"><span data-stu-id="ac868-109">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="ac868-110">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="ac868-110">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/canvas-how-to-topics.md)  
 [<span data-ttu-id="ac868-111">附加屬性概觀</span><span class="sxs-lookup"><span data-stu-id="ac868-111">Attached Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)
