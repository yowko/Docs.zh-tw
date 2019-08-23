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
# <a name="how-to-return-a-dialog-box-result"></a>HOW TO：傳回對話方塊結果
這個範例會示範如何透過呼叫<xref:System.Windows.Window.ShowDialog%2A>來抓取開啟之視窗的對話方塊結果。  
  
## <a name="example"></a>範例  
 在對話方塊關閉之前, 應該<xref:System.Windows.Window.DialogResult%2A> <xref:System.Nullable%601> <xref:System.Boolean>使用來設定其屬性, 以指出使用者關閉對話方塊的方式。 會傳回<xref:System.Windows.Window.ShowDialog%2A>這個值, 以允許用戶端程式代碼判斷對話方塊的關閉方式, 以及如何處理結果。  
  
> [!NOTE]
> <xref:System.Windows.Window.DialogResult%2A>只有在透過呼叫<xref:System.Windows.Window.ShowDialog%2A>開啟視窗時, 才能設定。  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 呼叫<xref:System.Windows.Window.ShowDialog%2A>需要有許可權才能使用所有的 windows 和使用者輸入事件, 而不受限制。
