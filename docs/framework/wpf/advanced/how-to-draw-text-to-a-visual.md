---
title: 作法：在視覺效果繪製文字
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
ms.openlocfilehash: bd760a06150098d0fff17dbdce95b55a0e5fe713
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963852"
---
# <a name="how-to-draw-text-to-a-visual"></a><span data-ttu-id="0142f-102">HOW TO：在視覺效果繪製文字</span><span class="sxs-lookup"><span data-stu-id="0142f-102">How to: Draw Text to a Visual</span></span>
<span data-ttu-id="0142f-103">下列範例示範如何<xref:System.Windows.Media.DrawingVisual> <xref:System.Windows.Media.DrawingContext>使用物件, 將文字繪製至。</span><span class="sxs-lookup"><span data-stu-id="0142f-103">The following example shows how to draw text to a <xref:System.Windows.Media.DrawingVisual> using a <xref:System.Windows.Media.DrawingContext> object.</span></span> <span data-ttu-id="0142f-104">繪製內容是藉由呼叫<xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> <xref:System.Windows.Media.DrawingVisual>物件的方法來傳回。</span><span class="sxs-lookup"><span data-stu-id="0142f-104">A drawing context is returned by calling the <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> method of a <xref:System.Windows.Media.DrawingVisual> object.</span></span> <span data-ttu-id="0142f-105">您可以在繪圖內容中繪製圖形和文字。</span><span class="sxs-lookup"><span data-stu-id="0142f-105">You can draw graphics and text into a drawing context.</span></span>  
  
 <span data-ttu-id="0142f-106">若要在繪圖內容中繪製文字, 請<xref:System.Windows.Media.DrawingContext.DrawText%2A>使用<xref:System.Windows.Media.DrawingContext>物件的方法。</span><span class="sxs-lookup"><span data-stu-id="0142f-106">To draw text into the drawing context, use the <xref:System.Windows.Media.DrawingContext.DrawText%2A> method of a <xref:System.Windows.Media.DrawingContext> object.</span></span> <span data-ttu-id="0142f-107">當您完成將內容繪製到繪圖內容時, 請呼叫<xref:System.Windows.Media.DrawingContext.Close%2A>方法來關閉繪圖內容並保存內容。</span><span class="sxs-lookup"><span data-stu-id="0142f-107">When you are finished drawing content into the drawing context, call the <xref:System.Windows.Media.DrawingContext.Close%2A> method to close the drawing context and persist the content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0142f-108">範例</span><span class="sxs-lookup"><span data-stu-id="0142f-108">Example</span></span>  
 [!code-csharp[DrawingVisualSample#110](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
> <span data-ttu-id="0142f-109">如需先前程式碼範例出處的完整程式碼範例，請參閱[使用 DrawingVisuals 進行點擊測試範例 (英文)](https://go.microsoft.com/fwlink/?LinkID=159994)。</span><span class="sxs-lookup"><span data-stu-id="0142f-109">For the complete code sample from which the preceding code example was extracted, see [Hit Test Using DrawingVisuals Sample](https://go.microsoft.com/fwlink/?LinkID=159994).</span></span>
