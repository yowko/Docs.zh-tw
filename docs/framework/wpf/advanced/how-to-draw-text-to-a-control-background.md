---
title: HOW TO：繪製文字至控制項的背景
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], drawing text to backgrounds
- text [WPF], drawing to control backgrounds
- drawing [WPF], text to control backgrounds
- backgrounds [WPF], drawing text to
- typography [WPF], drawing text to control backgrounds
ms.assetid: 686d8fba-f61c-4974-a871-c635d67a7f69
ms.openlocfilehash: 025b13d83aeb668fa3a9f8af35d7213ae677eefc
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378739"
---
# <a name="how-to-draw-text-to-a-controls-background"></a>HOW TO：繪製文字至控制項的背景
您也可以將文字字串轉換為直接至控制項背景繪製文字<xref:System.Windows.Media.FormattedText>物件，然後再將物件繪製至控制項的<xref:System.Windows.Media.DrawingContext>。 您也可以使用這項技術，繪製到背景工作的物件衍生自<xref:System.Windows.Controls.Panel>，這類<xref:System.Windows.Controls.Canvas>和<xref:System.Windows.Controls.StackPanel>。  
  
 ![文字顯示為背景的控制項](./media/drawtext2background01.png "DrawText2Background01")  
含自訂文字背景的控制項範例  
  
## <a name="example"></a>範例  
 若要繪製至控制項的背景，請建立新<xref:System.Windows.Media.DrawingBrush>物件，並轉換的文字繪製至物件的<xref:System.Windows.Media.DrawingContext>。 然後，指派給新<xref:System.Windows.Media.DrawingBrush>至控制項的背景屬性。  
  
 下列程式碼範例示範如何建立<xref:System.Windows.Media.FormattedText>物件，並繪製至背景<xref:System.Windows.Controls.Label>和<xref:System.Windows.Controls.Button>物件。  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Media.FormattedText>
- [繪製格式化的文字](drawing-formatted-text.md)
