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
# <a name="how-to-determine-if-a-page-is-browser-hosted"></a>如何：判斷頁面是否為瀏覽器主控
這個範例示範如何判斷 <xref:System.Windows.Controls.Page> 是否裝載于瀏覽器中。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Controls.Page> 可以是不可知的主機，因此可以載入數種不同類型的主機，包括 <xref:System.Windows.Controls.Frame>、<xref:System.Windows.Navigation.NavigationWindow>或瀏覽器。 當您的程式庫元件包含一或多個頁面，而且有多個獨立和可流覽（XAML 瀏覽器應用程式（XBAP））裝載應用程式時，就會發生這種情況。  
  
 下列範例示範如何使用 <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType> 來判斷 <xref:System.Windows.Controls.Page> 是否裝載于瀏覽器中。  
  
 [!code-csharp[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/CSharp/Page1.xaml.cs#isbrowserhostedcode)]
 [!code-vb[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/visualbasic/page1.xaml.vb#isbrowserhostedcode)]  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
