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
# <a name="how-to-bind-the-properties-of-two-controls"></a><span data-ttu-id="ed864-102">操作說明：繫結兩個控制項的屬性</span><span class="sxs-lookup"><span data-stu-id="ed864-102">How to: Bind the Properties of Two Controls</span></span>

<span data-ttu-id="ed864-103">這個範例會示範如何使用 <xref:System.Windows.Data.Binding.ElementName%2A> 屬性，將一個具現化控制項的屬性系結至另一個實例的屬性。</span><span class="sxs-lookup"><span data-stu-id="ed864-103">This example shows how to bind the property of one instantiated control to that of another using the <xref:System.Windows.Data.Binding.ElementName%2A> property.</span></span>

## <a name="example"></a><span data-ttu-id="ed864-104">範例</span><span class="sxs-lookup"><span data-stu-id="ed864-104">Example</span></span>

<span data-ttu-id="ed864-105">下列範例顯示如何將 <xref:System.Windows.Controls.Canvas> 的 <xref:System.Windows.Controls.Panel.Background%2A> 屬性系結至 <xref:System.Windows.Controls.ComboBox>的[SelectedItem](xref:System.Windows.Controls.ContentControl.Content%2A)屬性：</span><span class="sxs-lookup"><span data-stu-id="ed864-105">The following example shows how to bind the <xref:System.Windows.Controls.Panel.Background%2A> property of a <xref:System.Windows.Controls.Canvas> to the [SelectedItem.Content](xref:System.Windows.Controls.ContentControl.Content%2A) property of a <xref:System.Windows.Controls.ComboBox>:</span></span>

[!code-xaml[BindDptoDp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]

<span data-ttu-id="ed864-106">此範例轉譯後會如同以下所示︰</span><span class="sxs-lookup"><span data-stu-id="ed864-106">When this example is rendered it looks like the following:</span></span>

![螢幕擷取畫面：顯示已選取綠色值和綠色方形的下拉式方塊。](./media/how-to-bind-the-properties-of-two-controls/data-binding-bind-background-canvas.png)

> [!NOTE]
> <span data-ttu-id="ed864-108">系結目標屬性（在此範例中為 <xref:System.Windows.Controls.Panel.Background%2A> 屬性）必須是相依性屬性。</span><span class="sxs-lookup"><span data-stu-id="ed864-108">The binding target property (in this example, the <xref:System.Windows.Controls.Panel.Background%2A> property) must be a dependency property.</span></span> <span data-ttu-id="ed864-109">如需詳細資訊，請參閱 [資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="ed864-109">For more information, see [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ed864-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="ed864-110">See also</span></span>

- [<span data-ttu-id="ed864-111">指定繫結來源</span><span class="sxs-lookup"><span data-stu-id="ed864-111">Specify the Binding Source</span></span>](how-to-specify-the-binding-source.md)
- [<span data-ttu-id="ed864-112">「如何」主題</span><span class="sxs-lookup"><span data-stu-id="ed864-112">How-to Topics</span></span>](data-binding-how-to-topics.md)
