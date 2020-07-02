---
title: 如何：取得和設定主應用程式視窗
description: 請遵循此範例來取得並設定 Windows Presentation Foundation （WPF）應用程式內的主應用程式視窗。
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
ms.openlocfilehash: 9bb5bce9b90482796acd8c62e77dc8bd9a850eeb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622675"
---
# <a name="how-to-get-and-set-the-main-application-window"></a>如何：取得和設定主應用程式視窗
這個範例會示範如何取得和設定主應用程式視窗。  
  
## <a name="example"></a>範例  
 在 <xref:System.Windows.Window> Windows Presentation Foundation （WPF）應用程式中具現化的第一個會自動設定 <xref:System.Windows.Application> 為主應用程式視窗。 第一個 <xref:System.Windows.Window> 要具現化的可能是指定為啟動統一資源識別元（URI）的視窗（請參閱 <xref:System.Windows.Application.StartupUri%2A> ）。  
  
 第一個 <xref:System.Windows.Window> 也可以使用程式碼來具現化。 其中一個範例是在應用程式啟動期間開啟視窗，如下所示：  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 有時候，第一個具 <xref:System.Windows.Window> 現化的實際上並不是主應用程式視窗，例如啟動顯示畫面。 在此情況下，您可以使用標記來指定主應用程式視窗，如下所示：  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 無論是自動或手動指定主視窗，您都可以使用下列程式碼從取得主視窗 <xref:System.Windows.Application.MainWindow%2A> ，如下所示：  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
