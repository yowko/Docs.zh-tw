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
ms.openlocfilehash: 4fbb0931ee7d17d4b3264de512353dc75caf070d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-text-to-a-visual"></a>如何：繪製文字至視覺效果
下列範例顯示如何畫文字<xref:System.Windows.Media.DrawingVisual>使用<xref:System.Windows.Media.DrawingContext>物件。 繪製內容由呼叫<xref:System.Windows.Media.DrawingVisual.RenderOpen%2A>方法<xref:System.Windows.Media.DrawingVisual>物件。 您可以放入繪圖內容中繪製的圖形和文字。  
  
 若要繪製文字繪圖內容中，使用<xref:System.Windows.Media.DrawingContext.DrawText%2A>方法<xref:System.Windows.Media.DrawingContext>物件。 當您完成繪圖內容中繪製內容時，呼叫<xref:System.Windows.Media.DrawingContext.Close%2A>關閉繪製的內容，並將內容保存的方法。  
  
## <a name="example"></a>範例  
 [!code-csharp[DrawingVisualSample#110](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
>  如需先前程式碼範例出處的完整程式碼範例，請參閱[使用 DrawingVisuals 進行點擊測試範例 (英文)](http://go.microsoft.com/fwlink/?LinkID=159994)。
