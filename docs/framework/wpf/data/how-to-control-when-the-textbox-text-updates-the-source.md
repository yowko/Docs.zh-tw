---
title: "操作說明：TextBox 文字更新來源時控制"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source updates [WPF], timing of
- data binding [WPF], timing of source updates
- timing of source updates [WPF]
ms.assetid: ffb7b96a-351d-4c68-81e7-054033781c64
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c923a24f5abfdb059a436206a15181a67d03068f
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a><span data-ttu-id="684f4-102">操作說明：TextBox 文字更新來源時控制</span><span class="sxs-lookup"><span data-stu-id="684f4-102">How to: Control When the TextBox Text Updates the Source</span></span>
<span data-ttu-id="684f4-103">本主題描述如何使用<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>屬性，即可控制繫結來源更新的時機。</span><span class="sxs-lookup"><span data-stu-id="684f4-103">This topic describes how to use the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property to control the timing of binding source updates.</span></span> <span data-ttu-id="684f4-104">本主題將使用<xref:System.Windows.Controls.TextBox>控制項做為範例。</span><span class="sxs-lookup"><span data-stu-id="684f4-104">The topic uses the <xref:System.Windows.Controls.TextBox> control as an example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="684f4-105">範例</span><span class="sxs-lookup"><span data-stu-id="684f4-105">Example</span></span>  
 <span data-ttu-id="684f4-106"><xref:System.Windows.Controls.TextBox>。<xref:System.Windows.Controls.TextBox.Text%2A>屬性都有預設<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>值<xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>。</span><span class="sxs-lookup"><span data-stu-id="684f4-106">The <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> property has a default <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value of <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>.</span></span> <span data-ttu-id="684f4-107">這表示應用程式是否有<xref:System.Windows.Controls.TextBox>與資料繫結<xref:System.Windows.Controls.TextBox>。<xref:System.Windows.Controls.TextBox.Text%2A>屬性，您輸入的文字<xref:System.Windows.Controls.TextBox>不會更新直到來源<xref:System.Windows.Controls.TextBox>失去焦點 （例如，當您按一下而離開<xref:System.Windows.Controls.TextBox>).</span><span class="sxs-lookup"><span data-stu-id="684f4-107">This means if an application has a <xref:System.Windows.Controls.TextBox> with a data-bound <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> property, the text you type into the <xref:System.Windows.Controls.TextBox> does not update the source until the <xref:System.Windows.Controls.TextBox> loses focus (for instance, when you click away from the <xref:System.Windows.Controls.TextBox>).</span></span>  
  
 <span data-ttu-id="684f4-108">如果您想要做為更新來源您正在輸入，請將<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>繫結至的<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>。</span><span class="sxs-lookup"><span data-stu-id="684f4-108">If you want the source to get updated as you are typing, set the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> of the binding to <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span> <span data-ttu-id="684f4-109">在下列範例中，`Text`屬性兩者的<xref:System.Windows.Controls.TextBox>和<xref:System.Windows.Controls.TextBlock>繫結至相同的來源屬性。</span><span class="sxs-lookup"><span data-stu-id="684f4-109">In the following example, the `Text` properties of both the <xref:System.Windows.Controls.TextBox> and the <xref:System.Windows.Controls.TextBlock> are bound to the same source property.</span></span> <span data-ttu-id="684f4-110"><xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>屬性<xref:System.Windows.Controls.TextBox>繫結設定為<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>。</span><span class="sxs-lookup"><span data-stu-id="684f4-110">The <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property of the <xref:System.Windows.Controls.TextBox> binding is set to <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span>  
  
 [!code-xaml[SimpleBinding#USTHowTo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml#usthowto)]  
  
 <span data-ttu-id="684f4-111">如此一來，<xref:System.Windows.Controls.TextBlock>顯示相同的文字 （因為來源變更） 在使用者輸入的文字放到<xref:System.Windows.Controls.TextBox>，如下列範例的螢幕擷取畫面所示：</span><span class="sxs-lookup"><span data-stu-id="684f4-111">As a result, the <xref:System.Windows.Controls.TextBlock> shows the same text (because the source changes) as the user enters text into the <xref:System.Windows.Controls.TextBox>, as illustrated by the following screenshot of the sample:</span></span>  
  
 <span data-ttu-id="684f4-112">![簡單資料繫結範例螢幕擷取畫面](../../../../docs/framework/wpf/data/media/databindingsimplebindingsample2.png "DataBindingSimpleBindingSample2")</span><span class="sxs-lookup"><span data-stu-id="684f4-112">![Simple data binding sample screen shot](../../../../docs/framework/wpf/data/media/databindingsimplebindingsample2.png "DataBindingSimpleBindingSample2")</span></span>  
  
 <span data-ttu-id="684f4-113">如果您有一個對話方塊或使用者可編輯的表單，而且您想要延遲來源更新，直到使用者完成編輯欄位，並按一下 [確定]，您可以設定<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>的繫結，以值<xref:System.Windows.Data.UpdateSourceTrigger.Explicit>，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="684f4-113">If you have a dialog or a user-editable form and you want to defer source updates until the user is finished editing the fields and clicks "OK", you can set the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value of your bindings to <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, as in the following example:</span></span>  
  
 [!code-xaml[UpdateSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="684f4-114">當您將<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>值設定為<xref:System.Windows.Data.UpdateSourceTrigger.Explicit>，來源值只會變更當應用程式呼叫<xref:System.Windows.Data.BindingExpression.UpdateSource%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="684f4-114">When you set the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value to <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, the source value only changes when the application calls the <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> method.</span></span> <span data-ttu-id="684f4-115">下列範例示範如何呼叫<xref:System.Windows.Data.BindingExpression.UpdateSource%2A>如`itemNameTextBox`:</span><span class="sxs-lookup"><span data-stu-id="684f4-115">The following example shows how to call <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> for `itemNameTextBox`:</span></span>  
  
 [!code-csharp[UpdateSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]  
  
> [!NOTE]
>  <span data-ttu-id="684f4-116">您可以使用相同的技巧屬性的其他控制項，但請注意其他大多數屬性具有預設值<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>值<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>。</span><span class="sxs-lookup"><span data-stu-id="684f4-116">You can use the same technique for properties of other controls, but keep in mind that most other properties have a default <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value of <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span> <span data-ttu-id="684f4-117">如需詳細資訊，請參閱<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>屬性頁。</span><span class="sxs-lookup"><span data-stu-id="684f4-117">For more information, see the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="684f4-118"><xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>屬性處理來源的更新，因此才有意義的<xref:System.Windows.Data.BindingMode.TwoWay>或<xref:System.Windows.Data.BindingMode.OneWayToSource>繫結。</span><span class="sxs-lookup"><span data-stu-id="684f4-118">The <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property deals with source updates and therefore is only relevant for <xref:System.Windows.Data.BindingMode.TwoWay> or <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings.</span></span> <span data-ttu-id="684f4-119">如<xref:System.Windows.Data.BindingMode.TwoWay>和<xref:System.Windows.Data.BindingMode.OneWayToSource>運作，以提供屬性變更告知的來源物件需求的繫結。</span><span class="sxs-lookup"><span data-stu-id="684f4-119">For <xref:System.Windows.Data.BindingMode.TwoWay> and <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings to work, the source object needs to provide property change notifications.</span></span> <span data-ttu-id="684f4-120">如需詳細資訊，請參考本主題中引用的範例。</span><span class="sxs-lookup"><span data-stu-id="684f4-120">You can refer to the samples cited in this topic for more information.</span></span> <span data-ttu-id="684f4-121">此外，您還可以參閱[實作屬性變更通知](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md)。</span><span class="sxs-lookup"><span data-stu-id="684f4-121">In addition, you can look at [Implement Property Change Notification](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="684f4-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="684f4-122">See Also</span></span>  
 [<span data-ttu-id="684f4-123">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="684f4-123">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
