---
title: "如何：偵測何時按下 Enter 鍵"
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
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8311083b4b82d4ab4827e8d0a2cf958c67347014
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a><span data-ttu-id="2248a-102">如何：偵測何時按下 Enter 鍵</span><span class="sxs-lookup"><span data-stu-id="2248a-102">How to: Detect When the Enter Key Pressed</span></span>
<span data-ttu-id="2248a-103">此範例示範如何偵測何時<xref:System.Windows.Input.Key.Enter>鍵盤上按下按鍵。</span><span class="sxs-lookup"><span data-stu-id="2248a-103">This example shows how to detect when the <xref:System.Windows.Input.Key.Enter> key is pressed on the keyboard.</span></span>  
  
 <span data-ttu-id="2248a-104">這個範例包含[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案和程式碼後置檔案。</span><span class="sxs-lookup"><span data-stu-id="2248a-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2248a-105">範例</span><span class="sxs-lookup"><span data-stu-id="2248a-105">Example</span></span>  
 <span data-ttu-id="2248a-106">當使用者按<xref:System.Windows.Input.Key.Enter>中的索引鍵<xref:System.Windows.Controls.TextBox>，另一個區域中出現在文字方塊中輸入[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2248a-106">When the user presses the <xref:System.Windows.Input.Key.Enter> key in the <xref:System.Windows.Controls.TextBox>, the input in the text box appears in another area of the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="2248a-107">下列[!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)]建立使用者介面，其中包含<xref:System.Windows.Controls.StackPanel>、 <xref:System.Windows.Controls.TextBlock>，和<xref:System.Windows.Controls.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="2248a-107">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the user interface, which consists of a <xref:System.Windows.Controls.StackPanel>, a <xref:System.Windows.Controls.TextBlock>, and a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 [!code-xaml[keydown#KeyDownUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 <span data-ttu-id="2248a-108">下列程式碼後置建立<xref:System.Windows.UIElement.KeyDown>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="2248a-108">The following code behind creates the <xref:System.Windows.UIElement.KeyDown> event handler.</span></span>  <span data-ttu-id="2248a-109">如果要在按下的按鍵是<xref:System.Windows.Input.Key.Enter>索引鍵，訊息會顯示在<xref:System.Windows.Controls.TextBlock>。</span><span class="sxs-lookup"><span data-stu-id="2248a-109">If the key that is pressed is the <xref:System.Windows.Input.Key.Enter> key, a message is displayed in the <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 [!code-csharp[keydown#KeyDownSample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a><span data-ttu-id="2248a-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2248a-110">See Also</span></span>  
 [<span data-ttu-id="2248a-111">輸入概觀</span><span class="sxs-lookup"><span data-stu-id="2248a-111">Input Overview</span></span>](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [<span data-ttu-id="2248a-112">路由事件概觀</span><span class="sxs-lookup"><span data-stu-id="2248a-112">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
