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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143269"
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a>HOW TO：控制 TextBox 文字更新來源的時機
本主題描述如何使用<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>屬性，即可控制繫結來源更新的時機。 本主題使用<xref:System.Windows.Controls.TextBox>控制項做為範例。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Controls.TextBox>。<xref:System.Windows.Controls.TextBox.Text%2A> 屬性的預設值<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>的值<xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>。 這表示應用程式是否有<xref:System.Windows.Controls.TextBox>與資料繫結<xref:System.Windows.Controls.TextBox>。<xref:System.Windows.Controls.TextBox.Text%2A> 屬性，您輸入的文字<xref:System.Windows.Controls.TextBox>不會更新來源，直到<xref:System.Windows.Controls.TextBox>失去焦點 (例如，當您按一下 離開<xref:System.Windows.Controls.TextBox>)。  
  
 如果您想要更新您輸入的來源，設定<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>繫結至的<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>。 在下列範例中，反白顯示的幾行程式碼顯示`Text`兩者的屬性<xref:System.Windows.Controls.TextBox>而<xref:System.Windows.Controls.TextBlock>繫結至相同的來源屬性。 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>的屬性<xref:System.Windows.Controls.TextBox>繫結設定為<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>。  
  
 [!code-xaml[SimpleBinding#USTHowTo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=33-39,41-42)]  
  
 如此一來，<xref:System.Windows.Controls.TextBlock>顯示相同的文字 （因為來源變更時） 在使用者輸入的文字貼入<xref:System.Windows.Controls.TextBox>，如下列範例的螢幕擷取畫面所示：  
  
 ![簡單資料繫結範例螢幕擷取畫面](./media/databindingsimplebindingsample2.png "DataBindingSimpleBindingSample2")  
  
 如果您有一個對話方塊或使用者可編輯的表單，而且您想要延後來源更新，直到使用者完成欄位編輯並按一下 [確定]，您可以設定<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>若要將繫結的值<xref:System.Windows.Data.UpdateSourceTrigger.Explicit>，如下列範例所示：  
  
 [!code-xaml[UpdateSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]  
  
 當您設定<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>值<xref:System.Windows.Data.UpdateSourceTrigger.Explicit>，在來源值只會變更當應用程式呼叫<xref:System.Windows.Data.BindingExpression.UpdateSource%2A>方法。 下列範例示範如何呼叫<xref:System.Windows.Data.BindingExpression.UpdateSource%2A>針對`itemNameTextBox`:  
  
 [!code-csharp[UpdateSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]  
  
> [!NOTE]
>  您可以使用相同的技巧，屬性的其他控制項，但請記住，其他大多數屬性有預設值<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>的值<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>。 如需詳細資訊，請參閱<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>屬性頁。  
  
> [!NOTE]
>  <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>屬性處理來源更新，因此僅與相關<xref:System.Windows.Data.BindingMode.TwoWay>或<xref:System.Windows.Data.BindingMode.OneWayToSource>繫結。 針對<xref:System.Windows.Data.BindingMode.TwoWay>和<xref:System.Windows.Data.BindingMode.OneWayToSource>繫結得以生效，來源物件必須提供屬性變更通知。 如需詳細資訊，請參考本主題中引用的範例。 此外，您還可以參閱[實作屬性變更通知](how-to-implement-property-change-notification.md)。  
  
## <a name="see-also"></a>另請參閱

- [HOW TO 主題](data-binding-how-to-topics.md)
