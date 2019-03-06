---
title: HOW TO：使用 Canvas 的附加屬性置放子項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- attached properties [WPF Designer]
- Canvas control [WPF], attached properties
ms.assetid: 48f1d25d-3820-4107-a4cc-d6c1e5664a44
ms.openlocfilehash: a34bac644bd0fa4c15d76d72d0502b311c49d018
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365330"
---
# <a name="how-to-use-the-attached-properties-of-canvas-to-position-child-elements"></a><span data-ttu-id="7126a-102">HOW TO：使用 Canvas 的附加屬性置放子項目</span><span class="sxs-lookup"><span data-stu-id="7126a-102">How to: Use the Attached Properties of Canvas to Position Child Elements</span></span>
<span data-ttu-id="7126a-103">此範例示範如何使用附加的屬性<xref:System.Windows.Controls.Canvas>来放置子項目。</span><span class="sxs-lookup"><span data-stu-id="7126a-103">This example shows how to use the attached properties of <xref:System.Windows.Controls.Canvas> to position child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7126a-104">範例</span><span class="sxs-lookup"><span data-stu-id="7126a-104">Example</span></span>  
 <span data-ttu-id="7126a-105">下列範例會將四個<xref:System.Windows.Controls.Button>項目與子項目的父代<xref:System.Windows.Controls.Canvas>。</span><span class="sxs-lookup"><span data-stu-id="7126a-105">The following example adds four <xref:System.Windows.Controls.Button> elements as child elements of a parent <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="7126a-106">每個項目由<xref:System.Windows.Controls.Canvas.Bottom%2A>， <xref:System.Windows.Controls.Canvas.Left%2A>， <xref:System.Windows.Controls.Canvas.Right%2A>，和<xref:System.Windows.Controls.Canvas.Top%2A>。</span><span class="sxs-lookup"><span data-stu-id="7126a-106">Each element is represented by a <xref:System.Windows.Controls.Canvas.Bottom%2A>, <xref:System.Windows.Controls.Canvas.Left%2A>, <xref:System.Windows.Controls.Canvas.Right%2A>, and <xref:System.Windows.Controls.Canvas.Top%2A>.</span></span>
<span data-ttu-id="7126a-107">每個<xref:System.Windows.Controls.Button>相對於父代<xref:System.Windows.Controls.Canvas>並根據其指派的屬性值。</span><span class="sxs-lookup"><span data-stu-id="7126a-107">Each <xref:System.Windows.Controls.Button> is positioned relative to the parent <xref:System.Windows.Controls.Canvas> and according to its assigned property value.</span></span>  
  
 [!code-cpp[CanvasAttachedProperties#1](~/samples/snippets/cpp/VS_Snippets_Wpf/CanvasAttachedProperties/CPP/CanvasAttachedProps.cpp#1)]
 [!code-csharp[CanvasAttachedProperties#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasAttachedProperties/CSharp/CanvasAttachedProps.cs#1)]
 [!code-vb[CanvasAttachedProperties#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasAttachedProperties/VisualBasic/CanvasAttachedProps.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7126a-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7126a-108">See also</span></span>
- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.Canvas.Bottom%2A>
- <xref:System.Windows.Controls.Canvas.Left%2A>
- <xref:System.Windows.Controls.Canvas.Right%2A>
- <xref:System.Windows.Controls.Canvas.Top%2A>
- <xref:System.Windows.Controls.Button>
- [<span data-ttu-id="7126a-109">面板概觀</span><span class="sxs-lookup"><span data-stu-id="7126a-109">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="7126a-110">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="7126a-110">How-to Topics</span></span>](canvas-how-to-topics.md)
- [<span data-ttu-id="7126a-111">附加屬性概觀</span><span class="sxs-lookup"><span data-stu-id="7126a-111">Attached Properties Overview</span></span>](../advanced/attached-properties-overview.md)
