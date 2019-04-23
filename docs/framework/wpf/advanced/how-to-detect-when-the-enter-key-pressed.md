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
ms.openlocfilehash: a99da5804bbc31897198b9b6d9e21da9f17dfe26
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59204610"
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a><span data-ttu-id="3d447-102">HOW TO：偵測何時按下 Enter 鍵</span><span class="sxs-lookup"><span data-stu-id="3d447-102">How to: Detect When the Enter Key Pressed</span></span>
<span data-ttu-id="3d447-103">此範例示範如何偵測何時<xref:System.Windows.Input.Key.Enter>鍵盤上按下按鍵。</span><span class="sxs-lookup"><span data-stu-id="3d447-103">This example shows how to detect when the <xref:System.Windows.Input.Key.Enter> key is pressed on the keyboard.</span></span>  
  
 <span data-ttu-id="3d447-104">此範例中組成[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案和程式碼後置檔案。</span><span class="sxs-lookup"><span data-stu-id="3d447-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d447-105">範例</span><span class="sxs-lookup"><span data-stu-id="3d447-105">Example</span></span>  
 <span data-ttu-id="3d447-106">當使用者按下<xref:System.Windows.Input.Key.Enter>中的索引鍵<xref:System.Windows.Controls.TextBox>，在文字方塊中輸入會出現在另一個區域[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3d447-106">When the user presses the <xref:System.Windows.Input.Key.Enter> key in the <xref:System.Windows.Controls.TextBox>, the input in the text box appears in another area of the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="3d447-107">下列[!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)]建立使用者介面，其中包含<xref:System.Windows.Controls.StackPanel>，則<xref:System.Windows.Controls.TextBlock>，和<xref:System.Windows.Controls.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="3d447-107">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the user interface, which consists of a <xref:System.Windows.Controls.StackPanel>, a <xref:System.Windows.Controls.TextBlock>, and a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 [!code-xaml[keydown#KeyDownUI](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 <span data-ttu-id="3d447-108">下列程式碼後置建立<xref:System.Windows.UIElement.KeyDown>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="3d447-108">The following code behind creates the <xref:System.Windows.UIElement.KeyDown> event handler.</span></span>  <span data-ttu-id="3d447-109">如果已按下的按鍵<xref:System.Windows.Input.Key.Enter>鍵，訊息會顯示在<xref:System.Windows.Controls.TextBlock>。</span><span class="sxs-lookup"><span data-stu-id="3d447-109">If the key that is pressed is the <xref:System.Windows.Input.Key.Enter> key, a message is displayed in the <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 [!code-csharp[keydown#KeyDownSample](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a><span data-ttu-id="3d447-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d447-110">See also</span></span>

- [<span data-ttu-id="3d447-111">輸入概觀</span><span class="sxs-lookup"><span data-stu-id="3d447-111">Input Overview</span></span>](input-overview.md)
- [<span data-ttu-id="3d447-112">路由事件概觀</span><span class="sxs-lookup"><span data-stu-id="3d447-112">Routed Events Overview</span></span>](routed-events-overview.md)
