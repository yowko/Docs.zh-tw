---
title: HOW TO：控制 TextBox 文字更新來源的時機
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source updates [WPF], timing of
- data binding [WPF], timing of source updates
- timing of source updates [WPF]
ms.assetid: ffb7b96a-351d-4c68-81e7-054033781c64
ms.openlocfilehash: 5272a19f69b3caf80fd7d5187c9a6a386cd44621
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59143269"
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a><span data-ttu-id="78be4-102">HOW TO：控制 TextBox 文字更新來源的時機</span><span class="sxs-lookup"><span data-stu-id="78be4-102">How to: Control When the TextBox Text Updates the Source</span></span>
<span data-ttu-id="78be4-103">本主題描述如何使用<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>屬性，即可控制繫結來源更新的時機。</span><span class="sxs-lookup"><span data-stu-id="78be4-103">This topic describes how to use the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property to control the timing of binding source updates.</span></span> <span data-ttu-id="78be4-104">本主題使用<xref:System.Windows.Controls.TextBox>控制項做為範例。</span><span class="sxs-lookup"><span data-stu-id="78be4-104">The topic uses the <xref:System.Windows.Controls.TextBox> control as an example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78be4-105">範例</span><span class="sxs-lookup"><span data-stu-id="78be4-105">Example</span></span>  
 <span data-ttu-id="78be4-106"><xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A></span><span class="sxs-lookup"><span data-stu-id="78be4-106">The <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A></span></span> <span data-ttu-id="78be4-107">屬性的預設值<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>的值<xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>。</span><span class="sxs-lookup"><span data-stu-id="78be4-107">property has a default <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value of <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>.</span></span> <span data-ttu-id="78be4-108">這表示應用程式是否有<xref:System.Windows.Controls.TextBox>與資料繫結<xref:System.Windows.Controls.TextBox>。<xref:System.Windows.Controls.TextBox.Text%2A></span><span class="sxs-lookup"><span data-stu-id="78be4-108">This means if an application has a <xref:System.Windows.Controls.TextBox> with a data-bound <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A></span></span> <span data-ttu-id="78be4-109">屬性，您輸入的文字<xref:System.Windows.Controls.TextBox>不會更新來源，直到<xref:System.Windows.Controls.TextBox>失去焦點 (例如，當您按一下 離開<xref:System.Windows.Controls.TextBox>)。</span><span class="sxs-lookup"><span data-stu-id="78be4-109">property, the text you type into the <xref:System.Windows.Controls.TextBox> does not update the source until the <xref:System.Windows.Controls.TextBox> loses focus (for instance, when you click away from the <xref:System.Windows.Controls.TextBox>).</span></span>  
  
 <span data-ttu-id="78be4-110">如果您想要更新您輸入的來源，設定<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>繫結至的<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>。</span><span class="sxs-lookup"><span data-stu-id="78be4-110">If you want the source to be updated as you type, set the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> of the binding to <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span> <span data-ttu-id="78be4-111">在下列範例中，反白顯示的幾行程式碼顯示`Text`兩者的屬性<xref:System.Windows.Controls.TextBox>而<xref:System.Windows.Controls.TextBlock>繫結至相同的來源屬性。</span><span class="sxs-lookup"><span data-stu-id="78be4-111">In the following example, the highlighted lines of code show that the `Text` properties of both the <xref:System.Windows.Controls.TextBox> and the <xref:System.Windows.Controls.TextBlock> are bound to the same source property.</span></span> <span data-ttu-id="78be4-112"><xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>的屬性<xref:System.Windows.Controls.TextBox>繫結設定為<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>。</span><span class="sxs-lookup"><span data-stu-id="78be4-112">The <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property of the <xref:System.Windows.Controls.TextBox> binding is set to <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span>  
  
 [!code-xaml[SimpleBinding#USTHowTo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=33-39,41-42)]  
  
 <span data-ttu-id="78be4-113">如此一來，<xref:System.Windows.Controls.TextBlock>顯示相同的文字 （因為來源變更時） 在使用者輸入的文字貼入<xref:System.Windows.Controls.TextBox>，如下列範例的螢幕擷取畫面所示：</span><span class="sxs-lookup"><span data-stu-id="78be4-113">As a result, the <xref:System.Windows.Controls.TextBlock> shows the same text (because the source changes) as the user enters text into the <xref:System.Windows.Controls.TextBox>, as illustrated by the following screenshot of the sample:</span></span>  
  
 <span data-ttu-id="78be4-114">![簡單資料繫結範例螢幕擷取畫面](./media/databindingsimplebindingsample2.png "DataBindingSimpleBindingSample2")</span><span class="sxs-lookup"><span data-stu-id="78be4-114">![Simple data binding sample screenshot](./media/databindingsimplebindingsample2.png "DataBindingSimpleBindingSample2")</span></span>  
  
 <span data-ttu-id="78be4-115">如果您有一個對話方塊或使用者可編輯的表單，而且您想要延後來源更新，直到使用者完成欄位編輯並按一下 [確定]，您可以設定<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>若要將繫結的值<xref:System.Windows.Data.UpdateSourceTrigger.Explicit>，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="78be4-115">If you have a dialog or a user-editable form and you want to defer source updates until the user is finished editing the fields and clicks "OK", you can set the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value of your bindings to <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, as in the following example:</span></span>  
  
 [!code-xaml[UpdateSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="78be4-116">當您設定<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>值<xref:System.Windows.Data.UpdateSourceTrigger.Explicit>，在來源值只會變更當應用程式呼叫<xref:System.Windows.Data.BindingExpression.UpdateSource%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="78be4-116">When you set the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value to <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, the source value only changes when the application calls the <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> method.</span></span> <span data-ttu-id="78be4-117">下列範例示範如何呼叫<xref:System.Windows.Data.BindingExpression.UpdateSource%2A>針對`itemNameTextBox`:</span><span class="sxs-lookup"><span data-stu-id="78be4-117">The following example shows how to call <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> for `itemNameTextBox`:</span></span>  
  
 [!code-csharp[UpdateSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]  
  
> [!NOTE]
>  <span data-ttu-id="78be4-118">您可以使用相同的技巧，屬性的其他控制項，但請記住，其他大多數屬性有預設值<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>的值<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>。</span><span class="sxs-lookup"><span data-stu-id="78be4-118">You can use the same technique for properties of other controls, but keep in mind that most other properties have a default <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value of <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span> <span data-ttu-id="78be4-119">如需詳細資訊，請參閱<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>屬性頁。</span><span class="sxs-lookup"><span data-stu-id="78be4-119">For more information, see the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="78be4-120"><xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>屬性處理來源更新，因此僅與相關<xref:System.Windows.Data.BindingMode.TwoWay>或<xref:System.Windows.Data.BindingMode.OneWayToSource>繫結。</span><span class="sxs-lookup"><span data-stu-id="78be4-120">The <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property deals with source updates and therefore is only relevant for <xref:System.Windows.Data.BindingMode.TwoWay> or <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings.</span></span> <span data-ttu-id="78be4-121">針對<xref:System.Windows.Data.BindingMode.TwoWay>和<xref:System.Windows.Data.BindingMode.OneWayToSource>繫結得以生效，來源物件必須提供屬性變更通知。</span><span class="sxs-lookup"><span data-stu-id="78be4-121">For <xref:System.Windows.Data.BindingMode.TwoWay> and <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings to work, the source object needs to provide property change notifications.</span></span> <span data-ttu-id="78be4-122">如需詳細資訊，請參考本主題中引用的範例。</span><span class="sxs-lookup"><span data-stu-id="78be4-122">You can refer to the samples cited in this topic for more information.</span></span> <span data-ttu-id="78be4-123">此外，您還可以參閱[實作屬性變更通知](how-to-implement-property-change-notification.md)。</span><span class="sxs-lookup"><span data-stu-id="78be4-123">In addition, you can look at [Implement Property Change Notification](how-to-implement-property-change-notification.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78be4-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78be4-124">See also</span></span>

- [<span data-ttu-id="78be4-125">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="78be4-125">How-to Topics</span></span>](data-binding-how-to-topics.md)
