---
title: 如何： 取得和設定主應用程式視窗
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
ms.openlocfilehash: ae70b482eba8fb4e0bf587def06bb90d751a4312
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547978"
---
# <a name="how-to-get-and-set-the-main-application-window"></a><span data-ttu-id="f79fa-102">如何： 取得和設定主應用程式視窗</span><span class="sxs-lookup"><span data-stu-id="f79fa-102">How to: Get and Set the Main Application Window</span></span>
<span data-ttu-id="f79fa-103">這個範例示範如何取得及設定主應用程式視窗。</span><span class="sxs-lookup"><span data-stu-id="f79fa-103">This example shows how to get and set the main application window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f79fa-104">範例</span><span class="sxs-lookup"><span data-stu-id="f79fa-104">Example</span></span>  
 <span data-ttu-id="f79fa-105">第一個<xref:System.Windows.Window>，具現化在 Windows Presentation Foundation (WPF) 應用程式會自動設定由<xref:System.Windows.Application>與主應用程式視窗。</span><span class="sxs-lookup"><span data-stu-id="f79fa-105">The first <xref:System.Windows.Window> that is instantiated within a Windows Presentation Foundation (WPF) application is automatically set by <xref:System.Windows.Application> as the main application window.</span></span> <span data-ttu-id="f79fa-106">第一個<xref:System.Windows.Window>要具現化的會很有可能是指定為啟動視窗[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)](請參閱<xref:System.Windows.Application.StartupUri%2A>)。</span><span class="sxs-lookup"><span data-stu-id="f79fa-106">The first <xref:System.Windows.Window> to be instantiated will most likely be the window that is specified as the startup [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] (see <xref:System.Windows.Application.StartupUri%2A>).</span></span>  
  
 <span data-ttu-id="f79fa-107">第一個<xref:System.Windows.Window>可能也會使用具現化程式碼。</span><span class="sxs-lookup"><span data-stu-id="f79fa-107">The first <xref:System.Windows.Window> could also be instantiated using code.</span></span> <span data-ttu-id="f79fa-108">其中一個範例會開啟視窗的應用程式在啟動期間，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f79fa-108">One example is opening a window during application startup, like the following:</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 <span data-ttu-id="f79fa-109">某些情況下，第一個具現化<xref:System.Windows.Window>如啟動顯示畫面是實際上並不是主應用程式視窗。</span><span class="sxs-lookup"><span data-stu-id="f79fa-109">Sometimes, the first instantiated <xref:System.Windows.Window> is not actually the main application window e.g. a splash screen.</span></span> <span data-ttu-id="f79fa-110">在此情況下，您可以指定主應用程式視窗中，使用標記，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f79fa-110">In this case, you can specify the main application window using markup, like the following:</span></span>  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 <span data-ttu-id="f79fa-111">是否自動或手動指定主視窗，就可以從主視窗<xref:System.Windows.Application.MainWindow%2A>使用下列程式碼，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f79fa-111">Whether the main window is specified automatically or manually, you can get the main window from <xref:System.Windows.Application.MainWindow%2A> using the following code, like the following:</span></span>  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
