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
# <a name="how-to-return-a-dialog-box-result"></a>如何： 傳回對話方塊結果
這個範例示範如何擷取開啟的視窗，藉由呼叫的對話方塊結果<xref:System.Windows.Window.ShowDialog%2A>。  
  
## <a name="example"></a>範例  
 對話框會關閉之前，其<xref:System.Windows.Window.DialogResult%2A>屬性應該設定具有<xref:System.Nullable%601> <xref:System.Boolean> ，指出使用者關閉對話方塊中的方式。 這個值由<xref:System.Windows.Window.ShowDialog%2A>允許用戶端程式碼，來決定對話方塊關閉的方式，因此，如何處理的結果。  
  
> [!NOTE]
>  <xref:System.Windows.Window.DialogResult%2A> 您可以只將如果視窗已開啟藉由呼叫<xref:System.Windows.Window.ShowDialog%2A>。  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 呼叫<xref:System.Windows.Window.ShowDialog%2A>需要使用所有視窗和不受限制的使用者輸入的事件的權限。
