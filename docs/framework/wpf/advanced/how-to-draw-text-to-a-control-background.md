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
# <a name="how-to-draw-text-to-a-controls-background"></a>如何：繪製文字至控制項的背景
您可以藉由將文字字串轉換為 <xref:System.Windows.Media.FormattedText> 物件，然後將物件繪製至控制項的 <xref:System.Windows.Media.DrawingContext>，直接將文字繪製至控制項的背景。 您也可以使用這項技術來繪製至衍生自 <xref:System.Windows.Controls.Panel>的物件背景，例如 <xref:System.Windows.Controls.Canvas> 和 <xref:System.Windows.Controls.StackPanel>。  
  
 ![將文字顯示為背景之控制項的螢幕擷取畫面。](./media/how-to-draw-text-to-a-control-background/draw-text-background.png "DrawText2Background01")  
含自訂文字背景的控制項範例  
  
## <a name="example"></a>範例  
 若要繪製至控制項的背景，請建立新的 <xref:System.Windows.Media.DrawingBrush> 物件，並將已轉換的文字繪製至物件的 <xref:System.Windows.Media.DrawingContext>。 然後，將新的 <xref:System.Windows.Media.DrawingBrush> 指派給控制項的 background 屬性。  
  
 下列程式碼範例示範如何建立 <xref:System.Windows.Media.FormattedText> 物件，並繪製至 <xref:System.Windows.Controls.Label> 和 <xref:System.Windows.Controls.Button> 物件的背景。  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Media.FormattedText>
- [繪製格式化的文字](drawing-formatted-text.md)
