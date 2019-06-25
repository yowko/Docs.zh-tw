---
title: 作法：使用 StreamGeometry 建立圖形
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], shapes
- shapes [WPF], creating with StreamGeometry class
ms.assetid: 08f7c8ce-074b-49cd-9aba-cc9592d4ee51
ms.openlocfilehash: ce2097568349ad376540163f5fe05d6a3e5b0643
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348022"
---
# <a name="how-to-create-a-shape-using-a-streamgeometry"></a>HOW TO：使用 StreamGeometry 建立圖形
<xref:System.Windows.Media.StreamGeometry> 是輕量型替代方案<xref:System.Windows.Media.PathGeometry>來建立幾何圖形。 使用<xref:System.Windows.Media.StreamGeometry>當您需要描繪複雜幾何，但不是想資料繫結、 動畫或修改的額外負荷。 例如，因為其效率，<xref:System.Windows.Media.StreamGeometry>類別是不錯的選擇來描繪裝飾項。  
  
## <a name="example"></a>範例  
 下列範例會使用屬性語法以建立三角形<xref:System.Windows.Media.StreamGeometry>在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 如需詳細資訊<xref:System.Windows.Media.StreamGeometry>屬性的語法，請參閱[路徑標記語法](path-markup-syntax.md)頁面。  
  
## <a name="example"></a>範例  
 下一個範例使用<xref:System.Windows.Media.StreamGeometry>在程式碼中定義三角形。 首先，此範例會建立<xref:System.Windows.Media.StreamGeometry>，然後取得<xref:System.Windows.Media.StreamGeometryContext>並使用它來說明該三角形。  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryTriangleExample.cs#streamgeometrytriangleexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometrytriangleexample.vb#streamgeometrytriangleexamplewholepage)]  
  
## <a name="example"></a>範例  
 下一個範例會建立可使用的方法<xref:System.Windows.Media.StreamGeometry>和<xref:System.Windows.Media.StreamGeometryContext>定義幾何圖案，根據指定的參數。  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryExample.cs#streamgeometryexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometryexample.vb#streamgeometryexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Media.StreamGeometry>
- <xref:System.Windows.Media.StreamGeometryContext>
- [使用 PathGeometry 建立圖案](how-to-create-a-shape-by-using-a-pathgeometry.md)
- [幾何概觀](geometry-overview.md)
