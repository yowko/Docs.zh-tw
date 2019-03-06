---
title: HOW TO：以互動方式控制時鐘
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controlling clocks interactively [WPF]
- clocks [WPF], controlling interactively
ms.assetid: d0b520e0-2f18-4cef-977f-2909e709548a
ms.openlocfilehash: 6d3dbc8c39e63b46871b0cc88fbe8d5d51b63463
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57361651"
---
# <a name="how-to-interactively-control-a-clock"></a>HOW TO：以互動方式控制時鐘
A<xref:System.Windows.Media.Animation.Clock>物件的<xref:System.Windows.Media.Animation.ClockController>屬性可讓您以互動方式啟動、 暫停、 繼續、 搜尋、 前進到其填滿期間中，時鐘及停止時鐘。 您可以以互動方式控制只計時樹狀結構的根時鐘。  
  
> [!NOTE]
>  還有其他方式來以互動方式控制動畫，而不需要直接使用時鐘： 您也可以使用分鏡腳本。 分鏡腳本支援標記和程式碼。 如需範例，請參閱[使用分鏡腳本建立屬性的動畫](how-to-animate-a-property-by-using-a-storyboard.md)或[動畫概觀](animation-overview.md)。  
  
 在下列範例中，數個按鈕用來以互動方式控制動畫時鐘。  
  
## <a name="example"></a>範例  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a>另請參閱
- [使用分鏡腳本建立屬性的動畫](how-to-animate-a-property-by-using-a-storyboard.md)
- [動畫概觀](animation-overview.md)
