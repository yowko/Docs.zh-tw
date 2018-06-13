---
title: 如何： 開啟視窗
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- windows [WPF], opening
- opening windows [WPF]
ms.assetid: 6b91b2bb-fda7-491d-a72e-139dd630a5b0
ms.openlocfilehash: 23dc74666d8f47a0fb735d96ad22ed56c96bdbc5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545460"
---
# <a name="how-to-open-a-window"></a><span data-ttu-id="483af-102">如何： 開啟視窗</span><span class="sxs-lookup"><span data-stu-id="483af-102">How to: Open a Window</span></span>
<span data-ttu-id="483af-103">這個範例示範如何開啟視窗。</span><span class="sxs-lookup"><span data-stu-id="483af-103">This example shows how to open a window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="483af-104">範例</span><span class="sxs-lookup"><span data-stu-id="483af-104">Example</span></span>  
 <span data-ttu-id="483af-105">藉由執行個體化開啟的視窗<xref:System.Windows.Window>，然後呼叫<xref:System.Windows.Window.Show%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="483af-105">A window is opened by instantiating <xref:System.Windows.Window> and calling the <xref:System.Windows.Window.Show%2A> method.</span></span> <span data-ttu-id="483af-106"><xref:System.Windows.Window.Show%2A> 會開啟視窗並立即傳回而不等候新的視窗關閉。</span><span class="sxs-lookup"><span data-stu-id="483af-106"><xref:System.Windows.Window.Show%2A> opens a window and returns immediately without waiting for the new window to close.</span></span> <span data-ttu-id="483af-107">這類視窗就是所謂*非強制回應*視窗中，並不會限制使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="483af-107">This type of window is also known as a *modeless* window, and doesn't restrict user input.</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewWindowCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewwindowcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewWindowCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewwindowcode)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="483af-108">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="483af-108">.NET Framework Security</span></span>  
 <span data-ttu-id="483af-109">具現化<xref:System.Windows.Window>需要呼叫不安全的原生方法的權限 (請參閱<xref:System.Windows.Window.%23ctor%2A>)。</span><span class="sxs-lookup"><span data-stu-id="483af-109">Instantiating <xref:System.Windows.Window> requires permission to call unsafe native methods (see <xref:System.Windows.Window.%23ctor%2A>).</span></span>
