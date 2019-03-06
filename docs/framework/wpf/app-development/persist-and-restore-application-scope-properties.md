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
ms.openlocfilehash: 2ba3a31d1fe8efde436fd76f88ccfab2853df5ee
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377133"
---
# <a name="how-to-persist-and-restore-application-scope-properties-across-application-sessions"></a>HOW TO：跨應用程式工作階段保存和還原應用程式範圍的屬性
此範例示範如何在應用程式關閉時，何時及如何還原應用程式範圍的屬性時的應用程式是下一步 啟動保存應用程式範圍的屬性。  
  
## <a name="example"></a>範例  
 應用程式持續發生，應用程式範圍的屬性，並將它們還原從隔離儲存區。 隔離儲存區是沒有檔案存取權限的應用程式可以安全地使用受保護的儲存體區域。  *App.xaml*檔案會定義`App_Startup`做為處理常式方法<xref:System.Windows.Application.Startup?displayProperty=nameWithType>事件，而`App_Exit`做為處理常式方法<xref:System.Windows.Application.Exit?displayProperty=nameWithType>事件，醒目提示行的第一個範例所示。 第二個範例顯示的某一部分*App.xaml.cs*並*App.xaml.vb*會反白顯示的程式碼的檔案`App_Startup`方法，來還原應用程式範圍的屬性，以及`App_Exit`方法，將儲存應用程式範圍的屬性。
 
  
 [!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]
  
 [!code-csharp[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=17-55)]
 [!code-vb[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb#persistrestoreappscopepropertiescodebehind1)]
 
