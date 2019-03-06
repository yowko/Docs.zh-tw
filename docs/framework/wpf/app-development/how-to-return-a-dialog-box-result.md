---
title: HOW TO：傳回對話方塊結果
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], returning results
ms.assetid: 4c5cf286-746b-4052-934d-d80cbf8acba3
ms.openlocfilehash: b574a5bbc08d947371837116915c2fc8c13ec81d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357764"
---
# <a name="how-to-return-a-dialog-box-result"></a>HOW TO：傳回對話方塊結果
此範例示範如何擷取的視窗，藉由呼叫開啟的對話方塊結果<xref:System.Windows.Window.ShowDialog%2A>。  
  
## <a name="example"></a>範例  
 對話方塊關閉之前，其<xref:System.Windows.Window.DialogResult%2A>應設定屬性，與<xref:System.Nullable%601> <xref:System.Boolean> ，指出使用者關閉對話方塊的方式。 這個值由<xref:System.Windows.Window.ShowDialog%2A>以允許用戶端程式碼，來決定對話方塊關閉的方式，因此，如何處理結果。  
  
> [!NOTE]
>  <xref:System.Windows.Window.DialogResult%2A> 才會設定已開啟的視窗呼叫<xref:System.Windows.Window.ShowDialog%2A>。  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 呼叫<xref:System.Windows.Window.ShowDialog%2A>需要使用所有 windows 和不受限制的使用者輸入的事件的權限。
