---
title: 如何： 停止無法載入頁面
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pages [WPF], stopping from loading
- methods [WPF], Stoploading
- events [WPF], NavigationStopped
- NavigationStopped properties [WPF]
- stopping pages from loading [WPF]
- loading [WPF], stopping
ms.assetid: e2b695b0-517e-462c-8ccf-90cc8d6ba864
ms.openlocfilehash: e5cd7d1b881b816636c3acdd4d33565304ca9b63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545541"
---
# <a name="how-to-stop-a-page-from-loading"></a>如何： 停止無法載入頁面
這個範例示範如何呼叫<xref:System.Windows.Navigation.NavigationWindow.StopLoading%2A>停止完成之前將它下載的瀏覽內容的方法。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Navigation.NavigationWindow.StopLoading%2A> 停止下載要求的內容，並會導致<xref:System.Windows.Navigation.NavigationWindow.NavigationStopped>會引發事件。  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateStopLoadingCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatestoploadingcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateStopLoadingCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatestoploadingcode)]
