---
title: 如何：偵測何時按下 Enter 鍵
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
ms.openlocfilehash: 1de11cd30d1990dcd2bc927a69b60c66c721addb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a>如何：偵測何時按下 Enter 鍵
此範例示範如何偵測何時<xref:System.Windows.Input.Key.Enter>鍵盤上按下按鍵。  
  
 這個範例包含[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案和程式碼後置檔案。  
  
## <a name="example"></a>範例  
 當使用者按<xref:System.Windows.Input.Key.Enter>中的索引鍵<xref:System.Windows.Controls.TextBox>，另一個區域中出現在文字方塊中輸入[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]。  
  
 下列[!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)]建立使用者介面，其中包含<xref:System.Windows.Controls.StackPanel>、 <xref:System.Windows.Controls.TextBlock>，和<xref:System.Windows.Controls.TextBox>。  
  
 [!code-xaml[keydown#KeyDownUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 下列程式碼後置建立<xref:System.Windows.UIElement.KeyDown>事件處理常式。  如果要在按下的按鍵是<xref:System.Windows.Input.Key.Enter>索引鍵，訊息會顯示在<xref:System.Windows.Controls.TextBlock>。  
  
 [!code-csharp[keydown#KeyDownSample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a>另請參閱  
 [輸入概觀](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
