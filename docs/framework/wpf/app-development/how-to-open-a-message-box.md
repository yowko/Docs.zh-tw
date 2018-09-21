---
title: 如何： 開啟訊息方塊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message boxes [WPF], opening
- opening message boxes [WPF]
ms.assetid: acaad17f-af43-4eca-a004-f1c9e7c6f292
ms.openlocfilehash: f05190030ed6324917348fa1926abd5385e30f7e
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2018
ms.locfileid: "46507774"
---
# <a name="how-to-open-a-message-box"></a><span data-ttu-id="3402d-102">如何： 開啟訊息方塊</span><span class="sxs-lookup"><span data-stu-id="3402d-102">How to: Open a Message Box</span></span>
<span data-ttu-id="3402d-103">此範例示範如何開啟訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="3402d-103">This example shows how to open a message box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3402d-104">範例</span><span class="sxs-lookup"><span data-stu-id="3402d-104">Example</span></span>  
 <span data-ttu-id="3402d-105">訊息方塊是預先強制回應對話方塊向使用者顯示資訊。</span><span class="sxs-lookup"><span data-stu-id="3402d-105">A message box is a prefabricated modal dialog box for displaying information to users.</span></span> <span data-ttu-id="3402d-106">開啟訊息方塊，藉由呼叫靜態<xref:System.Windows.MessageBox.Show%2A>方法的<xref:System.Windows.MessageBox>類別。</span><span class="sxs-lookup"><span data-stu-id="3402d-106">A message box is opened by calling the static <xref:System.Windows.MessageBox.Show%2A> method of the <xref:System.Windows.MessageBox> class.</span></span> <span data-ttu-id="3402d-107">當<xref:System.Windows.MessageBox.Show%2A>是呼叫，將訊息傳遞使用字串參數。</span><span class="sxs-lookup"><span data-stu-id="3402d-107">When <xref:System.Windows.MessageBox.Show%2A> is called, the message is passed using a string parameter.</span></span> <span data-ttu-id="3402d-108">數個多載<xref:System.Windows.MessageBox.Show%2A>可讓您將會出現訊息方塊的方式 (請參閱<xref:System.Windows.MessageBox>)。</span><span class="sxs-lookup"><span data-stu-id="3402d-108">Several overloads of <xref:System.Windows.MessageBox.Show%2A> allow you to configure how a message box will appear (see <xref:System.Windows.MessageBox>).</span></span>  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a><span data-ttu-id="3402d-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3402d-109">See Also</span></span>  
 [<span data-ttu-id="3402d-110">MessageBox 範例</span><span class="sxs-lookup"><span data-stu-id="3402d-110">MessageBox Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160023)
