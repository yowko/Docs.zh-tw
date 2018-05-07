---
title: 如何：建立外框文字
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], linear gradient brush
- outlined text [WPF]
- gradient brush [WPF]
- linear gradient brush [WPF]
- typography [WPF], outline effects
ms.assetid: 4aa3cf6e-1953-4f26-8230-7c1409e5f28d
ms.openlocfilehash: c79f5c1c6812b1175119133664e39995af29bd4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-outlined-text"></a>如何：建立外框文字
在大部分情況下，當您加入裝飾中的文字字串時您[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]應用程式中，使用的文字方面的不連續字元或圖像 （glyph） 集合。 例如，您無法建立線形漸層筆刷並進行套用，以便<xref:System.Windows.Controls.Control.Foreground%2A>屬性<xref:System.Windows.Controls.TextBox>物件。 當您顯示或編輯文字方塊中時，線性漸層筆刷會自動套用至目前資料集的文字字串中的字元。  
  
 ![以線性漸層筆刷顯示的文字](../../../../docs/framework/wpf/advanced/media/outlinedtext01.jpg "OutlinedText01")  
線性漸層筆刷套用至文字方塊中的範例  
  
 不過，您也可以轉換成文字<xref:System.Windows.Media.Geometry>物件，可讓您建立其他類型的視覺化 rtf 文字。 例如，您可以建立<xref:System.Windows.Media.Geometry>物件根據外框的文字字串。  
  
 ![使用線性漸層筆刷文字外框](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")  
線性漸層筆刷套用至文字的外框的幾何的範例  
  
 當文字轉換成<xref:System.Windows.Media.Geometry>物件，它不會再為字元的集合，您無法修改的文字字串中的字元。 不過，您可以修改其筆劃與填滿屬性來影響轉換文字的外觀。 筆劃是指轉換文字的外框，填滿是指轉換文字外框內的區域。  
  
 下列範例會說明數種方式建立視覺效果，藉由修改筆劃和轉換的文字的填滿。  
  
 ![使用不同填色和筆觸色彩的文字](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")  
設定筆劃並填滿不同色彩的範例  
  
 ![影像筆刷套用至筆觸的文字](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")  
影像筆刷套用至筆劃的範例  
  
 它也可修改的週框方塊矩形或反白顯示轉換的文字。 下列範例會示範如何建立視覺效果藉由修改筆劃和反白顯示的轉換的文字。  
  
 ![影像筆刷套用至筆觸的文字](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")  
影像筆刷套用至筆劃並反白顯示的範例  
  
## <a name="example"></a>範例  
 要轉換的文字的索引鍵<xref:System.Windows.Media.Geometry>物件是使用<xref:System.Windows.Media.FormattedText>物件。 當您建立此物件之後時，您可以使用<xref:System.Windows.Media.FormattedText.BuildGeometry%2A>和<xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A>方法，以將文字轉換成<xref:System.Windows.Media.Geometry>物件。 第一種方法傳回之幾何的格式化的文字。第二個方法會傳回之幾何的格式化文字的週框方塊。 下列程式碼範例示範如何建立<xref:System.Windows.Media.FormattedText>物件，以及擷取格式化的文字和其周框方塊的幾何。  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 若要顯示擷取<xref:System.Windows.Media.Geometry>物件，您需要存取<xref:System.Windows.Media.DrawingContext>轉換的文字中顯示的物件。 在這些程式碼範例中，這是藉由建立衍生自的類別，以支援使用者定義轉換的自訂控制項物件。  
  
 若要顯示<xref:System.Windows.Media.Geometry>自訂控制項中的物件提供的覆寫<xref:System.Windows.UIElement.OnRender%2A>方法。 覆寫的方法應該使用<xref:System.Windows.Media.DrawingContext.DrawGeometry%2A>方法繪製<xref:System.Windows.Media.Geometry>物件。  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
## <a name="see-also"></a>另請參閱  
 [繪製格式化的文字](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)
