---
title: HOW TO：開啟的對話方塊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- opening dialog boxes [WPF]
- dialog boxes [WPF], opening
ms.assetid: 6b1557d2-da98-4ef4-9f68-4089f04ab9ea
ms.openlocfilehash: 0ed41d212eee74d0c3eed1d3341d64a6abc876a5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638141"
---
# <a name="how-to-open-a-dialog-box"></a><span data-ttu-id="6404a-102">HOW TO：開啟的對話方塊</span><span class="sxs-lookup"><span data-stu-id="6404a-102">How to: Open a Dialog Box</span></span>
<span data-ttu-id="6404a-103">此範例示範如何開啟的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6404a-103">This example shows how to open a dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6404a-104">範例</span><span class="sxs-lookup"><span data-stu-id="6404a-104">Example</span></span>  
 <span data-ttu-id="6404a-105">對話方塊是由具現化已開啟的視窗<xref:System.Windows.Window>，然後呼叫<xref:System.Windows.Window.ShowDialog%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="6404a-105">A dialog box is a window that is opened by instantiating <xref:System.Windows.Window> and calling the <xref:System.Windows.Window.ShowDialog%2A> method.</span></span> <span data-ttu-id="6404a-106"><xref:System.Windows.Window.ShowDialog%2A> 開啟視窗，並且不會在關閉 [新增] 對話方塊之前傳回。</span><span class="sxs-lookup"><span data-stu-id="6404a-106"><xref:System.Windows.Window.ShowDialog%2A> opens a window and doesn't return until the new dialog box has been closed.</span></span> <span data-ttu-id="6404a-107">這種視窗，也就是*強制回應* 視窗中，並限制使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="6404a-107">This type of window is also known as a *modal* window, and restricts user input.</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewdialogboxcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewdialogboxcode)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="6404a-108">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="6404a-108">.NET Framework Security</span></span>  
 <span data-ttu-id="6404a-109">呼叫<xref:System.Windows.Window.ShowDialog%2A>需要使用所有 windows 和不受限制的使用者輸入的事件的權限。</span><span class="sxs-lookup"><span data-stu-id="6404a-109">Calling <xref:System.Windows.Window.ShowDialog%2A> requires permission to use all windows and user input events without restriction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6404a-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6404a-110">See also</span></span>
- [<span data-ttu-id="6404a-111">傳回對話方塊結果</span><span class="sxs-lookup"><span data-stu-id="6404a-111">Return a Dialog Box Result</span></span>](../../../../docs/framework/wpf/app-development/how-to-return-a-dialog-box-result.md)
