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
# <a name="how-to-determine-if-a-page-is-browser-hosted"></a>如何： 判斷頁面是否為瀏覽器裝載
這個範例示範如何判斷如果<xref:System.Windows.Controls.Page>裝載在瀏覽器中。  
  
## <a name="example"></a>範例  
 A<xref:System.Windows.Controls.Page>可以是主機無從驗證，因此，可以先載入到數種不同的主機，包括<xref:System.Windows.Controls.Frame>、 <xref:System.Windows.Navigation.NavigationWindow>，或瀏覽器。 這種情形時有程式庫組件，其中包含一個或多個頁面，而是由多個獨立的參考和可瀏覽 ([!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]) 裝載應用程式。  
  
 下列範例示範如何使用<xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType>判斷<xref:System.Windows.Controls.Page>裝載在瀏覽器中。  
  
 [!code-csharp[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/CSharp/Page1.xaml.cs#isbrowserhostedcode)]
 [!code-vb[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/visualbasic/page1.xaml.vb#isbrowserhostedcode)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.Frame>  
 <xref:System.Windows.Controls.Page>
