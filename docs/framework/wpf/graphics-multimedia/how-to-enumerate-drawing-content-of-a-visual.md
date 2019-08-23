---
title: 作法：列舉視覺物件的繪圖內容
ms.date: 03/30/2017
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
ms.openlocfilehash: 25aa0c3706005c1e16cedd7e06914db764545ebb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930075"
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a>HOW TO：列舉視覺物件的繪圖內容
物件提供用<xref:System.Windows.Media.Visual>來列舉內容的物件模型。 <xref:System.Windows.Media.Drawing>  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A>方法來<xref:System.Windows.Media.DrawingGroup>取出的值<xref:System.Windows.Media.Visual> , 並加以列舉。  
  
> [!NOTE]
> 當您列舉視覺效果的內容時, 您會抓取<xref:System.Windows.Media.Drawing>物件, 而不是以向量圖形指示清單的形式呈現資料的基礎標記法。 如需詳細資訊，請參閱 [WPF 圖形轉譯概觀](wpf-graphics-rendering-overview.md)。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.VisualTreeHelper>
- [繪圖物件概觀](drawing-objects-overview.md)
- [WPF 圖形轉譯概觀](wpf-graphics-rendering-overview.md)
