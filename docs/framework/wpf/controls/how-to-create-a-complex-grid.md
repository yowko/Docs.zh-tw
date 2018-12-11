---
title: 如何建立複雜格線
description: 如何建立如下所示的每月的行事曆的版面配置使用方格控制項範例。
ms.date: 03/30/2017
helpviewer_keywords:
- calendar [WPF], creating
- monthly calendar [WPF], creating
- Grid control [WPF], creating [WPF], complex grid
ms.assetid: 4ce3040a-a156-4364-9596-98ca1eca5550
ms.openlocfilehash: e2356113457e8c9a6737132e9779e49c05a23d77
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149779"
---
# <a name="how-to-create-a-complex-grid"></a><span data-ttu-id="c1134-103">如何建立複雜格線</span><span class="sxs-lookup"><span data-stu-id="c1134-103">How to create a complex Grid</span></span>

<span data-ttu-id="c1134-104">此範例示範如何使用<xref:System.Windows.Controls.Grid>建立如下所示的每月的行事曆的版面配置控制項。</span><span class="sxs-lookup"><span data-stu-id="c1134-104">This example shows how to use a <xref:System.Windows.Controls.Grid> control to create a layout that looks like a monthly calendar.</span></span>

## <a name="example"></a><span data-ttu-id="c1134-105">範例</span><span class="sxs-lookup"><span data-stu-id="c1134-105">Example</span></span>

<span data-ttu-id="c1134-106">下列範例定義了八個資料列和八個資料行使用<xref:System.Windows.Controls.RowDefinition>和<xref:System.Windows.Controls.ColumnDefinition>類別。</span><span class="sxs-lookup"><span data-stu-id="c1134-106">The following example defines eight rows and eight columns by using the <xref:System.Windows.Controls.RowDefinition> and <xref:System.Windows.Controls.ColumnDefinition> classes.</span></span> <span data-ttu-id="c1134-107">它會使用<xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType>並<xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType>附加屬性，並搭配<xref:System.Windows.Shapes.Rectangle>項目，填滿各種不同的資料行和資料列的背景。</span><span class="sxs-lookup"><span data-stu-id="c1134-107">It uses the <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType> and <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType> attached properties, together with <xref:System.Windows.Shapes.Rectangle> elements, which fill the backgrounds of various columns and rows.</span></span> <span data-ttu-id="c1134-108">此設計可，因為多個項目可以存在於每個儲存格中<xref:System.Windows.Controls.Grid>，主要差異<xref:System.Windows.Controls.Grid>和<xref:System.Windows.Documents.Table>。</span><span class="sxs-lookup"><span data-stu-id="c1134-108">This design is possible because more than one element can exist in each cell in a <xref:System.Windows.Controls.Grid>, a principle difference between <xref:System.Windows.Controls.Grid> and <xref:System.Windows.Documents.Table>.</span></span>

<span data-ttu-id="c1134-109">此範例會使用垂直的漸層來<xref:System.Windows.Shapes.Shape.Fill%2A>的資料行和資料列來改善的視覺呈現方式和行事曆的可讀性。</span><span class="sxs-lookup"><span data-stu-id="c1134-109">The example uses vertical gradients to <xref:System.Windows.Shapes.Shape.Fill%2A> the columns and rows to improve the visual presentation and readability of the calendar.</span></span> <span data-ttu-id="c1134-110">樣式<xref:System.Windows.Controls.TextBlock>項目代表的日期和星期幾。</span><span class="sxs-lookup"><span data-stu-id="c1134-110">Styled <xref:System.Windows.Controls.TextBlock> elements represent the dates and days of the week.</span></span> <span data-ttu-id="c1134-111"><xref:System.Windows.Controls.TextBlock> 項目絕對定位在其儲存格使用<xref:System.Windows.FrameworkElement.Margin%2A>屬性和樣式的應用程式中所定義的對齊屬性。</span><span class="sxs-lookup"><span data-stu-id="c1134-111"><xref:System.Windows.Controls.TextBlock> elements are absolutely positioned within their cells by using the <xref:System.Windows.FrameworkElement.Margin%2A> property and alignment properties that are defined within the style for the application.</span></span>

[!code-xaml[GridComplex#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridComplex/CS/default.xaml#1)]

<span data-ttu-id="c1134-112">下圖顯示產生的控制項，可自訂的行事曆：</span><span class="sxs-lookup"><span data-stu-id="c1134-112">The following image shows the resulting control, a customizable calendar:</span></span>

![產生的控制項的螢幕擷取畫面](./media/how-to-create-a-complex-grid/wpf-manual-calendar.png)

## <a name="see-also"></a><span data-ttu-id="c1134-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1134-114">See also</span></span>

- <xref:System.Windows.Controls.Grid?displayProperty=nameWithType>
- <xref:System.Windows.Documents.TableCell?displayProperty=nameWithType>
- [<span data-ttu-id="c1134-115">使用純色和漸層繪製的概觀</span><span class="sxs-lookup"><span data-stu-id="c1134-115">Painting with Solid Colors and Gradients Overview</span></span>](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="c1134-116">面板概觀</span><span class="sxs-lookup"><span data-stu-id="c1134-116">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="c1134-117">資料表概觀</span><span class="sxs-lookup"><span data-stu-id="c1134-117">Table Overview</span></span>](../advanced/table-overview.md)