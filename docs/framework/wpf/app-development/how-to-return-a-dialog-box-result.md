---
title: 如何： 傳回對話方塊結果
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], returning results
ms.assetid: 4c5cf286-746b-4052-934d-d80cbf8acba3
ms.openlocfilehash: 8f754577a355a58060238bbbb487c36aea14658c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545583"
---
# <a name="how-to-return-a-dialog-box-result"></a><span data-ttu-id="c7fb4-102">如何： 傳回對話方塊結果</span><span class="sxs-lookup"><span data-stu-id="c7fb4-102">How to: Return a Dialog Box Result</span></span>
<span data-ttu-id="c7fb4-103">這個範例示範如何擷取開啟的視窗，藉由呼叫的對話方塊結果<xref:System.Windows.Window.ShowDialog%2A>。</span><span class="sxs-lookup"><span data-stu-id="c7fb4-103">This example shows how to retrieve the dialog result for a window that is opened by calling <xref:System.Windows.Window.ShowDialog%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7fb4-104">範例</span><span class="sxs-lookup"><span data-stu-id="c7fb4-104">Example</span></span>  
 <span data-ttu-id="c7fb4-105">對話框會關閉之前，其<xref:System.Windows.Window.DialogResult%2A>屬性應該設定具有<xref:System.Nullable%601> <xref:System.Boolean> ，指出使用者關閉對話方塊中的方式。</span><span class="sxs-lookup"><span data-stu-id="c7fb4-105">Before a dialog box closes, its <xref:System.Windows.Window.DialogResult%2A> property should be set with a <xref:System.Nullable%601><xref:System.Boolean> that indicates how the user closed the dialog box.</span></span> <span data-ttu-id="c7fb4-106">這個值由<xref:System.Windows.Window.ShowDialog%2A>允許用戶端程式碼，來決定對話方塊關閉的方式，因此，如何處理的結果。</span><span class="sxs-lookup"><span data-stu-id="c7fb4-106">This value is returned by <xref:System.Windows.Window.ShowDialog%2A> to allow client code to determine how the dialog box was closed and, consequently, how to process the result.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7fb4-107"><xref:System.Windows.Window.DialogResult%2A> 您可以只將如果視窗已開啟藉由呼叫<xref:System.Windows.Window.ShowDialog%2A>。</span><span class="sxs-lookup"><span data-stu-id="c7fb4-107"><xref:System.Windows.Window.DialogResult%2A> can only be set if a window was opened by calling <xref:System.Windows.Window.ShowDialog%2A>.</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="c7fb4-108">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="c7fb4-108">.NET Framework Security</span></span>  
 <span data-ttu-id="c7fb4-109">呼叫<xref:System.Windows.Window.ShowDialog%2A>需要使用所有視窗和不受限制的使用者輸入的事件的權限。</span><span class="sxs-lookup"><span data-stu-id="c7fb4-109">Calling <xref:System.Windows.Window.ShowDialog%2A> requires permission to use all windows and user input events without restriction.</span></span>
