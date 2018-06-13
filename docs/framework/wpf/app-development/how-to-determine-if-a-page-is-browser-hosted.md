---
title: 如何： 判斷頁面是否為瀏覽器裝載
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosted pages in browser [WPF]
- pages [WPF], hosted in browser
ms.assetid: 737e0f26-8371-49b4-9579-70879e51e1aa
ms.openlocfilehash: 6eb83429cb4f9dac5f3561b41997d24bcaa2c62f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545885"
---
# <a name="how-to-determine-if-a-page-is-browser-hosted"></a><span data-ttu-id="46ca5-102">如何： 判斷頁面是否為瀏覽器裝載</span><span class="sxs-lookup"><span data-stu-id="46ca5-102">How to: Determine If a Page is Browser Hosted</span></span>
<span data-ttu-id="46ca5-103">這個範例示範如何判斷如果<xref:System.Windows.Controls.Page>裝載在瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="46ca5-103">This example demonstrates how to determine if a <xref:System.Windows.Controls.Page> is hosted in a browser.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46ca5-104">範例</span><span class="sxs-lookup"><span data-stu-id="46ca5-104">Example</span></span>  
 <span data-ttu-id="46ca5-105">A<xref:System.Windows.Controls.Page>可以是主機無從驗證，因此，可以先載入到數種不同的主機，包括<xref:System.Windows.Controls.Frame>、 <xref:System.Windows.Navigation.NavigationWindow>，或瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="46ca5-105">A <xref:System.Windows.Controls.Page> can be host agnostic and, consequently, can be loaded into several different types of hosts, including a <xref:System.Windows.Controls.Frame>, a <xref:System.Windows.Navigation.NavigationWindow>, or a browser.</span></span> <span data-ttu-id="46ca5-106">這種情形時有程式庫組件，其中包含一個或多個頁面，而是由多個獨立的參考和可瀏覽 ([!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]) 裝載應用程式。</span><span class="sxs-lookup"><span data-stu-id="46ca5-106">This can happen when you have a library assembly that contains one or more pages, and which is referenced by multiple standalone and browsable ([!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]) host applications.</span></span>  
  
 <span data-ttu-id="46ca5-107">下列範例示範如何使用<xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType>判斷<xref:System.Windows.Controls.Page>裝載在瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="46ca5-107">The following example demonstrates how to use <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> to determine if a <xref:System.Windows.Controls.Page> is hosted in a browser.</span></span>  
  
 [!code-csharp[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/CSharp/Page1.xaml.cs#isbrowserhostedcode)]
 [!code-vb[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/visualbasic/page1.xaml.vb#isbrowserhostedcode)]  
  
## <a name="see-also"></a><span data-ttu-id="46ca5-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46ca5-108">See Also</span></span>  
 <xref:System.Windows.Controls.Frame>  
 <xref:System.Windows.Controls.Page>
