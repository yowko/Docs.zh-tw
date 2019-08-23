---
title: 作法：控制 TextBox 文字更新來源的時機
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source updates [WPF], timing of
- data binding [WPF], timing of source updates
- timing of source updates [WPF]
ms.assetid: ffb7b96a-351d-4c68-81e7-054033781c64
ms.openlocfilehash: d1d624d7550a1135431b7fffc7450e3a510855a7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966459"
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a><span data-ttu-id="fb6c0-102">作法：控制 TextBox 文字更新來源的時機</span><span class="sxs-lookup"><span data-stu-id="fb6c0-102">How to: Control When the TextBox Text Updates the Source</span></span>
<span data-ttu-id="fb6c0-103">本主題描述如何使用<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>屬性來控制系結來源更新的時機。</span><span class="sxs-lookup"><span data-stu-id="fb6c0-103">This topic describes how to use the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property to control the timing of binding source updates.</span></span> <span data-ttu-id="fb6c0-104">本主題使用<xref:System.Windows.Controls.TextBox>控制項做為範例。</span><span class="sxs-lookup"><span data-stu-id="fb6c0-104">The topic uses the <xref:System.Windows.Controls.TextBox> control as an example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb6c0-105">範例</span><span class="sxs-lookup"><span data-stu-id="fb6c0-105">Example</span></span>  
 <span data-ttu-id="fb6c0-106"><xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A></span><span class="sxs-lookup"><span data-stu-id="fb6c0-106">The <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A></span></span> <span data-ttu-id="fb6c0-107">屬性的預設<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>值為<xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>。</span><span class="sxs-lookup"><span data-stu-id="fb6c0-107">property has a default <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value of <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>.</span></span> <span data-ttu-id="fb6c0-108">這表示<xref:System.Windows.Controls.TextBox> , 如果應用程式具有具有資料<xref:System.Windows.Controls.TextBox>系結的。<xref:System.Windows.Controls.TextBox.Text%2A></span><span class="sxs-lookup"><span data-stu-id="fb6c0-108">This means if an application has a <xref:System.Windows.Controls.TextBox> with a data-bound <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A></span></span> <span data-ttu-id="fb6c0-109">屬性 (property), 您在中<xref:System.Windows.Controls.TextBox>輸入的文字不會更新來源<xref:System.Windows.Controls.TextBox> , 直到失去焦點為止 (例如, 當您按一下 [ <xref:System.Windows.Controls.TextBox>離開] 時)。</span><span class="sxs-lookup"><span data-stu-id="fb6c0-109">property, the text you type into the <xref:System.Windows.Controls.TextBox> does not update the source until the <xref:System.Windows.Controls.TextBox> loses focus (for instance, when you click away from the <xref:System.Windows.Controls.TextBox>).</span></span>  
  
 <span data-ttu-id="fb6c0-110">如果您想要在輸入時更新來源, 請將系結<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>的設定為。 <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged></span><span class="sxs-lookup"><span data-stu-id="fb6c0-110">If you want the source to be updated as you type, set the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> of the binding to <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span> <span data-ttu-id="fb6c0-111">在下列範例中, 反白顯示的程式`Text`程式碼顯示<xref:System.Windows.Controls.TextBox>和的<xref:System.Windows.Controls.TextBlock>屬性都會系結至相同的來源屬性。</span><span class="sxs-lookup"><span data-stu-id="fb6c0-111">In the following example, the highlighted lines of code show that the `Text` properties of both the <xref:System.Windows.Controls.TextBox> and the <xref:System.Windows.Controls.TextBlock> are bound to the same source property.</span></span> <span data-ttu-id="fb6c0-112">系結的<xref:System.Windows.Controls.TextBox> <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>屬性會設定為。 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A></span><span class="sxs-lookup"><span data-stu-id="fb6c0-112">The <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property of the <xref:System.Windows.Controls.TextBox> binding is set to <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span>  
  
 [!code-xaml[SimpleBinding#USTHowTo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=33-39,41-42)]  
  
 <span data-ttu-id="fb6c0-113">如此一來, <xref:System.Windows.Controls.TextBlock>當使用者在中輸入文字<xref:System.Windows.Controls.TextBox>時, 會顯示相同的文字 (因為來源變更), 如下列範例的螢幕擷取畫面所示:</span><span class="sxs-lookup"><span data-stu-id="fb6c0-113">As a result, the <xref:System.Windows.Controls.TextBlock> shows the same text (because the source changes) as the user enters text into the <xref:System.Windows.Controls.TextBox>, as illustrated by the following screenshot of the sample:</span></span>  
  
 ![顯示簡單資料系結的螢幕擷取畫面。](./media/how-to-control-when-the-textbox-text-updates-the-source/data-binding-simple-binding-sample.png)  
  
 <span data-ttu-id="fb6c0-115">如果您有對話方塊或使用者可編輯的表單, 而且想要延遲來源更新, 直到使用者完成編輯欄位, 並按一下 [確定], 您可以將系結<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>的值設定為<xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, 如下列範例所示:</span><span class="sxs-lookup"><span data-stu-id="fb6c0-115">If you have a dialog or a user-editable form and you want to defer source updates until the user is finished editing the fields and clicks "OK", you can set the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value of your bindings to <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, as in the following example:</span></span>  
  
 [!code-xaml[UpdateSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="fb6c0-116">當您將<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>值設定為<xref:System.Windows.Data.UpdateSourceTrigger.Explicit>時, 只有在應用程式呼叫<xref:System.Windows.Data.BindingExpression.UpdateSource%2A>方法時, 來源值才會變更。</span><span class="sxs-lookup"><span data-stu-id="fb6c0-116">When you set the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value to <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, the source value only changes when the application calls the <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> method.</span></span> <span data-ttu-id="fb6c0-117">下列範例顯示如何呼叫<xref:System.Windows.Data.BindingExpression.UpdateSource%2A>的: `itemNameTextBox`</span><span class="sxs-lookup"><span data-stu-id="fb6c0-117">The following example shows how to call <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> for `itemNameTextBox`:</span></span>  
  
 [!code-csharp[UpdateSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]  
  
> [!NOTE]
> <span data-ttu-id="fb6c0-118">對於其他控制項的屬性, 您可以使用相同的技術, 但請記住, 大部分的其他屬性都有<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>預設<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>值。</span><span class="sxs-lookup"><span data-stu-id="fb6c0-118">You can use the same technique for properties of other controls, but keep in mind that most other properties have a default <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value of <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span> <span data-ttu-id="fb6c0-119">如需詳細資訊, 請<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>參閱屬性頁。</span><span class="sxs-lookup"><span data-stu-id="fb6c0-119">For more information, see the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property page.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fb6c0-120">屬性會處理來源更新, 因此只<xref:System.Windows.Data.BindingMode.TwoWay>與或<xref:System.Windows.Data.BindingMode.OneWayToSource>系結相關。 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A></span><span class="sxs-lookup"><span data-stu-id="fb6c0-120">The <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property deals with source updates and therefore is only relevant for <xref:System.Windows.Data.BindingMode.TwoWay> or <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings.</span></span> <span data-ttu-id="fb6c0-121">若<xref:System.Windows.Data.BindingMode.TwoWay>要<xref:System.Windows.Data.BindingMode.OneWayToSource>讓和系結能夠正常執行, 來源物件必須提供屬性變更通知。</span><span class="sxs-lookup"><span data-stu-id="fb6c0-121">For <xref:System.Windows.Data.BindingMode.TwoWay> and <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings to work, the source object needs to provide property change notifications.</span></span> <span data-ttu-id="fb6c0-122">如需詳細資訊，請參考本主題中引用的範例。</span><span class="sxs-lookup"><span data-stu-id="fb6c0-122">You can refer to the samples cited in this topic for more information.</span></span> <span data-ttu-id="fb6c0-123">此外，您還可以參閱[實作屬性變更通知](how-to-implement-property-change-notification.md)。</span><span class="sxs-lookup"><span data-stu-id="fb6c0-123">In addition, you can look at [Implement Property Change Notification](how-to-implement-property-change-notification.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb6c0-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb6c0-124">See also</span></span>

- [<span data-ttu-id="fb6c0-125">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="fb6c0-125">How-to Topics</span></span>](data-binding-how-to-topics.md)
