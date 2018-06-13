---
title: 如何： 瀏覽的頁面
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pages [WPF], navigating to
- navigation [WPF], to page
ms.assetid: 2a556fc0-748b-417f-a58a-0d05a7afb66f
ms.openlocfilehash: 896287376979d40816e3937fff77b38bf71a62f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548384"
---
# <a name="how-to-navigate-to-a-page"></a><span data-ttu-id="1d87b-102">如何： 瀏覽的頁面</span><span class="sxs-lookup"><span data-stu-id="1d87b-102">How to: Navigate to a Page</span></span>
<span data-ttu-id="1d87b-103">此範例說明幾種方法中的頁面可以巡覽至<xref:System.Windows.Navigation.NavigationWindow>。</span><span class="sxs-lookup"><span data-stu-id="1d87b-103">This example illustrates several ways in which a page can be navigated to from a <xref:System.Windows.Navigation.NavigationWindow>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d87b-104">範例</span><span class="sxs-lookup"><span data-stu-id="1d87b-104">Example</span></span>  
 <span data-ttu-id="1d87b-105">可能會<xref:System.Windows.Navigation.NavigationWindow>瀏覽至頁面，使用下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="1d87b-105">It is possible for a <xref:System.Windows.Navigation.NavigationWindow> to navigate to a page using one of the following:</span></span>  
  
-   <span data-ttu-id="1d87b-106"><xref:System.Windows.Navigation.NavigationWindow.Source%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="1d87b-106">The <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property.</span></span>  
  
-   <span data-ttu-id="1d87b-107"><xref:System.Windows.Navigation.NavigationWindow.Navigate%2A> 方法</span><span class="sxs-lookup"><span data-stu-id="1d87b-107">The <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A> method.</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateToPageCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatetopagecode)]
 [!code-vb[HOWTONavigationSnippets#NavigateToPageCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatetopagecode)]  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_uri#initcap#plural](../../../../includes/tlasharptla-urisharpinitcapsharpplural-md.md)]<span data-ttu-id="1d87b-108"> 可以是相對或絕對。</span><span class="sxs-lookup"><span data-stu-id="1d87b-108"> can be either relative or absolute.</span></span> <span data-ttu-id="1d87b-109">如需詳細資訊，請參閱 [WPF 中的 Pack URI](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="1d87b-109">For more information, see [Pack URIs in WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d87b-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d87b-110">See Also</span></span>  
 <xref:System.Windows.Controls.Frame>  
 <xref:System.Windows.Controls.Page>  
 <xref:System.Windows.Navigation.NavigationService>
