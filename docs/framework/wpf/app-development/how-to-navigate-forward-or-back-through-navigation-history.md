---
title: "如何：在巡覽記錄中前移或後移"
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
- history [WPF], navigating forward
- navigation [WPF], through navigation history (forward)
ms.assetid: 5939d574-5f53-469e-85f5-1f2b13607caa
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7ad909af071d4006346d64ad8e4bd7b57c4eefad
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a><span data-ttu-id="4935d-102">如何：在巡覽記錄中前移或後移</span><span class="sxs-lookup"><span data-stu-id="4935d-102">How to: Navigate Forward or Back Through Navigation History</span></span>
<span data-ttu-id="4935d-103">此範例說明如何巡覽向前或向後巡覽記錄中的項目。</span><span class="sxs-lookup"><span data-stu-id="4935d-103">This example illustrates how to navigate forward or back to entries in navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4935d-104">範例</span><span class="sxs-lookup"><span data-stu-id="4935d-104">Example</span></span>  
 <span data-ttu-id="4935d-105">從下列主機中的內容中執行的程式碼可以巡覽向前或向後巡覽記錄中，一次的一個項目。</span><span class="sxs-lookup"><span data-stu-id="4935d-105">Code that runs from content in the following hosts can navigate forward or back through navigation history, one entry at a time.</span></span>  
  
-   <span data-ttu-id="4935d-106"><xref:System.Windows.Navigation.NavigationWindow>使用<xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="4935d-106"><xref:System.Windows.Navigation.NavigationWindow> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
-   <span data-ttu-id="4935d-107"><xref:System.Windows.Controls.Frame>使用<xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="4935d-107"><xref:System.Windows.Controls.Frame> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
-   [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]  
  
 <span data-ttu-id="4935d-108">您可以瀏覽正向的一個項目之前，您必須先檢查是否有的項目向前巡覽記錄中藉由檢查**CanGoForward**屬性。</span><span class="sxs-lookup"><span data-stu-id="4935d-108">Before you can navigate forward one entry, you must first check that there are entries in forward navigation history by inspecting the **CanGoForward** property.</span></span> <span data-ttu-id="4935d-109">若要瀏覽正向的一個項目，請呼叫**GoForward**方法。</span><span class="sxs-lookup"><span data-stu-id="4935d-109">To navigate forward one entry, you call the **GoForward** method.</span></span> <span data-ttu-id="4935d-110">下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="4935d-110">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 <span data-ttu-id="4935d-111">您可以瀏覽之前備份的一個項目，您必須先檢查是否有的項目向後巡覽記錄中藉由檢查**CanGoBack**屬性。</span><span class="sxs-lookup"><span data-stu-id="4935d-111">Before you can navigate back one entry, you must first check that there are entries in back navigation history by inspecting the **CanGoBack** property.</span></span> <span data-ttu-id="4935d-112">若要瀏覽回一項目，請呼叫**GoBack**方法。</span><span class="sxs-lookup"><span data-stu-id="4935d-112">To navigate back one entry, you call the **GoBack** method.</span></span> <span data-ttu-id="4935d-113">下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="4935d-113">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="4935d-114">**CanGoForward**， **GoForward**， **CanGoBack**，和**GoBack**由實作<xref:System.Windows.Navigation.NavigationWindow>， <xref:System.Windows.Controls.Frame>，和<xref:System.Windows.Navigation.NavigationService>。</span><span class="sxs-lookup"><span data-stu-id="4935d-114">**CanGoForward**, **GoForward**, **CanGoBack**, and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4935d-115">如果您呼叫**GoForward**，向前巡覽記錄中沒有任何項目，或如果您呼叫**GoBack**，並向後巡覽記錄中沒有任何項目<xref:System.InvalidOperationException>就會擲回。</span><span class="sxs-lookup"><span data-stu-id="4935d-115">If you call **GoForward**, and there are no entries in forward navigation history, or if you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is thrown.</span></span>
