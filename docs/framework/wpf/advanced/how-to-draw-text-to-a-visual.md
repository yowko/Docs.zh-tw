---
title: HOW TO：繪製文字至視覺效果
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
ms.openlocfilehash: 1ea31540ad59ab419e209e4133bcb88640cc01fe
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368898"
---
# <a name="how-to-draw-text-to-a-visual"></a><span data-ttu-id="bdc11-102">HOW TO：繪製文字至視覺效果</span><span class="sxs-lookup"><span data-stu-id="bdc11-102">How to: Draw Text to a Visual</span></span>
<span data-ttu-id="bdc11-103">下列範例示範如何繪製文字至<xref:System.Windows.Media.DrawingVisual>使用<xref:System.Windows.Media.DrawingContext>物件。</span><span class="sxs-lookup"><span data-stu-id="bdc11-103">The following example shows how to draw text to a <xref:System.Windows.Media.DrawingVisual> using a <xref:System.Windows.Media.DrawingContext> object.</span></span> <span data-ttu-id="bdc11-104">繪製的內容由呼叫<xref:System.Windows.Media.DrawingVisual.RenderOpen%2A>方法的<xref:System.Windows.Media.DrawingVisual>物件。</span><span class="sxs-lookup"><span data-stu-id="bdc11-104">A drawing context is returned by calling the <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> method of a <xref:System.Windows.Media.DrawingVisual> object.</span></span> <span data-ttu-id="bdc11-105">您可以繪製圖形和文字，放入繪圖內容。</span><span class="sxs-lookup"><span data-stu-id="bdc11-105">You can draw graphics and text into a drawing context.</span></span>  
  
 <span data-ttu-id="bdc11-106">若要繪製文字至繪製內容，請使用<xref:System.Windows.Media.DrawingContext.DrawText%2A>方法的<xref:System.Windows.Media.DrawingContext>物件。</span><span class="sxs-lookup"><span data-stu-id="bdc11-106">To draw text into the drawing context, use the <xref:System.Windows.Media.DrawingContext.DrawText%2A> method of a <xref:System.Windows.Media.DrawingContext> object.</span></span> <span data-ttu-id="bdc11-107">當您完成繪製至繪圖內容的內容時，呼叫<xref:System.Windows.Media.DrawingContext.Close%2A>方法來關閉繪製內容並保存內容。</span><span class="sxs-lookup"><span data-stu-id="bdc11-107">When you are finished drawing content into the drawing context, call the <xref:System.Windows.Media.DrawingContext.Close%2A> method to close the drawing context and persist the content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdc11-108">範例</span><span class="sxs-lookup"><span data-stu-id="bdc11-108">Example</span></span>  
 [!code-csharp[DrawingVisualSample#110](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
>  <span data-ttu-id="bdc11-109">如需先前程式碼範例出處的完整程式碼範例，請參閱[使用 DrawingVisuals 進行點擊測試範例 (英文)](https://go.microsoft.com/fwlink/?LinkID=159994)。</span><span class="sxs-lookup"><span data-stu-id="bdc11-109">For the complete code sample from which the preceding code example was extracted, see [Hit Test Using DrawingVisuals Sample](https://go.microsoft.com/fwlink/?LinkID=159994).</span></span>
