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
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a>操作說明：TextBox 文字更新來源時控制
本主題描述如何使用<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>屬性，即可控制繫結來源更新的時機。 本主題將使用<xref:System.Windows.Controls.TextBox>控制項做為範例。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Controls.TextBox>。<xref:System.Windows.Controls.TextBox.Text%2A>屬性都有預設<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>值<xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>。 這表示應用程式是否有<xref:System.Windows.Controls.TextBox>與資料繫結<xref:System.Windows.Controls.TextBox>。<xref:System.Windows.Controls.TextBox.Text%2A>屬性，您輸入的文字<xref:System.Windows.Controls.TextBox>不會更新直到來源<xref:System.Windows.Controls.TextBox>失去焦點 （例如，當您按一下而離開<xref:System.Windows.Controls.TextBox>).  
  
 如果您想要做為更新來源您正在輸入，請將<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>繫結至的<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>。 在下列範例中，`Text`屬性兩者的<xref:System.Windows.Controls.TextBox>和<xref:System.Windows.Controls.TextBlock>繫結至相同的來源屬性。 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>屬性<xref:System.Windows.Controls.TextBox>繫結設定為<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>。  
  
 [!code-xaml[SimpleBinding#USTHowTo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml#usthowto)]  
  
 如此一來，<xref:System.Windows.Controls.TextBlock>顯示相同的文字 （因為來源變更） 在使用者輸入的文字放到<xref:System.Windows.Controls.TextBox>，如下列範例的螢幕擷取畫面所示：  
  
 ![簡單資料繫結範例螢幕擷取畫面](../../../../docs/framework/wpf/data/media/databindingsimplebindingsample2.png "DataBindingSimpleBindingSample2")  
  
 如果您有一個對話方塊或使用者可編輯的表單，而且您想要延遲來源更新，直到使用者完成編輯欄位，並按一下 [確定]，您可以設定<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>的繫結，以值<xref:System.Windows.Data.UpdateSourceTrigger.Explicit>，如下列範例所示：  
  
 [!code-xaml[UpdateSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]  
  
 當您將<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>值設定為<xref:System.Windows.Data.UpdateSourceTrigger.Explicit>，來源值只會變更當應用程式呼叫<xref:System.Windows.Data.BindingExpression.UpdateSource%2A>方法。 下列範例示範如何呼叫<xref:System.Windows.Data.BindingExpression.UpdateSource%2A>如`itemNameTextBox`:  
  
 [!code-csharp[UpdateSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]  
  
> [!NOTE]
>  您可以使用相同的技巧屬性的其他控制項，但請注意其他大多數屬性具有預設值<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>值<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>。 如需詳細資訊，請參閱<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>屬性頁。  
  
> [!NOTE]
>  <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>屬性處理來源的更新，因此才有意義的<xref:System.Windows.Data.BindingMode.TwoWay>或<xref:System.Windows.Data.BindingMode.OneWayToSource>繫結。 如<xref:System.Windows.Data.BindingMode.TwoWay>和<xref:System.Windows.Data.BindingMode.OneWayToSource>運作，以提供屬性變更告知的來源物件需求的繫結。 如需詳細資訊，請參考本主題中引用的範例。 此外，您還可以參閱[實作屬性變更通知](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md)。  
  
## <a name="see-also"></a>另請參閱  
 [操作說明主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
