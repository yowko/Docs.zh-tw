---
title: HOW TO：判斷頁面是否由瀏覽器裝載
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosted pages in browser [WPF]
- pages [WPF], hosted in browser
ms.assetid: 737e0f26-8371-49b4-9579-70879e51e1aa
ms.openlocfilehash: d154de2f885101d1bd0c4613dfb1604be8acbe6a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "59978337"
---
# <a name="how-to-determine-if-a-page-is-browser-hosted"></a>HOW TO：判斷頁面是否由瀏覽器裝載
此範例示範如何判斷<xref:System.Windows.Controls.Page>裝載於瀏覽器。  
  
## <a name="example"></a>範例  
 A<xref:System.Windows.Controls.Page>可以是主機無從驗證，因此，可以載入數種不同的主機，包括<xref:System.Windows.Controls.Frame>、 <xref:System.Windows.Navigation.NavigationWindow>，或瀏覽器。 發生這種情況您有程式庫組件包含一或多個頁面，且這是由多個獨立部署所參考的和可瀏覽 ([!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]) 裝載應用程式。  
  
 下列範例示範如何使用<xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType>來判斷如果<xref:System.Windows.Controls.Page>裝載於瀏覽器。  
  
 [!code-csharp[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/CSharp/Page1.xaml.cs#isbrowserhostedcode)]
 [!code-vb[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/visualbasic/page1.xaml.vb#isbrowserhostedcode)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
