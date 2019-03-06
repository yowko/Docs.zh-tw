---
title: HOW TO：停止載入頁面
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
ms.openlocfilehash: c5694bb2cb6c618cd84bad3dc893ae3855e44892
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357842"
---
# <a name="how-to-stop-a-page-from-loading"></a>HOW TO：停止載入頁面
此範例示範如何呼叫<xref:System.Windows.Navigation.NavigationWindow.StopLoading%2A>下載完成之前停止瀏覽至內容的方法。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Navigation.NavigationWindow.StopLoading%2A> 停止下載要求的內容，並造成<xref:System.Windows.Navigation.NavigationWindow.NavigationStopped>會引發事件。  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateStopLoadingCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatestoploadingcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateStopLoadingCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatestoploadingcode)]
