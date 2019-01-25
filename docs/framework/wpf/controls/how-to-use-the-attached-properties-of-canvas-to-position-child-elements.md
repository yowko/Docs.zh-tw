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
ms.openlocfilehash: a0d0bc51466ee18e09eeffe80a568d277280248c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54682054"
---
# <a name="how-to-use-the-attached-properties-of-canvas-to-position-child-elements"></a>HOW TO：使用 Canvas 的附加屬性置放子項目
此範例示範如何使用附加的屬性<xref:System.Windows.Controls.Canvas>来放置子項目。  
  
## <a name="example"></a>範例  
 下列範例會將四個<xref:System.Windows.Controls.Button>項目與子項目的父代<xref:System.Windows.Controls.Canvas>。 每個項目由<xref:System.Windows.Controls.Canvas.Bottom%2A>， <xref:System.Windows.Controls.Canvas.Left%2A>， <xref:System.Windows.Controls.Canvas.Right%2A>，和<xref:System.Windows.Controls.Canvas.Top%2A>。
每個<xref:System.Windows.Controls.Button>相對於父代<xref:System.Windows.Controls.Canvas>並根據其指派的屬性值。  
  
 [!code-cpp[CanvasAttachedProperties#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/CanvasAttachedProperties/CPP/CanvasAttachedProps.cpp#1)]
 [!code-csharp[CanvasAttachedProperties#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasAttachedProperties/CSharp/CanvasAttachedProps.cs#1)]
 [!code-vb[CanvasAttachedProperties#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasAttachedProperties/VisualBasic/CanvasAttachedProps.vb#1)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.Canvas.Bottom%2A>
- <xref:System.Windows.Controls.Canvas.Left%2A>
- <xref:System.Windows.Controls.Canvas.Right%2A>
- <xref:System.Windows.Controls.Canvas.Top%2A>
- <xref:System.Windows.Controls.Button>
- [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)
- [HOW-TO 主題](../../../../docs/framework/wpf/controls/canvas-how-to-topics.md)
- [附加屬性概觀](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)
