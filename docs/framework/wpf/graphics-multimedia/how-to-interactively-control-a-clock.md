---
title: 如何：以互動方式控制時鐘
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controlling clocks interactively [WPF]
- clocks [WPF], controlling interactively
ms.assetid: d0b520e0-2f18-4cef-977f-2909e709548a
ms.openlocfilehash: 63e72c48afd9b72a6b334ccdc234d08cef7288f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-interactively-control-a-clock"></a>如何：以互動方式控制時鐘
A<xref:System.Windows.Media.Animation.Clock>物件的<xref:System.Windows.Media.Animation.ClockController>屬性可讓您以互動方式啟動、 暫停、 繼續、 搜尋、 前進到其填滿期間，時鐘和停止時鐘。 只有根時鐘的時間樹狀結構可以以互動方式控制。  
  
> [!NOTE]
>  還有其他方式來以互動方式控制動畫，而不需要直接處理時鐘： 您也可以使用分鏡腳本。 標記和程式碼中支援分鏡腳本。 如需範例，請參閱[使用分鏡腳本建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)或[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  
  
 在下列範例中，數個按鈕可用來以互動方式控制動畫時鐘。  
  
## <a name="example"></a>範例  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a>另請參閱  
 [使用分鏡腳本建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
