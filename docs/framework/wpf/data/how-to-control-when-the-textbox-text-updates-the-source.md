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
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a><span data-ttu-id="b4287-102">操作說明：TextBox 文字更新來源時控制</span><span class="sxs-lookup"><span data-stu-id="b4287-102">How to: Control When the TextBox Text Updates the Source</span></span>
<span data-ttu-id="b4287-103">本主題描述如何使用 [<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>] 屬性來控制系結來源更新的時機。</span><span class="sxs-lookup"><span data-stu-id="b4287-103">This topic describes how to use the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property to control the timing of binding source updates.</span></span> <span data-ttu-id="b4287-104">本主題使用 <xref:System.Windows.Controls.TextBox> 控制項做為範例。</span><span class="sxs-lookup"><span data-stu-id="b4287-104">The topic uses the <xref:System.Windows.Controls.TextBox> control as an example.</span></span>

## <a name="example"></a><span data-ttu-id="b4287-105">範例</span><span class="sxs-lookup"><span data-stu-id="b4287-105">Example</span></span>
 <span data-ttu-id="b4287-106"><xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> 屬性的預設 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 值為 <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>。</span><span class="sxs-lookup"><span data-stu-id="b4287-106">The <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> property has a default <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value of <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>.</span></span> <span data-ttu-id="b4287-107">這表示如果應用程式具有具有資料系結 <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> 屬性的 <xref:System.Windows.Controls.TextBox>，您輸入 <xref:System.Windows.Controls.TextBox> 的文字就不會更新來源，直到 <xref:System.Windows.Controls.TextBox> 失去焦點為止（例如，當您按一下 [<xref:System.Windows.Controls.TextBox>] 時）。</span><span class="sxs-lookup"><span data-stu-id="b4287-107">This means if an application has a <xref:System.Windows.Controls.TextBox> with a data-bound <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> property, the text you type into the <xref:System.Windows.Controls.TextBox> does not update the source until the <xref:System.Windows.Controls.TextBox> loses focus (for instance, when you click away from the <xref:System.Windows.Controls.TextBox>).</span></span>

 <span data-ttu-id="b4287-108">如果您想要在輸入時更新來源，請將系結的 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 設定為 <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>。</span><span class="sxs-lookup"><span data-stu-id="b4287-108">If you want the source to be updated as you type, set the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> of the binding to <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span> <span data-ttu-id="b4287-109">在下列範例中，反白顯示的程式程式碼顯示 <xref:System.Windows.Controls.TextBox> 和 <xref:System.Windows.Controls.TextBlock> 的 `Text` 屬性都會系結至相同的來源屬性。</span><span class="sxs-lookup"><span data-stu-id="b4287-109">In the following example, the highlighted lines of code show that the `Text` properties of both the <xref:System.Windows.Controls.TextBox> and the <xref:System.Windows.Controls.TextBlock> are bound to the same source property.</span></span> <span data-ttu-id="b4287-110"><xref:System.Windows.Controls.TextBox> 系結的 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 屬性會設定為 [<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>]。</span><span class="sxs-lookup"><span data-stu-id="b4287-110">The <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property of the <xref:System.Windows.Controls.TextBox> binding is set to <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span>

 [!code-xaml[SimpleBinding#USTHowTo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=33-39,41-42)]

 <span data-ttu-id="b4287-111">因此，當使用者在 <xref:System.Windows.Controls.TextBox>中輸入文字時，<xref:System.Windows.Controls.TextBlock> 會顯示相同的文字（因為來源變更），如下列範例的螢幕擷取畫面所示：</span><span class="sxs-lookup"><span data-stu-id="b4287-111">As a result, the <xref:System.Windows.Controls.TextBlock> shows the same text (because the source changes) as the user enters text into the <xref:System.Windows.Controls.TextBox>, as illustrated by the following screenshot of the sample:</span></span>

 ![顯示簡單資料系結的螢幕擷取畫面。](./media/how-to-control-when-the-textbox-text-updates-the-source/data-binding-simple-binding-sample.png)

 <span data-ttu-id="b4287-113">如果您有對話方塊或使用者可編輯的表單，而且想要延遲來源更新，直到使用者完成編輯欄位，並按一下 [確定]，您可以將系結的 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 值設定為 <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="b4287-113">If you have a dialog or a user-editable form and you want to defer source updates until the user is finished editing the fields and clicks "OK", you can set the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value of your bindings to <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, as in the following example:</span></span>

 [!code-xaml[UpdateSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]

 <span data-ttu-id="b4287-114">當您將 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 值設定為 <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>時，只有當應用程式呼叫 <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> 方法時，來源值才會變更。</span><span class="sxs-lookup"><span data-stu-id="b4287-114">When you set the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value to <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, the source value only changes when the application calls the <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> method.</span></span> <span data-ttu-id="b4287-115">下列範例顯示如何呼叫 `itemNameTextBox`的 <xref:System.Windows.Data.BindingExpression.UpdateSource%2A>：</span><span class="sxs-lookup"><span data-stu-id="b4287-115">The following example shows how to call <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> for `itemNameTextBox`:</span></span>

 [!code-csharp[UpdateSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]

> [!NOTE]
> <span data-ttu-id="b4287-116">對於其他控制項的屬性，您可以使用相同的技術，但請記住，大部分的其他屬性都有預設的 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 值為 <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>。</span><span class="sxs-lookup"><span data-stu-id="b4287-116">You can use the same technique for properties of other controls, but keep in mind that most other properties have a default <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value of <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span> <span data-ttu-id="b4287-117">如需詳細資訊，請參閱 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 屬性頁。</span><span class="sxs-lookup"><span data-stu-id="b4287-117">For more information, see the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property page.</span></span>

> [!NOTE]
> <span data-ttu-id="b4287-118"><xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 屬性會處理來源更新，因此僅適用于 <xref:System.Windows.Data.BindingMode.TwoWay> 或 <xref:System.Windows.Data.BindingMode.OneWayToSource> 系結。</span><span class="sxs-lookup"><span data-stu-id="b4287-118">The <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property deals with source updates and therefore is only relevant for <xref:System.Windows.Data.BindingMode.TwoWay> or <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings.</span></span> <span data-ttu-id="b4287-119">若要讓 <xref:System.Windows.Data.BindingMode.TwoWay> 和 <xref:System.Windows.Data.BindingMode.OneWayToSource> 系結能夠正常執行，來源物件必須提供屬性變更通知。</span><span class="sxs-lookup"><span data-stu-id="b4287-119">For <xref:System.Windows.Data.BindingMode.TwoWay> and <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings to work, the source object needs to provide property change notifications.</span></span> <span data-ttu-id="b4287-120">如需詳細資訊，請參考本主題中引用的範例。</span><span class="sxs-lookup"><span data-stu-id="b4287-120">You can refer to the samples cited in this topic for more information.</span></span> <span data-ttu-id="b4287-121">此外，您還可以參閱[實作屬性變更通知](how-to-implement-property-change-notification.md)。</span><span class="sxs-lookup"><span data-stu-id="b4287-121">In addition, you can look at [Implement Property Change Notification](how-to-implement-property-change-notification.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b4287-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="b4287-122">See also</span></span>

- [<span data-ttu-id="b4287-123">「如何」主題</span><span class="sxs-lookup"><span data-stu-id="b4287-123">How-to Topics</span></span>](data-binding-how-to-topics.md)
