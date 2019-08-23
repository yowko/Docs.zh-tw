---
title: 作法：建立和使用畫布
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Canvas
- Canvas control [WPF], creating
- Canvas control [WPF], using
ms.assetid: 420b9487-9a15-477c-9489-a22a4dec7779
ms.openlocfilehash: edef660b2da2f09e0a6edbc0a87f0d1f26eb03da
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964225"
---
# <a name="how-to-create-and-use-a-canvas"></a>HOW TO：建立和使用畫布
這個範例會示範如何建立和使用的實例<xref:System.Windows.Controls.Canvas>。  
  
## <a name="example"></a>範例  
 下列範例會<xref:System.Windows.Controls.Canvas.SetTop%2A>使用的和<xref:System.Windows.Controls.TextBlock>方法<xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.Canvas.SetLeft%2A>明確地放置兩個元素。 此範例也會將<xref:System.Windows.Controls.Control.Background%2A>的`LightSteelBlue`色彩指派給<xref:System.Windows.Controls.Canvas>。  
  
> [!NOTE]
> 當您使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]來定位<xref:System.Windows.Controls.TextBlock>元素時, 請<xref:System.Windows.Controls.Canvas.Top%2A>使用<xref:System.Windows.Controls.Canvas.Left%2A>和屬性。  
  
 [!code-csharp[CanvasCode#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasCode/CSharp/Canvas_Code.cs#1)]
 [!code-vb[CanvasCode#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasCode/VisualBasic/canvas_vb.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.TextBlock>
- <xref:System.Windows.Controls.Canvas.SetTop%2A>
- <xref:System.Windows.Controls.Canvas.SetLeft%2A>
- <xref:System.Windows.Controls.Canvas.Top%2A>
- <xref:System.Windows.Controls.Canvas.Left%2A>
- [面板概觀](panels-overview.md)
- [HOW-TO 主題](canvas-how-to-topics.md)
