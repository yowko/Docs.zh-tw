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
# <a name="how-to-detect-when-the-enter-key-pressed"></a><span data-ttu-id="21e1b-104">如何：偵測何時按下 Enter 鍵</span><span class="sxs-lookup"><span data-stu-id="21e1b-104">How to: Detect When the Enter Key Pressed</span></span>
<span data-ttu-id="21e1b-105">這個範例示範如何偵測 <xref:System.Windows.Input.Key.Enter> 鍵盤上按下按鍵的時間。</span><span class="sxs-lookup"><span data-stu-id="21e1b-105">This example shows how to detect when the <xref:System.Windows.Input.Key.Enter> key is pressed on the keyboard.</span></span>  
  
 <span data-ttu-id="21e1b-106">這個範例包含檔案 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 和程式碼後置檔案。</span><span class="sxs-lookup"><span data-stu-id="21e1b-106">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21e1b-107">範例</span><span class="sxs-lookup"><span data-stu-id="21e1b-107">Example</span></span>  
 <span data-ttu-id="21e1b-108">當使用者按下 <xref:System.Windows.Input.Key.Enter> 中的鍵時 <xref:System.Windows.Controls.TextBox> ，文字方塊中的輸入會出現在的另一個區域中 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="21e1b-108">When the user presses the <xref:System.Windows.Input.Key.Enter> key in the <xref:System.Windows.Controls.TextBox>, the input in the text box appears in another area of the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="21e1b-109">下列 XAML 會建立使用者介面，其中包含 <xref:System.Windows.Controls.StackPanel> 、 <xref:System.Windows.Controls.TextBlock> 和 <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="21e1b-109">The following XAML creates the user interface, which consists of a <xref:System.Windows.Controls.StackPanel>, a <xref:System.Windows.Controls.TextBlock>, and a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 [!code-xaml[keydown#KeyDownUI](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 <span data-ttu-id="21e1b-110">下列程式碼後置會建立 <xref:System.Windows.UIElement.KeyDown> 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="21e1b-110">The following code behind creates the <xref:System.Windows.UIElement.KeyDown> event handler.</span></span>  <span data-ttu-id="21e1b-111">如果按下的按鍵是 <xref:System.Windows.Input.Key.Enter> 金鑰，則會在中顯示訊息 <xref:System.Windows.Controls.TextBlock> 。</span><span class="sxs-lookup"><span data-stu-id="21e1b-111">If the key that is pressed is the <xref:System.Windows.Input.Key.Enter> key, a message is displayed in the <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 [!code-csharp[keydown#KeyDownSample](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a><span data-ttu-id="21e1b-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21e1b-112">See also</span></span>

- [<span data-ttu-id="21e1b-113">輸入概觀</span><span class="sxs-lookup"><span data-stu-id="21e1b-113">Input Overview</span></span>](input-overview.md)
- [<span data-ttu-id="21e1b-114">路由事件概觀</span><span class="sxs-lookup"><span data-stu-id="21e1b-114">Routed Events Overview</span></span>](routed-events-overview.md)
