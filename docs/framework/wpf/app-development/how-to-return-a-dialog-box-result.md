---
title: 作法：傳回對話方塊結果
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], returning results
ms.assetid: 4c5cf286-746b-4052-934d-d80cbf8acba3
ms.openlocfilehash: 5e3670006762bcd09634b29314ecf2d05b1a44da
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968237"
---
# <a name="how-to-return-a-dialog-box-result"></a><span data-ttu-id="315a2-102">HOW TO：傳回對話方塊結果</span><span class="sxs-lookup"><span data-stu-id="315a2-102">How to: Return a Dialog Box Result</span></span>
<span data-ttu-id="315a2-103">這個範例會示範如何透過呼叫<xref:System.Windows.Window.ShowDialog%2A>來抓取開啟之視窗的對話方塊結果。</span><span class="sxs-lookup"><span data-stu-id="315a2-103">This example shows how to retrieve the dialog result for a window that is opened by calling <xref:System.Windows.Window.ShowDialog%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="315a2-104">範例</span><span class="sxs-lookup"><span data-stu-id="315a2-104">Example</span></span>  
 <span data-ttu-id="315a2-105">在對話方塊關閉之前, 應該<xref:System.Windows.Window.DialogResult%2A> <xref:System.Nullable%601> <xref:System.Boolean>使用來設定其屬性, 以指出使用者關閉對話方塊的方式。</span><span class="sxs-lookup"><span data-stu-id="315a2-105">Before a dialog box closes, its <xref:System.Windows.Window.DialogResult%2A> property should be set with a <xref:System.Nullable%601><xref:System.Boolean> that indicates how the user closed the dialog box.</span></span> <span data-ttu-id="315a2-106">會傳回<xref:System.Windows.Window.ShowDialog%2A>這個值, 以允許用戶端程式代碼判斷對話方塊的關閉方式, 以及如何處理結果。</span><span class="sxs-lookup"><span data-stu-id="315a2-106">This value is returned by <xref:System.Windows.Window.ShowDialog%2A> to allow client code to determine how the dialog box was closed and, consequently, how to process the result.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="315a2-107"><xref:System.Windows.Window.DialogResult%2A>只有在透過呼叫<xref:System.Windows.Window.ShowDialog%2A>開啟視窗時, 才能設定。</span><span class="sxs-lookup"><span data-stu-id="315a2-107"><xref:System.Windows.Window.DialogResult%2A> can only be set if a window was opened by calling <xref:System.Windows.Window.ShowDialog%2A>.</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="315a2-108">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="315a2-108">.NET Framework Security</span></span>  
 <span data-ttu-id="315a2-109">呼叫<xref:System.Windows.Window.ShowDialog%2A>需要有許可權才能使用所有的 windows 和使用者輸入事件, 而不受限制。</span><span class="sxs-lookup"><span data-stu-id="315a2-109">Calling <xref:System.Windows.Window.ShowDialog%2A> requires permission to use all windows and user input events without restriction.</span></span>
