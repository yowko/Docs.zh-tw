---
title: HOW TO：建立和使用畫布
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Canvas
- Canvas control [WPF], creating
- Canvas control [WPF], using
ms.assetid: 420b9487-9a15-477c-9489-a22a4dec7779
ms.openlocfilehash: 33b98024699a88f56d27b7e5ab8d5216c906e7ec
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59190765"
---
# <a name="how-to-create-and-use-a-canvas"></a>HOW TO：建立和使用畫布
此範例示範如何建立和使用的執行個體<xref:System.Windows.Controls.Canvas>。  
  
## <a name="example"></a>範例  
 下列範例明確地將兩個<xref:System.Windows.Controls.TextBlock>使用的項目<xref:System.Windows.Controls.Canvas.SetTop%2A>並<xref:System.Windows.Controls.Canvas.SetLeft%2A>方法<xref:System.Windows.Controls.Canvas>。 此範例也會將指派<xref:System.Windows.Controls.Control.Background%2A>色彩`LightSteelBlue`至<xref:System.Windows.Controls.Canvas>。  
  
> [!NOTE]
>  當您使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]位置<xref:System.Windows.Controls.TextBlock>項目，會使用<xref:System.Windows.Controls.Canvas.Top%2A>和<xref:System.Windows.Controls.Canvas.Left%2A>屬性。  
  
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
- [HOW TO 主題](canvas-how-to-topics.md)
