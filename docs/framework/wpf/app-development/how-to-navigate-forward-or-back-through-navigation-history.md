---
title: 作法：在瀏覽記錄中向前或向後巡覽
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating forward
- navigation [WPF], through navigation history (forward)
ms.assetid: 5939d574-5f53-469e-85f5-1f2b13607caa
ms.openlocfilehash: 76a78debdce14123cc465ac9abf4db906fe0a2df
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961357"
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a><span data-ttu-id="edf8d-102">作法：在瀏覽記錄中向前或向後巡覽</span><span class="sxs-lookup"><span data-stu-id="edf8d-102">How to: Navigate Forward or Back Through Navigation History</span></span>
<span data-ttu-id="edf8d-103">此範例說明如何向前或向後導覽至導覽歷程記錄中的專案。</span><span class="sxs-lookup"><span data-stu-id="edf8d-103">This example illustrates how to navigate forward or back to entries in navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="edf8d-104">範例</span><span class="sxs-lookup"><span data-stu-id="edf8d-104">Example</span></span>  
 <span data-ttu-id="edf8d-105">從下列主機中的內容執行的程式碼可以透過導覽歷程記錄 (一次一個專案) 來向前或向後導覽。</span><span class="sxs-lookup"><span data-stu-id="edf8d-105">Code that runs from content in the following hosts can navigate forward or back through navigation history, one entry at a time.</span></span>  
  
- <span data-ttu-id="edf8d-106"><xref:System.Windows.Navigation.NavigationWindow>用<xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="edf8d-106"><xref:System.Windows.Navigation.NavigationWindow> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
- <span data-ttu-id="edf8d-107"><xref:System.Windows.Controls.Frame>用<xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="edf8d-107"><xref:System.Windows.Controls.Frame> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
- <span data-ttu-id="edf8d-108">Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="edf8d-108">Internet Explorer</span></span>  
  
 <span data-ttu-id="edf8d-109">在向前導覽一個專案之前, 您必須先檢查**CanGoForward**屬性, 確認正嚮導覽歷程記錄中有專案。</span><span class="sxs-lookup"><span data-stu-id="edf8d-109">Before you can navigate forward one entry, you must first check that there are entries in forward navigation history by inspecting the **CanGoForward** property.</span></span> <span data-ttu-id="edf8d-110">若要向前流覽一個專案, 請呼叫**GoForward**方法。</span><span class="sxs-lookup"><span data-stu-id="edf8d-110">To navigate forward one entry, you call the **GoForward** method.</span></span> <span data-ttu-id="edf8d-111">如下列範例所示:</span><span class="sxs-lookup"><span data-stu-id="edf8d-111">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 <span data-ttu-id="edf8d-112">您必須先檢查**CanGoBack**屬性, 確認上一頁導覽歷程記錄中有專案, 才能導覽回一個專案。</span><span class="sxs-lookup"><span data-stu-id="edf8d-112">Before you can navigate back one entry, you must first check that there are entries in back navigation history by inspecting the **CanGoBack** property.</span></span> <span data-ttu-id="edf8d-113">若要流覽回一個專案, 請呼叫**GoBack**方法。</span><span class="sxs-lookup"><span data-stu-id="edf8d-113">To navigate back one entry, you call the **GoBack** method.</span></span> <span data-ttu-id="edf8d-114">如下列範例所示:</span><span class="sxs-lookup"><span data-stu-id="edf8d-114">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="edf8d-115">**CanGoForward**、 **GoForward**、 **CanGoBack**和**GoBack**是由<xref:System.Windows.Navigation.NavigationWindow>、 <xref:System.Windows.Controls.Frame>和<xref:System.Windows.Navigation.NavigationService>所執行。</span><span class="sxs-lookup"><span data-stu-id="edf8d-115">**CanGoForward**, **GoForward**, **CanGoBack**, and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="edf8d-116">如果您呼叫**GoForward**, 而且正嚮導覽歷程記錄中沒有任何專案, 或者如果您呼叫**GoBack**, 而且後端導覽歷程<xref:System.InvalidOperationException>記錄中沒有任何專案, 則會擲回。</span><span class="sxs-lookup"><span data-stu-id="edf8d-116">If you call **GoForward**, and there are no entries in forward navigation history, or if you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is thrown.</span></span>
