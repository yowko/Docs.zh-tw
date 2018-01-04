---
title: "如何： 開啟的對話方塊"
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
- opening dialog boxes [WPF]
- dialog boxes [WPF], opening
ms.assetid: 6b1557d2-da98-4ef4-9f68-4089f04ab9ea
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2e6201b7dbcc57a15583b7d95d6b603ab50e951a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-open-a-dialog-box"></a><span data-ttu-id="6cda8-102">如何： 開啟的對話方塊</span><span class="sxs-lookup"><span data-stu-id="6cda8-102">How to: Open a Dialog Box</span></span>
<span data-ttu-id="6cda8-103">這個範例示範如何開啟的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6cda8-103">This example shows how to open a dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6cda8-104">範例</span><span class="sxs-lookup"><span data-stu-id="6cda8-104">Example</span></span>  
 <span data-ttu-id="6cda8-105">對話方塊是開啟的視窗，藉由執行個體化<xref:System.Windows.Window>，然後呼叫<xref:System.Windows.Window.ShowDialog%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="6cda8-105">A dialog box is a window that is opened by instantiating <xref:System.Windows.Window> and calling the <xref:System.Windows.Window.ShowDialog%2A> method.</span></span> <span data-ttu-id="6cda8-106"><xref:System.Windows.Window.ShowDialog%2A>會開啟視窗並不會在關閉新的對話方塊之前傳回。</span><span class="sxs-lookup"><span data-stu-id="6cda8-106"><xref:System.Windows.Window.ShowDialog%2A> opens a window and doesn't return until the new dialog box has been closed.</span></span> <span data-ttu-id="6cda8-107">這類視窗就是所謂*強制回應*視窗中，並限制使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="6cda8-107">This type of window is also known as a *modal* window, and restricts user input.</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewdialogboxcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewdialogboxcode)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="6cda8-108">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="6cda8-108">.NET Framework Security</span></span>  
 <span data-ttu-id="6cda8-109">呼叫<xref:System.Windows.Window.ShowDialog%2A>需要使用所有視窗和不受限制的使用者輸入的事件的權限。</span><span class="sxs-lookup"><span data-stu-id="6cda8-109">Calling <xref:System.Windows.Window.ShowDialog%2A> requires permission to use all windows and user input events without restriction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cda8-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="6cda8-110">See Also</span></span>  
 [<span data-ttu-id="6cda8-111">傳回對話方塊結果</span><span class="sxs-lookup"><span data-stu-id="6cda8-111">Return a Dialog Box Result</span></span>](../../../../docs/framework/wpf/app-development/how-to-return-a-dialog-box-result.md)
