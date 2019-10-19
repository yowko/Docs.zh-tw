---
title: 如何：流覽至頁面
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pages [WPF], navigating to
- navigation [WPF], to page
ms.assetid: 2a556fc0-748b-417f-a58a-0d05a7afb66f
ms.openlocfilehash: 25a0dbbc609c7b6f8f2878d2068e61e492a59c7e
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582544"
---
# <a name="how-to-navigate-to-a-page"></a><span data-ttu-id="08ac5-102">如何：流覽至頁面</span><span class="sxs-lookup"><span data-stu-id="08ac5-102">How to: Navigate to a Page</span></span>
<span data-ttu-id="08ac5-103">這個範例說明可從 <xref:System.Windows.Navigation.NavigationWindow> 流覽頁面的數種方式。</span><span class="sxs-lookup"><span data-stu-id="08ac5-103">This example illustrates several ways in which a page can be navigated to from a <xref:System.Windows.Navigation.NavigationWindow>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08ac5-104">範例</span><span class="sxs-lookup"><span data-stu-id="08ac5-104">Example</span></span>  
 <span data-ttu-id="08ac5-105">@No__t_0 可以使用下列其中一種方式流覽至頁面：</span><span class="sxs-lookup"><span data-stu-id="08ac5-105">It is possible for a <xref:System.Windows.Navigation.NavigationWindow> to navigate to a page using one of the following:</span></span>  
  
- <span data-ttu-id="08ac5-106"><xref:System.Windows.Navigation.NavigationWindow.Source%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="08ac5-106">The <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property.</span></span>  
  
- <span data-ttu-id="08ac5-107"><xref:System.Windows.Navigation.NavigationWindow.Navigate%2A> 方法</span><span class="sxs-lookup"><span data-stu-id="08ac5-107">The <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A> method.</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatetopagecode)]
 [!code-vb[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatetopagecode)]  
  
> [!NOTE]
> <span data-ttu-id="08ac5-108">統一資源識別項（Uri）可以是 [相對] 或 [絕對]。</span><span class="sxs-lookup"><span data-stu-id="08ac5-108">Uniform resource identifiers (URIs) can be either relative or absolute.</span></span> <span data-ttu-id="08ac5-109">如需詳細資訊，請參閱 [WPF 中的 Pack URI](pack-uris-in-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="08ac5-109">For more information, see [Pack URIs in WPF](pack-uris-in-wpf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08ac5-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="08ac5-110">See also</span></span>

- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.NavigationService>
