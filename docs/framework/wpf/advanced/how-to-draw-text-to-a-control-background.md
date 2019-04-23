---
title: HOW TO：在控制項的背景繪製文字
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], drawing text to backgrounds
- text [WPF], drawing to control backgrounds
- drawing [WPF], text to control backgrounds
- backgrounds [WPF], drawing text to
- typography [WPF], drawing text to control backgrounds
ms.assetid: 686d8fba-f61c-4974-a871-c635d67a7f69
ms.openlocfilehash: 76449c88f9a720741c8ed61255e04a40e6a8613f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59128449"
---
# <a name="how-to-draw-text-to-a-controls-background"></a><span data-ttu-id="af037-102">HOW TO：在控制項的背景繪製文字</span><span class="sxs-lookup"><span data-stu-id="af037-102">How to: Draw Text to a Control's Background</span></span>
<span data-ttu-id="af037-103">您也可以將文字字串轉換為直接至控制項背景繪製文字<xref:System.Windows.Media.FormattedText>物件，然後再將物件繪製至控制項的<xref:System.Windows.Media.DrawingContext>。</span><span class="sxs-lookup"><span data-stu-id="af037-103">You can draw text directly to the background of a control by converting a text string to a <xref:System.Windows.Media.FormattedText> object, and then drawing the object to the control's <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="af037-104">您也可以使用這項技術，繪製到背景工作的物件衍生自<xref:System.Windows.Controls.Panel>，這類<xref:System.Windows.Controls.Canvas>和<xref:System.Windows.Controls.StackPanel>。</span><span class="sxs-lookup"><span data-stu-id="af037-104">You can also use this technique for drawing to the background of objects derived from <xref:System.Windows.Controls.Panel>, such as <xref:System.Windows.Controls.Canvas> and <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
 <span data-ttu-id="af037-105">![文字顯示為背景的控制項](./media/drawtext2background01.png "DrawText2Background01")</span><span class="sxs-lookup"><span data-stu-id="af037-105">![Controls displaying text as background](./media/drawtext2background01.png "DrawText2Background01")</span></span>  
<span data-ttu-id="af037-106">含自訂文字背景的控制項範例</span><span class="sxs-lookup"><span data-stu-id="af037-106">Example of controls with custom text backgrounds</span></span>  
  
## <a name="example"></a><span data-ttu-id="af037-107">範例</span><span class="sxs-lookup"><span data-stu-id="af037-107">Example</span></span>  
 <span data-ttu-id="af037-108">若要繪製至控制項的背景，請建立新<xref:System.Windows.Media.DrawingBrush>物件，並轉換的文字繪製至物件的<xref:System.Windows.Media.DrawingContext>。</span><span class="sxs-lookup"><span data-stu-id="af037-108">To draw to the background of a control, create a new <xref:System.Windows.Media.DrawingBrush> object and draw the converted text to the object's <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="af037-109">然後，指派給新<xref:System.Windows.Media.DrawingBrush>至控制項的背景屬性。</span><span class="sxs-lookup"><span data-stu-id="af037-109">Then, assign the new <xref:System.Windows.Media.DrawingBrush> to the control's background property.</span></span>  
  
 <span data-ttu-id="af037-110">下列程式碼範例示範如何建立<xref:System.Windows.Media.FormattedText>物件，並繪製至背景<xref:System.Windows.Controls.Label>和<xref:System.Windows.Controls.Button>物件。</span><span class="sxs-lookup"><span data-stu-id="af037-110">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and draw to the background of a <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Button> object.</span></span>  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a><span data-ttu-id="af037-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af037-111">See also</span></span>

- <xref:System.Windows.Media.FormattedText>
- [<span data-ttu-id="af037-112">繪製格式化的文字</span><span class="sxs-lookup"><span data-stu-id="af037-112">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
