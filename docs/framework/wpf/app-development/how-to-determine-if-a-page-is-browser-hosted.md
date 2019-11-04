---
title: 如何：判斷頁面是否為瀏覽器主控
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosted pages in browser [WPF]
- pages [WPF], hosted in browser
ms.assetid: 737e0f26-8371-49b4-9579-70879e51e1aa
ms.openlocfilehash: c4cb1065807d16c1d1f5a95c8ac9c9cbe5a0fdab
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424695"
---
# <a name="how-to-determine-if-a-page-is-browser-hosted"></a><span data-ttu-id="18365-102">如何：判斷頁面是否為瀏覽器主控</span><span class="sxs-lookup"><span data-stu-id="18365-102">How to: Determine If a Page is Browser Hosted</span></span>
<span data-ttu-id="18365-103">這個範例示範如何判斷 <xref:System.Windows.Controls.Page> 是否裝載于瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="18365-103">This example demonstrates how to determine if a <xref:System.Windows.Controls.Page> is hosted in a browser.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18365-104">範例</span><span class="sxs-lookup"><span data-stu-id="18365-104">Example</span></span>  
 <span data-ttu-id="18365-105"><xref:System.Windows.Controls.Page> 可以是不可知的主機，因此可以載入數種不同類型的主機，包括 <xref:System.Windows.Controls.Frame>、<xref:System.Windows.Navigation.NavigationWindow>或瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="18365-105">A <xref:System.Windows.Controls.Page> can be host agnostic and, consequently, can be loaded into several different types of hosts, including a <xref:System.Windows.Controls.Frame>, a <xref:System.Windows.Navigation.NavigationWindow>, or a browser.</span></span> <span data-ttu-id="18365-106">當您的程式庫元件包含一或多個頁面，而且有多個獨立和可流覽（XAML 瀏覽器應用程式（XBAP））裝載應用程式時，就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="18365-106">This can happen when you have a library assembly that contains one or more pages, and which is referenced by multiple standalone and browsable (XAML browser application (XBAP)) host applications.</span></span>  
  
 <span data-ttu-id="18365-107">下列範例示範如何使用 <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> 來判斷 <xref:System.Windows.Controls.Page> 是否裝載于瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="18365-107">The following example demonstrates how to use <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> to determine if a <xref:System.Windows.Controls.Page> is hosted in a browser.</span></span>  
  
 [!code-csharp[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/CSharp/Page1.xaml.cs#isbrowserhostedcode)]
 [!code-vb[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/visualbasic/page1.xaml.vb#isbrowserhostedcode)]  
  
## <a name="see-also"></a><span data-ttu-id="18365-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="18365-108">See also</span></span>

- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
