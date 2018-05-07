---
title: 如何： 重新整理頁面
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pages [WPF], refreshing
- refreshing pages [WPF]
ms.assetid: 06dd1bbd-81c4-40ad-ac0d-7a5b326b1465
ms.openlocfilehash: 27735450360206e0a15ecae00cc9d45f93e4e838
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-refresh-a-page"></a>如何： 重新整理頁面
這個範例示範如何呼叫<xref:System.Windows.Navigation.NavigationWindow.Refresh%2A>方法，以重新整理目前的內容中<xref:System.Windows.Navigation.NavigationWindow>。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Navigation.NavigationWindow.Refresh%2A> 重新整理的目前內容中<xref:System.Windows.Navigation.NavigationWindow>從來源重新載入。  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateRefreshCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigaterefreshcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateRefreshCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigaterefreshcode)]
