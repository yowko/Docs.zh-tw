---
title: HOW TO：偵測何時按下 Enter 鍵
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
ms.openlocfilehash: e2337826077c836696937f91541d6d261f1270aa
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004818"
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a>HOW TO：偵測何時按下 Enter 鍵
這個範例示範如何偵測何時按下鍵盤上的 <xref:System.Windows.Input.Key.Enter> 鍵。  
  
 這個範例是由 @no__t 0 檔案和程式碼後置檔案所組成。  
  
## <a name="example"></a>範例  
 當使用者按下 <xref:System.Windows.Controls.TextBox> 中的 <xref:System.Windows.Input.Key.Enter> 鍵時，文字方塊中的輸入會出現在 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 的另一個區域中。  
  
 下列 XAML 會建立使用者介面，其中包含 <xref:System.Windows.Controls.StackPanel>、<xref:System.Windows.Controls.TextBlock> 和 <xref:System.Windows.Controls.TextBox>。  
  
 [!code-xaml[keydown#KeyDownUI](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 下列程式碼後置會建立 <xref:System.Windows.UIElement.KeyDown> 事件處理常式。  如果按下的索引鍵是 <xref:System.Windows.Input.Key.Enter> 鍵，則會在 <xref:System.Windows.Controls.TextBlock> 中顯示訊息。  
  
 [!code-csharp[keydown#KeyDownSample](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a>另請參閱

- [輸入概觀](input-overview.md)
- [路由事件概觀](routed-events-overview.md)
