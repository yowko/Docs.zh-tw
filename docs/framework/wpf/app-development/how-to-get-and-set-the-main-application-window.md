---
title: HOW TO：取得及設定主應用程式視窗
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- windows objects [WPF], setting
- setting windows objects [WPF]
- windows objects [WPF], getting
- getting windows objects [WPF]
ms.assetid: ec902bc4-4a59-46f5-8ec1-963b46789356
ms.openlocfilehash: ea8333aa82f1159afb438215940ee1e7c2605e96
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373552"
---
# <a name="how-to-get-and-set-the-main-application-window"></a>HOW TO：取得及設定主應用程式視窗
此範例示範如何取得及設定主應用程式視窗。  
  
## <a name="example"></a>範例  
 第一個<xref:System.Windows.Window>的具現化在 Windows Presentation Foundation (WPF) 應用程式會由自動設定<xref:System.Windows.Application>與主應用程式視窗。 第一個<xref:System.Windows.Window>是具現化的會最有可能被指定為啟動視窗[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)](請參閱<xref:System.Windows.Application.StartupUri%2A>)。  
  
 第一個<xref:System.Windows.Window>可能也會使用具現化程式碼。 其中一個範例會開啟視窗的應用程式在啟動期間，如下所示：  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 某些情況下，第一個具現化<xref:System.Windows.Window>例如啟動顯示畫面是實際上並不是主應用程式視窗。 在此情況下，您可以指定主應用程式視窗中，使用標記，如下所示：  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 是否自動或手動指定主視窗，則您可以取得主視窗和<xref:System.Windows.Application.MainWindow%2A>使用下列程式碼，如下所示：  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
