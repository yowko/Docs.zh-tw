---
title: 如何：在巡覽記錄中前移或後移
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating forward
- navigation [WPF], through navigation history (forward)
ms.assetid: 5939d574-5f53-469e-85f5-1f2b13607caa
ms.openlocfilehash: ac3b8b71b6adf04d71cf35edbb042b82c57d8e1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a>如何：在巡覽記錄中前移或後移
此範例說明如何巡覽向前或向後巡覽記錄中的項目。  
  
## <a name="example"></a>範例  
 從下列主機中的內容中執行的程式碼可以巡覽向前或向後巡覽記錄中，一次的一個項目。  
  
-   <xref:System.Windows.Navigation.NavigationWindow> 使用 <xref:System.Windows.Navigation.NavigationService>  
  
-   <xref:System.Windows.Controls.Frame> 使用 <xref:System.Windows.Navigation.NavigationService>  
  
-   [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]  
  
 您可以瀏覽正向的一個項目之前，您必須先檢查是否有的項目向前巡覽記錄中藉由檢查**CanGoForward**屬性。 若要瀏覽正向的一個項目，請呼叫**GoForward**方法。 下列範例所示：  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 您可以瀏覽之前備份的一個項目，您必須先檢查是否有的項目向後巡覽記錄中藉由檢查**CanGoBack**屬性。 若要瀏覽回一項目，請呼叫**GoBack**方法。 下列範例所示：  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoForward**， **GoForward**， **CanGoBack**，和**GoBack**由實作<xref:System.Windows.Navigation.NavigationWindow>， <xref:System.Windows.Controls.Frame>，和<xref:System.Windows.Navigation.NavigationService>。  
  
> [!NOTE]
>  如果您呼叫**GoForward**，向前巡覽記錄中沒有任何項目，或如果您呼叫**GoBack**，並向後巡覽記錄中沒有任何項目<xref:System.InvalidOperationException>就會擲回。
