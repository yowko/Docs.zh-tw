---
title: 如何：開啟訊息方塊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message boxes [WPF], opening
- opening message boxes [WPF]
ms.assetid: acaad17f-af43-4eca-a004-f1c9e7c6f292
ms.openlocfilehash: bd2c4dce78e46163eb4628cb3aab829fc0173edf
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77123723"
---
# <a name="how-to-open-a-message-box"></a><span data-ttu-id="820e7-102">如何：開啟訊息方塊</span><span class="sxs-lookup"><span data-stu-id="820e7-102">How to: Open a Message Box</span></span>
<span data-ttu-id="820e7-103">這個範例顯示如何開啟訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="820e7-103">This example shows how to open a message box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="820e7-104">範例</span><span class="sxs-lookup"><span data-stu-id="820e7-104">Example</span></span>  
 <span data-ttu-id="820e7-105">訊息方塊是用來向使用者顯示資訊的換成強制回應對話方塊。</span><span class="sxs-lookup"><span data-stu-id="820e7-105">A message box is a prefabricated modal dialog box for displaying information to users.</span></span> <span data-ttu-id="820e7-106">藉由呼叫 <xref:System.Windows.MessageBox> 類別的靜態 <xref:System.Windows.MessageBox.Show%2A> 方法，即可開啟訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="820e7-106">A message box is opened by calling the static <xref:System.Windows.MessageBox.Show%2A> method of the <xref:System.Windows.MessageBox> class.</span></span> <span data-ttu-id="820e7-107">呼叫 <xref:System.Windows.MessageBox.Show%2A> 時，會使用字串參數來傳遞訊息。</span><span class="sxs-lookup"><span data-stu-id="820e7-107">When <xref:System.Windows.MessageBox.Show%2A> is called, the message is passed using a string parameter.</span></span> <span data-ttu-id="820e7-108"><xref:System.Windows.MessageBox.Show%2A> 的數個多載可讓您設定訊息方塊的顯示方式（請參閱 <xref:System.Windows.MessageBox>）。</span><span class="sxs-lookup"><span data-stu-id="820e7-108">Several overloads of <xref:System.Windows.MessageBox.Show%2A> allow you to configure how a message box will appear (see <xref:System.Windows.MessageBox>).</span></span>  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a><span data-ttu-id="820e7-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="820e7-109">See also</span></span>

- [<span data-ttu-id="820e7-110">MessageBox 範例</span><span class="sxs-lookup"><span data-stu-id="820e7-110">MessageBox Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/MessageBox)
