---
title: 如何： 向後巡覽瀏覽歷程記錄
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating back
- navigation [WPF], through navigation history (back)
ms.assetid: 9343234b-d864-441d-b8a7-d895cba80a87
ms.openlocfilehash: 9acbc5d3388a8df0ec7d7b5326f449f092f0cb03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546666"
---
# <a name="how-to-navigate-back-through-navigation-history"></a><span data-ttu-id="512dc-102">如何： 向後巡覽瀏覽歷程記錄</span><span class="sxs-lookup"><span data-stu-id="512dc-102">How to: Navigate Back Through Navigation History</span></span>
<span data-ttu-id="512dc-103">此範例說明如何瀏覽至項目在上一步瀏覽歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="512dc-103">This example illustrates how to navigate to entries in back navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="512dc-104">範例</span><span class="sxs-lookup"><span data-stu-id="512dc-104">Example</span></span>  
 <span data-ttu-id="512dc-105">從裝載中的內容中執行程式碼<xref:System.Windows.Navigation.NavigationWindow>，<xref:System.Windows.Controls.Frame>使用<xref:System.Windows.Navigation.NavigationService>，或[!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]可以向後巡覽瀏覽歷程記錄，一次的一個項目。</span><span class="sxs-lookup"><span data-stu-id="512dc-105">Code that is running from content that is hosted in a <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame> use <xref:System.Windows.Navigation.NavigationService>, or [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)] can navigate back through navigation history, one entry at a time.</span></span>  
  
 <span data-ttu-id="512dc-106">瀏覽回一個項目需要先檢查是否有項目向後巡覽記錄中藉由檢查**CanGoBack**屬性之前瀏覽回一個項目，藉由呼叫**GoBack**方法。</span><span class="sxs-lookup"><span data-stu-id="512dc-106">Navigating back one entry requires first checking that there are entries in back navigation history, by inspecting the **CanGoBack** property, before navigating back one entry, by calling the **GoBack** method.</span></span> <span data-ttu-id="512dc-107">下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="512dc-107">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="512dc-108">**CanGoBack**和**GoBack**由實作<xref:System.Windows.Navigation.NavigationWindow>， <xref:System.Windows.Controls.Frame>，和<xref:System.Windows.Navigation.NavigationService>。</span><span class="sxs-lookup"><span data-stu-id="512dc-108">**CanGoBack** and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="512dc-109">如果您呼叫**GoBack**，並向後巡覽記錄中沒有任何項目<xref:System.InvalidOperationException>，就會引發。</span><span class="sxs-lookup"><span data-stu-id="512dc-109">If you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is raised.</span></span>
