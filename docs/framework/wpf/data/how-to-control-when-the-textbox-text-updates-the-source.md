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
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a>作法：控制 TextBox 文字更新來源的時機
本主題描述如何使用<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>屬性來控制系結來源更新的時機。 本主題使用<xref:System.Windows.Controls.TextBox>控制項做為範例。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> 屬性的預設<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>值為<xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>。 這表示<xref:System.Windows.Controls.TextBox> , 如果應用程式具有具有資料<xref:System.Windows.Controls.TextBox>系結的。<xref:System.Windows.Controls.TextBox.Text%2A> 屬性 (property), 您在中<xref:System.Windows.Controls.TextBox>輸入的文字不會更新來源<xref:System.Windows.Controls.TextBox> , 直到失去焦點為止 (例如, 當您按一下 [ <xref:System.Windows.Controls.TextBox>離開] 時)。  
  
 如果您想要在輸入時更新來源, 請將系結<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>的設定為。 <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> 在下列範例中, 反白顯示的程式`Text`程式碼顯示<xref:System.Windows.Controls.TextBox>和的<xref:System.Windows.Controls.TextBlock>屬性都會系結至相同的來源屬性。 系結的<xref:System.Windows.Controls.TextBox> <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>屬性會設定為。 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>  
  
 [!code-xaml[SimpleBinding#USTHowTo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=33-39,41-42)]  
  
 如此一來, <xref:System.Windows.Controls.TextBlock>當使用者在中輸入文字<xref:System.Windows.Controls.TextBox>時, 會顯示相同的文字 (因為來源變更), 如下列範例的螢幕擷取畫面所示:  
  
 ![顯示簡單資料系結的螢幕擷取畫面。](./media/how-to-control-when-the-textbox-text-updates-the-source/data-binding-simple-binding-sample.png)  
  
 如果您有對話方塊或使用者可編輯的表單, 而且想要延遲來源更新, 直到使用者完成編輯欄位, 並按一下 [確定], 您可以將系結<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>的值設定為<xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, 如下列範例所示:  
  
 [!code-xaml[UpdateSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]  
  
 當您將<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>值設定為<xref:System.Windows.Data.UpdateSourceTrigger.Explicit>時, 只有在應用程式呼叫<xref:System.Windows.Data.BindingExpression.UpdateSource%2A>方法時, 來源值才會變更。 下列範例顯示如何呼叫<xref:System.Windows.Data.BindingExpression.UpdateSource%2A>的: `itemNameTextBox`  
  
 [!code-csharp[UpdateSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]  
  
> [!NOTE]
> 對於其他控制項的屬性, 您可以使用相同的技術, 但請記住, 大部分的其他屬性都有<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>預設<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>值。 如需詳細資訊, 請<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>參閱屬性頁。  
  
> [!NOTE]
> 屬性會處理來源更新, 因此只<xref:System.Windows.Data.BindingMode.TwoWay>與或<xref:System.Windows.Data.BindingMode.OneWayToSource>系結相關。 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 若<xref:System.Windows.Data.BindingMode.TwoWay>要<xref:System.Windows.Data.BindingMode.OneWayToSource>讓和系結能夠正常執行, 來源物件必須提供屬性變更通知。 如需詳細資訊，請參考本主題中引用的範例。 此外，您還可以參閱[實作屬性變更通知](how-to-implement-property-change-notification.md)。  
  
## <a name="see-also"></a>另請參閱

- [HOW-TO 主題](data-binding-how-to-topics.md)
