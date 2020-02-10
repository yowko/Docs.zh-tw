---
title: 如何：繪製文字至視覺效果
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], drawing text to visuals
- visuals [WPF], drawing text to
- text [WPF], drawing to visuals
- drawing [WPF], text to visuals
ms.assetid: fee4003c-e8a6-46ec-babd-2c7f4231a101
ms.openlocfilehash: 654bfadb42f053b6dcf353d4423bddf281d69478
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094549"
---
# <a name="how-to-draw-text-to-a-visual"></a>如何：繪製文字至視覺效果
下列範例示範如何使用 <xref:System.Windows.Media.DrawingContext> 物件繪製文字到 <xref:System.Windows.Media.DrawingVisual>。 繪製內容是藉由呼叫 <xref:System.Windows.Media.DrawingVisual> 物件的 <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> 方法來傳回。 您可以在繪圖內容中繪製圖形和文字。  
  
 若要在繪圖內容中繪製文字，請使用 <xref:System.Windows.Media.DrawingContext> 物件的 <xref:System.Windows.Media.DrawingContext.DrawText%2A> 方法。 當您完成將內容繪製到繪圖內容時，請呼叫 <xref:System.Windows.Media.DrawingContext.Close%2A> 方法來關閉繪圖內容並保存內容。  
  
## <a name="example"></a>範例  
 [!code-csharp[DrawingVisualSample#110](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
> 如需先前程式碼範例出處的完整程式碼範例，請參閱[使用 DrawingVisuals 進行點擊測試範例 (英文)](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual)。
