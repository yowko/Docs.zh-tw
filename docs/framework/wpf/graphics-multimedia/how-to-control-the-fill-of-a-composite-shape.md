---
title: 作法：控制複合圖形的填色
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], composite [WPF], controlling fill
- composite shapes [WPF], controlling fill
- graphics [WPF], composite shapes
- fill [WPF], controlling
ms.assetid: c1c94575-9eca-48a5-a49a-2ec65259f229
ms.openlocfilehash: 89f69d392e8838af99538c759a2f06453e1bcd60
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855907"
---
# <a name="how-to-control-the-fill-of-a-composite-shape"></a>作法：控制複合圖形的填色

<xref:System.Windows.Media.GeometryGroup>或的屬性會指定「規則」 ，讓複合圖形用來判斷指定的點是否為幾何的一部分。<xref:System.Windows.Media.PathGeometry> <xref:System.Windows.Media.GeometryGroup.FillRule%2A> 有兩個可能的<xref:System.Windows.Media.FillRule>值： <xref:System.Windows.Media.FillRule.EvenOdd>和。 <xref:System.Windows.Media.FillRule.Nonzero> 以下各節將說明如何使用這兩個規則。

**EvenOdd**此規則會以任何方向繪製從該點到無限大的光線，並計算給定形狀中光線相交的路徑線段數目，藉此判斷某個點是否在填滿區域中。 如果這個數字是奇數，該點即是在區域內；如為偶數，該點即在區域外。

例如，下列 XAML 會建立由一系列的同心圓（目標）組成的複合圖形， <xref:System.Windows.Media.GeometryGroup.FillRule%2A>其設定為。 <xref:System.Windows.Media.FillRule.EvenOdd>

[!code-xaml[GeometriesMiscSnippets_snip#FillRuleEvenOddValue](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillruleevenoddvalue)]

下圖顯示上一個範例中所建立的圖案。

![由具有交替色彩的數列同心環組成的圓形。](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-evenodd-property.png)

在上圖中，請注意中央和第三個環形不會填滿。 這是因為從這兩個環形中的任何點所繪製的光線，會通過偶數數目的線段。 請參閱下圖：

![圖表，顯示在圓形中繪製的 EvenOdd 光線。](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-evenodd-rays.png)

**零下**此規則會以任何方向繪製從該點到無限大的光線，然後檢查圖形線段與光線相交的位置，藉以決定該點是否在路徑填滿區域中。 從零開始計算，路徑線段每次從左到右與光線交會就加一，每次從右到左與光線交會就減一。 計算交會後，如果結果為零，則點即在路徑外。 否則就在路徑內。

[!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValueEllipseGeometry](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovalueellipsegeometry)]

使用上述範例時，的值<xref:System.Windows.Media.FillRule.Nonzero> <xref:System.Windows.Media.GeometryGroup.FillRule%2A>會提供下圖的結果：

![由一連串同心環形組成的圓形，全都以相同的色彩填滿。](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-value-nonzero.png)

如您所見，所有環形都會填滿。 這是因為所有的線段都是相同的方向，因此從任何點所繪製的光線會與一或多個線段交會，而相交的總和不等於零。 例如，在下圖中，紅色箭號代表線段繪製的方向，而白色箭號代表從最內層環形的某個點執行的任意光線。 起始值為零，針對光線交會的每個線段，值會增加 1，因為線段由左至右與光線交會。

![顯示 FillRule 屬性值等於非零的圖表。](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-value-equal-nonzero.png)

為了更清楚地示範「 <xref:System.Windows.Media.FillRule.Nonzero>規則」的行為，需要以不同的方向執行區段。 下列 XAML 程式碼會建立與上一個範例類似的圖形，不同之處在于它<xref:System.Windows.Media.PathGeometry>是使用建立<xref:System.Windows.Media.EllipseGeometry>的，而後者會建立四個同心圓，而不是完全封閉的同心圓。

[!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValuePathGeometry](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovaluepathgeometry)]

下圖顯示上一個範例中所建立的圖案。

![由數列同心圓組成的圓形，其中包含未填滿第三個弧線的交替色彩。](./media/how-to-control-the-fill-of-a-composite-shape/pathgeometry-concentric-arcs.png)

請注意，由中心開始的第三個弧形不會填滿。 下圖顯示為何這種情況。 在圖中，紅色箭頭代表繪製線段的方向。 兩個白色箭頭代表兩個從「未填滿」區域中的點射出的任意光線。 從圖中可以看出，交會線段的指定光線，在其路徑中之值的總和為零。 如上面所定義，總和為零表示該點不屬於幾何的一部分 (並非填滿的一部分)，而「非」零的總和 (包含負值) 則屬於幾何的一部分。

![顯示任意光線交叉線段的圖表。](./media/how-to-control-the-fill-of-a-composite-shape/arbitrary-ray-cross-segment.png)

> [!NOTE]
> 基於的目的<xref:System.Windows.Media.FillRule>，所有圖形都會被視為已關閉。 如果線段中有間隙，請繪製虛構線段將它封閉。 在上面的範例中，環形中有小型的間隙。 有鑑於此，我們可能會預期通過間隙射出的光線，會提供與另一個方向的光線不同的結果。 以下是其中一個間距的放大圖，以及關閉它的「虛數區段」（針對套用所<xref:System.Windows.Media.FillRule>繪製的區段）。

![此圖顯示永遠關閉的 FillRule 區段。](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-closed-segments.png)

## <a name="example"></a>範例

## <a name="see-also"></a>另請參閱

- [建立複合圖案](how-to-create-a-composite-shape.md)
- [幾何概觀](geometry-overview.md)
