---
title: HOW TO：在瀏覽記錄中向前或向後巡覽
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating forward
- navigation [WPF], through navigation history (forward)
ms.assetid: 5939d574-5f53-469e-85f5-1f2b13607caa
ms.openlocfilehash: 4c20ebfab45a24cf34b1476fb94dae6913fb4d99
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947754"
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a>HOW TO：在瀏覽記錄中向前或向後巡覽
此範例說明如何巡覽向前或向後巡覽記錄中的項目。  
  
## <a name="example"></a>範例  
 從下列主控件中的內容中執行的程式碼可以巡覽向前或向後巡覽記錄，一次的一個項目。  
  
- <xref:System.Windows.Navigation.NavigationWindow> 使用 <xref:System.Windows.Navigation.NavigationService>  
  
- <xref:System.Windows.Controls.Frame> 使用 <xref:System.Windows.Navigation.NavigationService>  
  
- [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]  
  
 您可以瀏覽正向的一個項目之前，您必須先檢查，有項目向前巡覽記錄中藉由檢查**CanGoForward**屬性。 若要瀏覽正向的一個項目，請呼叫**GoForward**方法。 下列範例所示：  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 您可以瀏覽之前後一個項目，您必須先檢查項目中沒有向後巡覽記錄藉由檢查**CanGoBack**屬性。 若要瀏覽回上一項目，請呼叫**GoBack**方法。 下列範例所示：  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoForward**， **GoForward**， **CanGoBack**，和**GoBack**實作<xref:System.Windows.Navigation.NavigationWindow>， <xref:System.Windows.Controls.Frame>，以及<xref:System.Windows.Navigation.NavigationService>。  
  
> [!NOTE]
>  如果您呼叫**GoForward**，並向前巡覽記錄中沒有任何項目或如果您呼叫**GoBack**，並向後巡覽記錄中沒有任何項目<xref:System.InvalidOperationException>就會擲回。
