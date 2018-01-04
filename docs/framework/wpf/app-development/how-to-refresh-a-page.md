---
title: "如何： 重新整理頁面"
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
- pages [WPF], refreshing
- refreshing pages [WPF]
ms.assetid: 06dd1bbd-81c4-40ad-ac0d-7a5b326b1465
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4e250c8dbb04aa3c6dc5397c711a7f97a637f0a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-refresh-a-page"></a><span data-ttu-id="d60a7-102">如何： 重新整理頁面</span><span class="sxs-lookup"><span data-stu-id="d60a7-102">How to: Refresh a Page</span></span>
<span data-ttu-id="d60a7-103">這個範例示範如何呼叫<xref:System.Windows.Navigation.NavigationWindow.Refresh%2A>方法，以重新整理目前的內容中<xref:System.Windows.Navigation.NavigationWindow>。</span><span class="sxs-lookup"><span data-stu-id="d60a7-103">This example shows how to call the <xref:System.Windows.Navigation.NavigationWindow.Refresh%2A> method to refresh the current content in a <xref:System.Windows.Navigation.NavigationWindow>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d60a7-104">範例</span><span class="sxs-lookup"><span data-stu-id="d60a7-104">Example</span></span>  
 <span data-ttu-id="d60a7-105"><xref:System.Windows.Navigation.NavigationWindow.Refresh%2A>重新整理的目前內容中<xref:System.Windows.Navigation.NavigationWindow>從來源重新載入。</span><span class="sxs-lookup"><span data-stu-id="d60a7-105"><xref:System.Windows.Navigation.NavigationWindow.Refresh%2A> refreshes the current content in a <xref:System.Windows.Navigation.NavigationWindow> to be reloaded from its source.</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateRefreshCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigaterefreshcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateRefreshCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigaterefreshcode)]
