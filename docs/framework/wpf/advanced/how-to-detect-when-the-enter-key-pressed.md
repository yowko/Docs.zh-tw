---
title: 如何：偵測何時按下 Enter 鍵
description: 當 Windows Presentation Foundation 中的鍵盤上選取了 Enter 鍵時，請加以偵測。 這個範例包含 XAML 和程式碼後置檔案。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
ms.openlocfilehash: a955f52ec7bf93b32c70259b27fb51747664ac2e
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163185"
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a>如何：偵測何時按下 Enter 鍵
這個範例示範如何偵測 <xref:System.Windows.Input.Key.Enter> 鍵盤上按下按鍵的時間。  
  
 這個範例包含檔案 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 和程式碼後置檔案。  
  
## <a name="example"></a>範例  
 當使用者按下 <xref:System.Windows.Input.Key.Enter> 中的鍵時 <xref:System.Windows.Controls.TextBox> ，文字方塊中的輸入會出現在的另一個區域中 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 。  
  
 下列 XAML 會建立使用者介面，其中包含 <xref:System.Windows.Controls.StackPanel> 、 <xref:System.Windows.Controls.TextBlock> 和 <xref:System.Windows.Controls.TextBox> 。  
  
 [!code-xaml[keydown#KeyDownUI](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 下列程式碼後置會建立 <xref:System.Windows.UIElement.KeyDown> 事件處理常式。  如果按下的按鍵是 <xref:System.Windows.Input.Key.Enter> 金鑰，則會在中顯示訊息 <xref:System.Windows.Controls.TextBlock> 。  
  
 [!code-csharp[keydown#KeyDownSample](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a>另請參閱

- [輸入概觀](input-overview.md)
- [路由事件概觀](routed-events-overview.md)
