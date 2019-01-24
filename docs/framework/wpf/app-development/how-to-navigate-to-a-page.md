---
title: HOW TO：瀏覽的頁面
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pages [WPF], navigating to
- navigation [WPF], to page
ms.assetid: 2a556fc0-748b-417f-a58a-0d05a7afb66f
ms.openlocfilehash: 7b76a12cbe6e1622e5624f5416abf24a4ca292a4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536903"
---
# <a name="how-to-navigate-to-a-page"></a><span data-ttu-id="1a4ec-102">HOW TO：瀏覽的頁面</span><span class="sxs-lookup"><span data-stu-id="1a4ec-102">How to: Navigate to a Page</span></span>
<span data-ttu-id="1a4ec-103">此範例說明數種方式，在其中一個頁面可以巡覽到從<xref:System.Windows.Navigation.NavigationWindow>。</span><span class="sxs-lookup"><span data-stu-id="1a4ec-103">This example illustrates several ways in which a page can be navigated to from a <xref:System.Windows.Navigation.NavigationWindow>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a4ec-104">範例</span><span class="sxs-lookup"><span data-stu-id="1a4ec-104">Example</span></span>  
 <span data-ttu-id="1a4ec-105">可能會<xref:System.Windows.Navigation.NavigationWindow>瀏覽至頁面，使用下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="1a4ec-105">It is possible for a <xref:System.Windows.Navigation.NavigationWindow> to navigate to a page using one of the following:</span></span>  
  
-   <span data-ttu-id="1a4ec-106"><xref:System.Windows.Navigation.NavigationWindow.Source%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="1a4ec-106">The <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property.</span></span>  
  
-   <span data-ttu-id="1a4ec-107"><xref:System.Windows.Navigation.NavigationWindow.Navigate%2A> 方法</span><span class="sxs-lookup"><span data-stu-id="1a4ec-107">The <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A> method.</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateToPageCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatetopagecode)]
 [!code-vb[HOWTONavigationSnippets#NavigateToPageCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatetopagecode)]  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_uri#initcap#plural](../../../../includes/tlasharptla-urisharpinitcapsharpplural-md.md)] <span data-ttu-id="1a4ec-108">可以是相對或絕對。</span><span class="sxs-lookup"><span data-stu-id="1a4ec-108">can be either relative or absolute.</span></span> <span data-ttu-id="1a4ec-109">如需詳細資訊，請參閱 [WPF 中的 Pack URI](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="1a4ec-109">For more information, see [Pack URIs in WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a4ec-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a4ec-110">See also</span></span>
- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.NavigationService>
