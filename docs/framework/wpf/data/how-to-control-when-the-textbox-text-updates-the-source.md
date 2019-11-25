---
title: 操作說明：TextBox 文字更新來源時控制
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source updates [WPF], timing of
- data binding [WPF], timing of source updates
- timing of source updates [WPF]
ms.assetid: ffb7b96a-351d-4c68-81e7-054033781c64
ms.openlocfilehash: b211eb67e3bac95f74255935a39cc0d6aec61531
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974791"
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a>操作說明：TextBox 文字更新來源時控制
本主題描述如何使用 [<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>] 屬性來控制系結來源更新的時機。 本主題使用 <xref:System.Windows.Controls.TextBox> 控制項做為範例。

## <a name="example"></a>範例
 <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> 屬性的預設 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 值為 <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>。 這表示如果應用程式具有具有資料系結 <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> 屬性的 <xref:System.Windows.Controls.TextBox>，您輸入 <xref:System.Windows.Controls.TextBox> 的文字就不會更新來源，直到 <xref:System.Windows.Controls.TextBox> 失去焦點為止（例如，當您按一下 [<xref:System.Windows.Controls.TextBox>] 時）。

 如果您想要在輸入時更新來源，請將系結的 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 設定為 <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>。 在下列範例中，反白顯示的程式程式碼顯示 <xref:System.Windows.Controls.TextBox> 和 <xref:System.Windows.Controls.TextBlock> 的 `Text` 屬性都會系結至相同的來源屬性。 <xref:System.Windows.Controls.TextBox> 系結的 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 屬性會設定為 [<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>]。

 [!code-xaml[SimpleBinding#USTHowTo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=33-39,41-42)]

 因此，當使用者在 <xref:System.Windows.Controls.TextBox>中輸入文字時，<xref:System.Windows.Controls.TextBlock> 會顯示相同的文字（因為來源變更），如下列範例的螢幕擷取畫面所示：

 ![顯示簡單資料系結的螢幕擷取畫面。](./media/how-to-control-when-the-textbox-text-updates-the-source/data-binding-simple-binding-sample.png)

 如果您有對話方塊或使用者可編輯的表單，而且想要延遲來源更新，直到使用者完成編輯欄位，並按一下 [確定]，您可以將系結的 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 值設定為 <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>，如下列範例所示：

 [!code-xaml[UpdateSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]

 當您將 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 值設定為 <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>時，只有當應用程式呼叫 <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> 方法時，來源值才會變更。 下列範例顯示如何呼叫 `itemNameTextBox`的 <xref:System.Windows.Data.BindingExpression.UpdateSource%2A>：

 [!code-csharp[UpdateSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]

> [!NOTE]
> 對於其他控制項的屬性，您可以使用相同的技術，但請記住，大部分的其他屬性都有預設的 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 值為 <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>。 如需詳細資訊，請參閱 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 屬性頁。

> [!NOTE]
> <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 屬性會處理來源更新，因此僅適用于 <xref:System.Windows.Data.BindingMode.TwoWay> 或 <xref:System.Windows.Data.BindingMode.OneWayToSource> 系結。 若要讓 <xref:System.Windows.Data.BindingMode.TwoWay> 和 <xref:System.Windows.Data.BindingMode.OneWayToSource> 系結能夠正常執行，來源物件必須提供屬性變更通知。 如需詳細資訊，請參考本主題中引用的範例。 此外，您還可以參閱[實作屬性變更通知](how-to-implement-property-change-notification.md)。

## <a name="see-also"></a>請參閱

- [「如何」主題](data-binding-how-to-topics.md)
