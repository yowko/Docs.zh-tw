---
title: "如何：TextBox 文字更新來源時控制 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "資料繫結, 來源更新的時機"
  - "來源更新, 時機"
  - "來源更新的時機"
ms.assetid: ffb7b96a-351d-4c68-81e7-054033781c64
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：TextBox 文字更新來源時控制
本主題說明如何使用 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 屬性，控制[繫結來源](GTMT)的更新時機。  本主題使用 <xref:System.Windows.Controls.TextBox> 控制項做為範例。  
  
## 範例  
 <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> 屬性預設的 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 值為 <xref:System.Windows.Data.UpdateSourceTrigger>。  這表示，如果應用程式有 <xref:System.Windows.Controls.TextBox>，其中包含資料繫結的 <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> 屬性，則在 <xref:System.Windows.Controls.TextBox> 失去焦點 \(例如，當您按一下 <xref:System.Windows.Controls.TextBox> 以外的其他位置\) 前，您輸入 <xref:System.Windows.Controls.TextBox> 中的文字並不會更新來源。  
  
 如果您想要在鍵入文字時更新來源，請將繫結的 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 設定為 <xref:System.Windows.Data.UpdateSourceTrigger>。  在下列範例中，<xref:System.Windows.Controls.TextBox> 和 <xref:System.Windows.Controls.TextBlock> 的 `Text` 屬性都會繫結至相同的來源屬性。  <xref:System.Windows.Controls.TextBox> 繫結的 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 屬性會設定為 <xref:System.Windows.Data.UpdateSourceTrigger>。  
  
 [!code-xml[SimpleBinding#USTHowTo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml#usthowto)]  
  
 因此，當使用者輸入文字到 <xref:System.Windows.Controls.TextBox> 時，<xref:System.Windows.Controls.TextBlock> 會顯示相同的文字 \(因為來源變更了\)，如下列範例的螢幕擷取畫面所示：  
  
 ![簡單資料繫結範例螢幕擷取畫面](../../../../docs/framework/wpf/data/media/databindingsimplebindingsample2.png "DataBindingSimpleBindingSample2")  
  
 如果您有對話方塊或使用者可編輯的表單，而且想要將來源更新延到使用者完成欄位編輯並按一下 \[確定\] 後，您可以將繫結的 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 值設定為 <xref:System.Windows.Data.UpdateSourceTrigger>，如下列範例所示：  
  
 [!code-xml[UpdateSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]  
  
 如果您將 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 值設定為 <xref:System.Windows.Data.UpdateSourceTrigger>，只有在應用程式呼叫 <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> 方法時，才會變更來源值。  下列範例顯示如何對 `itemNameTextBox` 呼叫 <xref:System.Windows.Data.BindingExpression.UpdateSource%2A>：  
  
 [!code-csharp[UpdateSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]  
  
> [!NOTE]
>  您可以對其他控制項的屬性使用相同的方法，但請記得其他大部分屬性都具有 <xref:System.Windows.Data.UpdateSourceTrigger> 的預設 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 值。  如需詳細資訊，請參閱 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 屬性頁面。  
  
> [!NOTE]
>  <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 屬性會處理來源更新，因此僅與 <xref:System.Windows.Data.BindingMode> 或 <xref:System.Windows.Data.BindingMode> 繫結相關。  為了讓 <xref:System.Windows.Data.BindingMode> 和 <xref:System.Windows.Data.BindingMode> 繫結得以生效，來源物件必須提供屬性變更告知。  如需詳細資訊，請參考本主題中引用的範例。  此外，您還可以參閱 [實作屬性變更通知](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md)。  
  
## 請參閱  
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)