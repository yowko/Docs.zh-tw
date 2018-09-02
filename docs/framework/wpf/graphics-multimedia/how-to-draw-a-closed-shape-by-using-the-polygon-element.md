---
title: 如何：使用 Polygon 項目繪製封閉的形狀
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], Polygon elements
- closed shapes [WPF], drawing with Polygon elements
- Polygon elements [WPF]
- drawing [WPF], closed shapes with Polygon elements
ms.assetid: 4b0ca008-29ce-48dd-8bc3-f3a20ffca6a6
ms.openlocfilehash: 89c78877e196e803f6b4139ffcfa2b4def1a07d7
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43468088"
---
# <a name="how-to-draw-a-closed-shape-by-using-the-polygon-element"></a>如何：使用 Polygon 項目繪製封閉的形狀
此範例示範如何使用來繪製封閉的形狀<xref:System.Windows.Shapes.Polygon>項目。 若要繪製封閉的形狀，建立<xref:System.Windows.Shapes.Polygon>項目，並使用其<xref:System.Windows.Shapes.Polygon.Points%2A>屬性來指定圖形的頂點。 自動繪製線條連接的第一個和最後一個點。 最後，指定<xref:System.Windows.Shapes.Shape.Fill%2A>、 <xref:System.Windows.Shapes.Shape.Stroke%2A>，或兩者。  
  
## <a name="example"></a>範例  
 在  [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，有效的語法，點是以逗號分隔的 x 和 y 座標組的逗號分隔清單。  
  
 [!code-xaml[drawingwithshapeelements#PolygonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polygonexample.xaml#polygonexample1)]  
  
 雖然此範例會使用<xref:System.Windows.Controls.Canvas>包含多邊形，您可以使用 polygon 項目 （和其他圖形元素） 與任何<xref:System.Windows.Controls.Panel>或<xref:System.Windows.Controls.Control>支援非文字內容。  
  
 這個範例屬於較大型的範例;如需完整的範例，請參閱[圖形元素範例](https://go.microsoft.com/fwlink/?LinkID=160037)。
