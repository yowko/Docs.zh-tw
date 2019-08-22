---
title: 作法：跨應用程式工作階段保存和還原應用程式範圍的屬性
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
ms.openlocfilehash: d9c2dda2745e7528902b6b1c4f46d17264d1a8d8
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666720"
---
# <a name="how-to-persist-and-restore-application-scope-properties-across-application-sessions"></a>作法：跨應用程式工作階段保存和還原應用程式範圍的屬性
這個範例示範如何在應用程式關閉時保存應用程式範圍的屬性, 以及如何在下次啟動應用程式時還原應用程式範圍的屬性。  
  
## <a name="example"></a>範例  
 應用程式會將應用程式範圍的屬性保存至, 並從隔離儲存區進行還原。 隔離儲存區是受保護的儲存區域, 應用程式可以安全地使用它, 而不需要檔案存取權限。  *App.xaml*檔案`App_Startup`會將方法定義為<xref:System.Windows.Application.Startup?displayProperty=nameWithType>事件的處理常式, 並<xref:System.Windows.Application.Exit?displayProperty=nameWithType>將`App_Exit`方法定義為事件的處理常式, 如第一個範例的反白顯示行所示。 第二個範例會顯示*App.xaml.cs*和*app.xaml*檔案的一部分, 這些檔案會反白顯示`App_Startup`方法的程式碼, 這會還原應用程式範圍的屬性, 以及`App_Exit`可儲存應用程式範圍的方法。屬性.

 [!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]
  
 [!code-csharp[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=17-55)]
 [!code-vb[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb?highlight=14-45)]
