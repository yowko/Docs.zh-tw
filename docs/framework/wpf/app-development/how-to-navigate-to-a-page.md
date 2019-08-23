---
title: 作法：巡覽至頁面
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pages [WPF], navigating to
- navigation [WPF], to page
ms.assetid: 2a556fc0-748b-417f-a58a-0d05a7afb66f
ms.openlocfilehash: 38814268c9bb271ad3d88d549fb6ec4c6cbfed40
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966033"
---
# <a name="how-to-navigate-to-a-page"></a>作法：巡覽至頁面
這個範例說明可從<xref:System.Windows.Navigation.NavigationWindow>流覽至之頁面的數種方式。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Navigation.NavigationWindow>使用下列其中一種方式, 可以流覽至頁面:  
  
- <xref:System.Windows.Navigation.NavigationWindow.Source%2A> 屬性。  
  
- <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A> 方法  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatetopagecode)]
 [!code-vb[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatetopagecode)]  
  
> [!NOTE]
> [!INCLUDE[TLA#tla_uri#initcap#plural](../../../../includes/tlasharptla-urisharpinitcapsharpplural-md.md)]可以是 [相對] 或 [絕對]。 如需詳細資訊，請參閱 [WPF 中的 Pack URI](pack-uris-in-wpf.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.NavigationService>
