---
title: 如何：繪製文字至控制項的背景
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], drawing text to backgrounds
- text [WPF], drawing to control backgrounds
- drawing [WPF], text to control backgrounds
- backgrounds [WPF], drawing text to
- typography [WPF], drawing text to control backgrounds
ms.assetid: 686d8fba-f61c-4974-a871-c635d67a7f69
ms.openlocfilehash: 14300f763b67c6ac67ee408de2009c328d499c13
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424380"
---
# <a name="how-to-draw-text-to-a-controls-background"></a><span data-ttu-id="59e6f-102">如何：繪製文字至控制項的背景</span><span class="sxs-lookup"><span data-stu-id="59e6f-102">How to: Draw Text to a Control's Background</span></span>
<span data-ttu-id="59e6f-103">您可以藉由將文字字串轉換為 <xref:System.Windows.Media.FormattedText> 物件，然後將物件繪製至控制項的 <xref:System.Windows.Media.DrawingContext>，直接將文字繪製至控制項的背景。</span><span class="sxs-lookup"><span data-stu-id="59e6f-103">You can draw text directly to the background of a control by converting a text string to a <xref:System.Windows.Media.FormattedText> object, and then drawing the object to the control's <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="59e6f-104">您也可以使用這項技術來繪製至衍生自 <xref:System.Windows.Controls.Panel>的物件背景，例如 <xref:System.Windows.Controls.Canvas> 和 <xref:System.Windows.Controls.StackPanel>。</span><span class="sxs-lookup"><span data-stu-id="59e6f-104">You can also use this technique for drawing to the background of objects derived from <xref:System.Windows.Controls.Panel>, such as <xref:System.Windows.Controls.Canvas> and <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
 <span data-ttu-id="59e6f-105">![將文字顯示為背景之控制項的螢幕擷取畫面。](./media/how-to-draw-text-to-a-control-background/draw-text-background.png "DrawText2Background01")</span><span class="sxs-lookup"><span data-stu-id="59e6f-105">![Screenshot of controls displaying text as background.](./media/how-to-draw-text-to-a-control-background/draw-text-background.png "DrawText2Background01")</span></span>  
<span data-ttu-id="59e6f-106">含自訂文字背景的控制項範例</span><span class="sxs-lookup"><span data-stu-id="59e6f-106">Example of controls with custom text backgrounds</span></span>  
  
## <a name="example"></a><span data-ttu-id="59e6f-107">範例</span><span class="sxs-lookup"><span data-stu-id="59e6f-107">Example</span></span>  
 <span data-ttu-id="59e6f-108">若要繪製至控制項的背景，請建立新的 <xref:System.Windows.Media.DrawingBrush> 物件，並將已轉換的文字繪製至物件的 <xref:System.Windows.Media.DrawingContext>。</span><span class="sxs-lookup"><span data-stu-id="59e6f-108">To draw to the background of a control, create a new <xref:System.Windows.Media.DrawingBrush> object and draw the converted text to the object's <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="59e6f-109">然後，將新的 <xref:System.Windows.Media.DrawingBrush> 指派給控制項的 background 屬性。</span><span class="sxs-lookup"><span data-stu-id="59e6f-109">Then, assign the new <xref:System.Windows.Media.DrawingBrush> to the control's background property.</span></span>  
  
 <span data-ttu-id="59e6f-110">下列程式碼範例示範如何建立 <xref:System.Windows.Media.FormattedText> 物件，並繪製至 <xref:System.Windows.Controls.Label> 和 <xref:System.Windows.Controls.Button> 物件的背景。</span><span class="sxs-lookup"><span data-stu-id="59e6f-110">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and draw to the background of a <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Button> object.</span></span>  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a><span data-ttu-id="59e6f-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="59e6f-111">See also</span></span>

- <xref:System.Windows.Media.FormattedText>
- [<span data-ttu-id="59e6f-112">繪製格式化的文字</span><span class="sxs-lookup"><span data-stu-id="59e6f-112">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
