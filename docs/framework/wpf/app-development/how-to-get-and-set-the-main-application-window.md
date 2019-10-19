---
title: 如何：取得和設定主應用程式視窗
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
ms.openlocfilehash: 5894761c4b6258cbf90d369a722ffc5abca51885
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582550"
---
# <a name="how-to-get-and-set-the-main-application-window"></a>如何：取得和設定主應用程式視窗
這個範例會示範如何取得和設定主應用程式視窗。  
  
## <a name="example"></a>範例  
 Windows Presentation Foundation （WPF）應用程式中具現化的第一個 <xref:System.Windows.Window> 會由 <xref:System.Windows.Application> 自動設定為主應用程式視窗。 第一個要具現化的 <xref:System.Windows.Window> 很可能是指定為啟動統一資源識別元（URI）的視窗（請參閱 <xref:System.Windows.Application.StartupUri%2A>）。  
  
 第一個 <xref:System.Windows.Window> 也可以使用程式碼來具現化。 其中一個範例是在應用程式啟動期間開啟視窗，如下所示：  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 有時候，第一個具現化的 <xref:System.Windows.Window> 實際上並不是主應用程式視窗，例如啟動顯示畫面。 在此情況下，您可以使用標記來指定主應用程式視窗，如下所示：  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 無論是自動或手動指定主視窗，您都可以使用下列程式碼從 <xref:System.Windows.Application.MainWindow%2A> 取得主視窗，如下所示：  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
