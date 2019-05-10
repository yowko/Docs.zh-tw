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
ms.openlocfilehash: 00a41fcf85583ec0d081a2fa099f3a77cfcd2900
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625362"
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a><span data-ttu-id="4aec2-102">HOW TO：在瀏覽記錄中向前或向後巡覽</span><span class="sxs-lookup"><span data-stu-id="4aec2-102">How to: Navigate Forward or Back Through Navigation History</span></span>
<span data-ttu-id="4aec2-103">此範例說明如何巡覽向前或向後巡覽記錄中的項目。</span><span class="sxs-lookup"><span data-stu-id="4aec2-103">This example illustrates how to navigate forward or back to entries in navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4aec2-104">範例</span><span class="sxs-lookup"><span data-stu-id="4aec2-104">Example</span></span>  
 <span data-ttu-id="4aec2-105">從下列主控件中的內容中執行的程式碼可以巡覽向前或向後巡覽記錄，一次的一個項目。</span><span class="sxs-lookup"><span data-stu-id="4aec2-105">Code that runs from content in the following hosts can navigate forward or back through navigation history, one entry at a time.</span></span>  
  
- <span data-ttu-id="4aec2-106"><xref:System.Windows.Navigation.NavigationWindow> 使用 <xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="4aec2-106"><xref:System.Windows.Navigation.NavigationWindow> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
- <span data-ttu-id="4aec2-107"><xref:System.Windows.Controls.Frame> 使用 <xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="4aec2-107"><xref:System.Windows.Controls.Frame> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
- [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]  
  
 <span data-ttu-id="4aec2-108">您可以瀏覽正向的一個項目之前，您必須先檢查，有項目向前巡覽記錄中藉由檢查**CanGoForward**屬性。</span><span class="sxs-lookup"><span data-stu-id="4aec2-108">Before you can navigate forward one entry, you must first check that there are entries in forward navigation history by inspecting the **CanGoForward** property.</span></span> <span data-ttu-id="4aec2-109">若要瀏覽正向的一個項目，請呼叫**GoForward**方法。</span><span class="sxs-lookup"><span data-stu-id="4aec2-109">To navigate forward one entry, you call the **GoForward** method.</span></span> <span data-ttu-id="4aec2-110">下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="4aec2-110">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 <span data-ttu-id="4aec2-111">您可以瀏覽之前後一個項目，您必須先檢查項目中沒有向後巡覽記錄藉由檢查**CanGoBack**屬性。</span><span class="sxs-lookup"><span data-stu-id="4aec2-111">Before you can navigate back one entry, you must first check that there are entries in back navigation history by inspecting the **CanGoBack** property.</span></span> <span data-ttu-id="4aec2-112">若要瀏覽回上一項目，請呼叫**GoBack**方法。</span><span class="sxs-lookup"><span data-stu-id="4aec2-112">To navigate back one entry, you call the **GoBack** method.</span></span> <span data-ttu-id="4aec2-113">下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="4aec2-113">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="4aec2-114">**CanGoForward**， **GoForward**， **CanGoBack**，和**GoBack**實作<xref:System.Windows.Navigation.NavigationWindow>， <xref:System.Windows.Controls.Frame>，以及<xref:System.Windows.Navigation.NavigationService>。</span><span class="sxs-lookup"><span data-stu-id="4aec2-114">**CanGoForward**, **GoForward**, **CanGoBack**, and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4aec2-115">如果您呼叫**GoForward**，並向前巡覽記錄中沒有任何項目或如果您呼叫**GoBack**，並向後巡覽記錄中沒有任何項目<xref:System.InvalidOperationException>就會擲回。</span><span class="sxs-lookup"><span data-stu-id="4aec2-115">If you call **GoForward**, and there are no entries in forward navigation history, or if you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is thrown.</span></span>
