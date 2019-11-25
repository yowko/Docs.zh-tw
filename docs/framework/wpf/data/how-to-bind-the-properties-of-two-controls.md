---
title: 操作說明：繫結兩個控制項的屬性
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: d38c473b8c4d3f71f1e3decd4f66be248665c57b
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974808"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a>操作說明：繫結兩個控制項的屬性

這個範例會示範如何使用 <xref:System.Windows.Data.Binding.ElementName%2A> 屬性，將一個具現化控制項的屬性系結至另一個實例的屬性。

## <a name="example"></a>範例

下列範例顯示如何將 <xref:System.Windows.Controls.Canvas> 的 <xref:System.Windows.Controls.Panel.Background%2A> 屬性系結至 <xref:System.Windows.Controls.ComboBox>的[SelectedItem](xref:System.Windows.Controls.ContentControl.Content%2A)屬性：

[!code-xaml[BindDptoDp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]

此範例轉譯後會如同以下所示︰

![螢幕擷取畫面：顯示已選取綠色值和綠色方形的下拉式方塊。](./media/how-to-bind-the-properties-of-two-controls/data-binding-bind-background-canvas.png)

> [!NOTE]
> 系結目標屬性（在此範例中為 <xref:System.Windows.Controls.Panel.Background%2A> 屬性）必須是相依性屬性。 如需詳細資訊，請參閱 [資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)。

## <a name="see-also"></a>請參閱

- [指定繫結來源](how-to-specify-the-binding-source.md)
- [「如何」主題](data-binding-how-to-topics.md)
