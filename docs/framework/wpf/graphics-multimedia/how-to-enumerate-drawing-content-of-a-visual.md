---
title: HOW TO：列舉視覺物件的繪圖內容
ms.date: 03/30/2017
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
ms.openlocfilehash: 4f0afc1075fe66c7f154fcef3cd883709db55316
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108000"
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a>HOW TO：列舉視覺物件的繪圖內容
<xref:System.Windows.Media.Drawing>物件提供列舉的內容的物件模型<xref:System.Windows.Media.Visual>。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A>方法來擷取<xref:System.Windows.Media.DrawingGroup>的值<xref:System.Windows.Media.Visual>並列舉它。  
  
> [!NOTE]
>  當您要列舉的視覺效果內容時，您要擷取<xref:System.Windows.Media.Drawing>物件和不基礎表示法的轉譯資料作為向量圖形指示清單。 如需詳細資訊，請參閱 [WPF 圖形轉譯概觀](wpf-graphics-rendering-overview.md)。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.VisualTreeHelper>
- [繪圖物件概觀](drawing-objects-overview.md)
- [WPF 圖形轉譯概觀](wpf-graphics-rendering-overview.md)
