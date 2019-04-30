---
title: HOW TO：重新整理頁面
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pages [WPF], refreshing
- refreshing pages [WPF]
ms.assetid: 06dd1bbd-81c4-40ad-ac0d-7a5b326b1465
ms.openlocfilehash: 71a71c91384a8905413358d023531afec23f2d41
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947663"
---
# <a name="how-to-refresh-a-page"></a>HOW TO：重新整理頁面
此範例示範如何呼叫<xref:System.Windows.Navigation.NavigationWindow.Refresh%2A>方法，以重新整理中目前的內容<xref:System.Windows.Navigation.NavigationWindow>。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Navigation.NavigationWindow.Refresh%2A> 重新整理中的目前內容<xref:System.Windows.Navigation.NavigationWindow>與其來源重新載入。  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateRefreshCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigaterefreshcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateRefreshCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigaterefreshcode)]
