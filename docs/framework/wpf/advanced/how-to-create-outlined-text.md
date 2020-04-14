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
ms.openlocfilehash: 86bfa396a2aa44eb511c014687501d60e170a396
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278921"
---
# <a name="how-to-create-outlined-text"></a>如何:建立大綱文字

在大多數情況下,當您在[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]應用程式中向文字字串添加修飾時,您將使用文本作為離散字元或字形的集合。 例如,您可以創建線性漸變畫筆並將其應用於<xref:System.Windows.Controls.Control.Foreground%2A><xref:System.Windows.Controls.TextBox>物件的屬性。 顯示或編輯文字框時,線性漸變畫筆將自動應用於文字字串中的當前字元集。  
  
 ![以線性漸層筆刷顯示的文字](./media/how-to-create-outlined-text/text-linear-gradient.jpg)
  
 但是,您還可以將文本轉換為<xref:System.Windows.Media.Geometry>對象,從而創建其他類型的視覺豐富的文本。 例如,可以基於文本字串的<xref:System.Windows.Media.Geometry>輪廓創建物件。  
  
 ![以線性漸層筆刷繪製外框的文字](./media/how-to-create-outlined-text/text-outline-linear-gradient.jpg)  
  
 將文字轉換為物件時<xref:System.Windows.Media.Geometry>,它不再是字元的集合,無法修改文本字串中的字元。 不過，您可以修改其筆劃與填滿屬性來影響轉換文字的外觀。 筆劃是指轉換文字的外框，填滿是指轉換文字外框內的區域。  
  
 以下範例說明了透過修改描邊和填充轉換文本來創建視覺效果的幾種方法。  
  
 ![使用不同填色和筆觸色彩的文字](./media/how-to-create-outlined-text/fill-stroke-text-effect.jpg)  
  
 ![影像筆刷套用至筆觸的文字](./media/how-to-create-outlined-text/image-brush-application.jpg)
  
 還可以修改轉換文本的邊界框矩形或高光。 下面的範例說明了透過修改轉換文本的描邊和高光來創建視覺效果的方法。  
  
 ![套用影像筆刷描邊和高光的文字](./media/how-to-create-outlined-text/image-brush-text-application.jpg)

## <a name="example"></a>範例  
 將文字轉換為<xref:System.Windows.Media.Geometry>對象的鍵是<xref:System.Windows.Media.FormattedText>使用該 物件。 建立此物件後,可以使用<xref:System.Windows.Media.FormattedText.BuildGeometry%2A>和<xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A>方法將文本轉換為<xref:System.Windows.Media.Geometry>物件。 第一種方法返回格式化文本的幾何體;第二種方法返回格式化文本的邊界框的幾何體。 以下代碼示例演示如何創建<xref:System.Windows.Media.FormattedText>對象並檢索格式化文本及其邊界框的幾何體。  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 為了顯示檢索到<xref:System.Windows.Media.Geometry>的物件,您需要存<xref:System.Windows.Media.DrawingContext>取 顯示轉換文本的物件。 在這些代碼示例中,通過創建從支援使用者定義的呈現的類派生的自定義控制項物件來實現此訪問。  
  
 要在<xref:System.Windows.Media.Geometry>自定義控制項中顯示物件,請<xref:System.Windows.UIElement.OnRender%2A>為方法提供重寫。 重寫的方法應使用<xref:System.Windows.Media.DrawingContext.DrawGeometry%2A>方法<xref:System.Windows.Media.Geometry>繪製 物件。  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
  有關範例自定義使用者控制件物件的源,請參閱[C# 和](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs)[大綱文本控制.vb 的 OutlineTextControl.cs。](https://github.com/dotnet/docs/blob/master/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb)
  
## <a name="see-also"></a>另請參閱

- [繪製格式化的文字](drawing-formatted-text.md)
