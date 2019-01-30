---
title: HOW TO：跨應用程式工作階段保存和還原應用程式範圍的屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application-scope properties [WPF], persisting
- persisting application-scope properties [WPF]
- properties [WPF], persisting
- restoring application-scope properties [WPF]
- properties [WPF], restoring
- application-scope properties [WPF], restoring
ms.assetid: 55d5904a-f444-4eb5-abd3-6bc74dd14226
ms.openlocfilehash: c64b13717a427bf7ad8f9cab0a450162ad0c6cde
ms.sourcegitcommit: e39d93d358974b9ed4541cedf4e25c0101015c3c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2019
ms.locfileid: "55204696"
---
# <a name="how-to-persist-and-restore-application-scope-properties-across-application-sessions"></a><span data-ttu-id="5ee89-102">HOW TO：跨應用程式工作階段保存和還原應用程式範圍的屬性</span><span class="sxs-lookup"><span data-stu-id="5ee89-102">How to: Persist and Restore Application-Scope Properties Across Application Sessions</span></span>
<span data-ttu-id="5ee89-103">此範例示範如何在應用程式關閉時，何時及如何還原應用程式範圍的屬性時的應用程式是下一步 啟動保存應用程式範圍的屬性。</span><span class="sxs-lookup"><span data-stu-id="5ee89-103">This example shows how to persist application-scope properties when an application shuts down, and how to restore application-scope properties when an application is next launch.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ee89-104">範例</span><span class="sxs-lookup"><span data-stu-id="5ee89-104">Example</span></span>  
 <span data-ttu-id="5ee89-105">應用程式持續發生，應用程式範圍的屬性，並將它們還原從隔離儲存區。</span><span class="sxs-lookup"><span data-stu-id="5ee89-105">The application persists application-scope properties to, and restores them from, isolated storage.</span></span> <span data-ttu-id="5ee89-106">隔離儲存區是沒有檔案存取權限的應用程式可以安全地使用受保護的儲存體區域。</span><span class="sxs-lookup"><span data-stu-id="5ee89-106">Isolated storage is a protected storage area that can safely be used by applications without file access permission.</span></span>  <span data-ttu-id="5ee89-107">*App.xaml*檔案會定義`App_Startup`做為處理常式方法<xref:System.Windows.Application.Startup?displayProperty=nameWithType>事件，而`App_Exit`做為處理常式方法<xref:System.Windows.Application.Exit?displayProperty=nameWithType>事件，醒目提示行的第一個範例所示。</span><span class="sxs-lookup"><span data-stu-id="5ee89-107">The *App.xaml* file defines the `App_Startup` method as the handler for the <xref:System.Windows.Application.Startup?displayProperty=nameWithType> event, and the `App_Exit` method as the handler for the  <xref:System.Windows.Application.Exit?displayProperty=nameWithType> event, as shown in the highlighted lines of the first example.</span></span> <span data-ttu-id="5ee89-108">第二個範例顯示的某一部分*App.xaml.cs*並*App.xaml.vb*會反白顯示的程式碼的檔案`App_Startup`方法，來還原應用程式範圍的屬性，以及`App_Exit`方法，將儲存應用程式範圍的屬性。</span><span class="sxs-lookup"><span data-stu-id="5ee89-108">The second example shows a portion of the *App.xaml.cs* and *App.xaml.vb* files that highlights the code for the `App_Startup` method, which restores application-scope properties, and the `App_Exit` method, which saves application-scope properties.</span></span>
 
  
 [!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]
  
 [!code-csharp[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=17-55)]
 [!code-vb[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb#persistrestoreappscopepropertiescodebehind1)]
 
