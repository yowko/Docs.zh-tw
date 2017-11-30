---
title: "如何：繪製文字至控制項的背景"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], drawing text to backgrounds
- text [WPF], drawing to control backgrounds
- drawing [WPF], text to control backgrounds
- backgrounds [WPF], drawing text to
- typography [WPF], drawing text to control backgrounds
ms.assetid: 686d8fba-f61c-4974-a871-c635d67a7f69
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f0c98422e337678e68a8e4b72979635e8c867b4f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-text-to-a-control39s-background"></a>如何：繪製文字至控制項的背景
您可以直接對控制項的背景繪製文字的文字字串轉換成<xref:System.Windows.Media.FormattedText>物件，然後再加入控制項的繪製物件<xref:System.Windows.Media.DrawingContext>。 您也可以使用這項技術，物件的背景繪製衍生自<xref:System.Windows.Controls.Panel>，例如<xref:System.Windows.Controls.Canvas>和<xref:System.Windows.Controls.StackPanel>。  
  
 ![控制項文字當做背景顯示](../../../../docs/framework/wpf/advanced/media/drawtext2background01.png "DrawText2Background01")  
含自訂文字背景的控制項範例  
  
## <a name="example"></a>範例  
 若要繪製控制項的背景，建立新<xref:System.Windows.Media.DrawingBrush>物件，並繪製物件的轉換的文字<xref:System.Windows.Media.DrawingContext>。 然後，將指派新<xref:System.Windows.Media.DrawingBrush>至控制項的背景屬性。  
  
 下列程式碼範例示範如何建立<xref:System.Windows.Media.FormattedText>物件，並繪製背景的<xref:System.Windows.Controls.Label>和<xref:System.Windows.Controls.Button>物件。  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.FormattedText>  
 [繪製格式化的文字](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)
