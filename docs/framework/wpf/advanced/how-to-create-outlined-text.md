---
title: HOW TO：建立外框文字
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
ms.openlocfilehash: 5de1068401dac61c5de5b86604da9417e18a94ae
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58125937"
---
# <a name="how-to-create-outlined-text"></a>HOW TO：建立外框文字
在大部分情況下，當您要新增到文字字串中的裝飾您[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]應用程式中，您使用的以不連續的字元或圖像 （glyph） 的集合的文字。 例如，您可以建立線形漸層筆刷，並將它套用至<xref:System.Windows.Controls.Control.Foreground%2A>屬性<xref:System.Windows.Controls.TextBox>物件。 當您顯示或編輯文字方塊中時，線性漸層筆刷會自動套用至目前集合中的文字字串的字元。  
  
 ![以線性漸層筆刷顯示的文字](./media/how-to-create-outlined-text/text-linear-gradient.jpg)    
  
 不過，您也可以轉換成文字<xref:System.Windows.Media.Geometry>物件，可讓您建立其他類型的視覺效果豐富的文字。 例如，您可以在其中建立<xref:System.Windows.Media.Geometry>物件根據文字字串的外框。  
  
 ![以線性漸層筆刷繪製外框的文字](./media/how-to-create-outlined-text/text-outline-linear-gradient.jpg)  
  
 當文字轉換成<xref:System.Windows.Media.Geometry>物件時，它不再是字元集合，您無法修改文字字串中的字元。 不過，您可以修改其筆劃與填滿屬性來影響轉換文字的外觀。 筆劃是指轉換文字的外框，填滿是指轉換文字外框內的區域。  
  
 下列範例說明幾個方法可透過修改筆劃並填滿轉換的文字建立視覺效果。  
  
 ![使用不同填色和筆觸色彩的文字](./media/how-to-create-outlined-text/fill-stroke-text-effect.jpg)  
  
 ![影像筆刷套用至筆觸的文字](./media/how-to-create-outlined-text/image-brush-application.jpg)
  
 它也可修改的週框方塊矩形或反白顯示轉換的文字。 下列範例會說明建立視覺效果的方式，透過修改筆劃並反白顯示轉換的文字。  
  
 ![影像筆刷套用至描邊，並反白顯示的文字](./media/how-to-create-outlined-text/image-brush-text-application.jpg)

## <a name="example"></a>範例  
 要轉換文字的索引鍵<xref:System.Windows.Media.Geometry>物件是使用<xref:System.Windows.Media.FormattedText>物件。 當您建立此物件之後時，您可以使用<xref:System.Windows.Media.FormattedText.BuildGeometry%2A>並<xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A>方法，以將文字轉換成<xref:System.Windows.Media.Geometry>物件。 第一種方法會傳回格式化文字; geometry第二個方法會傳回之幾何的格式化文字的週框方塊。 下列程式碼範例示範如何建立<xref:System.Windows.Media.FormattedText>物件並擷取格式化的文字和其週框方塊的幾何。  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 若要顯示所擷取<xref:System.Windows.Media.Geometry>物件，您需要存取<xref:System.Windows.Media.DrawingContext>顯示轉換的文字的物件。 在這些程式碼範例中，這是由建立衍生自的類別，以支援使用者定義轉換的自訂控制項物件。  
  
 若要顯示<xref:System.Windows.Media.Geometry>在自訂控制項中，物件所提供的覆寫<xref:System.Windows.UIElement.OnRender%2A>方法。 覆寫的方法應該使用<xref:System.Windows.Media.DrawingContext.DrawGeometry%2A>方法來繪製<xref:System.Windows.Media.Geometry>物件。  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
  範例自訂使用者控制項物件的來源，請參閱[OutlineTextControl.cs 的C#](https://github.com/dotnet/samples/blob/master/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs)並[OutlineTextControl.vb Visual basic](https://github.com/dotnet/samples/blob/master/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb)。 
  
## <a name="see-also"></a>另請參閱
- [繪製格式化的文字](drawing-formatted-text.md)
