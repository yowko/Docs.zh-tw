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
ms.openlocfilehash: f79ec4f2c394fdc9462f4fd00942673b4536d713
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542973"
---
# <a name="how-to-draw-text-to-a-control39s-background"></a><span data-ttu-id="bb4c8-102">如何：繪製文字至控制項的背景</span><span class="sxs-lookup"><span data-stu-id="bb4c8-102">How to: Draw Text to a Control&#39;s Background</span></span>
<span data-ttu-id="bb4c8-103">您可以直接對控制項的背景繪製文字的文字字串轉換成<xref:System.Windows.Media.FormattedText>物件，然後再加入控制項的繪製物件<xref:System.Windows.Media.DrawingContext>。</span><span class="sxs-lookup"><span data-stu-id="bb4c8-103">You can draw text directly to the background of a control by converting a text string to a <xref:System.Windows.Media.FormattedText> object, and then drawing the object to the control's <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="bb4c8-104">您也可以使用這項技術，物件的背景繪製衍生自<xref:System.Windows.Controls.Panel>，例如<xref:System.Windows.Controls.Canvas>和<xref:System.Windows.Controls.StackPanel>。</span><span class="sxs-lookup"><span data-stu-id="bb4c8-104">You can also use this technique for drawing to the background of objects derived from <xref:System.Windows.Controls.Panel>, such as <xref:System.Windows.Controls.Canvas> and <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
 <span data-ttu-id="bb4c8-105">![控制項文字當做背景顯示](../../../../docs/framework/wpf/advanced/media/drawtext2background01.png "DrawText2Background01")</span><span class="sxs-lookup"><span data-stu-id="bb4c8-105">![Controls displaying text as background](../../../../docs/framework/wpf/advanced/media/drawtext2background01.png "DrawText2Background01")</span></span>  
<span data-ttu-id="bb4c8-106">含自訂文字背景的控制項範例</span><span class="sxs-lookup"><span data-stu-id="bb4c8-106">Example of controls with custom text backgrounds</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb4c8-107">範例</span><span class="sxs-lookup"><span data-stu-id="bb4c8-107">Example</span></span>  
 <span data-ttu-id="bb4c8-108">若要繪製控制項的背景，建立新<xref:System.Windows.Media.DrawingBrush>物件，並繪製物件的轉換的文字<xref:System.Windows.Media.DrawingContext>。</span><span class="sxs-lookup"><span data-stu-id="bb4c8-108">To draw to the background of a control, create a new <xref:System.Windows.Media.DrawingBrush> object and draw the converted text to the object's <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="bb4c8-109">然後，將指派新<xref:System.Windows.Media.DrawingBrush>至控制項的背景屬性。</span><span class="sxs-lookup"><span data-stu-id="bb4c8-109">Then, assign the new <xref:System.Windows.Media.DrawingBrush> to the control's background property.</span></span>  
  
 <span data-ttu-id="bb4c8-110">下列程式碼範例示範如何建立<xref:System.Windows.Media.FormattedText>物件，並繪製背景的<xref:System.Windows.Controls.Label>和<xref:System.Windows.Controls.Button>物件。</span><span class="sxs-lookup"><span data-stu-id="bb4c8-110">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and draw to the background of a <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Button> object.</span></span>  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a><span data-ttu-id="bb4c8-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb4c8-111">See Also</span></span>  
 <xref:System.Windows.Media.FormattedText>  
 [<span data-ttu-id="bb4c8-112">繪製格式化的文字</span><span class="sxs-lookup"><span data-stu-id="bb4c8-112">Drawing Formatted Text</span></span>](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)
