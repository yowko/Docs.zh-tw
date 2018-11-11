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
ms.sourcegitcommit: 5fd80619c760fa8c25d33a6f5661247cb65da465
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50743920"
---
# <a name="how-to-create-a-complex-grid"></a>如何建立複雜格線

此範例示範如何使用<xref:System.Windows.Controls.Grid>建立如下所示的每月的行事曆的版面配置控制項。

## <a name="example"></a>範例

下列範例定義了八個資料列和八個資料行使用<xref:System.Windows.Controls.RowDefinition>和<xref:System.Windows.Controls.ColumnDefinition>類別。 它會使用<xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType>並<xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType>附加屬性，並搭配<xref:System.Windows.Shapes.Rectangle>項目，填滿各種不同的資料行和資料列的背景。 此設計可，因為多個項目可以存在於每個儲存格中<xref:System.Windows.Controls.Grid>，主要差異<xref:System.Windows.Controls.Grid>和<xref:System.Windows.Documents.Table>。

此範例會使用垂直的漸層來<xref:System.Windows.Shapes.Shape.Fill%2A>的資料行和資料列來改善的視覺呈現方式和行事曆的可讀性。 樣式<xref:System.Windows.Controls.TextBlock>項目代表的日期和星期幾。 <xref:System.Windows.Controls.TextBlock> 項目絕對定位在其儲存格使用<xref:System.Windows.FrameworkElement.Margin%2A>屬性和樣式的應用程式中所定義的對齊屬性。

[!code-xaml[GridComplex#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridComplex/CS/default.xaml#1)]

下圖顯示產生的控制項，可自訂的行事曆：

![產生的控制項的螢幕擷取畫面](./media/how-to-create-a-complex-grid/wpf-manual-calendar.png)

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.Grid?displayProperty=nameWithType>
- <xref:System.Windows.Documents.TableCell?displayProperty=nameWithType>
- [使用純色和漸層繪製的概觀](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [面板概觀](panels-overview.md)
- [資料表概觀](../advanced/table-overview.md)