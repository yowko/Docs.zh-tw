---
title: HOW TO：控制複合圖形的填色
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], composite [WPF], controlling fill
- composite shapes [WPF], controlling fill
- graphics [WPF], composite shapes
- fill [WPF], controlling
ms.assetid: c1c94575-9eca-48a5-a49a-2ec65259f229
ms.openlocfilehash: 9b3ab1f7b81c296aa1ee766136b6c95b82cab105
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084046"
---
# <a name="how-to-control-the-fill-of-a-composite-shape"></a>HOW TO：控制複合圖形的填色
<xref:System.Windows.Media.GeometryGroup.FillRule%2A>的屬性<xref:System.Windows.Media.GeometryGroup>或<xref:System.Windows.Media.PathGeometry>，指定一個 「 規則 」 會使用複合圖案用來判斷指定的點是否為幾何的一部分。 有兩個可能的值，如<xref:System.Windows.Media.FillRule>:<xref:System.Windows.Media.FillRule.EvenOdd>和<xref:System.Windows.Media.FillRule.Nonzero>。 以下各節將說明如何使用這兩個規則。  
  
 **EvenOdd:** 此規則會判斷某個點是否在填滿區域中，藉由從該點朝任意方向繪製無限遠的光線，並且計算給定圖案中與光線相交中的路徑區段數目。 如果這個數字是奇數，該點即是在區域內；如為偶數，該點即在區域外。  
  
 例如，下列 XAML 會建立一系列同心環 （目標） 所組成的複合圖案<xref:System.Windows.Media.GeometryGroup.FillRule%2A>設定為<xref:System.Windows.Media.FillRule.EvenOdd>。  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleEvenOddValue](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillruleevenoddvalue)]  
  
 下圖顯示上一個範例中所建立的圖案。  
  
 ![螢幕擷取畫面：EvenOdd Fillrule](./media/fillruleevenoddfirstone.png "FillRuleEvenOddFirstOne")  
  
 在上圖中，請注意中間和第 3 個環形不會填滿。 這是因為從這兩個環形中的任何點所繪製的光線，會通過偶數數目的線段。 請參閱下圖︰  
  
 ![圖表：為 EvenOdd 的 FillRule 屬性值](./media/fillruleevenodd2.png "FillRuleEvenOdd2")  
  
 **非零值：** 此規則會判斷某個點是否在路徑填滿區域中，從該點朝任意方向繪製無限遠的光線，然後檢查圖案線段與光線交的所在的位置。 從零開始計算，路徑線段每次從左到右與光線交會就加一，每次從右到左與光線交會就減一。 計算交會後，如果結果為零，則點即在路徑外。 否則就在路徑內。  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValueEllipseGeometry](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovalueellipsegeometry)]  
  
 使用上述的值範例<xref:System.Windows.Media.FillRule.Nonzero>針對<xref:System.Windows.Media.GeometryGroup.FillRule%2A>因此提供下圖：  
  
 ![螢幕擷取畫面：NonZero fillrule](./media/fillrulenonzero1.png "FillRuleNonZero1")  
  
 如您所見，所有環形都會填滿。 這是因為所有的線段都是相同的方向，因此從任何點所繪製的光線會與一或多個線段交會，而相交的總和不等於零。 例如，在下圖中，紅色箭頭代表繪製線段的方向，而白色箭頭代表從最內側環形中的點射出的任意光線。 起始值為零，針對光線交會的每個線段，值會增加 1，因為線段由左至右與光線交會。  
  
 ![圖表：屬性值等於 NonZero FillRule](./media/fillrulenonzero2.png "FillRuleNonZero2")  
  
 若要更適當展現的行為<xref:System.Windows.Media.FillRule.Nonzero>規則更複雜的圖形具有不同方向的區段是必要。 下列 XAML 程式碼會建立在上一個範例所示形狀相似之處在於它使用建立<xref:System.Windows.Media.PathGeometry>而不是然後<xref:System.Windows.Media.EllipseGeometry>這會建立四個同心弧而不是完全封閉的同心圓。  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValuePathGeometry](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovaluepathgeometry)]  
  
 下圖顯示上一個範例中所建立的圖案。  
  
 ![螢幕擷取畫面：FillRule 屬性值為 NonZero](./media/fillrulenonzero3.png "FillRuleNonZero3")  
  
 請注意，由中心開始的第三個弧形不會填滿。 下圖說明其原因。 在圖中，紅色箭頭代表繪製線段的方向。 兩個白色箭頭代表兩個從「未填滿」區域中的點射出的任意光線。 從圖中可以看出，交會線段的指定光線，在其路徑中之值的總和為零。 如上面所定義，總和為零表示該點不屬於幾何的一部分 (並非填滿的一部分)，而「非」零的總和 (包含負值) 則屬於幾何的一部分。  
  
 ![圖表：FillRule 屬性值為 NonZero](./media/fillrulenonzero4.png "FillRuleNonZero4")  
  
 **注意：** 針對目的<xref:System.Windows.Media.FillRule>，所有圖案都視為封閉式。 如果線段中有間隙，請繪製虛構線段將它封閉。 在上面的範例中，環形中有小型的間隙。 有鑑於此，我們可能會預期通過間隙射出的光線，會提供與另一個方向的光線不同的結果。 以下是其中一個間隙以及 「 虛構線段 」 的放大的圖 (基於套用繪製的線段<xref:System.Windows.Media.FillRule>)，將它關閉。  
  
 ![圖表：針對 FillRule，區段保持關閉](./media/fillruleclosedshapes.png "FillRuleClosedShapes")  
  
## <a name="example"></a>範例  
  
## <a name="see-also"></a>另請參閱

- [建立複合圖形](how-to-create-a-composite-shape.md)
- [幾何概觀](geometry-overview.md)
