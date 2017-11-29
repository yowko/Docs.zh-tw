---
title: "操作說明：在事件發生時套用轉換至元素"
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
helpviewer_keywords:
- graphics [WPF], transformations as event responses
- properties [WPF], LayoutTransform
- transformations as event responses [WPF]
- properties [WPF], RenderTransform
- LayoutTransform property [WPF]
ms.assetid: 71e4327e-ca57-444c-a3cf-09fb381491a0
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 58ef8c008eea4c10228ebb10ceadb5806dfbc0f4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-a-transform-to-an-element-when-an-event-occurs"></a>操作說明：在事件發生時套用轉換至元素
這個範例示範如何套用<xref:System.Windows.Media.ScaleTransform>事件發生時。 這裡所示範的概念，與您用來套用其他類型轉換的概念相同。 如需可用的轉換類型的詳細資訊，請參閱<xref:System.Windows.Media.Transform>類別或[轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)。  
  
 您可以透過下列兩種方式其中之一，將轉換套用至元素：  
  
-   如果您這樣做*不*想要影響版面配置，請使用的轉換<xref:System.Windows.UIElement.RenderTransform%2A>元素的屬性。  
  
-   如果您想要影響版面配置的轉換，使用<xref:System.Windows.FrameworkElement.LayoutTransform%2A>元素的屬性。  
  
 下列範例會套用<xref:System.Windows.Media.ScaleTransform>至<xref:System.Windows.UIElement.RenderTransform%2A>按鈕的屬性。 當滑鼠停留在按鈕，<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>和<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>屬性<xref:System.Windows.Media.ScaleTransform>設為`2`，這會使按鈕變得越來越大。 當滑鼠按鈕，關閉<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>和<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>設為`1`，因而導致按鈕回到其原始大小。  
  
## <a name="example"></a>範例  
 [!code-xaml[ButtonTransform#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml#1)]  
  
 [!code-csharp[ButtonTransform#1cb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml.cs#1cb)]
 [!code-vb[ButtonTransform#1cb](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ButtonTransform/VisualBasic/ButtonTransformExample.xaml.vb#1cb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.ScaleTransform>  
 [轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [操作說明主題](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)  
 [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
