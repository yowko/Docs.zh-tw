---
title: "如何： 傳回對話方塊結果"
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
helpviewer_keywords: dialog boxes [WPF], returning results
ms.assetid: 4c5cf286-746b-4052-934d-d80cbf8acba3
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5f8133ffa7be9cb4e0600fc2681402d5e0f7471c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-return-a-dialog-box-result"></a>如何： 傳回對話方塊結果
這個範例示範如何擷取開啟的視窗，藉由呼叫的對話方塊結果<xref:System.Windows.Window.ShowDialog%2A>。  
  
## <a name="example"></a>範例  
 對話框會關閉之前，其<xref:System.Windows.Window.DialogResult%2A>屬性應該設定具有<xref:System.Nullable%601> <xref:System.Boolean> ，指出使用者關閉對話方塊中的方式。 這個值由<xref:System.Windows.Window.ShowDialog%2A>允許用戶端程式碼，來決定對話方塊關閉的方式，因此，如何處理的結果。  
  
> [!NOTE]
>  <xref:System.Windows.Window.DialogResult%2A>您可以只將如果視窗已開啟藉由呼叫<xref:System.Windows.Window.ShowDialog%2A>。  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 呼叫<xref:System.Windows.Window.ShowDialog%2A>需要使用所有視窗和不受限制的使用者輸入的事件的權限。
